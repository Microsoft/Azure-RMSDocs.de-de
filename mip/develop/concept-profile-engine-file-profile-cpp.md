---
title: 'Konzepte: Das Profile-Objekt der File-API'
description: In diesem Artikel werden die Konzepte des Profile-Objekts der File-API erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 5534cf804422de2d02a53e8c21ceae77af52691d
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69886089"
---
# <a name="microsoft-information-protection-sdk---file-api-profile-concepts"></a>Microsoft Information Protection SDK: Konzepte für das Profile-Objekt der File-API

Das Profil ist die Stammklasse für alle Vorgänge im MIP SDK. Vor der Verwendung einer der Funktionen der File-API muss ein `FileProfile` erstellt werden, und alle zukünftigen Operationen werden vom Profil oder von anderen Objekten ausgeführt, die dem Profil *hinzugefügt* wurden.

Es gibt einige Codevoraussetzungen, die erfüllt sein sollten, bevor versucht wird, ein Profil zu instanziieren:

- `MipContext`wurde erstellt und in einem-Objekt gespeichert, auf das `mip::FileProfile` das-Objekt zugreifen kann.
- `AuthDelegateImpl`implementiert `mip::AuthDelegate`.
- `ConsentDelegateImpl`implementiert `mip::ConsentDelegate`.
- Die Anwendung wurde [in Azure Active Directory registriert](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad.md), und die Client-ID ist in der Anwendung oder den Konfigurationsdateien hartcodiert.
- Eine Klasse, die von `mip::FileProfile::Observer` erbt, wurde ordnungsgemäß implementiert.

## <a name="load-a-profile"></a>Laden eines Profils

Nachdem die `ProfileObserver`-, `ConsentDelegateImpl`- und `AuthDelegateImpl`-Elemente definiert wurden,kann `mip::FileProfile` nun instanziiert werden. Zum Erstellen `mip::FileProfile` des-`mip::MipContext` [`mip::FileProfile::Settings`](reference/class_mip_fileprofile_settings.md) Objekts ist [] erforderlich, damit alle Einstellungs Informationen über die `FileProfile`gespeichert werden können.

### <a name="fileprofilesettings-parameters"></a>FileProfile::Settings Parameters

Der `FileProfile::Settings`-Konstruktor nimmt die unten aufgeführten fünf Parameter an:

- `std::shared_ptr<MipContext>`: Das `mip::MipContext` Objekt, das zum Speichern von Anwendungsinformationen, Zustands Pfad usw. initialisiert wurde.
- `mip::CacheStorageType`: Definiert, wie der Zustand gespeichert wird: Im Arbeitsspeicher, auf dem Datenträger oder auf dem Datenträger gespeichert und verschlüsselt.
- `std::shared_ptr<mip::AuthDelegate>`: Ein frei gegebener Zeiger der `mip::AuthDelegate`-Klasse.
- `std::shared_ptr<mip::ConsentDelegate>`: Ein frei gegebener Zeiger der [`mip::ConsentDelegate`](reference/class_mip_consentdelegate.md)-Klasse.
- `std::shared_ptr<mip::FileProfile::Observer> observer`: Ein frei gegebener Zeiger auf die `Observer` Profil Implementierung ( [`PolicyProfile`](reference/class_mip_policyprofile_observer.md)in [`ProtectionProfile`](reference/class_mip_protectionprofile_observer.md), und [`FileProfile`](reference/class_mip_fileprofile_observer.md)).

Die folgenden Beispiele zeigen, wie das `profileSettings`-Objekt mithilfe des lokalen Speichers für den Zustandsspeicher oder ausschließlich im Arbeitsspeicher erstellt wird. Es wird in beiden Beispielen davon ausgegangen, dass das `authDelegateImpl`-Objekt bereits erstellt wurde.

#### <a name="store-state-in-memory-only"></a>Speichern der Status im Arbeitsspeicher (ausschließlich)

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

FileProfile::Settings profileSettings(
    mipContext,                                   // mipContext object
    mip::CacheStorageType::InMemory,              // use in memory storage
    authDelegateImpl,                             // auth delegate object
    std::make_shared<ConsentDelegateImpl>(),      // new consent delegate
    std::make_shared<FileProfileObserverImpl>()); // new protection profile observer
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Einstellungen für das Profil mit Lese-/Schreibzugriff aus dem Speicherpfad auf dem Datenträger

Der folgende Codeausschnitt weist `FileProfile` an, alle Daten zum App-Zustand in `./mip_app_data` zu speichern.

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

FileProfile::Settings profileSettings(
    mipContext,                                    // mipContext object
    mip::CacheStorageType::OnDisk,                 // use on disk storage
    authDelegateImpl,                              // auth delegate object
    std::make_shared<ConsentDelegateImpl>(),       // new consent delegate
    std::make_shared<FileProfileObserverImpl>());  // new protection profile observer
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

    FileProfile::Settings profileSettings(
        mipContext,                                    // mipContext object
        mip::CacheStorageType::OnDisk,                 // use on disk storage
        authDelegateImpl,                              // auth delegate object
        std::make_shared<ConsentDelegateImpl>(),       // new consent delegate
        std::make_shared<FileProfileObserverImpl>());  // new file profile observer

        auto profilePromise = std::make_shared<promise<shared_ptr<FileProfile>>>();
        auto profileFuture = profilePromise->get_future();
        FileProfile::LoadAsync(profileSettings, profilePromise);
        auto profile = profileFuture.get();
}
```

Somit wurde das Profil vollständig geladen und im Objekt `profile` gespeichert.

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun das Profil hinzugefügt haben, können Sie in einem nächsten Schritt dem Profil eine Engine hinzuzufügen. 

- [Konzepte der Dateiengine](concept-profile-engine-file-engine-cpp.md)
