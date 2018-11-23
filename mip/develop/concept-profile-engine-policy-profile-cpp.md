---
title: 'Konzepte: das Profilobjekt der Richtlinien-API'
description: In diesem Artikel werden die Konzepte des Profilobjekts für die Richtlinie erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b229148c3028f4478f83cbbc928e19666c2f44b5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445426"
---
# <a name="microsoft-information-protection-sdk---policy-api-profile-concepts"></a>Microsoft Information Protection SDK: Konzepte für das Profil der Richtlinien-API

Bevor Vorgänge ausgeführt werden können, die die Richtlinien-API betreffen, muss `mip::Profile` geladen werden.

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

## <a name="load-a-profile"></a>Laden eines Profils

Da die Objekte `ProfileObserver` und `AuthDelegateImpl` bereits definiert sind, können sie nun zum Instanziieren von `mip::PolicyProfile` verwendet werden. Damit das `mip::PolicyProfile`-Objekt erstellt werden kann, werden die [`mip::PolicyProfile::Settings`](reference/class_mip_PolicyProfile_settings.md)-Parameter benötigt.

### <a name="profilesettings-parameters"></a>Profile::Settings-Parameter

- `std::string path`: Pfad, in dem Protokollierung, Telemetriedaten und weitere persistente Status zum Schutz gespeichert sind
- `bool useInMemoryStorage`: definiert, ob alle Status im Arbeitsspeicher anstatt auf dem Datenträger gespeichert werden sollen
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: ein gemeinsamer Zeiger der Klasse `mip::AuthDelegate` 
- `std::shared_ptr<mip::PolicyProfile::Observer> observer`: ein gemeinsamer Zeiger auf die `PolicyProfile::Observer`-Implementierung
- `mip::ApplicationInfo applicationInfo`: Objekt. Wird verwendet, um Informationen zur Anwendung bereitzustellen, die das SDK nutzt

Anhand der beiden nachfolgenden Beispiele sehen Sie, wie Sie mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich für den Arbeitsspeicher das profileSettings-Objekt erstellen können. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

#### <a name="store-state-in-memory-only"></a>Speichern der Status im Arbeitsspeicher (ausschließlich)

```cpp
Profile::Settings profileSettings("",
    true,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Einstellungen für das Profil mit Lese-/Schreibzugriff aus dem Speicherpfad auf dem Datenträger

```cpp
Profile::Settings profileSettings("./mip_app_data",
    false,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
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

Da Sie nun die Beobachter und den Authentifizierungsdelegaten vollständig implementiert haben, können Sie jetzt ein vollständiges Profil laden. In dem nachfolgenden Codeausschnitt wird davon ausgegangen, dass alle benötigten Header bereits hinzugefügt wurden.

```cpp
int main()
{
    const string userName = "MyTestUser@consoto.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    Profile::Settings profileSettings("", false, authDelegateImpl, std::make_shared<ProfileObserver>(), mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<Profile>>>();
    auto profileFuture = profilePromise->get_future();
    Profile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Somit wurde das Profil vollständig geladen und im Objekt `profile` gespeichert.

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun das Profil hinzugefügt haben, können Sie in einem nächsten Schritt dem Profil eine Engine hinzuzufügen.

[Konzepte der Richtlinien-Engine](concept-profile-engine-policy-engine-cpp.md)