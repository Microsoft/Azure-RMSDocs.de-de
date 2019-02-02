---
title: 'Schnellstart: Initialisierung für Microsoft Information Protection (MIP) SDK C# Clients'
description: Eine schnellstartanleitung veranschaulicht, wie die Initialisierungslogik für eine Microsoft Information Protection (MIP) SDK schreiben C# -Clientanwendungen.
author: tommoser
ms.service: information-protection
ms.topic: quickstart
ms.date: 01/04/2019
ms.author: tommos
ms.openlocfilehash: 7efaaba799afa01b07a5eefc0b6798983cc590d2
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652369"
---
# <a name="quickstart-client-application-initialization-c"></a>Schnellstart: Initialisieren der Client-Anwendung (C#)

Dieser Schnellstart zeigt Ihnen, wie der Client-Initialisierung-Muster verwendet vom Wrapper MIP SDK für .NET zur Laufzeit implementiert.

> [!NOTE]
> Die in dieser schnellstartanleitung beschriebenen Schritte müssen für jede Clientanwendung, die Datei oder Richtlinie APIs des MIP-.NET Wrappers verwendet. Der Datenschutz-API ist noch nicht verfügbar. Dieser Schnellstart konzentriert sich zwar auf die Verwendung der Datei-APIs, das gleiche Muster ist jedoch auch auf Clients anwendbar, die Richtlinien- und Datenschutz-APIs verwenden. Beginnend mit diesem Schnellstart sollten die nächsten Schnellstarts nacheinander ausgeführt werden, da diese aufeinander aufbauen.

## <a name="prerequisites"></a>Vorraussetzungen

Stellen Sie Folgendes sicher, sofern dies noch nicht geschehen ist:

- Führen Sie die Schritte unter [Microsoft Information Protection (MIP) SDK: Setup und Konfiguration](setup-configure-mip.md) aus. Dieser Schnellstart „Initialisierung der Clientanwendung“ hat das ordnungsgemäße Setup und die ordnungsgemäße Konfiguration des SDK zum Thema.
- Optional:
  - Überprüfen Sie [Profile and engine objects](concept-profile-engine-cpp.md) (Profil- und Engine-Objekte). Bei den Profil- und Engine-Objekten handelt es sich um universelle Konzepte, die von Clients benötigt werden, die die MIP-Datei-/Richtlinien-/Datenschutz-APIs verwenden. 
  - Überprüfen Sie [Authentifizierungskonzepte](concept-authentication-cpp.md), um zu erfahren, wie die Authentifizierung und die Zustimmung von der SDK- und der Clientanwendung implementiert werden.

## <a name="create-a-visual-studio-solution-and-project"></a>Erstellen einer Visual Studio-Lösung und eines -Projekts

Zunächst erstellen und konfigurieren wir die erste Lösung und das erste Projekt in Visual Studio. Dies bildet die Grundlage für die anderen Schnellstarts.

1. Öffnen Sie Visual Studio 2017, wählen Sie das Menü **Datei** und anschließend **Neu** > **Projekt** aus. Geben Sie im Dialogfeld **Neues Projekt** Folgendes ein:
   - Klicken Sie im linken Bereich unter **installiert**, **Visual C#** Option **Windows Desktop**.
   - Wählen Sie im mittleren Bereich **Konsolen-App ((.NET Framework)**
   - Aktualisieren Sie im unteren Bereich das Projekt **Name** > **Speicherort** und entsprechend den darin enthaltenen **Projektmappennamen**.
   - Wenn Sie fertig sind, klicken Sie in der unteren rechten Ecke auf die Schaltfläche **OK**. 

     [![Erstellen der Visual Studio-Projektmappe](media/quick-app-initialization-csharp/create-vs-solution.png)](media/quick-app-initialization-csharp/create-vs-solution.png#lightbox)

2. Fügen Sie das Nuget-Paket für die Datei-API des MIP SDK zu Ihrem Projekt hinzu:
   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten (direkt unter dem obersten Knoten bzw. dem Projektmappenknoten), und wählen Sie **NuGet-Pakete verwalten...** aus:
   - Gehen Sie wie folgt vor, wenn im Bereich „Editor-Gruppe“ die Registerkarte **NuGet-Paket-Manager** geöffnet wird:
     - Wählen Sie **Durchsuchen** aus.
     - Geben Sie „Microsoft.InformationProtection“ in das Suchfeld ein.
     - Wählen Sie das Paket „Microsoft.InformationProtection.File“ aus.
     - Klicken Sie auf „Installieren“ und anschließend auf „OK“, wenn das Bestätigungsdialogfeld **Vorschau der Änderungen** angezeigt wird.

3. Wiederholen Sie die oben genannten Schritte für das Paket MIP SDK-Datei-API hinzugefügt, aber stattdessen wird die Anwendung "Microsoft.IdentityModel.Clients.ActiveDirectory" hinzugefügt.

## <a name="implement-an-authentication-delegate"></a>Implementieren eines Authentifizierungsdelegats

Das MIP SDK implementiert die Authentifizierung mithilfe der Klassenerweiterbarkeit, die einen Mechanismus zur Freigabe der Authentifizierung für die Clientanwendung bietet. Der Client muss ein geeignetes OAuth2-Zugriffstoken abrufen und zur Laufzeit für das MIP SDK bereitstellen.

Nun erstellen Sie eine Implementierung für einen Delegaten Authentifizierung durch die SDK Erweiterung `Microsoft.InformationProtection.IAuthDelegate` -Schnittstelle und das Überschreiben/implementieren die `IAuthDelegate.AcquireToken()` virtuelle Funktion. Der authentifizierungsdelegat wird instanziiert und später von der `FileProfile` und `FileEngine` Objekte.

1. Mit der rechten Maustaste in Visual Studio, wählen des Namens des Projekts **hinzufügen** dann **Klasse**.
2. Geben Sie "AuthDelegateImplementation" in der **Namen** Feld. Klicken Sie auf **Hinzufügen**.
3. Fügen Sie die using-Anweisungen für die Active Directory Authentication Library (ADAL) und die MIP-Bibliothek hinzu:

     ```csharp
     using Microsoft.InformationProtection;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     ```

4. Legen Sie `AuthDelegateImplementation` erben `Microsoft.InformationProtection.IAuthDelegate` und implementieren Sie eine private Variable der `Microsoft.InformationProtection.ApplicationInfo` und einen Konstruktor, der den gleichen Typ akzeptiert.

     ```csharp
     public class AuthDelegateImplementation : IAuthDelegate
     {
        private ApplicationInfo _appInfo;
        private string redirectUri = "mip-sdk-app://authorize";
        public AuthDelegateImplementation(ApplicationInfo appInfo)
        {
            _appInfo = appInfo;
        }
     }
     ```

Die `ApplicationInfo` -Objekt enthält zwei Eigenschaften. Die `_appInfo.ApplicationId` verwendet werden, der `AuthDelegateImplementation` -Klasse, die Client-ID in der Authentifizierungsbibliothek bereitzustellen.

5. Hinzufügen der `public string AcquireToken()` Klasse. Diese Klasse sollte akzeptieren `Microsoft.InformationProtection.Identity`, und zwei Zeichenfolgen: Autorität und folgenden Ressourcen. Diese Zeichenfolgenvariablen übergeben werden, die Authentifizierungsbibliothek von der API und sollte nicht bearbeitet werden. Bearbeiten von kann dazu führen, dass ein Fehler bei der Authentifizierung.

     ```csharp
     public string AcquireToken(Identity identity, string authority, string resource)
     {
          AuthenticationContext authContext = new AuthenticationContext(authority);
          var result = authContext.AcquireTokenAsync(resource, _appInfo.ApplicationId, new Uri(redirectUri), new PlatformParameters(PromptBehavior.Auto, null), UserIdentifier.AnyUser).Result;
          return result.AccessToken;
     }
     ```

## <a name="implement-a-consent-delegate"></a>Implementieren eines Zustimmungsdelegats

Nun erstellen Sie eine Implementierung für einen Delegaten Zustimmung durch die SDK Erweiterung `Microsoft.InformationProtection.IConsentDelegate` -Schnittstelle und das Überschreiben/implementieren `GetUserConsent()`. Der Zustimmungsdelegat wird später von den Profil- und Engine-Objekten der Datei instanziiert und verwendet. Mit der Adresse des Diensts der Benutzer zustimmen muss, die Verwendung in der Delegaten für die Zustimmung erhält die `url` Parameter. Der Delegat sollte in der Regel einige Flow bereitstellen, mit dem Benutzer zum annehmen oder ablehnen, um die Zustimmung für den Zugriff auf den Dienst. Für diesen Quickstart-Code schwer `Consent.Accept`.

1. Fügen Sie mit der gleichen Visual Studio-Funktion „Klasse hinzufügen“, die wir vorher verwendet haben, eine weitere Klasse zu Ihrem Projekt hinzu. Dieses Mal Geben Sie "ConsentDelegateImplementation" in der **Klassenname** Feld. 

2. Jetzt aktualisieren **ConsentDelegateImpl.cs** die neue Klasse der Zustimmung Delegaten implementieren. Fügen Sie den using-Anweisung für `Microsoft.InformationProtection` und legen Sie die Klasse erbt `IConsentDelegate`.

     ```csharp
     class ConsentDelegateImplementation : IConsentDelegate
     {
          public Consent GetUserConsent(string url)
          {
               return Consent.Accept;
          }
     }
     ```

3. Optional, bei dem Versuch, erstellen Sie die Projektmappe, um sicherzustellen, dass es ohne Fehler kompiliert wird.

## <a name="initialize-the-mip-sdk-managed-wrapper"></a>Den verwaltete Wrapper für MIP SDK initialisieren

1. Von **Projektmappen-Explorer**, öffnen Sie die CS-Datei im Projekt, das die Implementierung enthält die `Main()` Methode. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Entfernen Sie die generierte Implementierung von `main()`. 

3. Der verwaltete Wrapper enthält eine statische Klasse, `Microsoft.InformationProtection.MIP` zum Initialisieren, Profile zu laden und Freigeben von Ressourcen. Rufen Sie zum Initialisieren des Wrappers für Datei-API-Vorgänge MIP. Initialize-übergebe `MipComponent.File` , die für Dateivorgänge erforderlichen Bibliotheken zu laden. 

4. In `Main()` in *"Program.cs"* fügen Sie Folgendes hinzu, und Ersetzen Sie dabei **\<Anwendungs-Id\>** mit der ID der Azure AD-Anwendungsregistrierung, die zuvor erstellt haben.

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.InformationProtection;
using Microsoft.InformationProtection.File;

namespace mip_sdk_dotnet_quickstart
{
    class Program
    {
        private const string clientId = "<application-id>";
        private const string appName = "<friendly-name>";

        static void Main(string[] args)
        {
            //Initialize Wrapper for File API operations 
            MIP.Initialize(MipComponent.File);
        }
    }
}
```

## <a name="construct-a-file-profile-and-engine"></a>Erstellen eines Datei-Profils und -Engine

Wie bereits erwähnt, sind die Profile und -Engine-Objekte für SDK-Clients mithilfe von MIP-APIs erforderlich. Führen Sie den Schreiben von Code Teil dieser Schnellstartanleitung, durch das Hinzufügen von Code aus, um die nativen DLLs laden, und klicken Sie dann das Profil und -Engine-Objekte zu instanziieren.

   ```csharp
using System;
using System.Threading.Tasks;
using Microsoft.InformationProtection;
using Microsoft.InformationProtection.File;

namespace mip_sdk_dotnet_quickstart
{
     class Program
     {
          private const string clientId = "<application-id>";
          private const string appName = "<friendly-name>";

          static void Main(string[] args)
          {
               //Initialize Wrapper for File API operations
               MIP.Initialize(MipComponent.File);

               //Create ApplicationInfo, setting the clientID from Azure AD App Registration as the ApplicationId
               ApplicationInfo appInfo = new ApplicationInfo()
               {
                    ApplicationId = clientId,
                    ApplicationName = appName,
                    ApplicationVersion = "1.0.0"
               };

               //Instatiate the AuthDelegateImpl object, passing in AppInfo. 
               AuthDelegateImplementation authDelegate = new AuthDelegateImplementation(appInfo);

               //Initialize and instantiate the File Profile
               //Create the FileProfileSettings object
               var profileSettings = new FileProfileSettings("mip_data", false, authDelegate, new ConsentDelegateImplementation(), appInfo, LogLevel.Trace);

               //Load the Profile async and wait for the result
               var fileProfile = Task.Run(async () => await MIP.LoadFileProfileAsync(profileSettings)).Result;

               //Create a FileEngineSettings object, then use that to add an engine to the profile
               var engineSettings = new FileEngineSettings("user1@tenant.com", "", "en-US");
               engineSettings.Identity = new Identity("user1@tenant.com");
               var fileEngine = Task.Run(async () => await fileProfile.AddEngineAsync(engineSettings)).Result;
          }
     }
}
``` 

3. Ersetzen Sie die Platzhalterwerte im Quellcode, den Sie in eingefügt haben, mithilfe der folgenden Werte:

   | Platzhalter | Wert | Beispiel |
   |:----------- |:----- |:--------|
   | \<application-id\> | Die ID der Azure AD-Anwendung wird der unter „MIP SDK: Setup und Konfiguration“ registrierten Anwendung zugewiesen (zwei Instanzen).  | 0edbblll-8773-44de-b87c-b8c6276d41eb |
   | \<friendly-name\> | Ein benutzerdefinierter Anzeigename für Ihre Anwendung. | AppInitialization |


4. Nun können Sie die Anwendung endgültig fertigstellen und etwaige Fehler beheben. Ihr Code sollte erfolgreich erstellt.

## <a name="next-steps"></a>Nächste Schritte

Jetzt, da Ihr Initialisierungscode vollständig ist, können Sie mit dem nächsten Schnellstart fortfahren. Darin lernen Sie die MIP-Datei-APIs kennen.

> [!div class="nextstepaction"]
> [Auflisten der Vertraulichkeitsbezeichnungen](quick-file-list-labels-csharp.md)
