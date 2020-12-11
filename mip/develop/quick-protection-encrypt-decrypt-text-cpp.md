---
title: 'Schnellstart: Verschlüsseln/Entschlüsseln von Text mit der Schutz-API im MIP SDK für C++'
description: Dieser Schnellstart zeigt die Verwendung der Schutz-API im Microsoft Information Protection SDK für C++, um Ad-hoc-Text mithilfe einer Schutzvorlage zu verschlüsseln und zu entschlüsseln (C++).
services: information-protection
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 03/30/2020
ms.author: v-anikep
ms.openlocfilehash: 1258bfcd6c47611b439a29406ed0e78b644a5803
ms.sourcegitcommit: 6322f840388067edbe3642661e313ff225be5563
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96535840"
---
# <a name="quickstart-encryptdecrypt-text-using-mip-sdk-c"></a>Schnellstart: Verschlüsseln/Entschlüsseln von Text mit dem MIP SDK (C++)

In diesem Schnellstart wird gezeigt, wie Sie weitere MIP-Schutz-APIs nutzen. Sie verwenden eine der im vorherigen Schnellstart aufgelisteten Schutzvorlagen, um mit einem Schutzhandler Ad-hoc-Text zu verschlüsseln. Die Schutzhandlerklasse macht verschiedene Vorgänge zum Anwenden/Entfernen von Schutz verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Bearbeiten Sie zunächst den [Schnellstart: Auflisten von Schutzvorlagen (C++)](quick-protection-list-templates-cpp.md), in dem eine Visual Studio-Startprojektmappe erstellt wird, um die Schutzvorlagen aufzulisten, die einem authentifizierten Benutzer zur Verfügung stehen. Der vorliegende Schnellstart zum Verschlüsseln/Entschlüsseln von Text baut auf dem vorherigen Schnellstart auf.
- Optional: Sehen Sie sich die Konzepte unter [ProtectionHandler im MIP SDK](concept-handler-protection-cpp.md) an.

## <a name="implement-an-observer-class-to-monitor-the-protection-handler-object"></a>Implementieren einer Observer-Klasse zum Überwachen des Schutzhandlerobjekts

Ähnlich wie bei dem Observer, den Sie (für Schutzprofil und -Engine) im Schnellstart zur Anwendungsinitialisierung implementiert haben, implementieren Sie jetzt eine Observer-Klasse für ein Schutzhandlerobjekt.

Erstellen Sie eine grundlegende Implementierung für die Observer-Klasse für einen Schutzhandler, indem Sie die `mip::ProtectionHandler::Observer`-Klasse des SDK erweitern. Der Observer wird instanziiert und später zum Überwachen von Schutzhandlervorgängen verwendet.

1. Öffnen Sie die Visual Studio-Projektmappe, an der Sie im vorherigen Artikel „Schnellstart: Auflisten von Schutzvorlagen (C++)“ gearbeitet haben.

2. Fügen Sie eine neue Klasse zu Ihrem Projekt hinzu, durch die die Dateien „header/.h“ und „implementation/.cpp“ für Sie generiert werden:

   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Hinzufügen** > **Klasse** aus.
   - Gehen Sie im Dialogfeld **Klasse hinzufügen** folgendermaßen vor:
     - Geben Sie im Feld **Klassenname** „handler_observer“ ein. Beachten Sie, dass sowohl das Feld **H-Datei** als auch das Feld **CPP-Datei** anhand des eingegebenen Namens automatisch aufgefüllt werden.
     - Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK**.

3. Nach dem Generieren der H- und der CPP-Datei für die Klasse werden beide Dateien auf Editor-Gruppenregisterkarten geöffnet. Aktualisieren Sie jetzt jede Datei, um Ihre neue Observer-Klasse zu implementieren:

   - Aktualisieren Sie „handler_observer.h“, indem Sie die generierte `handler_observer`-Klasse auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include <memory>
     #include "mip/protection/protection_engine.h"
     using std::shared_ptr;
     using std::exception_ptr;

     class ProtectionHandlerObserver final : public mip::ProtectionHandler::Observer {
          public:
          ProtectionHandlerObserver() { }
          void OnCreateProtectionHandlerSuccess(const shared_ptr<mip::ProtectionHandler>& protectionHandler, const shared_ptr<void>& context) override;
          void OnCreateProtectionHandlerFailure(const exception_ptr& Failure, const shared_ptr<void>& context) override;
          };

     ```

   - Aktualisieren Sie „handler_observer.cpp“, indem Sie die generierte `handler_observer`-Klassenimplementierung auswählen/löschen. Entfernen Sie **nicht** die im vorherigen Schritt generierten Präprozessoranweisungen (#pragma, #include). Kopieren Sie anschließend die folgende Quelle, und fügen Sie sie in der Datei nach vorhandenen Präprozessoranweisungen ein:

     ```cpp
     #include "handler_observer.h"
     using std::shared_ptr;
     using std::promise;
     using std::exception_ptr;

     void ProtectionHandlerObserver::OnCreateProtectionHandlerSuccess(
          const shared_ptr<mip::ProtectionHandler>& protectionHandler,const shared_ptr<void>& context) {
               auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
               createProtectionHandlerPromise->set_value(protectionHandler);
               };

     void ProtectionHandlerObserver::OnCreateProtectionHandlerFailure(
          const exception_ptr& Failure, const shared_ptr<void>& context) {
               auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get())
               createProtectionHandlerPromise->set_exception(Failure);
               };

     ```

4. Verwenden Sie optional STRG+UMSCHALT+B (**Projektmappe erstellen**), um eine Testkompilierung/-verknüpfung Ihrer Projektmappe auszuführen und vor dem Fortfahren sicherzustellen, dass sie erfolgreich erstellt wird.

## <a name="add-logic-to-encrypt-and-decrypt-ad-hoc-text"></a>Hinzufügen von Logik zum Verschlüsseln und Entschlüsseln von Ad-hoc-Text

Fügen Sie mit dem Schutz-Engine-Objekt Logik zum Verschlüsseln und Entschlüsseln von Ad-hoc-Text hinzu.

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält.

2. Fügen Sie die folgenden #include- und using-Direktiven unter den entsprechenden vorhandenen Direktiven am Anfang der Datei hinzu:

   ```cpp
     #include "mip/protection/protection_descriptor_builder.h"
     #include "mip/protection_descriptor.h"
     #include "handler_observer.h"

     using mip::ProtectionDescriptor;
     using mip::ProtectionDescriptorBuilder;
     using mip::ProtectionHandler;
   ```

3. Fügen Sie gegen Ende des `Main()`-Texts – an der Stelle, an der Sie im vorherigen Schnellstart aufgehört haben – den folgenden Code ein:

   ```cpp
   //Encrypt/Decrypt text:
   string templateId = "<Template-ID>";//Template ID from previous QuickStart e.g. "bb7ed207-046a-4caf-9826-647cff56b990"
   string inputText = "<Sample-Text>";//Sample Text

   //Refer to ProtectionDescriptor docs for details on creating the descriptor
   auto descriptorBuilder = mip::ProtectionDescriptorBuilder::CreateFromTemplate(templateId);
   const std::shared_ptr<mip::ProtectionDescriptor>& descriptor = descriptorBuilder->Build();

   //Create Publishing settings using a descriptor
   mip::ProtectionHandler::PublishingSettings publishingSettings = mip::ProtectionHandler::PublishingSettings(descriptor);

   //Create a publishing protection handler using Protection Descriptor
   auto handlerObserver = std::make_shared<ProtectionHandlerObserver>();
   engine->CreateProtectionHandlerForPublishingAsync(publishingSettings, handlerObserver, pHandlerPromise);
   auto publishingHandler = pHandlerFuture.get();

   std::vector<uint8_t> inputBuffer(inputText.begin(), inputText.end());

   //Show action plan
   cout << "Applying Template ID " + templateId + " to: " << endl << inputText << endl;

   //Encrypt buffer using Publishing Handler
   std::vector<uint8_t> encryptedBuffer;
   encryptedBuffer.resize(static_cast<size_t>(publishingHandler->GetProtectedContentLength(inputText.size(), true)));

   publishingHandler->EncryptBuffer(0,
                         &inputBuffer[0],
                         static_cast<int64_t>(inputBuffer.size()),
                         &encryptedBuffer[0],
                         static_cast<int64_t>(encryptedBuffer.size()),
                         true);

   std::string encryptedText(encryptedBuffer.begin(), encryptedBuffer.end());
   cout << "Encrypted Text :" + encryptedText;

   //Show action plan
   cout << endl << "Decrypting string: " << endl << endl;

   //Generate publishing licence, so it can be used later to decrypt text.
   auto serializedPublishingLicense = publishingHandler->GetSerializedPublishingLicense();

   //Use same PL to decrypt the encryptedText.
   auto cHandlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
   auto cHandlerFuture = cHandlerPromise->get_future();
   shared_ptr<ProtectionHandlerObserver> cHandlerObserver = std::make_shared<ProtectionHandlerObserver>();

   //Create consumption settings using serialised publishing licence.
   mip::ProtectionHandler::ConsumptionSettings consumptionSettings = mip::ProtectionHandler::ConsumptionSettings(serializedPublishingLicense);
   engine->CreateProtectionHandlerForConsumptionAsync(consumptionSettings, cHandlerObserver, cHandlerPromise);

   auto consumptionHandler = cHandlerFuture.get();

   //Use consumption handler to decrypt the text.
   std::vector<uint8_t> decryptedBuffer(static_cast<size_t>(encryptedText.size()));

   int64_t decryptedSize = consumptionHandler->DecryptBuffer(
        0,
        &encryptedBuffer[0],
        static_cast<int64_t>(encryptedBuffer.size()),
        &decryptedBuffer[0],
        static_cast<int64_t>(decryptedBuffer.size()),
        true);

   decryptedBuffer.resize(static_cast<size_t>(decryptedSize));

   std::string decryptedText(decryptedBuffer.begin(), decryptedBuffer.end());

   // Output decrypted content. Should match original input text.
   cout << "Decrypted Text :" + decryptedText << endl;

   ```

4. Suchen Sie am Ende von `main()` den Block zum Herunterfahren der Anwendung, den Sie im ersten Schnellstart erstellt haben, und fügen Sie die folgenden Zeilen zum Freigeben der Handlerressourcen hinzu:

   ```cpp
    publishingHandler = nullptr;
    consumptionHandler = nullptr;
   ```

5. Ersetzen Sie die Platzhalterwerte in dem Quellcode folgendermaßen durch Zeichenfolgenkonstanten:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<sample-text\> | Beispieltext, den Sie schützen möchten. Beispiel: `"cipher text"`. |
   | \<Template-Id\> | Die Vorlagen-ID, die Sie zum Schützen des Texts verwenden möchten. Beispiel: `"bb7ed207-046a-4caf-9826-647cff56b990"` |
  
## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B (**Projektmappe erstellen**), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, fragt die Anwendung jedes Mal nach einem Zugriffstoken, wenn das SDK Ihre `AcquireOAuth2Token()`-Methode aufruft. Führen Sie das PowerShell-Skript wie zuvor im Schnellstart „Auflisten von Schutzvorlagen“ aus, um bei jedem Vorgang das Token anhand der angegebenen Werte für $authority und $resourceUrl abzurufen.

   ```console
   *** Template List:
   Name: Confidential \ All Employees : a74f5027-f3e3-4c55-abcd-74c2ee41b607
   Name: Highly Confidential \ All Employees : bb7ed207-046a-4caf-9826-647cff56b990
   Name: Confidential : 174bc02a-6e22-4cf2-9309-cb3d47142b05
   Name: Contoso Employees Only : 667466bf-a01b-4b0a-8bbf-a79a3d96f720
   Applying Template ID bb7ed207-046a-4caf-9826-647cff56b990 to:
   <Sample-Text>
   Encrypted Text :y¬╩$Ops7Γ╢╖¢t
   Decrypting string:

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/94f69844-8d34-4794-bde4-3ac89ad2b664/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Decrypted Text :<Sample-Text>
   C:\MIP Sample Apps\ProtectionQS\Debug\ProtectionQS.exe (process 8252) exited with code 0.
   To automatically close the console when debugging stops, enable Tools->Options->Debugging->Automatically close the console when debugging stops.
   Press any key to close this window . . .
   ```
