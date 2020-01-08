---
title: 'Konzepte: das Profilobjekt der Schutz-API'
description: In diesem Artikel werden die Konzepte des Profilobjekts für den Schutz erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: 45234963d7401107dca26a4c461e92818226465b
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75555227"
---
# <a name="microsoft-information-protection-sdk---protection-api-profile-concepts"></a>Microsoft Information Protection SDK: Konzepte für das Profil der Schutz-API

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

## <a name="load-a-profile"></a>Laden eines Profils

Da die Objekte `ProtectionProfileObserverImpl` und `AuthDelegateImpl` bereits definiert sind, können sie nun zum Instanziieren von `mip::ProtectionProfile` verwendet werden. Damit das `mip::ProtectionProfile`-Objekt erstellt werden kann, werden die [`mip::ProtectionProfile::Settings`](reference/class_mip_ProtectionProfile_settings.md)-Parameter benötigt.

### <a name="protectionprofilesettings-parameters"></a>ProtectionProfile::Settings-Parameter

- `std::shared_ptr<MipContext>`: das `mip::MipContext` Objekt, das zum Speichern von Anwendungsinformationen, Zustands Pfad usw. initialisiert wurde.
- `mip::CacheStorageType`: definiert, wie der Zustand gespeichert wird: im Arbeitsspeicher, auf dem Datenträger oder auf dem Datenträger und verschlüsselt.
- `std::shared_ptr<mip::AuthDelegate>`: ein gemeinsamer Zeiger der Klasse `mip::AuthDelegate`
- `std::shared_ptr<mip::ConsentDelegate>`: ein gemeinsam genutzter Zeiger der-Klasse [`mip::ConsentDelegate`](reference/class_mip_consentdelegate.md).
- `std::shared_ptr<mip::ProtectionProfile::Observer> observer`: ein frei gegebener Zeiger auf das Profil `Observer` Implementierung (in [`PolicyProfile`](reference/class_mip_policyprofile_observer.md), [`ProtectionProfile`](reference/class_mip_protectionprofile_observer.md)und [`FileProfile`](reference/class_mip_fileprofile_observer.md)).

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

#### <a name="store-state-in-memory-only"></a>Speichern der Status im Arbeitsspeicher (ausschließlich)

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

ProtectionProfile::Settings profileSettings(
    mipContext,                                        // mipContext object
    mip::CacheStorageType::InMemory,                   // use in memory storage
    authDelegateImpl,                                  // auth delegate object
    std::make_shared<ConsentDelegateImpl>(),           // new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>()); // new protection profile observer
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Einstellungen für das Profil mit Lese-/Schreibzugriff aus dem Speicherpfad auf dem Datenträger

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

ProtectionProfile::Settings profileSettings(
    mipContext,                                         // mipContext object
    mip::CacheStorageType::OnDisk,                      // use on disk storage
    authDelegateImpl,                                   // auth delegate object
    std::make_shared<ConsentDelegateImpl>(),            // new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>()); // new protection profile
```

Verwenden Sie als nächstes das Promise-Future-Muster, um das `ProtectionProfile` zu laden.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<ProtectionProfile>>>();
auto profileFuture = profilePromise->get_future();
ProtectionProfile::LoadAsync(profileSettings, profilePromise);
```

Wenn ein Profil geladen und dieser Vorgang erfolgreich durchgeführt wird, wird `ProtectionProfileObserverImpl::OnLoadSuccess`, also die Implementierung von `mip::ProtectionProfile::Observer::OnLoadSuccess`, aufgerufen. Das sich ergebende Objekt oder der Ausnahmezeiger sowie der Kontext werden an die Funktion als Parameter übergeben. Beim Kontext handelt es sich auf einen Zeiger auf das `std::promise`-Objekt, das Sie erstellt haben, um den asynchronen Vorgang zu verarbeiten. Die Funktion legt nur den Wert des Promise an das ProtectionProfile-Objekt fest (Kontext). Wenn die Hauptfunktion `Future.get()` verwendet, kann das Ergebnis in einem neuen Objekt gespeichert werden.

```cpp
//get the future value and store in profile.
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>Gesamtbild

Da Sie nun die Beobachter und den Authentifizierungsdelegaten vollständig implementiert haben, können Sie jetzt ein vollständiges Profil laden. In dem nachfolgenden Codeausschnitt wird davon ausgegangen, dass alle benötigten Header bereits eingebunden wurden.

```cpp
int main()
{
    const string userName = "MyTestUser@contoso.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";

    mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

    auto authDelegateImpl = std::make_shared<sample::auth::AuthDelegateImpl>(appInfo, userName, password);

    auto mipContext = mip::MipContext::Create(appInfo,
                        "mip_app_data",
                        mip::LogLevel::Trace,
                        nullptr /*loggerDelegateOverride*/,
                        nullptr /*telemetryOverride*/);

    ProtectionProfile::Settings profileSettings(
        mipContext,                                    // mipContext object
        mip::CacheStorageType::OnDisk,                 // use on disk storage
        authDelegateImpl,                              // auth delegate object
        std::make_shared<ConsentDelegateImpl>(),       // new consent delegate
        std::make_shared<ProfileObserver>());          // new protection profile observer

    auto profilePromise = std::make_shared<promise<shared_ptr<ProtectionProfile>>>();
    auto profileFuture = profilePromise->get_future();
    ProtectionProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Somit wurde das Profil vollständig geladen und im Objekt `profile` gespeichert.

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun das Profil hinzugefügt haben, können Sie in einem nächsten Schritt dem Profil eine Engine hinzuzufügen.

[Protection engine concepts (Konzepte der Schutz-Engine)](concept-profile-engine-protection-engine-cpp.md)
