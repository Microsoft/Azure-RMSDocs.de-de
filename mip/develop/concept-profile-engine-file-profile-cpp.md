---
title: 'Konzepte: Das Profile-Objekt der File-API'
description: In diesem Artikel werden die Konzepte des Profile-Objekts der File-API erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 33ec266068d15e827267b7d518344aebd0f8f072
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445902"
---
# <a name="microsoft-information-protection-sdk---file-api-profile-concepts"></a>Microsoft Information Protection SDK: Konzepte für das Profile-Objekt der File-API

Das Profil ist die Stammklasse für alle Vorgänge im MIP SDK. Vor der Verwendung einer der Funktionen der File-API muss ein `FileProfile` erstellt werden, und alle zukünftigen Operationen werden vom Profil oder von anderen Objekten ausgeführt, die dem Profil *hinzugefügt* wurden.

Es gibt einige Codevoraussetzungen, die erfüllt sein sollten, bevor versucht wird, ein Profil zu instanziieren:

- `AuthDelegateImpl` wird implementiert, um `mip::AuthDelegate` zu erweitern.
- `ConsentDelegateImpl` wird implementiert, um `mip::ConsentDelegate` zu erweitern.
- Die Anwendung wurde [in Azure Active Directory registriert](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad.md), und die Client-ID ist in der Anwendung oder den Konfigurationsdateien hartcodiert. 
- Eine Klasse, die von `mip::FileProfile::Observer` erbt, wurde ordnungsgemäß implementiert.

## <a name="load-a-profile"></a>Laden eines Profils

Nachdem die `ProfileObserver`-, `ConsentDelegateImpl`- und `AuthDelegateImpl`-Elemente definiert wurden,kann `mip::FileProfile` nun instanziiert werden. Für das Erstellen des `mip::FileProfile`-Objekts muss [`mip::FileProfile::Settings`](reference/class_mip_fileprofile_settings.md) alle Einstellungsinformationen zum `FileProfile` speichern.

### <a name="fileprofilesettings-parameters"></a>FileProfile::Settings Parameters

Der `FileProfile::Settings`-Konstruktor nimmt die unten aufgeführten fünf Parameter an:

- `std::string path`: Der Dateipfad, unter dem die Protokollierung, die Telemetriedaten und weitere persistente Zustände gespeichert sind.
- `bool useInMemoryStorage`: Definiert, ob alle Zustände im Arbeitsspeicher anstatt auf dem Datenträger gespeichert werden sollen.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Ein gemeinsamer Zeiger der Klasse `mip::AuthDelegate`. 
- `std::shared_ptr<mip::ConsentDelegate>`: 
- `std::shared_ptr<mip::FileProfile::Observer> observer`: Ein gemeinsamer Zeiger auf die `FileProfile::Observer`-Implementierung.
- `mip::ApplicationInfo applicationInfo`: Ein Objekt. Wird verwendet, um Informationen zu der Anwendung bereitzustellen, die das SDK nutzt.

Die folgenden Beispiele zeigen, wie das `profileSettings`-Objekt mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich im Arbeitsspeicher erstellt wird. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

#### <a name="store-state-in-memory-only"></a>Speichern der Zustands ausschließlich im Arbeitsspeicher

```cpp
FileProfile::Settings profileSettings(
    "",                                          //path to store settings
    true,                                        //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Einstellungen für das Profil mit Lese-/Schreibzugriff aus dem Speicherpfad auf dem Datenträger

Der folgende Codeausschnitt weist `FileProfile` an, alle Daten zum App-Zustand in `./mip_app_data` zu speichern.

```cpp
FileProfile::Settings profileSettings(
    "./mip_app_data",                            //path to store settings
    false,                                       //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="load-the-profile"></a>Laden des Profils

Verwenden Sie die Details eines der Ansätze oben, um nun das Promise-/Future-Muster zum Laden des `FileProfile` zu nutzen.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<FileProfile>>>();
auto profileFuture = profilePromise->get_future();
FileProfile::LoadAsync(profileSettings, profilePromise);
```

Wenn ein Profil geladen und dieser Vorgang erfolgreich durchgeführt wird, wird `ProfileObserver::OnLoadSuccess` (also die Implementierung von `mip::FileProfile::Observer::OnLoadSuccess`) aufgerufen. Das sich ergebende Objekt oder der Ausnahmezeiger sowie der Kontext werden an die Funktion als Parameter übergeben. Beim Kontext handelt es sich um einen Zeiger auf das `std::promise`-Objekt, das Sie erstellt haben, um den asynchronen Vorgang zu verarbeiten. Die Funktion legt schlichtweg den Wert der Zusage an das FileProfile-Objekt fest, das für den ersten Parameter übergeben wurde. Wenn die Hauptfunktion `Future.get()` verwendet, kann das Ergebnis in einem neuen Objekt gespeichert werden.

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
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    FileProfile::Settings profileSettings("",
            false,
            authDelegateImpl,
            std::make_shared<ConsentDelegateImpl>(),
            std::make_shared<ProfileObserver>(),
            mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<FileProfile>>>();
    auto profileFuture = profilePromise->get_future();
    FileProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Somit wurde das Profil vollständig geladen und im `profile`-Objekt gespeichert.

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun das Profil hinzugefügt haben, können Sie in einem nächsten Schritt dem Profil eine Engine hinzuzufügen. 

- [Konzepte der Dateiengine](concept-profile-engine-file-engine-cpp.md)