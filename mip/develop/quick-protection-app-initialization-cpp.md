---
title: 'Schnellstart: Initialisierung von Clients (C++) für das Microsoft Information Protection (MIP) SDK'
description: Ein Schnellstart zum Schreiben der Initialisierungslogik für Clientanwendungen eines Microsoft Information Protection (MIP) SDK.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 03/30/2020
ms.author: v-anikep
ms.openlocfilehash: e0f77c27c38b8b2f1baf4385efce1ee7336c8f9d
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81766387"
---
# <a name="quickstart-client-application-initialization-for-protection-apis-c"></a>Schnellstart: Initialisierung der Clientanwendung für Schutz-APIs (C++)

In diesem Schnellstart lernen Sie, wie Sie das Muster für die Clientinitialisierung implementieren können, das zur Laufzeit des Microsoft Information Protection (MIP) SDK für C++ verwendet wird.

> [!NOTE]
> Die in diesem Schnellstart beschriebenen Schritte müssen für sämtliche Clientanwendungen ausgeführt werden, die MIP-Schutz-APIs verwenden. Diese Schnellstarts müssen nach der Anwendungsinitialisierung und der Implementierung von Klassen für Authentifizierungsdelegate und Zustimmungsdelegate nacheinander ausgeführt werden.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie Folgendes sicher, sofern dies noch nicht geschehen ist:

- Führen Sie die Schritte unter [Microsoft Information Protection (MIP) SDK: Setup und Konfiguration](setup-configure-mip.md) aus. Dieser Schnellstart „Initialisierung der Clientanwendung“ hat das ordnungsgemäße Setup und die ordnungsgemäße Konfiguration des SDK zum Thema.
- Optional:
  - Überprüfen Sie [Profil- und Engine-Objekte](concept-profile-engine-cpp.md). Bei den Objekten für Profil und Engine handelt es sich um universelle Konzepte, die von Clients benötigt werden, die die MIP-Datei-/Richtlinien-/Schutz-APIs verwenden.
  - Überprüfen Sie [Authentifizierungskonzepte](concept-authentication-cpp.md), um zu erfahren, wie die Authentifizierung und die Zustimmung von der SDK- und der Clientanwendung implementiert werden.
  - Überprüfen Sie [Observer-Konzepte](concept-async-observers.md), um mehr über Observer und ihre Implementierung zu erfahren. Das MSIP SDK nutzt mithilfe des Observer-Musters asynchrone Ereignisbenachrichtigungen.

## <a name="create-a-visual-studio-solution-and-project"></a>Erstellen einer Visual Studio-Lösung und eines -Projekts

Zunächst erstellen und konfigurieren Sie die erste Projektmappe und das erste Projekt in Visual Studio. Dies bildet die Grundlage für die anderen Schnellstarts.

1. Öffnen Sie Visual Studio 2017, wählen Sie das Menü **Datei** und anschließend **Neu** > **Projekt** aus. Geben Sie im Dialogfeld **Neues Projekt** Folgendes ein:
   - Wählen Sie im linken Bereich unter **Installiert** > **Andere Sprachen** den Eintrag **Visual C++** aus.
   - Wählen Sie im mittleren Bereich **Windows Console Application** (Windows-Konsolenanwendung) aus.
   - Aktualisieren Sie im unteren Bereich das Projekt **Name** > **Speicherort** und entsprechend den darin enthaltenen **Projektmappennamen**.
   - Wenn Sie fertig sind, klicken Sie in der unteren rechten Ecke auf die Schaltfläche **OK**.

     [![Erstellen der Visual Studio-Projektmappe](media/quick-app-initialization-cpp/create-vs-solution.png)](media/quick-app-initialization-cpp/create-vs-solution.png#lightbox)

2. Fügen Sie Ihrem Projekt das Nuget-Paket für die MIP SDK-Schutz-API hinzu:
   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten (direkt unter dem obersten Knoten bzw. dem Projektmappenknoten), und wählen Sie **NuGet-Pakete verwalten...** aus:
   - Gehen Sie wie folgt vor, wenn im Bereich „Editor-Gruppe“ die Registerkarte **NuGet-Paket-Manager** geöffnet wird:
     - Wählen Sie **Durchsuchen** aus.
     - Geben Sie „Microsoft.InformationProtection“ in das Suchfeld ein.
     - Wählen Sie das Paket „Microsoft.InformationProtection.Protection“ aus.
     - Klicken Sie auf „Installieren“ und anschließend auf „OK“, wenn das Bestätigungsdialogfeld **Vorschau der Änderungen** angezeigt wird.

     [![NuGet-Paket in Visual Studio hinzufügen](media/quick-app-initialization-cpp/add-nuget-package.png)](media/quick-app-initialization-cpp/add-nuget-package.png#lightbox)

## <a name="implement-observer-classes-to-monitor-the-protection-profile-and-engine-objects"></a>Implementieren von Observer-Klassen zum Überwachen der Objekte für Schutzprofil und -Engine

Jetzt erstellen Sie eine grundlegende Implementierung für eine Observer-Klasse des Schutzprofils, indem Sie die Klasse `mip::ProtectionProfile::Observer` des SDK erweitern. Der Observer wird später instanziiert und verwendet, um den Ladevorgang des Schutzprofilobjekts zu überwachen und das Engine-Objekt zum Profil hinzuzufügen.

1. Fügen Sie eine neue Klasse zu Ihrem Projekt hinzu, durch die die Dateien „header/.h“ und „implementation/.cpp“ für Sie generiert werden:

   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Hinzufügen** > **Klasse** aus.
   - Gehen Sie im Dialogfeld **Klasse hinzufügen** folgendermaßen vor:
     - Geben Sie im Feld **Klassenname** „profile_observer“ ein. Beachten Sie, dass sowohl das Feld **H-Datei** als auch das Feld **CPP-Datei** anhand des eingegebenen Namens automatisch aufgefüllt werden.
     - Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK**.

     [![Klasse in Visual Studio hinzufügen](media/quick-app-initialization-cpp/add-class.png)](media/quick-app-initialization-cpp/add-class.png#lightbox)

2. Nach dem Generieren der H- und der CPP-Datei für die Klasse werden beide Dateien in Editor-Gruppenregisterkarten geöffnet. Aktualisieren Sie jetzt jede Datei, um Ihre neue Observer-Klasse zu implementieren:

   - Aktualisieren Sie „profile_observer.h“, indem Sie die generierte Klasse `profile_observer` auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include <memory>
     #include "mip/protection/protection_profile.h"
     using std::exception_ptr;
     using std::shared_ptr;


     class ProtectionProfileObserver final : public mip::ProtectionProfile::Observer {
     public:
          ProtectionProfileObserver() { }
          void OnLoadSuccess(const std::shared_ptr<mip::ProtectionProfile>& profile, const std::shared_ptr<void>& context) override;
          void OnLoadFailure(const std::exception_ptr& Failure, const std::shared_ptr<void>& context) override;
          void OnAddEngineSuccess(const std::shared_ptr<mip::ProtectionEngine>& engine, const std::shared_ptr<void>& context) override;
          void OnAddEngineFailure(const std::exception_ptr& Failure, const std::shared_ptr<void>& context) override;
     };
     ```

   - Aktualisieren Sie „profile_observer.cpp“, indem Sie die Implementierung der generierten Klasse `profile_observer` auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include <future>

     using std::promise;
     using std::shared_ptr;
     using std::static_pointer_cast;
     using mip::ProtectionEngine;
     using mip::ProtectionProfile;

     void ProtectionProfileObserver::OnLoadSuccess(const shared_ptr<ProtectionProfile>& profile, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<ProtectionProfile>>>(context);
          promise->set_value(profile);
     }

     void ProtectionProfileObserver::OnLoadFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<ProtectionProfile>>>(context);
          promise->set_exception(error);
     }

     void ProtectionProfileObserver::OnAddEngineSuccess(const shared_ptr<ProtectionEngine>& engine, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<ProtectionEngine>>>(context);
          promise->set_value(engine);
     }

     void ProtectionProfileObserver::OnAddEngineFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<ProtectionEngine>>>(context);
          promise->set_exception(error);
     }
     ```

3. Fügen Sie Ihrem Projekt gemäß den Schritten unter 1. eine neue Klasse für die Schutz-Engine-Beobachtung – „engine_observer“ – hinzu, durch die die Dateien „header/.h“ und „implementation/.cpp“ für Sie generiert werden.

4. Nach dem Generieren der H- und der CPP-Datei für die Klasse werden beide Dateien in Editor-Gruppenregisterkarten geöffnet. Aktualisieren Sie jetzt jede Datei, um Ihre neue Observer-Klasse zu implementieren:

   - Aktualisieren Sie „engine_observer.h“, indem Sie die generierte Klasse `engine_observer` auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include <memory>
     #include "mip/protection/protection_engine.h"
     using std::vector;
     using std::exception_ptr;
     using std::shared_ptr;

     class ProtectionEngineObserver final : public mip::ProtectionEngine::Observer {
       public:
       ProtectionEngineObserver() {}
       void OnGetTemplatesSuccess(const vector<std::shared_ptr<mip::TemplateDescriptor>>& templateDescriptors, const shared_ptr<void>& context) override;
       void OnGetTemplatesFailure(const exception_ptr& Failure, const shared_ptr<void>& context) override;

     };
     ```

   - Aktualisieren Sie „engine_observer.cpp“, indem Sie die Implementierung der generierten Klasse `engine_observer` auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include "mip/protection/protection_profile.h"
     #include "engine_observer.h"

     using std::promise;
     void ProtectionEngineObserver::OnGetTemplatesSuccess(const vector<shared_ptr<mip::TemplateDescriptor>>& templateDescriptors,const shared_ptr<void>& context) {
         auto loadPromise = static_cast<promise<vector<shared_ptr<mip::TemplateDescriptor>>>*>(context.get());
         loadPromise->set_value(templateDescriptors);
       };

       void ProtectionEngineObserver::OnGetTemplatesFailure(const exception_ptr& Failure, const shared_ptr<void>& context) {
         auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
         loadPromise->set_exception(Failure);
       };
     ```

5. Verwenden Sie optional STRG+UMSCHALT+B (**Projektmappe erstellen**), um eine Testkompilierung/-verknüpfung Ihrer Projektmappe auszuführen und vor dem Fortfahren sicherzustellen, dass sie erfolgreich erstellt wird.

## <a name="implement-an-authentication-delegate-and-a-consent-delegate"></a>Implementieren eines Authentifizierungs- und Zustimmungsdelegaten

Das MIP SDK implementiert die Authentifizierung mithilfe der Klassenerweiterbarkeit, die einen Mechanismus zur Freigabe der Authentifizierung für die Clientanwendung bietet. Der Client muss ein geeignetes OAuth2-Zugriffstoken abrufen und zur Laufzeit für das MIP SDK bereitstellen.

Erstellen Sie eine Implementierung für einen Authentifizierungsdelegaten, indem Sie die Klasse `mip::AuthDelegate` des SDK erweitern und die rein virtuelle Funktion `mip::AuthDelegate::AcquireOAuth2Token()` überschreiben/implementieren. **Folgen Sie den Schritten unter [Schnellstart: Initialisierung der Clientanwendung (C++)](quick-app-initialization-cpp.md).** Der Authentifizierungsdelegat wird später von den Objekten für Schutzprofil und -Engine instanziiert und verwendet.

## <a name="implement-a-consent-delegate"></a>Implementieren eines Zustimmungsdelegaten

Nun erstellen Sie eine Implementierung für einen Zustimmungsdelegaten, indem Sie die Klasse `mip::ConsentDelegate` des SDK erweitern und die rein virtuelle Funktion `mip::AuthDelegate::GetUserConsent()` überschreiben/implementieren.  **Folgen Sie den Schritten unter [Schnellstart: Initialisierung der Clientanwendung (C++)](quick-app-initialization-cpp.md).** Der Zustimmungsdelegat wird später von den Objekten für Schutzprofil und -Engine instanziiert und verwendet.

## <a name="construct-a-protection-profile-and-engine"></a>Erstellen von Schutzprofil und -Engine

Wie bereits erwähnt sind für SDK-Clients, die MSIP-APIs verwenden, Objekte für Profil und Engine erforderlich. Vervollständigen Sie den Codierungsabschnitt dieses Schnellstarts, indem Sie Code hinzufügen, um die Profil- und Engine-Objekte zu instanziieren:

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Entfernen Sie die generierte Implementierung von `main()`. Entfernen Sie **keine** Präprozessordirektiven, die während der Projekterstellung von Visual Studio generiert wurden (#pragma, #include). Hängen Sie folgenden Code hinter Präprozessordirektiven an:

  ```cpp
  #include "mip/mip_init.h"
  #include "mip/mip_context.h"  
  #include "auth_delegate.h"
  #include "consent_delegate.h"
  #include "profile_observer.h"
  #include"engine_observer.h"

  using std::promise;
  using std::future;
  using std::make_shared;
  using std::shared_ptr;
  using std::string;
  using std::cout;
  using mip::ApplicationInfo;
  using mip::ProtectionProfile;
  using mip::ProtectionEngine;

  int main(){
    // Construct/initialize objects required by the application's profile object
    ApplicationInfo appInfo{"<application-id>",                    // ApplicationInfo object (App ID, name, version)
                            "<application-name>",
                            "<application-version>"};

    auto mipContext = mip::MipContext::Create(appInfo,
                                              "file_sample",
                                              mip::LogLevel::Trace,
                                              false,
                                              nullptr /*loggerDelegateOverride*/,
                                              nullptr /*telemetryOverride*/);


    auto profileObserver = make_shared<ProtectionProfileObserver>(); // Observer object
    auto authDelegateImpl = make_shared<AuthDelegateImpl>("<application-id>"); // Authentication delegate object (App ID)
    auto consentDelegateImpl = make_shared<ConsentDelegateImpl>(); // Consent delegate object

    // Construct/initialize profile object
    ProtectionProfile::Settings profileSettings(
      mipContext,
      mip::CacheStorageType::OnDisk,      
      consentDelegateImpl,
      profileObserver);

    // Set up promise/future connection for async profile operations; load profile asynchronously
    auto profilePromise = make_shared<promise<shared_ptr<ProtectionProfile>>>();
    auto profileFuture = profilePromise->get_future();
    try
    {
      mip::ProtectionProfile::LoadAsync(profileSettings, profilePromise);
    }
    catch (const std::exception& e)
    {
      cout << "An exception occurred... are the Settings and ApplicationInfo objects populated correctly?\n\n"
            << e.what() << "'\n";
      system("pause");
      return 1;
    }

    auto profile = profileFuture.get();

    // Construct/initialize engine object
    ProtectionEngine::Settings engineSettings(
       authDelegateImpl,                          // Reference to mip::AuthDelegate implementation
       mip::Identity("<engine-account>"),         // Engine identity (account used for authentication)
       "<engine-state>",                          // User-defined engine state
       "en-US");                                  // Locale (default = en-US)

    // Set up promise/future connection for async engine operations; add engine to profile asynchronously
    auto enginePromise = make_shared<promise<shared_ptr<ProtectionEngine>>>();
    auto engineFuture = enginePromise->get_future();
    profile->AddEngineAsync(engineSettings, enginePromise);
    std::shared_ptr<ProtectionEngine> engine;

    try
    {
      engine = engineFuture.get();
    }
    catch (const std::exception& e)
    {
      cout << "An exception occurred... is the access token incorrect/expired?\n\n"
           << e.what() << "'\n";
      system("pause");
      return 1;
    }

    // Application shutdown. Null out profile and engine, call ReleaseAllResources();
    // Application may crash at shutdown if resources aren't properly released.
    engine = nullptr;
    profile = nullptr;
    mipContext = nullptr;

    return 0;
  }
   ```

3. Ersetzen Sie alle Platzhalterwerte in dem Quellcode, den Sie gerade eingefügt haben, mithilfe von Zeichenfolgenkonstanten:

   | Platzhalter | Wert | Beispiel |
   |:----------- |:----- |:--------|
   | \<application-id\> | Die ID der Azure AD-Anwendung (GUID) wird der in Schritt 2 im Artikel „Einrichten und Konfigurieren des MIP SDK“ (setup-configure-mip.md) registrierten Anwendung zugewiesen. Ersetzen Sie zwei Instanzen. | `"0edbblll-8773-44de-b87c-b8c6276d41eb"` |
   | \<application-name\> | Ein benutzerdefinierter Anzeigename für Ihre Anwendung. Dieser muss aus gültigen ASCII-Zeichen (außer ;) bestehen und im Idealfall mit dem Anwendungsnamen übereinstimmen, den Sie während der Azure AD-Registrierung verwendet haben. | `"AppInitialization"` |
   | \<application-version\> | Die benutzerdefinierten Versionsinformationen für Ihre Anwendung – diese muss aus gültigen ASCII-Zeichen (außer ;) bestehen. | `"1.1.0.0"` |
   | \<engine-account\> | Das Konto, das für die Identität der Engine verwendet wird. Wenn Sie sich während des Tokenabrufs bei einem Benutzerkonto authentifizieren, muss es diesem Wert entsprechen. | `"user1@tenant.onmicrosoft.com"` |
   | \<engine-state\> | Der benutzerdefinierte Status, der der Engine zugeordnet werden soll. | `"My App State"` |

4. Nun können Sie die Anwendung endgültig fertigstellen und etwaige Fehler beheben. Ihr Code müsste erfolgreich erstellt werden, wird jedoch erst dann ordnungsgemäß ausgeführt, wenn Sie den nächsten Schnellstart abgeschlossen haben. Bei der Ausführung der Anwendung wird Ihnen eine Ausgabe wie die folgende angezeigt. Das Schutzprofil und die Schutz-Engine würden erfolgreich von der Anwendung erstellt werden, aber da keine Auslösung des Authentifizierungsmoduls erfolgt, würden Sie über kein Zugriffstoken verfügen, bis Sie den nächsten Schnellstart abgeschlossen haben.

   ```console
    C:\MIP Sample Apps\ProtectionQS\Debug\ProtectionQS.exe (process 8252) exited with code 0.
    To automatically close the console when debugging stops, enable Tools->Options->Debugging->Automatically close the console when debugging stops.
    Press any key to close this window . . .
   ```

## <a name="next-steps"></a>Nächste Schritte

Jetzt, da Ihr Initialisierungscode vollständig ist, können Sie mit dem nächsten Schnellstart fortfahren. Darin beginnen Sie damit, die MIP-Schutz-API zu testen.

> [!div class="nextstepaction"]
> [Auflisten von Schutzvorlagen](quick-protection-list-templates-cpp.md)
