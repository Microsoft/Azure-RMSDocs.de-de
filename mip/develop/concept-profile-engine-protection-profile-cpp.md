---
title: 'Konzepte: das Profilobjekt der Schutz-API'
description: In diesem Artikel werden die Konzepte des Profilobjekts für den Schutz erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: ae6699212d45a6c8a2fa95f648e7f5a2be3de93e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445307"
---
# <a name="microsoft-information-protection-sdk---protection-api-profile-concepts"></a>Microsoft Information Protection SDK: Konzepte für das Profil der Schutz-API

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

## <a name="load-a-profile"></a>Laden eines Profils

Da die Objekte `ProtectionProfileObserverImpl` und `AuthDelegateImpl` bereits definiert sind, können sie nun zum Instanziieren von `mip::ProtectionProfile` verwendet werden. Damit das `mip::ProtectionProfile`-Objekt erstellt werden kann, werden die [`mip::ProtectionProfile::Settings`](reference/class_mip_ProtectionProfile_settings.md)-Parameter benötigt.

### <a name="protectionprofilesettings-parameters"></a>ProtectionProfile::Settings-Parameter

- `std::string path`: Pfad, in dem Protokollierung, Telemetriedaten und weitere persistente Status zum Schutz gespeichert sind
- `bool useInMemoryStorage`: definiert, ob alle Status im Arbeitsspeicher anstatt auf dem Datenträger gespeichert werden sollen
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: ein gemeinsamer Zeiger der Klasse `mip::AuthDelegate`
- `std::shared_ptr<mip::ProtectionProfile::Observer> observer`: ein gemeinsamer Zeiger auf die `ProtectionProfile::Observer`-Implementierung
- `mip::ApplicationInfo applicationInfo`: Objekt Wird verwendet, um Informationen zur Anwendung bereitzustellen, die das SDK nutzt

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

#### <a name="store-state-in-memory-only"></a>Speichern der Status im Arbeitsspeicher (ausschließlich)

```cpp
ProtectionProfile::Settings profileSettings(
    "",                                     //path to store settings
    true,                                   //useInMemoryStorage
    authDelegateImpl,                       //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),//new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Einstellungen für das Profil mit Lese-/Schreibzugriff aus dem Speicherpfad auf dem Datenträger

```cpp
ProtectionProfile::Settings profileSettings(
    "./mip_app_data",                       //path to store settings
    false,                                  //useInMemoryStorage
    authDelegateImpl,                       //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),//new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>(), //new protection profile
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

Verwenden Sie als nächstes das Promise-Future-Muster, um das `ProtectionProfile` zu laden.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<ProtectionProfile>>>();
auto profileFuture = profilePromise->get_future();
ProtectionProfile::LoadAsync(profileSettings, profilePromise);
```

Wenn ein Profil geladen und dieser Vorgang erfolgreich durchgeführt wird, wird `ProtectionProfileObserverImpl::OnLoadSuccess`, also die Implementierung von `mip::ProtectionProfile::Observer::OnLoadSuccess`, aufgerufen. Das daraus entstandene Objekt oder der Ausnahmezeiger sowie der Kontext werden der Funktion als Parameter übergeben. Beim Kontext handelt es sich auf einen Zeiger auf das `std::promise`-Objekt, das Sie erstellt haben, um den asynchronen Vorgang zu verarbeiten. Die Funktion legt nur den Wert des Promise an das ProtectionProfile-Objekt fest (Kontext). Wenn die Hauptfunktion `Future.get()` verwendet, kann das Ergebnis in einem neuen Objekt gespeichert werden.

```cpp
//get the future value and store in profile.
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>Gesamtbild

Da Sie nun die Beobachter und den Authentifizierungsdelegaten vollständig implementiert haben, können Sie jetzt ein vollständiges Profil laden. In dem nachfolgenden Codeausschnitt wird davon ausgegangen, dass alle benötigten Header bereits hinzugefügt wurden.

```cpp
int main()
{
    const string userName = "MyTestUser@contoso.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    ProtectionProfile::Settings profileSettings("",
        false,
        authDelegateImpl,
        std::make_shared<ConsentDelegateImpl>(),
        std::make_shared<ProfileObserver>(),
        mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

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