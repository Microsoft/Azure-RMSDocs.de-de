---
title: 'Schnellstart: Initialisierung für C#-Clients des MSIP SDK'
description: Schnellstart zum Schreiben der Initialisierungslogik für C#-Clientanwendungen des MSIP SDK (Microsoft Azure Information Protection)
author: tommoser
ms.service: information-protection
ms.topic: quickstart
ms.date: 07/30/2019
ms.author: tommos
ms.custom: has-adal-ref
ms.openlocfilehash: fa8b41850468ed545512f8facc488ff0517a8b41
ms.sourcegitcommit: 298843953f9792c5879e199fd1695abf3d25aa70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2020
ms.locfileid: "82972083"
---
# <a name="quickstart-client-application-initialization-c"></a>Schnellstart: Initialisierung der Clientanwendung (C#)

In diesem Schnellstart lernen Sie, wie Sie das Muster für die Clientinitialisierung implementieren können, das vom .NET-Wrapper für das MSIP SDK zur Laufzeit verwendet wird.

> [!NOTE]
> Die in diesem Schnellstart beschriebenen Schritte müssen für sämtliche Clientanwendungen ausgeführt werden, für die die Datei- oder Richtlinien-APIs des .NET-Wrappers für das MSIP SDK verwendet werden. Die Schutz-API ist noch nicht verfügbar. Dieser Schnellstart konzentriert sich zwar auf die Verwendung der Datei-APIs, das gleiche Muster ist jedoch auch auf Clients anwendbar, die Richtlinien- und Datenschutz-APIs verwenden. Beginnend mit diesem Schnellstart sollten die nächsten Schnellstarts nacheinander ausgeführt werden, da diese aufeinander aufbauen.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie Folgendes sicher, sofern dies noch nicht geschehen ist:

- Führen Sie die Schritte unter [Microsoft Information Protection (MIP) SDK: Setup und Konfiguration](setup-configure-mip.md) aus. Dieser Schnellstart „Initialisierung der Clientanwendung“ hat das ordnungsgemäße Setup und die ordnungsgemäße Konfiguration des SDK zum Thema.
- Optional:
  - Überprüfen Sie [Profile and engine objects](concept-profile-engine-cpp.md) (Profil- und Engine-Objekte). Bei den Profil- und Engine-Objekten handelt es sich um universelle Konzepte, die von Clients benötigt werden, die die MIP-Datei-/Richtlinien-/Datenschutz-APIs verwenden.
  - Überprüfen Sie [Authentifizierungskonzepte](concept-authentication-cpp.md), um zu erfahren, wie die Authentifizierung und die Zustimmung von der SDK- und der Clientanwendung implementiert werden.

## <a name="create-a-visual-studio-solution-and-project"></a>Erstellen einer Visual Studio-Lösung und eines -Projekts

Zunächst erstellen und konfigurieren wir die erste Lösung und das erste Projekt in Visual Studio. Dies bildet die Grundlage für die anderen Schnellstarts.

1. Öffnen Sie Visual Studio 2017, wählen Sie das Menü **Datei** und anschließend **Neu** > **Projekt** aus. Geben Sie im Dialogfeld **Neues Projekt** Folgendes ein:
   - Wählen Sie im linken Bereich unter **Installiert** > **Visual C#** den Eintrag **Windows Desktop** aus.
   - Wählen Sie im mittleren Bereich **Konsolen-App (.NET Framework)** aus.
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

3. Wiederholen Sie die oben aufgeführten Schritte, um das Paket für die Datei-API des MSIP SDK hinzuzufügen, aber fügen Sie diesmal „Microsoft.IdentityModel.Clients.ActiveDirectory“ zur Anwendung hinzu.

## <a name="implement-an-authentication-delegate"></a>Implementieren eines Authentifizierungsdelegats

Das MIP SDK implementiert die Authentifizierung mithilfe der Klassenerweiterbarkeit, die einen Mechanismus zur Freigabe der Authentifizierung für die Clientanwendung bietet. Der Client muss ein geeignetes OAuth2-Zugriffstoken abrufen und zur Laufzeit für das MIP SDK bereitstellen.

Erstellen Sie nun eine Implementierung für einen Authentifizierungsdelegaten, indem Sie die Schnittstelle `Microsoft.InformationProtection.IAuthDelegate` des SDK erweitern und die virtuelle Funktion `IAuthDelegate.AcquireToken()` überschreiben bzw. implementieren. Der Authentifizierungsdelegat wird später von den Objekten `FileProfile` und `FileEngine` der Datei instanziiert und verwendet.

1. Klicken Sie mit der rechten Maustaste auf den Projektnamen in Visual Studio, und klicken Sie dann auf **Hinzufügen** > **Klasse**.
2. Geben Sie im Feld **Name** „AuthDelegateImplementation“ ein. Klicken Sie auf **Hinzufügen**.
3. Fügen Sie using-Anweisungen für die ADAL- und die MSIP-Bibliothek hinzu:

     ```csharp
     using Microsoft.InformationProtection;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     ```

4. Legen Sie `AuthDelegateImplementation` darauf fest, `Microsoft.InformationProtection.IAuthDelegate` zu erben und eine private Variable von `Microsoft.InformationProtection.ApplicationInfo` sowie einen Konstruktor zu implementieren, der den gleichen Dateityp akzeptiert.

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

Das Objekt `ApplicationInfo` enthält drei Eigenschaften. `_appInfo.ApplicationId` wird in der Klasse `AuthDelegateImplementation` verwendet, um der Authentifizierungsbibliothek die Client-ID bereitzustellen. `ApplicationName` und `ApplicationVersion` werden in Azure Information Protection Analytics-Berichten aufgeführt.

5. Fügen Sie die Methode `public string AcquireToken()` hinzu. Diese Methode akzeptiert `Microsoft.InformationProtection.Identity` und drei Zeichenfolgen: Autoritäts-URL, Ressourcen-URI und Ansprüche, sofern erforderlich. Diese Zeichenfolgenvariablen werden über die API an die Authentifizierungsbibliothek übergeben und sollten nicht geändert werden. Änderungen können zu Authentifizierungsfehlern führen.

     ```csharp
     public string AcquireToken(Identity identity, string authority, string resource, string claims)
     {
          AuthenticationContext authContext = new AuthenticationContext(authority);
          var result = Task.Run(async() => await authContext.AcquireTokenAsync(resource, AppInfo.ApplicationId, new Uri(redirectUri), new PlatformParameters(PromptBehavior.Always))).Result;
          return result.AccessToken;
     }
     ```

## <a name="implement-a-consent-delegate"></a>Implementieren eines Zustimmungsdelegats

Erstellen Sie nun eine Implementierung für einen Zustimmungsdelegaten, indem Sie die Schnittstelle `Microsoft.InformationProtection.IConsentDelegate` des SDK erweitern und `GetUserConsent()` überschreiben bzw. implementieren. Der Zustimmungsdelegat wird später von den Profil- und Engine-Objekten der Datei instanziiert und verwendet. Der Zustimmungsdelegat enthält im Parameter `url` die Adresse des Diensts, dessen Aufruf der Benutzer zustimmen muss. Der Delegat sollte einen Ablauf enthalten, durch den der Benutzer dem Zugriff auf den Dienst zustimmen oder diesen ablehnen kann. Hartcodieren Sie `Consent.Accept` für diesen Schnellstart.

1. Fügen Sie mit der gleichen Visual Studio-Funktion „Klasse hinzufügen“, die wir vorher verwendet haben, eine weitere Klasse zu Ihrem Projekt hinzu. Geben Sie dieses Mal „ConsentDelegateImplementation“ in das Feld **Klassenname** ein.

2. Aktualisieren Sie jetzt **ConsentDelegateImpl.cs**, damit Ihre neue Zustimmungsdelegatklasse implementiert wird: Fügen Sie die using-Anweisung für `Microsoft.InformationProtection` hinzu, und legen Sie die Klasse darauf fest, `IConsentDelegate` zu erben.

     ```csharp
     class ConsentDelegateImplementation : IConsentDelegate
     {
          public Consent GetUserConsent(string url)
          {
               return Consent.Accept;
          }
     }
     ```

3. Sie können optional versuchen, die Projektmappe zu erstellen, um sicherzustellen, dass diese fehlerfrei kompiliert wird.

## <a name="initialize-the-mip-sdk-managed-wrapper"></a>Initialisieren des verwalteten Wrappers des MSIP SDK

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CS-Datei im Projekt, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Entfernen Sie die generierte Implementierung von `main()`.

3. Der verwaltete Wrapper enthält eine statische Klasse (`Microsoft.InformationProtection.MIP`), die für die Initialisierung, das Erstellen eines `MipContext`-Elements, das Laden von Profilen und das Freigeben von Ressourcen verwendet wird. Zum Initialisieren des Wrappers für Datei-API-Vorgänge rufen Sie `MIP.Initialize()` auf und übergeben `MipComponent.File`, um die erforderlichen Bibliotheken für Dateivorgänge zu laden.

4. Fügen Sie in der `Main()`-Methode der Datei *Program.cs* folgenden Codeausschnitt ein. Ersetzen Sie **\<application-id\>** hierbei durch die ID der Azure AD-Anwendungsregistierung, die Sie zuvor erstellt haben.

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.InformationProtection;
using Microsoft.InformationProtection.Exceptions;
using Microsoft.InformationProtection.File;
using Microsoft.InformationProtection.Protection;

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

## <a name="construct-a-file-profile-and-engine"></a>Erstellen eines Dateiprofils und einer Datei-Engine

Wie bereits erwähnt sind für SDK-Clients, die MSIP-APIs verwenden, Profilobjekte und Engine-Objekte erforderlich. Vervollständigen Sie den Programmierabschnitt dieses Schnellstarts, indem Sie Code hinzufügen, um die nativen DLLs zu laden und anschließend die Profilobjekte und Engine-Objekte zu instanziieren.



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
               // Initialize Wrapper for File API operations.
               MIP.Initialize(MipComponent.File);

               // Create ApplicationInfo, setting the clientID from Azure AD App Registration as the ApplicationId.
               ApplicationInfo appInfo = new ApplicationInfo()
               {
                    ApplicationId = clientId,
                    ApplicationName = appName,
                    ApplicationVersion = "1.0.0"
               };

               // Instantiate the AuthDelegateImpl object, passing in AppInfo.
               AuthDelegateImplementation authDelegate = new AuthDelegateImplementation(appInfo);

               MipContext mipContext = MIP.CreateMipContext(appInfo,
                                        "mip_data",
                                        LogLevel.Trace,
                                        null,
                                        null);

               // Initialize and instantiate the File Profile.
               // Create the FileProfileSettings object.
               // Initialize file profile settings to create/use local state.
               var profileSettings = new FileProfileSettings(mipContext,
                                        CacheStorageType.OnDiskEncrypted,
                                        new ConsentDelegateImplementation());

               // Load the Profile async and wait for the result.
               var fileProfile = Task.Run(async () => await MIP.LoadFileProfileAsync(profileSettings)).Result;

               // Create a FileEngineSettings object, then use that to add an engine to the profile.
               var engineSettings = new FileEngineSettings("user1@tenant.com", authDelegate "", "en-US");
               engineSettings.Identity = new Identity("user1@tenant.com");
               var fileEngine = Task.Run(async () => await fileProfile.AddEngineAsync(engineSettings)).Result;

               // Application Shutdown
               // handler = null; // This will be used in later quick starts.
               fileEngine = null;
               fileProfile = null;
               mipContext = null;
          }
     }
}
```

3. Ersetzen Sie die Platzhalterwerte in dem Quellcode, den Sie eingefügt haben, durch die folgenden Werte:

   | Platzhalter | Wert | Beispiel |
   |:----------- |:----- |:--------|
   | \<application-id\> | Die ID der Azure AD-Anwendung wird der unter „MIP SDK: Setup und Konfiguration“ registrierten Anwendung zugewiesen (zwei Instanzen).  | 0edbblll-8773-44de-b87c-b8c6276d41eb |
   | \<friendly-name\> | Ein benutzerdefinierter Anzeigename für Ihre Anwendung. | AppInitialization |


4. Nun können Sie die Anwendung endgültig fertigstellen und etwaige Fehler beheben. Der Code sollte dann erfolgreich erstellt werden.

## <a name="next-steps"></a>Nächste Schritte

Jetzt, da Ihr Initialisierungscode vollständig ist, können Sie mit dem nächsten Schnellstart fortfahren. Darin lernen Sie die MIP-Datei-APIs kennen.

> [!div class="nextstepaction"]
> [Auflisten der Vertraulichkeitsbezeichnungen](quick-file-list-labels-csharp.md)
