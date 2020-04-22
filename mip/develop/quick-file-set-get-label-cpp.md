---
title: 'Schnellstart: Festlegen und Abrufen einer Vertraulichkeitsbezeichnung für eine Datei mit dem C++ MIP SDK'
description: In diesem Schnellstart wird veranschaulicht, wie Sie mit dem Microsoft Information Protection C++ SDK eine Vertraulichkeitsbezeichnung für eine Datei festlegen und abrufen können.
services: information-protection
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 6923bdf83f76a3e2a30e49bae27e9f7be963a623
ms.sourcegitcommit: a3f901e479abbe056f8936a96b7253f0826d1415
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "75556026"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>Schnellstart: Festlegen und Abrufen einer Vertraulichkeitsbezeichnung (C++)

In diesem Schnellstart wird gezeigt, wie Sie weitere MIP-Datei-APIs nutzen. Durch Verwendung einer der Vertraulichkeitsbezeichnungen, die Sie im vorherigen Schnellstart aufgelistet haben, verwenden Sie einen Dateihandler zum Festlegen/Abrufen der Bezeichnung für eine Datei. Die Dateihandlerklasse macht verschiedene Vorgänge für das Festlegen/Abrufen von Bezeichnungen oder Schutz für unterstützte Dateitypen verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst [Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C++)](quick-file-list-labels-cpp.md) ab. Darin wird eine Visual Studio-Startprojektmappe zum Auflisten der Vertraulichkeitsbezeichnungen einer Organisation erstellt. Dieser Schnellstart „Festlegen und Abrufen einer Vertraulichkeitsbezeichnung“ baut auf den vorherigen auf.
- Optional: Sehen Sie sich die Konzepte zu [Dateihandlern im MIP SDK](concept-handler-file-cpp.md) an.

## <a name="implement-an-observer-class-to-monitor-the-file-handler-object"></a>Implementieren einer Observer-Klasse zum Überwachen des Dateihandlerobjekts

Ähnlich wie bei dem Observer, den Sie (für Dateiprofil und -Engine) im Schnellstart zur Anwendungsinitialisierung implementiert haben, implementieren Sie jetzt eine Observer-Klasse für ein Dateihandlerobjekt.

Erstellen Sie eine grundlegende Implementierung für die Observer-Klasse für einen Dateihandler, indem Sie die `mip::FileHandler::Observer`-Klasse des SDK erweitern. Der Observer wird instanziiert und später zum Überwachen von Dateihandlervorgängen verwendet.

1. Öffnen Sie die Visual Studio-Projektmappe, an der Sie im vorherigen Artikel „Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C++)“ gearbeitet haben.

2. Fügen Sie Ihrem Projekt eine neue Klasse hinzu, durch die die Dateien „header/.h“ und „implementation/.cpp“ für Sie generiert werden:

   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Hinzufügen** > **Klasse** aus.
   - Gehen Sie im Dialogfeld **Klasse hinzufügen** folgendermaßen vor:
     - Geben Sie im Feld **Klassenname** „filehandler_observer“ ein. Beachten Sie, dass sowohl das Feld **H-Datei** als auch das Feld **CPP-Datei** anhand des eingegebenen Namens automatisch aufgefüllt werden.
     - Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK**.

3. Nach dem Generieren der H- und der CPP-Datei für die Klasse werden beide Dateien auf Editor-Gruppenregisterkarten geöffnet. Aktualisieren Sie jetzt jede Datei, um die neue Observer-Klasse zu implementieren:

   - Aktualisieren Sie „filehandler_observer.h“, indem Sie die generierte `filehandler_observer`-Klasse auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include <memory>
     #include "mip/file/file_engine.h"
     #include "mip/file/file_handler.h"

     class FileHandlerObserver final : public mip::FileHandler::Observer {
     public:
        FileHandlerObserver() { }
        // Observer implementation
        void OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) override;
        void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
        void OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) override;
        void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;       
     };
     ```

   - Aktualisieren Sie „filehandler_observer.cpp“, indem Sie die generierte `filehandler_observer`-Klassenimplementierung auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     void FileHandlerObserver::OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_value(fileHandler);
     }

     void FileHandlerObserver::OnCreateFileHandlerFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_exception(error);
     }

     void FileHandlerObserver::OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_value(committed);
     }

     void FileHandlerObserver::OnCommitFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_exception(error);
     }
     ```

4. Verwenden Sie optional F6 (**Projektmappe erstellen**), um eine Testkompilierung/-verknüpfung Ihrer Lösung auszuführen und vor dem Fortfahren sicherzustellen, dass sie erfolgreich erstellt wird.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>Hinzufügen von Logik zum Festlegen und Abrufen einer Vertraulichkeitsbezeichnung

Fügen Sie Logik hinzu, um eine Vertraulichkeitsbezeichnung für eine Datei mit dem Datei-Engine-Objekt festzulegen oder abzurufen. 

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben. 

2. Fügen Sie die folgenden `#include`- und `using`-Anweisungen unter den entsprechenden vorhandenen Anweisungen am Anfang der Datei hinzu:

   ```cpp
   #include "filehandler_observer.h" 
   #include "mip/file/file_handler.h" 

   using mip::FileHandler;
   ```
3. Fügen Sie gegen Ende des `main()`-Texts, zwischen `system("pause");` und `return 0;` (wo Sie im vorherigen Schnellstart aufgehört haben) den folgenden Code ein:

   ```cpp
   // Set up async FileHandler for input file operations
   string inputFilePath = "<input-file-path>";
   string actualFilePath = "<content-identifier>";
   std::shared_ptr<FileHandler> handler;
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(
             inputFilePath,
             actualFilePath,                       
             true, 
             std::make_shared<FileHandlerObserver>(), 
             handlerPromise);
        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid input file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Set a label on input file
   try
   {
        string labelId = "<label-id>";
        cout << "\nApplying Label ID " << labelId << " to " << filePathIn << endl;
        mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED);
        handler->SetLabel(engine->GetLabelById(labelId), labelingOptions, new ProtectionSettings());
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Commit changes, save as a different/output file
   string filePathOut = "<output-file-path>";
   try
   {
        cout << "Committing changes" << endl;
        auto commitPromise = std::make_shared<std::promise<bool>>();
        auto commitFuture = commitPromise->get_future();
        handler->CommitAsync(filePathOut, commitPromise);
        if (commitFuture.get()) {
            cout << "\nLabel committed to file: " << filePathOut << endl;
        }
        else {
            cout << "Failed to label: " + filePathOut << endl;
            return 1;
        }
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid commit file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");

   // Set up async FileHandler for output file operations
   actualFilePath = "<content-identifier>";
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(
             filePathOut,
             actualFilePath,
             true,
             std::make_shared<FileHandlerObserver>(),
             handlerPromise);

        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid output file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Get the label from output file
   try
   {
        cout << "\nGetting the label committed to file: " << filePathOut << endl;
        auto label = handler->GetLabel();
        cout << "Name: " + label->GetLabel()->GetName() << endl;
        cout << "Id: " + label->GetLabel()->GetId() << endl;
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");
   ```

4. Suchen Sie am Ende von `main()` den Block zum Herunterfahren der Anwendung, den Sie in der ersten Schnellstartanleitung erstellt haben, und heben Sie die Auskommentierung der Zeile für den Handler auf:

   ```cpp
   // Application shutdown. Null out profile and engine, call ReleaseAllResources();
   // Application may crash at shutdown if resources aren't properly released.
   profile = nullptr;
   engine = nullptr;
   handler = nullptr;
   mipContext = nullptr;
   ```

5. Ersetzen Sie die Platzhalterwerte in dem Quellcode folgendermaßen durch Zeichenfolgenkonstanten:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<input-file-path\> | Der vollständige Pfad zu einer Testeingabedatei. Beispiel: `"c:\\Test\\Test.docx"`. |
   | \<content-identifier\> | Ein lesbarer Inhaltsbezeichner. Beispiele: <ul><li>Verwenden Sie für eine Datei das Format Pfad\Dateiname: `"c:\Test\Test.docx"`.</li><li>Verwenden Sie für eine E-Mail das Format Betreff:Absender: `"RE: Audit design:user1@contoso.com"`.</li></ul> |
   | \<label-id\> | Eine Vertraulichkeitsbezeichnungs-ID, die aus der Konsolenausgabe im vorherigen Schnellstart kopiert wird. Beispiel: `"f42a3342-8706-4288-bd31-ebb85995028z"`. |
   | \<output-file-path\> | Der vollständige Pfad zur Ausgabedatei, die eine bezeichnete Kopie der Eingabedatei ist. Beispiel: `"c:\\Test\\Test_labeled.docx"`. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung. 

1. Verwenden Sie F6 (**Projektmappe erstellen**) zum Erstellen der Clientanwendung. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, fragt die Anwendung jedes Mal nach einem Zugriffstoken, wenn das SDK Ihre `AcquireOAuth2Token()`-Methode aufruft. Führen Sie das PowerShell-Skript wie zuvor im Schnellstart „Auflisten von Vertraulichkeitsbezeichnungen“ aus, um jedes Mal das Token anhand der angegebenen Werte für $authority und $resourceUrl abzurufen. 

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
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

   Applying Label ID 074e457c-5848-4542-9a6f-34a182080e7z to c:\Test\Test.docx
   Committing changes

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Label committed to file: c:\Test\Test_labeled.docx
   Press any key to continue . . .

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/94f69844-8d34-4794-bde4-3ac89ad2b664/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Getting the label committed to file: c:\Test\Test_labeled.docx
   Name: Confidential
   Id: 074e457c-5848-4542-9a6f-34a182080e7z
   Press any key to continue . . .
   ```

Sie können die Anwendung der Bezeichnung verifizieren, indem Sie die Ausgabedatei öffnen und die Information Protection-Einstellungen des Dokuments visuell überprüfen.

> [!NOTE]
> Wenn Sie ein Office-Dokument mit einer Bezeichnung versehen, sich aber nicht mit einem Konto des Azure Active Directory-Mandanten angemeldet haben, von dem das Zugriffstoken abgerufen wurde, werden Sie (wenn Vertraulichkeitsbezeichnungen konfiguriert sind) möglicherweise aufgefordert, sich anzumelden, bevor Sie das bezeichnete Dokument öffnen können. 



