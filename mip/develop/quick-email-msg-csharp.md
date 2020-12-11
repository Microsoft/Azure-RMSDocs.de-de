---
title: 'Datei-API: Verarbeiten von E-Mail-Dateien (MSG-Dateien) (C#)'
description: In diesem Artikel erfahren Sie, wie Sie MSG-Dateien mithilfe der Datei-API des MIP-SDK verarbeiten können (C#).
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 04/08/2020
ms.author: v-anikep
ms.openlocfilehash: 04fc40fcf5e638c6b86723c90a3880f421af8025
ms.sourcegitcommit: 6322f840388067edbe3642661e313ff225be5563
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96535993"
---
# <a name="file-api---process-email-msg-files-c"></a>Datei-API: Verarbeiten von E-Mail-Dateien (MSG-Dateien) (C#)

Die Datei-API unterstützt Schutzvorgänge für MSG-Dateien genau wie für jeden anderen Dateityp. Der Unterschied besteht lediglich darin, dass für das SDK erforderlich ist, das MSG-Featureflag in der Anwendung zu aktivieren. Hier wird erläutert, wie dieses Flag festgelegt wird.

Wie bereits erläutert, erfordert die Instanziierung von `IFileEngine` ein Einstellungsobjekt, `FileEngineSettings`. Sie können FileEngineSettings verwenden, um Parameter für benutzerdefinierte Einstellungen zu übergeben, die die Anwendung für eine bestimmte Instanz festlegen muss. Die `CustomSettings`-Eigenschaft von `FileEngineSettings` wird verwendet, um das Flag für `enable_msg_file_type` festzulegen, damit MSG-Dateien verarbeitet werden können.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart für die Initialisierung der Clientanwendung (C#)](quick-app-initialization-csharp.md) ab, in dem Sie eine Visual Studio-Projektmappe für den Einstieg erstellen. Dieser Schnellstart zum Verarbeiten von E-Mail-Dateien (MSG-Dateien) für C# baut auf dem vorherigen auf.
- Lesen Sie die Konzepte zu [E-Mail-Dateien](concept-email.md) für das MIP-SDK durch.
- Optional: Lesen Sie die Konzepte zu [Datei-Engines](concept-profile-engine-file-engine-cpp.md) für das MIP-SDK durch.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MSIP SDK](concept-handler-file-cpp.md) durch.

## <a name="set-enable_msg_file_type-and-use-file-api-for-protecting-msg-file"></a>Festlegen von enable_msg_file_type und Verwenden der Datei-API zum Schutz von MSG-Dateien

Sie können den Schnellstart zur Anwendunginitialisierung mit der Datei-API fortsetzen, indem Sie den Konstruktionscode für die Datei-Engine so ändern, dass `enable_msg_file_type flag` festgelegt ist. Anschließend können Sie die Datei-Engine verwenden, um MSG-Dateien zu schützen.

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Anwendungsinitialisierung mit der Datei-API (C#)“.

2. Öffnen Sie im Projektmappen-Explorer die CS-Datei des Projekts, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Entfernen Sie die Implementierung der `Main()`-Funktion aus dem vorherigen Schnellstart. Fügen Sie im `Main()`-Bereich folgenden Code ein. Im folgenden Codeblock wird das `enable_msg_file_type`-Flag während der Erstellung der Datei-Engine festgelegt. Anschließend kann eine MSG-Datei von `IFileHandler`-Objekten verarbeitet werden, die mithilfe der Datei-Engine erstellt werden.

    ```csharp
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

        MipContext mipContext = MIP.CreateMipContext(appInfo,"mip_data",LogLevel.Trace,null,null);

        // Initialize and instantiate the File Profile.
        // Create the FileProfileSettings object.
        // Initialize file profile settings to create/use local state.
        var profileSettings = new FileProfileSettings(mipContext, 
                                    CacheStorageType.OnDiskEncrypted, 
                                    new ConsentDelegateImplementation());

        // Load the Profile async and wait for the result.
        var fileProfile = Task.Run(async () => await MIP.LoadFileProfileAsync(profileSettings)).Result;

        // Create a FileEngineSettings object, then use that to add an engine to the profile.
        var customSettings = new List<KeyValuePair<string, string>>();
        customSettings.Add(new KeyValuePair<string, string>("enable_msg_file_type", "true"));

        // Create a FileEngineSettings object, then use that to add an engine to the profile.
        var engineSettings = new FileEngineSettings("user1@tenant.com", authDelegate, "", "en-US");
        engineSettings.Identity = new Identity("user1@tenant.com");
        //set custom settings for the engine
        engineSettings.CustomSettings = customSettings;

        //Add fileEngine to profile
        var fileEngine = Task.Run(async () => await fileProfile.AddEngineAsync(engineSettings)).Result;

        //Set file paths
        string inputFilePath = "<input-file-path>"; //.msg file to be protected
        string actualFilePath = inputFilePath;
        string outputFilePath = "<output-file-path>"; //protected .msg file
        string actualOutputFilePath = outputFilePath;

        //Create a file handler for original file
        var fileHandler = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(inputFilePath, 
                                                                    actualFilePath, 
                                                                    true)).Result;

        // List templates available to the user and use one of them to protect the mail file.

            /// Listing of protection templates has to be performed by creating protection engine as described in protection quick start

        string templateId = "<template-id>"; //protection template retrieved using protection engine

        // Construct a protection descriptor on input file and use the same to set protection to the file
        ProtectionDescriptor descriptor = new ProtectionDescriptor(templateId);
        fileHandler.SetProtection(descriptor, new ProtectionSettings());

        // Commit changes, save as outputFilePath
        var result = Task.Run(async () => await fileHandler.CommitAsync(outputFilePath)).Result;

        // Create a new handler to read the protected file metadata
        var handlerModified = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(outputFilePath, 
                                                                        actualOutputFilePath, 
                                                                        true)).Result;

        Console.WriteLine(string.Format("Original file: {0}", inputFilePath));
        Console.WriteLine(string.Format("Protected file: {0}", outputFilePath));
        Console.WriteLine(string.Format("TemplateID applied to file: {0} \r\nProtectionOwner: {1}", 
            handlerModified.Protection.ProtectionDescriptor.TemplateId,handlerModified.Protection.Owner));
        Console.WriteLine("Press a key to continue.");
        Console.ReadKey();

        // Application Shutdown
        fileHandler = null;
        handlerModified = null;
        fileEngine = null;
        fileProfile = null;
        mipContext = null;
    }

    ```

    Weitere Informationen zu Dateivorgängen finden Sie unter [Dateihandlerkonzepte](concept-handler-file-cpp.md).

4. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<input-file-path\> | Der vollständige Pfad zu einer Testeingabedatei für Meldungen, zum Beispiel `c:\\Test\\message.msg` |
   | \<output-file-path\> | Der vollständige Pfad zur Ausgabedatei, die eine bezeichnete Kopie der Eingabedatei ist. Beispiel: `c:\\Test\\message_protected.msg`. |
   | \<template-id\> | Die Vorlagen-ID, die mithilfe der Schutz-Engine abgerufen wurde, zum Beispiel `667466bf-a01b-4b0a-8bbf-a79a3d96f720` |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Drücken Sie **F6** (Projektmappe erstellen), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, drücken Sie **F5** (Debuggen starten), um Ihre Anwendung auszuführen.

```Console
    Original file: C:\Test.msg
    Protected file: C:\Test_protected.msg
    TemplateID applied to file: 667466bf-a01b-4b0a-8bbf-a79a3d96f720
    ProtectionOwner: user1@tenant.com
    Press a key to continue.
```

## <a name="troubleshooting"></a>Problembehandlung

### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C#-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| NetworkException: Der RMS-Dienst hat ungültige Eingaben in der Anforderung erkannt. RMS-Fehlercode: Microsoft.RightsManagement.Exceptions.BadInputException | * Die Parameter sind ungültig, wenn sowohl „TemplateID“ als auch „Policy“ NULL sind. CorrelationId=f265b189-ebf6-4b30-a191-41539cdff215, CorrelationId.Description=FileHandler, HttpRequest.Id=04990d53-cf12-4969-9c80-06e365b312f2;d5fb4794-ac84-4445-abc6-647e41df62b2, HttpRequest.SanitizedUrl=https://api.aadrm.com/my/v2/publishinglicenses, HttpResponse.StatusCode=400, NetworkError.Category=FailureResponseCode* | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, ist der Wert für templateID wahrscheinlich ungültig. Korrigieren Sie die Vorlagen-ID für den Schutz im Codeblock, und führen Sie das Projekt erneut aus. |
| TemplateNotFoundException | *Die Vorlagen-ID wurde nicht erkannt., CorrelationId=abb2ef59-ad09-4aa0-b731-f59a92711dad, CorrelationId.Description=FileHandler, HttpRequest.Id=8c688752-ccd2-4dca-ace3-b67b44176689;78538a57-a9fd-4717-8924-33581a04598b* | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, ist der Wert für templateID wahrscheinlich ungültig. Korrigieren Sie die Vorlagen-ID für den Schutz im Codeblock, und führen Sie das Projekt erneut aus. |
