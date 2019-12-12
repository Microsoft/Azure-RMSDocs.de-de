---
title: 'Konzepte: das Profilobjekt der Richtlinien-API'
description: In diesem Artikel werden die Konzepte des Profilobjekts für die Richtlinie erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 9b3b32464cae35560c74a05b28506ca60dc963d2
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "69886053"
---
# <a name="microsoft-information-protection-sdk---policy-api-profile-concepts"></a>Microsoft Information Protection SDK: Konzepte für das Profil der Richtlinien-API

Bevor Vorgänge ausgeführt werden können, die die Richtlinien-API betreffen, muss `mip::Profile` geladen werden.

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

## <a name="load-a-profile"></a>Laden eines Profils

Nun, da die `MipContext`, `ProfileObserver`und `AuthDelegateImpl` definiert sind, verwenden wir diese, um `mip::PolicyProfile`zu instanziieren. Zum Erstellen des `mip::PolicyProfile` Objekts sind [`mip::PolicyProfile::Settings`](reference/class_mip_PolicyProfile_settings.md) und `mip::MipContext`erforderlich.

### <a name="profilesettings-parameters"></a>Profile::Settings-Parameter

Der `PolicyProfile::Settings`-Konstruktor akzeptiert vier Parameter, die unten aufgeführt sind:

- `const std::shared_ptr<MipContext>`: das `mip::MipContext` Objekt, das zum Speichern von Anwendungsinformationen, Zustands Pfad usw. initialisiert wurde.
- `mip::CacheStorageType`: definiert, wie der Zustand gespeichert wird: im Arbeitsspeicher, auf dem Datenträger oder auf dem Datenträger und verschlüsselt. Weitere Informationen finden Sie in den [Konzepten des Cache Speichers](concept-cache-storage.md).
- `std::shared_ptr<mip::AuthDelegate>`: Ein gemeinsamer Zeiger der Klasse `mip::AuthDelegate`.
- `std::shared_ptr<mip::PolicyProfile::Observer> observer`: ein frei gegebener Zeiger auf das Profil `Observer` Implementierung (in [`PolicyProfile`](reference/class_mip_policyprofile_observer.md), [`ProtectionProfile`](reference/class_mip_protectionprofile_observer.md)und [`FileProfile`](reference/class_mip_fileprofile_observer.md)).

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

#### <a name="store-state-in-memory-only"></a>Speichern der Status im Arbeitsspeicher (ausschließlich)

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

PolicyProfile::Settings profileSettings(
    mipContext,                                   // mipContext object
    mip::CacheStorageType::InMemory,              // use in memory storage
    authDelegateImpl,                             // auth delegate object
    std::make_shared<PolicyProfileObserverImpl>()); // new protection profile observer
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Einstellungen für das Profil mit Lese-/Schreibzugriff aus dem Speicherpfad auf dem Datenträger

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

PolicyProfile::Settings profileSettings(
    mipContext,                                    // mipContext object
    mip::CacheStorageType::OnDisk,                 // use on disk storage
    authDelegateImpl,                              // auth delegate object
    std::make_shared<PolicyProfileObserverImpl>());  // new protection profile observer
```

Verwenden Sie als nächstes das Promise-Future-Muster, um das `Profile` zu laden.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<Profile>>>();
auto profileFuture = profilePromise->get_future();
Profile::LoadAsync(profileSettings, profilePromise);
```

Wenn ein Profil erfolgreich geladen wird (`ProfileObserver::OnLoadSuccess`), wird die Implementierung von `mip::Profile::Observer::OnLoadSuccess` benachrichtigt. Das daraus entstandene Objekt (in diesem Fall ein `mip::Profile`-Objekt) sowie der Kontext werden der Observer-Funktion als Parameter übergeben.

Beim *context* handelt es sich auf einen Zeiger auf das `std::promise`-Objekt, das Sie erstellt haben, um den asynchronen Vorgang zu verarbeiten. Die Funktion legt schlichtweg den Wert des Promise an das Profile-Objekt fest, das für den ersten Parameter übergeben wurde. Wenn die Hauptfunktion `Future.get()` verwendet, kann das Ergebnis in einem neuen Objekt im aufrufenden Thread gespeichert werden.

```cpp
//get the future value and store in profile.
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>Gesamtbild

Da Sie nun die Beobachter und den Authentifizierungsdelegaten vollständig implementiert haben, können Sie jetzt ein vollständiges Profil laden. In dem nachfolgenden Codeausschnitt wird davon ausgegangen, dass alle benötigten Header bereits eingebunden wurden.

```cpp
int main()
{
    const string userName = "MyTestUser@consoto.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";

    mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

    auto authDelegateImpl = std::make_shared<sample::auth::AuthDelegateImpl>(appInfo, userName, password);

    auto mipContext = mip::MipContext::Create(appInfo,
                        "mip_app_data",
                        mip::LogLevel::Trace,
                        nullptr /*loggerDelegateOverride*/,
                        nullptr /*telemetryOverride*/);

    PolicyProfile::Settings profileSettings(
        mipContext,                                    // mipContext object
        mip::CacheStorageType::OnDisk,                 // use on disk storage
        authDelegateImpl,                              // auth delegate object
        std::make_shared<PolicyProfileObserverImpl>());  // new protection profile observer

    auto profilePromise = std::make_shared<promise<shared_ptr<PolicyProfile>>>();
    auto profileFuture = profilePromise->get_future();
    Profile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Somit wurde das Profil vollständig geladen und im Objekt `profile` gespeichert.

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun das Profil hinzugefügt haben, können Sie in einem nächsten Schritt dem Profil eine Engine hinzuzufügen.

[Konzepte der Richtlinien-Engine](concept-profile-engine-policy-engine-cpp.md)
