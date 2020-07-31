---
title: Herabstufen oder Entfernen einer Bezeichnung mit erforderlicher Begründung (C++)
description: In diesem Artikel erfahren Sie, wie Sie eine Bezeichnung herabstufen oder entfernen, für die eine Begründung erforderlich ist.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 04/14/2020
ms.author: v-anikep
ms.openlocfilehash: 96bd94398c2a5c0bbe2cd87c12ec8e6a0af7e18b
ms.sourcegitcommit: 84b45c949d85a7291c088a050d2a66d356fc9af2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87135673"
---
# <a name="microsoft-information-protection-sdk-file-api---action-justification-for-lowering-a-sensitivity-label-on-a-file-c"></a>Microsoft Azure Information Protection: Datei-API – Aktionsbegründung zum Herabstufen einer Vertraulichkeitsbezeichnung in einer Datei (C++)

In diesem Schnellstart wird das Herabstufen einer Bezeichnung behandelt, wenn die Bezeichnungsrichtlinie eine Begründung voraussetzt. Hier wird die Klasse `mip::FileHandler` verwendet, um die Bezeichnungen einer Datei zu ändern. Weitere Informationen finden Sie in der [API-Referenz](./reference/mip-sdk-reference.md).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart zum Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C++)](quick-file-set-get-label-cpp.md) ab. Darin wird eine Visual Studio-Startprojektmappe zum Auflisten der Vertraulichkeitsbezeichnungen einer Organisation erstellt, mit der Vertraulichkeitsbezeichnungen in einer Datei festgelegt oder aus dieser gelesen werden können. Dieser Schnellstart zum Herabstufen oder Entfernen einer Bezeichnung mit erforderlicher Begründung in C++ baut auf dem vorherigen auf.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MIP-SDK](concept-handler-file-cpp.md) durch.

## <a name="add-logic-to-set-a-lower-label-to-a-protected-file"></a>Hinzufügen von Logik zum Festlegen einer niedrigeren Bezeichnung für eine geschützte Datei

Fügen Sie Logik hinzu, um eine Vertraulichkeitsbezeichnung für eine Datei mit dem `mip::FileHandler`-Objekt festzulegen.

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel [Schnellstart: Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C++)](quick-file-set-get-label-cpp.md) erstellt haben.

2. Öffnen Sie im Projektmappen-Explorer die CPP-Datei des Projekts, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Fügen Sie die folgenden #include- und using-Direktiven unter den entsprechenden vorhandenen Direktiven am Anfang der Datei hinzu:

    ```cpp

        #include "mip/file/file_error.h"

        using mip::JustificationRequiredError;
        using std::cin;

    ```

4. Aktualisieren Sie den `<label-id>`-Wert aus dem vorherigen Schnellstart auf eine Vertraulichkeitsbezeichnung, die eine Begründung für die Herabstufung voraussetzt. Während dieses Schnellstarts legen Sie diese Bezeichnung zunächst fest und versuchen dann, sie in weiteren Schritten über Codeausschnitte herabzustufen.

5. Fügen Sie gegen Ende des `main()`-Bereichs zwischen `system("pause");` und dem oben aufgeführten Block zum Herunterfahren (wo Sie im vorherigen Schnellstart aufgehört haben) den folgenden Code ein:

```cpp

// Downgrade label
// Set paths and lower label ID
// Set a new label on input file.

string lowerlabelId = "<lower-label-id>";
cout << "\nApplying new Label ID " << lowerlabelId << " to " << filePathOut << endl;
mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED);

// Try to apply a label with lower sensitivity.
try
{
    handler->SetLabel(engine->GetLabelById(lowerlabelId), labelingOptions, mip::ProtectionSettings());
}

catch (const mip::JustificationRequiredError& e)
{
    // Request justification from user.
    cout<<"Please provide justification for downgrading a label: "<<endl;
    string justification;
    cin >> justification;

    // Set Justification provided flag
    bool isDowngradeJustified = true;
    mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED);
    labelingOptions.SetDowngradeJustification(isDowngradeJustified,justification);

    //Set new label.
    handler->SetLabel(engine->GetLabelById(lowerlabelId), labelingOptions, mip::ProtectionSettings());
}

catch (const std::exception& e)
{
    cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
    system("pause");
    return 1;
}

// Commit changes, save as a different output file
string lowerFilePathOut = "<lower-output-file-path>";
try
{
    cout << "Committing changes" << endl;
    auto commitPromise = std::make_shared<std::promise<bool>>();
    auto commitFuture = commitPromise->get_future();
    handler->CommitAsync(lowerFilePathOut, commitPromise);
    if (commitFuture.get()) {
        cout << "\nLabel committed to file: " << lowerFilePathOut << endl;
    }
    else {
        cout << "Failed to label: " + lowerFilePathOut << endl;
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
string lowerActualFilePath = "<lower-content-identifier>";
try
{
    auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
    auto handlerFuture = handlerPromise->get_future();
    engine->CreateFileHandlerAsync(
        lowerFilePathOut,
        lowerActualFilePath,
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

// Get the lowered label from output file
try
{
    cout << "\nGetting the label committed to file: " << lowerFilePathOut << endl;
    auto lowerLabel = handler->GetLabel();
    cout << "Name: " + lowerLabel->GetLabel()->GetName() << endl;
    cout << "Id: " + lowerLabel->GetLabel()->GetId() << endl;
}
catch (const std::exception& e)
{
    cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
    system("pause");
    return 1;
}
system("pause");

```

6. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<lower-label-id\> | Eine Bezeichnungs-ID, die aus der Konsolenausgabe im vorherigen Schnellstart kopiert wurde, zum Beispiel `bb7ed207-046a-4caf-9826-647cff56b990`. Stellen Sie sicher, dass die Vertraulichkeit niedriger als die der vorherigen Bezeichnung der geschützten Datei ist. |
   | \<lower-output-file-path\> | Der Ausgabedateipfad, in dem die geänderte Datei gespeichert werden soll |
   | \<lower-content-identifier\> | Ein lesbarer Inhaltsbezeichner. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B (**Projektmappe erstellen**), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, fragt die Anwendung jedes Mal nach einem Zugriffstoken, wenn das SDK Ihre `AcquireOAuth2Token()`-Methode aufruft. Führen Sie das PowerShell-Skript wie zuvor im Schnellstart „Festlegen und Abrufen von Vertraulichkeitsbezeichnungen“ aus, um jedes Mal das Token anhand der angegebenen Werte für $authority und $resourceUrl abzurufen.

  ```console
    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/common
    Set $resourceUrl to: https://syncservice.o365syncservice.com/
    Sign in with user account: user1@tenant.onmicrosoft.com
    Enter access token: <paste-access-token-here>
    Press any key to continue . . .

    Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
    Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
    General : f42a3342-8706-4288-bd31-ebb85995028z
    Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
    Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z
    Press any key to continue . . .

    Applying Label ID f55c2dea-db0f-47cd-8520-a52e1590fb6z to c:\Test\Test.docx
    Committing changes

    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/common
    Set $resourceUrl to: https://aadrm.com
    Sign in with user account: user1@tenant.onmicrosoft.com
    Enter access token: <paste-access-token-here>
    Press any key to continue . . .

    Label committed to file: c:\Test\Test.docx
    Press any key to continue . . .

    Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
    Set $authority to: https://login.windows.net/37f4583d-9985-4e7f-a1ab-71afd8b55ba0
    Set $resourceUrl to: https://aadrm.com
    Sign in with user account: user1@tenant.onmicrosoft.com
    Enter access token: <paste-access-token-here>
    Press any key to continue . . .

    Getting the label committed to file: c:\Test\Test_labeled.docx
    Name: Highly Confidential
    Id: f55c2dea-db0f-47cd-8520-a52e1590fb6z
    Press any key to continue . . .

    Applying new Label ID f42a3342-8706-4288-bd31-ebb85995028z to c:\Test\Test_labeled.docx
    Please provide justification for downgrading a label:
    Need for sharing with wider audience.
    Committing changes

    Label committed to file: c:\Test\Test_downgraded.docx
    Press any key to continue . . .

    Getting the label committed to file: c:\Test\Test_downgraded.docx
    Name: General
    Id: f42a3342-8706-4288-bd31-ebb85995028z
    Press any key to continue . . .
   ```

Falls für die Bezeichnung, die aus einer Datei gelöscht wird, gemäß der Bezeichnungsrichtlinie eine Begründung erforderlich ist, sollten Sie einen ähnlichen Ansatz für den `DeleteLabel()`-Vorgang befolgen. Die -Funktion Die `DeleteLabel()`-Funktion löst eine `mip::JustificationRequiredError`-Ausnahme aus. Das `isDowngradeJustified`-Flag sollte in der Ausnahmebehandlung auf „true“ festgelegt werden, bevor die Bezeichnung gelöscht wird.
