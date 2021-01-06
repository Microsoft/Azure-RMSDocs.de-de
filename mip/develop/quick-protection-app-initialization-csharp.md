---
title: 'Schnellstart: Initialisierung der Clientanwendung – Schutz-API (C#)'
description: Schnellstart zum Schreiben der Initialisierungslogik für Clientanwendungen mit Schutz-API des Microsoft Information Protection (MIP) SDK für C#.
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.date: 03/30/2020
ms.author: mbaldwin
ms.openlocfilehash: bfa1866618e65f1f9f215cb70fd76254623777d0
ms.sourcegitcommit: 8e48016754e6bc6d051138b3e3e3e3edbff56ba5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865177"
---
# <a name="quickstart-client-application-initialization-for-protection-apis-c"></a>Schnellstart: Initialisierung der Clientanwendung für Schutz-APIs (C#)

In diesem Schnellstart lernen Sie, wie Sie das Muster für die Clientinitialisierung implementieren können, das vom .NET-Wrapper für das MIP SDK zur Laufzeit verwendet wird.

> [!NOTE]
> Die in diesem Schnellstart beschriebenen Schritte müssen für sämtliche Clientanwendungen ausgeführt werden, die die Schutz-API des .NET-Wrappers für MIP verwenden. Diese Schnellstarts müssen nach der Anwendungsinitialisierung und der Implementierung von Klassen für Authentifizierungsdelegate und Zustimmungsdelegate nacheinander ausgeführt werden.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie Folgendes sicher, sofern dies noch nicht geschehen ist:

- Führen Sie die Schritte unter [Microsoft Information Protection (MIP) SDK: Setup und Konfiguration](setup-configure-mip.md) aus. Dieser Schnellstart zum Einrichten von Schutzprofil und -Engine basiert auf der ordnungsgemäßen Einrichtung und Konfiguration des SDK.
- Optional:
  - Überprüfen Sie [Profil- und Engine-Objekte](concept-profile-engine-cpp.md). Bei den Profil- und Engine-Objekten handelt es sich um universelle Konzepte, die von Clients benötigt werden, die die MIP-Datei-/Richtlinien-/Datenschutz-APIs verwenden.
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

3. Wiederholen Sie die oben aufgeführten Schritte, um das Paket für die Schutz-API des MIP SDK hinzuzufügen, aber fügen Sie dieses Mal „Microsoft.IdentityModel.Clients.ActiveDirectory“ zur Anwendung hinzu.

## <a name="implement-an-authentication-delegate-and-a-consent-delegate"></a>Implementieren eines Authentifizierungs- und Zustimmungsdelegaten

Sofern nicht bereits geschehen, führen Sie die unter [Schnellstart: Initialisierung der Clientanwendung (C#)](quick-app-initialization-csharp.md) aufgeführten Schritte aus, um einen Authentifizierungs- und Zustimmungsdelegaten zu implementieren.

## <a name="initialize-the-mip-sdk-managed-wrapper"></a>Initialisieren des verwalteten Wrappers des MIP SDK

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CS-Datei im Projekt, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Entfernen Sie die generierte Implementierung von `main()`.

3. Der verwaltete Wrapper enthält eine statische Klasse (`Microsoft.InformationProtection.MIP`), die für die Initialisierung, das Erstellen eines `MipContext`-Elements, das Laden von Profilen und das Freigeben von Ressourcen verwendet wird. Zum Initialisieren des Wrappers für Datei-API-Vorgänge rufen Sie `MIP.Initialize()` auf und übergeben `MipComponent.Protection`, um die benötigten Bibliotheken für Schutzvorgänge zu laden.

4. Fügen Sie in der `Main()`-Methode der Datei *Program.cs* folgenden Codeausschnitt ein. Ersetzen Sie **\<application-id\>** hierbei durch die ID der Azure AD-Anwendungsregistierung, die Sie zuvor erstellt haben.

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.InformationProtection;
using Microsoft.InformationProtection.Exceptions;
using Microsoft.InformationProtection.Protection;

namespace mip_sdk_dotnet_quickstart
{
    class Program
    {
        private const string clientId = "<application-id>";
        private const string appName = "<friendly-name>";

        static void Main(string[] args)
        {
            //Initialize Wrapper for Protection API operations
            MIP.Initialize(MipComponent.Protection);
        }
    }
}
```

## <a name="construct-a-protection-profile-and-engine"></a>Erstellen von Schutzprofil und -Engine

Wie bereits erwähnt, sind für SDK-Clients mit Verwendung von MIP-APIs Profilobjekte und Engine-Objekte erforderlich. Vervollständigen Sie den Programmierabschnitt dieses Schnellstarts, indem Sie Code hinzufügen, um die nativen DLLs zu laden und anschließend die Profilobjekte und Engine-Objekte zu instanziieren.

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.InformationProtection;
using Microsoft.InformationProtection.Exceptions;
using Microsoft.InformationProtection.Protection;

namespace mip_sdk_dotnet_quickstart
{
     class Program
     {
          private const string clientId = "<application-id>";
          private const string appName = "<friendly-name>";

          static void Main(string[] args)
          {
               // Initialize Wrapper for Protection API operations.
               MIP.Initialize(MipComponent.Protection);

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

               // Initialize and instantiate the ProtectionProfile.
               // Create the ProtectionProfileSettings object.
               // Initialize protection profile settings to create/use local state.
               var profileSettings = new ProtectionProfileSettings(mipContext,
                                        CacheStorageType.OnDiskEncrypted,                                        
                                        new ConsentDelegateImplementation());

               // Load the Profile async and wait for the result.
               var protectionProfile = Task.Run(async () => await MIP.LoadProtectionProfileAsync(profileSettings)).Result;

               // Create a ProtectionEngineSettings object, then use that to add an engine to the profile.
               var engineSettings = new ProtectionEngineSettings("user1@tenant.com", authDelegate, "", "en-US");
               engineSettings.Identity = new Identity("user1@tenant.com");
               var protectionEngine = Task.Run(async () => await protectionProfile.AddEngineAsync(engineSettings)).Result;

               // Application Shutdown
               // handler = null; // This will be used in later quick starts.
               protectionEngine = null;
               protectionProfile = null;
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

Jetzt, da Ihr Initialisierungscode vollständig ist, können Sie mit dem nächsten Schnellstart fortfahren. Darin beginnen Sie damit, die MIP-Schutz-API zu testen.

> [!div class="nextstepaction"]
> [Auflisten von Schutzvorlagen](quick-protection-list-templates-csharp.md)
