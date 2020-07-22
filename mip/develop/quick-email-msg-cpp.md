---
title: 'Datei-API: Verarbeiten von E-Mail-Dateien (.msg-Dateien) (C++)'
description: In diesem Artikel erfahren Sie, wie Sie MSG-Dateien mithilfe der Datei-API des MIP-SDK verarbeiten können.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 04/08/2020
ms.author: v-anikep
ms.openlocfilehash: ef6f8db6915242a830d252eec4509fa67eecbb8c
ms.sourcegitcommit: 36413b0451ae28045193c04cbe2d3fb2270e9773
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403311"
---
# <a name="file-api---process-email-msg-files-c"></a>Datei-API: Verarbeiten von E-Mail-Dateien (.msg-Dateien) (C++)

Die Datei-API unterstützt Schutzvorgänge für MSG-Dateien genau wie für jeden anderen Dateityp. Der Unterschied besteht lediglich darin, dass für das SDK erforderlich ist, das MSG-Featureflag in der Anwendung zu aktivieren. Hier wird erläutert, wie dieses Flag festgelegt wird.

Wie bereits erläutert, erfordert die Instanziierung von `mip::FileEngine` ein Einstellungsobjekt, `mip::FileEngineSettings`. Sie können FileEngineSettings verwenden, um Parameter für benutzerdefinierte Einstellungen zu übergeben, die die Anwendung für eine bestimmte Instanz festlegen muss. Die `CustomSettings`-Eigenschaft von `mip::FileEngineSettings` wird verwendet, um das Flag für `enable_msg_file_type` festzulegen, damit MSG-Dateien verarbeitet werden können.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart für die Initialisierung der Datei-API (C++)](quick-app-initialization-cpp.md) ab, in dem Sie eine Visual Studio-Projektmappe für den Einstieg erstellen. Dieser Schnellstart zum Verarbeiten von E-Mail-Dateien (MSG-Dateien) für C++ baut auf dem vorherigen auf.
- Lesen Sie den Artikel [Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C++)](quick-file-list-labels-cpp.md).
- Lesen Sie den Artikel [Schnellstart: Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C++)](quick-file-set-get-label-cpp.md).
- Lesen Sie die Konzepte zu [E-Mail-Dateien](concept-email.md) für das MIP-SDK durch.
- Optional: Lesen Sie die Konzepte zu [Datei-Engines](concept-profile-engine-file-engine-cpp.md) für das MIP-SDK durch.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MSIP SDK](concept-handler-file-cpp.md) durch.

## <a name="prerequisite-implementation-steps"></a>Erforderliche Schritte vor der Implementierung

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Initialisierung der Clientanwendung (C++)“ erstellt haben.

2. Erstellen Sie ein PowerShell-Skript, um Zugriffstoken zu generieren. Dies wird im Schnellstart [Auflisten von Vertraulichkeitsbezeichnungen (C++)](quick-file-list-labels-cpp.md#create-a-powershell-script-to-generate-access-tokens) erläutert.

3. Implementieren Sie die Observerklasse, um `mip::FileHandler` zu überwachen. Dies wird im Schnellstart [Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C++)](quick-file-set-get-label-cpp.md#implement-an-observer-class-to-monitor-the-file-handler-object) erläutert.

## <a name="set-enable_msg_file_type-and-use-file-api-to-protect-msg-file"></a>Festlegen von enable_msg_file_type und Verwenden der Datei-API zum Schutz von MSG-Dateien

Fügen Sie den folgenden Konstruktionscode für die Datei-Engine ein, um `enable_msg_file_type flag` festzulegen und die Datei-Engine zum Schutz einer MSG-Datei zu verwenden.

1. Öffnen Sie mithilfe des *Projektmappen-Explorers* die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Fügen Sie die folgenden #include- und using-Direktiven unter den entsprechenden vorhandenen Direktiven am Anfang der Datei hinzu:

    ```cpp
    #include "filehandler_observer.h" 
    #include "mip/file/file_handler.h" 
    #include <iostream>
    #include "mip/protection/protection_descriptor_builder.h"
    #include "mip/protection_descriptor.h"
    using mip::FileHandler;
    using mip::ProtectionDescriptor;
    using mip::ProtectionDescriptorBuilder;
    using mip::ProtectionSettings;
    using std::endl;
    ```

3. Entfernen Sie die Implementierung der `main()`-Funktion aus dem vorherigen Schnellstart. Fügen Sie im `main()`-Bereich folgenden Code ein. Im folgenden Codeblock wird das `enable_msg_file_type`-Flag während der Erstellung der Datei-Engine festgelegt. Anschließend kann eine MSG-Datei von `mip::FileHandler`-Objekten verarbeitet werden, die mithilfe der Datei-Engine erstellt werden.

```cpp
int main()
{
    // Construct/initialize objects required by the application's profile object
    ApplicationInfo appInfo { "<application-id>",                    // ApplicationInfo object (App ID, name, version)
                              "<application-name>", 
                              "1.0" 
    };

    auto mipContext = mip::MipContext::Create(appInfo,
                                                "file_sample",
                                                mip::LogLevel::Trace,
                                                false,
                                                nullptr /*loggerDelegateOverride*/,
                                                nullptr /*telemetryOverride*/);

    auto profileObserver = make_shared<ProfileObserver>();                      // Observer object
    auto authDelegateImpl = make_shared<AuthDelegateImpl>("<application-id>");  // Authentication delegate object (App ID)
    auto consentDelegateImpl = make_shared<ConsentDelegateImpl>();              // Consent delegate object

    // Construct/initialize profile object
    FileProfile::Settings profileSettings(mipContext,mip::CacheStorageType::OnDisk,authDelegateImpl,
        consentDelegateImpl,profileObserver);

    // Set up promise/future connection for async profile operations; load profile asynchronously
    auto profilePromise = make_shared<promise<shared_ptr<FileProfile>>>();
    auto profileFuture = profilePromise->get_future();
    try
    {
        mip::FileProfile::LoadAsync(profileSettings, profilePromise);
    }
    catch (const std::exception& e)
    {
        std::cout << "An exception occurred. Are the Settings and ApplicationInfo objects populated correctly?\n\n"<< e.what() << "'\n";
        system("pause");
        return 1;
    }

    auto profile = profileFuture.get();

    // Construct/initialize engine object
    FileEngine::Settings engineSettings(
                            mip::Identity("<engine-account>"),      // Engine identity (account used for authentication)
                            "<engine-state>",                       // User-defined engine state
                            "en-US");                               // Locale (default = en-US)

    //Set enamble_msg_file_type flag as true
    std::vector<std::pair<string, string>> customSettings;
    customSettings.emplace_back(mip::GetCustomSettingEnableMsgFileType(), "true");
    engineSettings.SetCustomSettings(customSettings);

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
        cout << "An exception occurred... is the access token incorrect/expired?\n\n"<< e.what() << "'\n";
        system("pause");
        return 1;
    }

    //Set file paths
    string inputFilePath = "<input-file-path>"; //.msg file to be protected
    string actualFilePath = inputFilePath;
    string outputFilePath = "<output-file-path>"; //protected .msg file
    string actualOutputFilePath = outputFilePath;

    //Create a file handler for original file
    auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
    auto handlerFuture = handlerPromise->get_future();

    engine->CreateFileHandlerAsync(inputFilePath,
                                    actualFilePath,
                                    true,
                                    std::make_shared<FileHandlerObserver>(),
                                    handlerPromise);

    auto fileHandler = handlerFuture.get();

    //List templates available to the user and use one of them to protect the mail file.

    ///Listing of protection templates must be performed by creating protection engine as described in protection quick start

    string templateId = "<template-id>"; //protection template retrieved using protection engine

    //Create a protection descriptor using templateID and use it to set protection to the file
    auto descriptorBuilder = mip::ProtectionDescriptorBuilder::CreateFromTemplate(templateId);
    const std::shared_ptr<mip::ProtectionDescriptor>& descriptor = descriptorBuilder->Build();
    fileHandler->SetProtection(descriptor, ProtectionSettings());

    // Commit changes, save as outputFilePath
    auto commitPromise = std::make_shared<std::promise<bool>>();
    auto commitFuture = commitPromise->get_future();
    fileHandler->CommitAsync(outputFilePath, commitPromise);
    if (commitFuture.get()) {
        cout << "\n Protection applied to file: " << outputFilePath << endl;
    }
    else {
        cout << "Failed to protect: " + outputFilePath << endl;
        return 1;
    }

    // Create a new handler to read the protected file metadata
    auto protectedHandlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
    auto protectedHandlerFuture = protectedHandlerPromise->get_future();
    engine->CreateFileHandlerAsync(outputFilePath, 
                                   actualOutputFilePath, 
                                   true, 
                                   std::make_shared<FileHandlerObserver>(), 
                                   protectedHandlerPromise);

    auto protectedFileHandler = protectedHandlerFuture.get();

    cout << "Original file: " << inputFilePath << endl;
    cout << "Protected file: " << outputFilePath << endl;
    cout << "TemplateID applied to protected file : " 
            << protectedFileHandler->GetProtection()->GetProtectionDescriptor()->GetTemplateId() 
            << endl;
    cout << "Protection Owner of protected file : " 
            << protectedFileHandler->GetProtection()->GetProtectionDescriptor()->GetOwner() 
            << endl;

    // Application shutdown. Null out profile and engine, call ReleaseAllResources();
    // Application may crash at shutdown if resources aren't properly released.
    protectedFileHandler = nullptr;
    fileHandler = nullptr;
    engine = nullptr;
    profile = nullptr;
    mipContext = nullptr;

    return 0;
}
```

Weitere Informationen zu Dateivorgängen finden Sie unter [Dateihandlerkonzepte](concept-handler-file-cpp.md).

4. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<application-id\> | Die Anwendungs-ID, die beim Azure AD-Mandanten registriert ist, zum Beispiel `0edbblll-8773-44de-b87c-b8c6276d41eb` |
   | \<engine-account\> | Das Konto, das für die Identität der Engine verwendet wird, zum Beispiel `user@tenant.onmicrosoft.com` |
   | \<engine-state\> | Der benutzerdefinierte Anwendungsstatus, zum Beispiel `My engine state` |
   | \<input-file-path\> | Der vollständige Pfad zu einer Testeingabedatei für Meldungen, zum Beispiel `c:\\Test\\message.msg` |
   | \<output-file-path\> | Der vollständige Pfad zur Ausgabedatei, die eine bezeichnete Kopie der Eingabedatei ist. Beispiel: `c:\\Test\\message_protected.msg`. |
   | \<template-id\> | Die Vorlagen-ID, die mithilfe der Schutz-Engine abgerufen wurde, zum Beispiel `667466bf-a01b-4b0a-8bbf-a79a3d96f720` |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Drücken Sie **F6** (Projektmappe erstellen), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, drücken Sie **F5** (Debuggen starten), um Ihre Anwendung auszuführen.

```Console
    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/common
    Set $resourceUrl to: https://syncservice.o365syncservice.com/
    Sign in with user account: User@Contoso.onmicrosoft.com
    Enter access token: <Paste token here>
    Press any key to continue . . .

    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/common
    Set $resourceUrl to: https://aadrm.com
    Sign in with user account: User@Contoso.onmicrosoft.com
    Enter access token: <Paste token here>
    Press any key to continue . . .

    Protection applied to file: C:\Test_protected.msg

    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/37f4583d-9985-4e7f-a1ab-71afd8b55ba0
    Set $resourceUrl to: https://aadrm.com
    Sign in with user account: User@Contoso.onmicrosoft.com
    Enter access token: <Paste token here>
    Press any key to continue . . .
    Original file: C:\Test.msg
    Protected file: C:\Test_protected.msg
    TemplateID applied to protected file : 667466bf-a01b-4b0a-8bbf-a79a3d96f720
    Protection Owner of protected file : User@Contoso.OnMicrosoft.com

```

## <a name="troubleshooting"></a>Problembehandlung

### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C#-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| TemplateNotFoundException | Die Vorlagen-ID wurde nicht erkannt., CorrelationId=abb2ef59-ad09-4aa0-b731-f59a92711dad, CorrelationId.Description=FileHandler, HttpRequest.Id=8c688752-ccd2-4dca-ace3-b67b44176689;78538a57-a9fd-4717-8924-33581a04598b| Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, ist der Wert für templateID wahrscheinlich ungültig. Korrigieren Sie die Vorlagen-ID für den Schutz im Codeblock, und führen Sie das Projekt erneut aus. |