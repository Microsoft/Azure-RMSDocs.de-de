---
title: 'Vorgehensweise: Erneutes Veröffentlichen in C++'
description: In diesem Artikel erfahren Sie, wie Sie den Schutzhandler zum erneuten Veröffentlichen wiederverwenden.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 05/01/2020
ms.author: v-anikep
ms.openlocfilehash: 49fac8fb748cec60abbe3af779670c928c1608a1
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91421149"
---
# <a name="file-api-re-publishing-quickstart-c"></a>Schnellstart für die erneute Veröffentlichung mit der Datei-API ( C++ )

## <a name="overview"></a>Übersicht

Eine Übersicht zu diesem Szenario und dessen Verwendung finden Sie unter [Erneutes Veröffentlichen mit dem MIP SDK](concept-republishing.md).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart zum Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C++)](quick-file-set-get-label-cpp.md) ab. Darin wird eine Visual Studio-Startprojektmappe zum Auflisten der Vertraulichkeitsbezeichnungen einer Organisation erstellt, mit der Vertraulichkeitsbezeichnungen in einer Datei festgelegt oder aus dieser gelesen werden können. Dieser Schnellstart zum Herabstufen oder Entfernen einer Bezeichnung mit erforderlicher Begründung in C++ baut auf dem vorherigen auf.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MIP SDK](concept-handler-file-cpp.md) durch.
- Optional: Lesen Sie sich die Konzepte zu [Schutzhandlern im MIP SDK](concept-handler-protection-cpp.md) durch.

## <a name="add-logic-to-filehandler-observer-class"></a>Hinzufügen von Logik zur FileHandler Observer-Klasse

Sie müssen Rückrufe für die async-Methode für Erfolg und Fehler wie unten beschrieben definieren, um in der Lage zu sein, eine geschützte Datei mit der `GetDecryptedTemporaryFileAsync()`-Methode zu entschlüsseln, die durch `mip::FileHandler` verfügbar gemacht wird.

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C++)“.

2. Öffnen Sie über den Projektmappen-Explorer die `filehandler_observer.h`-Datei in Ihrem Projekt. Fügen Sie vor dem Ende der FileHandler-Definition, vor `};`, die folgenden Zeilen hinzu, um die Methode zu deklarieren.

    ```cpp
        void OnGetDecryptedTemporaryFileSuccess(const std::string& decryptedFilePath, const std::shared_ptr<void>& context) override;
        void OnGetDecryptedTemporaryFileFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
    ```

3. Öffnen Sie über den Projektmappen-Explorer die `filehandler_observer.cpp`-Datei in Ihrem Projekt. Fügen Sie am Ende der Datei die folgenden Zeilen hinzu, um die Methode zu definieren.

    ```cpp

        void FileHandlerObserver::OnGetDecryptedTemporaryFileSuccess(const std::string& decryptedFilePath, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::string>>(context);
        promise->set_value(decryptedFilePath);
        }

        void FileHandlerObserver::OnGetDecryptedTemporaryFileFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::string>>(context);
        promise->set_exception(error);
        }
    ```

## <a name="add-logic-to-edit-and-republish-a-protected-file"></a>Hinzufügen von Logik zum Bearbeiten und erneuten Veröffentlichen einer geschützten Datei

1. Öffnen Sie im Projektmappen-Explorer die CPP-Datei des Projekts, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Fügen Sie gegen Ende des main()-Abschnitts zwischen system("pause"); und return0; (wo Sie im vorherigen Schnellstart aufgehört haben) den folgenden Code ein:

```cpp
//Originally protected file's path.
std::string protectedFilePath = "<protected-file-path>";

// Create file handler for the file
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
auto handlerFuture = handlerPromise->get_future();
engine->CreateFileHandlerAsync(protectedFilePath, 
                                protectedFilePath, 
                                true, 
                                std::make_shared<FileHandlerObserver>(), 
                                handlerPromise);
auto protectedFileHandler = handlerFuture.get();

// retieve and store protection handler from file
auto protectionHandler = protectedFileHandler->GetProtection();

//Check if the user has the 'Edit' right to the file and if so decrypt the file.
if (protectionHandler->AccessCheck("Edit")) {

    // Decrypt file to temp path using the same file handler
    auto tempPromise = std::make_shared<std::promise<string>>();
    auto tempFuture = tempPromise->get_future();
    protectedFileHandler->GetDecryptedTemporaryFileAsync(tempPromise);
    auto tempPath = tempFuture.get();

    /// Write code here to perform further operations for edit ///

    /// Follow steps below for re-protecting the edited file ///

    // Create a new file handler using the temporary file path.
    auto reprotectPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
    auto reprotectFuture = reprotectPromise->get_future();
    engine->CreateFileHandlerAsync(tempPath, 
                                    tempPath, 
                                    true, 
                                    std::make_shared<FileHandlerObserver>(), 
                                    reprotectPromise);
    auto republishHandler = reprotectFuture.get();

    // Set protection using the ProtectionHandler from the original consumption operation.
    republishHandler->SetProtection(protectionHandler);
    std::string reprotectedFilePath = "<protected-file-path>";

    // Commit changes
    auto republishPromise = std::make_shared<std::promise<bool>>();
    auto republishFuture = republishPromise->get_future();
    republishHandler->CommitAsync(reprotectedFilePath, republishPromise);

    // Validate republishing
    cout << "Protected File: " + protectedFilePath<<endl;
    cout << "Protected Label ID: " + protectedFileHandler->GetLabel()->GetLabel()->GetId() << endl;
    cout << "Protection Owner: " + protectedFileHandler->GetProtection()->GetOwner() << endl<<endl;

    cout << "Republished File: " + reprotectedFilePath<<endl;
    cout << "Republished Label ID: " + republishHandler->GetLabel()->GetLabel()->GetId() << endl;
    cout << "Republished Owner: " + republishHandler->GetProtection()->GetOwner() << endl;
}
```

3. Suchen Sie am Ende der Main()-Methode den Block zum Herunterfahren der Anwendung, den Sie im vorherigen Schnellstart erstellt haben, und fügen Sie die folgenden Handlerzeilen zum Freigeben der Ressourcen hinzu:

    ````csharp
        protectedFileHandler = nullptr;
        protectionHandler = nullptr;

    ````

4. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<protected-file-path\> | Dies ist die geschützte Datei aus der vorherigen Schnellstartanleitung. |
   | \<reprotected-file-path\> | Dies ist der Ausgabedateipfad für die erneute Veröffentlichung der angepassten Datei. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B ( **Projektmappe erstellen** ), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 ( **Debuggen starten** ) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, fragt die Anwendung jedes Mal nach einem Zugriffstoken, wenn das SDK Ihre `AcquireOAuth2Token()`-Methode aufruft. Führen Sie das PowerShell-Skript wie zuvor im Schnellstart „Festlegen und Abrufen von Vertraulichkeitsbezeichnungen“ aus, um jedes Mal das Token anhand der angegebenen Werte für $authority und $resourceUrl abzurufen.

  ```console
    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/common
    Set $resourceUrl to: https://syncservice.o365syncservice.com/
    Sign in with user account: user1@tenant.onmicrosoft.com
    Enter access token: <paste-access-token-here>
    Press any key to continue . . .

    Sensitivity labels for your organization:
    Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
    Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
    General : f42a3342-8706-4288-bd31-ebb85995028z
    Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
    Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z
    Press any key to continue . . .

    Applying Label ID 074e457c-5848-4542-9a6f-34a182080e7z to C:\Test\Test.docx
    Committing changes

    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/common
    Set $resourceUrl to: https://aadrm.com
    Sign in with user account: user1@tenant.onmicrosoft.com
    Enter access token: <paste-access-token-here>
    Press any key to continue . . .

    Label committed to file: C:\Test\Test_labeled.docx
    Press any key to continue . . .

    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/37f4583d-9985-4e7f-a1ab-71afd8b55ba0
    Set $resourceUrl to: https://aadrm.com
    Sign in with user account: user1@tenant.onmicrosoft.com
    Enter access token: <paste-access-token-here>
    Press any key to continue . . .

    Getting the label committed to file: C:\Test\Test_labeled.docx
    Name: Confidential
    Id: 074e457c-5848-4542-9a6f-34a182080e7z
    Press any key to continue . . .
    Protected File: C:\Test\Test_labeled.docx
    Protected Label ID: 074e457c-5848-4542-9a6f-34a182080e7z
    Protection Owner: user1@tenant.onmicrosoft.com

    Republished File: c:\Test\Test_republished.docx
    Republished Label ID: 074e457c-5848-4542-9a6f-34a182080e7z
    Republished Owner: user1@tenant.onmicrosoft.com

    Press any key to close this window . . .

   ```
   