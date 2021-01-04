---
title: 'Schnellstart: Initialisierung für MIP SDK C++-Clients mit der Datei-API'
description: Ein Schnellstart zum Schreiben der Initialisierungslogik für Clientanwendungen eines Microsoft Information Protection (MIP) SDK mit der Datei-API.
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 688fe04d993ae1d286458fa9d41b0915838e6406
ms.sourcegitcommit: 437057990372948c9435b620052a7398360264b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2020
ms.locfileid: "97701678"
---
# <a name="quickstart-client-application-initialization-c"></a>Schnellstart: Initialisierung der Clientanwendung (C++) 

In diesem Schnellstart lernen Sie, wie Sie das Muster für die Clientinitialisierung implementieren können, das zur Laufzeit vom MSIP SDK für C++ verwendet wird. 

> [!NOTE]
> Die in diesem Schnellstart beschriebenen Schritte müssen für sämtliche Clientanwendungen ausgeführt werden, die MIP-Datei-, Richtlinien- oder Datenschutz-APIs verwenden. Dieser Schnellstart konzentriert sich zwar auf die Verwendung der Datei-APIs, das gleiche Muster ist jedoch auch auf Clients anwendbar, die Richtlinien- und Datenschutz-APIs verwenden. Beginnen Sie mit diesem Schnellstart, und schließen Sie die nächsten Schnellstarts nacheinander ab, da diese aufeinander aufbauen.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie Folgendes sicher, sofern dies noch nicht geschehen ist:

- Führen Sie die Schritte unter [Microsoft Information Protection (MIP) SDK: Setup und Konfiguration](setup-configure-mip.md) aus. Dieser Schnellstart „Initialisierung der Clientanwendung“ hat das ordnungsgemäße Setup und die ordnungsgemäße Konfiguration des SDK zum Thema.
- Optional:
  - Überprüfen Sie [Profile and engine objects](concept-profile-engine-cpp.md) (Profil- und Engine-Objekte). Bei den Profil- und Engine-Objekten handelt es sich um universelle Konzepte, die von Clients benötigt werden, die die MIP-Datei-/Richtlinien-/Datenschutz-APIs verwenden. 
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

2. Fügen Sie das Nuget-Paket für die Datei-API des MIP SDK zu Ihrem Projekt hinzu:
   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten (direkt unter dem obersten Knoten bzw. dem Projektmappenknoten), und wählen Sie **NuGet-Pakete verwalten...** aus:
   - Gehen Sie wie folgt vor, wenn im Bereich „Editor-Gruppe“ die Registerkarte **NuGet-Paket-Manager** geöffnet wird:
     - Wählen Sie **Durchsuchen** aus.
     - Geben Sie „Microsoft.InformationProtection“ in das Suchfeld ein.
     - Wählen Sie das Paket „Microsoft.InformationProtection.File“ aus.
     - Klicken Sie auf „Installieren“ und anschließend auf „OK“, wenn das Bestätigungsdialogfeld **Vorschau der Änderungen** angezeigt wird.
   
     [![NuGet-Paket in Visual Studio hinzufügen](media/quick-app-initialization-cpp/add-nuget-package.png)](media/quick-app-initialization-cpp/add-nuget-package.png#lightbox)
 
## <a name="implement-an-observer-class-to-monitor-the-file-profile-and-engine-objects"></a>Implementieren einer Observer-Klasse zum Überwachen der Profil- und Engine-Objekte der Datei

Nun erstellen Sie eine grundlegende Implementierung für eine Observer-Klasse des Dateiprofils, indem Sie die Klasse `mip::FileProfile::Observer` des SDK erweitern. Der Observer wird später instanziiert und verwendet, um den Ladevorgang des Profilobjekts der Datei zu überwachen und das Engine-Objekt zum Profil hinzuzufügen.

1. Fügen Sie Ihrem Projekt eine neue Klasse hinzu, durch die die Dateien „header/.h“ und „implementation/.cpp“ für Sie generiert werden:

   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Hinzufügen** > **Klasse** aus.
   - Gehen Sie im Dialogfeld **Klasse hinzufügen** folgendermaßen vor:
     - Geben Sie im Feld **Klassenname** „profile_observer“ ein. Beachten Sie, dass sowohl das Feld **H-Datei** als auch das Feld **CPP-Datei** anhand des eingegebenen Namens automatisch aufgefüllt werden.
     - Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK**.

     [![Klasse in Visual Studio hinzufügen](media/quick-app-initialization-cpp/add-class.png)](media/quick-app-initialization-cpp/add-class.png#lightbox)

2. Nach dem Generieren der H- und der CPP-Datei für die Klasse werden beide Dateien auf Editor-Gruppenregisterkarten geöffnet. Aktualisieren Sie jetzt jede Datei, um die neue Observer-Klasse zu implementieren:

   - Aktualisieren Sie „profile_observer.h“, indem Sie die generierte Klasse `profile_observer` auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include <memory>
     #include "mip/file/file_profile.h"

     class ProfileObserver final : public mip::FileProfile::Observer {
     public:
          ProfileObserver() { }
          void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) override;
          void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
          void OnAddEngineSuccess(const std::shared_ptr<mip::FileEngine>& engine, const std::shared_ptr<void>& context) override;
          void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
     };
     ```

   - Aktualisieren Sie „profile_observer.cpp“, indem Sie die Implementierung der generierten Klasse `profile_observer` auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include <future>

     using std::promise;
     using std::shared_ptr;
     using std::static_pointer_cast;
     using mip::FileEngine;
     using mip::FileProfile;

     void ProfileObserver::OnLoadSuccess(const shared_ptr<FileProfile>& profile, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_value(profile);
     }

     void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_exception(error);
     }

     void ProfileObserver::OnAddEngineSuccess(const shared_ptr<FileEngine>& engine, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_value(engine);
     }

     void ProfileObserver::OnAddEngineFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_exception(error);
     }
     ```

3. Verwenden Sie optional F6 (**Projektmappe erstellen**), um eine Testkompilierung/-verknüpfung Ihrer Lösung auszuführen und vor dem Fortfahren sicherzustellen, dass sie erfolgreich erstellt wird.

## <a name="implement-an-authentication-delegate"></a>Implementieren eines Authentifizierungsdelegats

Das MIP SDK implementiert die Authentifizierung mithilfe der Klassenerweiterbarkeit, die einen Mechanismus zur Freigabe der Authentifizierung für die Clientanwendung bietet. Der Client muss ein geeignetes OAuth2-Zugriffstoken abrufen und zur Laufzeit für das MIP SDK bereitstellen. 

Nun erstellen Sie eine Implementierung für einen Authentifizierungsdelegaten, indem Sie die Klasse `mip::AuthDelegate` des SDK erweitern und die rein virtuelle Funktion `mip::AuthDelegate::AcquireOAuth2Token()` überschreiben/implementieren. Der Authentifizierungsdelegat wird später von den Profil- und Engine-Objekten der Datei instanziiert und verwendet.

1. Fügen Sie mit der gleichen Visual Studio-Funktion „Klasse hinzufügen“, die wir im vorherigen Abschnitt in Schritt 1 verwendet haben, eine weitere Klasse zu Ihrem Projekt hinzu. Geben Sie dieses Mal „auth_delegate“ in das Feld **Klassenname** ein. 

2. Aktualisieren Sie jetzt jede Datei, um Ihre neue Authentifizierungsdelegatklasse zu implementieren:

   - Aktualisieren Sie „auth_delegate.h“, indem Sie den gesamten Code der Klasse `auth_delegate` durch die folgende Quelle ersetzen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include):

     ```cpp
     #include <string>
     #include "mip/common_types.h"

     class AuthDelegateImpl final : public mip::AuthDelegate {
     public:
          AuthDelegateImpl() = delete;        // Prevents default constructor

          AuthDelegateImpl(
            const std::string& appId)         // AppID for registered AAD app
            : mAppId(appId) {};

          bool AcquireOAuth2Token(            // Called by MIP SDK to get a token
            const mip::Identity& identity,    // Identity of the account to be authenticated, if known
            const OAuth2Challenge& challenge, // Authority (AAD tenant issuing token), and resource (API being accessed; "aud" claim).
            OAuth2Token& token) override;     // Token handed back to MIP SDK

     private:
          std::string mAppId;
          std::string mToken;
          std::string mAuthority;
          std::string mResource;
     };
     ```

   - Aktualisieren Sie „auth_delegate.cpp“, indem Sie die Implementierung der gesamten Klasse `auth_delegate` durch die folgende Quelle ersetzen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). 

     > [!IMPORTANT]
     > Der folgende Code für den Tokenabruf eignet sich nicht für die Produktion. In der Produktion muss dieser durch Code ersetzt werden, mit dem ein Token dynamisch abgerufen wird, und zwar mithilfe von:
     > - Der appId und dem Antwort- bzw. Umleitungs-URI, die in der Registrierung Ihrer Azure AD-App angegeben sind (der Antwort- bzw. Umleitungs-URI **muss** Ihrer App-Registrierung entsprechen)
     > - Der Autoritäts- und Ressourcen-URL, die vom SDK im Argument `challenge` übergeben werden (die Ressourcen-URL **muss** der API bzw. den Berechtigungen Ihrer App-Registrierung entsprechen)
     > - Gültigen App- bzw. Benutzeranmeldeinformationen, bei denen das Konto dem vom SDK übergebenen Argument `identity` entspricht. „Native“ OAuth2-Clients sollten zur Eingabe von Benutzeranmeldeinformationen auffordern und den Fluss „Autorisierungscode“ verwenden. „Vertrauliche“ OAuth2-Clients können ihre eigenen sicheren Anmeldeinformationen mit dem Fluss „Clientanmeldeinformationen“ (z.B. ein Dienst) verwenden oder über den Fluss „Autorisierungscode“ (z.B. eine Web-App) zur Eingabe von Benutzeranmeldeinformationen auffordern. 
     >
     > Bei dem OAuth2-Tokenabruf handelt es sich um ein komplexes Protokoll. Er erfolgt in der Regel über eine Bibliothek. TokenAcquireOAuth2Token() wird **nur** vom MIP SDK aufgerufen (nach Bedarf).

     ```cpp
     #include <iostream>
     using std::cout;
     using std::cin;
     using std::string;

     bool AuthDelegateImpl::AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) 
     {
          // Acquire a token manually, reuse previous token if same authority/resource. In production, replace with token acquisition code.
          string authority = challenge.GetAuthority();
          string resource = challenge.GetResource();
          if (mToken == "" || (authority != mAuthority || resource != mResource))
          {
              cout << "\nRun the PowerShell script to generate an access token using the following values, then copy/paste it below:\n";
              cout << "Set $authority to: " + authority + "\n";
              cout << "Set $resourceUrl to: " + resource + "\n";
              cout << "Sign in with user account: " + identity.GetEmail() + "\n";
              cout << "Enter access token: ";
              cin >> mToken;
              mAuthority = authority;
              mResource = resource;
              system("pause");
          }

          // Pass access token back to MIP SDK
          token.SetAccessToken(mToken);

          // True = successful token acquisition; False = failure
          return true;
     }
     ```

3. Verwenden Sie optional F6 (**Projektmappe erstellen**), um eine Testkompilierung/-verknüpfung Ihrer Lösung auszuführen und vor dem Fortfahren sicherzustellen, dass sie erfolgreich erstellt wird.

## <a name="implement-a-consent-delegate"></a>Implementieren eines Zustimmungsdelegats

Nun erstellen Sie eine Implementierung für einen Zustimmungsdelegaten, indem Sie die Klasse `mip::ConsentDelegate` des SDK erweitern und die rein virtuelle Funktion `mip::AuthDelegate::GetUserConsent()` überschreiben/implementieren. Der Zustimmungsdelegat wird später von den Profil- und Engine-Objekten der Datei instanziiert und verwendet.

1. Fügen Sie mit der gleichen Visual Studio-Funktion „Klasse hinzufügen“, die wir vorher verwendet haben, eine weitere Klasse zu Ihrem Projekt hinzu. Geben Sie dieses Mal „content_delegate“ in das Feld **Klassenname** ein. 

2. Aktualisieren Sie jetzt jede Datei, um Ihre neue Zustimmungsdelegatklasse zu implementieren:

   - Aktualisieren Sie „consent_delegate.h“, indem Sie den gesamten Code der Klasse `consent_delegate` durch die folgende Quelle ersetzen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include):

     ```cpp
     #include "mip/common_types.h"
     #include <string>

     class ConsentDelegateImpl final : public mip::ConsentDelegate {
     public:
          ConsentDelegateImpl() = default;
          virtual mip::Consent GetUserConsent(const std::string& url) override;
     };
     ```

   - Aktualisieren Sie „consent_delegate.cpp“, indem Sie die Implementierung der gesamten Klasse `consent_delegate` durch die folgende Quelle ersetzen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). 

     ```cpp
     #include <iostream>
     using mip::Consent;
     using std::string;

     Consent ConsentDelegateImpl::GetUserConsent(const string& url) 
     {
          // Accept the consent to connect to the url
          std::cout << "SDK will connect to: " << url << std::endl;
          return Consent::AcceptAlways;
     }
     ``` 
     
3. Verwenden Sie optional F6 (**Projektmappe erstellen**), um eine Testkompilierung/-verknüpfung Ihrer Lösung auszuführen und vor dem Fortfahren sicherzustellen, dass sie erfolgreich erstellt wird.

## <a name="construct-a-file-profile-and-engine"></a>Erstellen eines Profils und einer Engine für die Datei

Wie bereits erwähnt sind für SDK-Clients, die MSIP-APIs verwenden, Profilobjekte und Engine-Objekte erforderlich. Vervollständigen Sie den Codierungsabschnitt dieses Schnellstarts, indem Sie Code hinzufügen, um die Profil- und Engine-Objekte zu instanziieren: 

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Entfernen Sie die generierte Implementierung von `main()`. Entfernen Sie **keine** Präprozessordirektiven, die während der Projekterstellung von Visual Studio generiert wurden (#pragma, #include). Hängen Sie folgenden Code hinter Präprozessordirektiven an:

   ```cpp
   #include "mip/mip_context.h"  
   #include "auth_delegate.h"
   #include "consent_delegate.h"
   #include "profile_observer.h"

   using std::promise;
   using std::future;
   using std::make_shared;
   using std::shared_ptr;
   using std::string;
   using std::cout;
   using mip::ApplicationInfo;
   using mip::FileProfile;
   using mip::FileEngine;

   int main()
   {
     // Construct/initialize objects required by the application's profile object
     ApplicationInfo appInfo{"<application-id>",                    // ApplicationInfo object (App ID, name, version)
                 "<application-name>",
                 "<application-version>"};

     auto mipContext = mip::MipContext::Create(appInfo,
                         "file_sample",
                         mip::LogLevel::Trace,
                         nullptr /*loggerDelegateOverride*/,
                         nullptr /*telemetryOverride*/);

     auto profileObserver = make_shared<ProfileObserver>();         // Observer object
     auto authDelegateImpl = make_shared<AuthDelegateImpl>(         // Authentication delegate object (App ID)
                 "<application-id>");
     auto consentDelegateImpl = make_shared<ConsentDelegateImpl>(); // Consent delegate object
 
     // Construct/initialize profile object
     FileProfile::Settings profileSettings(
       mipContext,
       mip::CacheStorageType::OnDisk,
       authDelegateImpl,
       consentDelegateImpl,
       profileObserver);

     // Set up promise/future connection for async profile operations; load profile asynchronously
     auto profilePromise = make_shared<promise<shared_ptr<FileProfile>>>();
     auto profileFuture = profilePromise->get_future();
    try
    { 
        mip::FileProfile::LoadAsync(profileSettings, profilePromise);
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
     FileEngine::Settings engineSettings(
       mip::Identity("<engine-account>"),         // Engine identity (account used for authentication)
       "<engine-state>",                          // User-defined engine state
       "en-US");                                  // Locale (default = en-US)

     // Set up promise/future connection for async engine operations; add engine to profile asynchronously
     auto enginePromise = make_shared<promise<shared_ptr<FileEngine>>>();
     auto engineFuture = enginePromise->get_future();
     profile->AddEngineAsync(engineSettings, enginePromise);
     std::shared_ptr<FileEngine> engine; 
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
   // handler = nullptr; // This will be used in later quick starts.
   engine = nullptr;
   profile = nullptr;   
   mipContext = nullptr;

   return 0;
   }
   ``` 

3. Ersetzen Sie alle Platzhalterwerte in dem Quellcode, den Sie gerade eingefügt haben, mithilfe von Zeichenfolgenkonstanten:

   | Platzhalter | Wert | Beispiel |
   |:----------- |:----- |:--------|
   | \<application-id\> | Die ID der Azure AD-Anwendung (GUID) wird der in Schritt 2 des Artikels [MIP SDK setup and configuration (MSIP SDK: Setup und Konfiguration)](./setup-configure-mip.md#register-a-client-application-with-azure-active-directory) registrierten Anwendung zugewiesen. Ersetzen Sie zwei Instanzen. | `"0edbblll-8773-44de-b87c-b8c6276d41eb"` |
   | \<application-name\> | Ein benutzerdefinierter Anzeigename für Ihre Anwendung. Dieser muss aus gültigen ASCII-Zeichen (außer ;) bestehen und im Idealfall mit dem Anwendungsnamen übereinstimmen, den Sie während der Azure AD-Registrierung verwendet haben. | `"AppInitialization"` |
   | \<application-version\> | Die benutzerdefinierten Versionsinformationen für Ihre Anwendung – diese muss aus gültigen ASCII-Zeichen (außer ;) bestehen. | `"1.1.0.0"` |
   | \<engine-account\> | Das Konto, das für die Identität der Engine verwendet wird. Wenn Sie sich während des Tokenabrufs bei einem Benutzerkonto authentifizieren, muss es diesem Wert entsprechen. | `"user1@tenant.onmicrosoft.com"` |
   | \<engine-state\> | Der benutzerdefinierte Status, der der Engine zugeordnet werden soll. | `"My App State"` |


4. Nun können Sie die Anwendung endgültig fertigstellen und etwaige Fehler beheben. Ihr Code müsste erfolgreich erstellt werden, wird jedoch erst dann ordnungsgemäß ausgeführt, wenn Sie den nächsten Schnellstart abgeschlossen haben. Bei der Ausführung der Anwendung wird Ihnen eine Ausgabe wie die folgende angezeigt. Sie können erst dann ein Zugriffstoken bereitstellen, wenn Sie den nächsten Schnellstart abgeschlossen haben.


## <a name="next-steps"></a>Nächste Schritte

Jetzt, da Ihr Initialisierungscode vollständig ist, können Sie mit dem nächsten Schnellstart fortfahren. Darin lernen Sie die MIP-Datei-APIs kennen.

> [!div class="nextstepaction"]
> [Auflisten der Vertraulichkeitsbezeichnungen](quick-file-list-labels-cpp.md)