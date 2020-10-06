---
title: Herabstufen oder Entfernen einer Bezeichnung mit erforderlicher Begründung (C#)
description: In diesem Artikel erfahren Sie, wie Sie eine Bezeichnung herabstufen oder entfernen, für die eine Begründung erforderlich ist.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 05/01/2020
ms.author: v-anikep
ms.openlocfilehash: 666b0c7fdbc483f638f76def37ec3082c9eb7377
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91421196"
---
# <a name="microsoft-information-protection-sdk-file-api---action-justification-for-lowering-a-sensitivity-label-on-a-file-c"></a>Microsoft Azure Information Protection: Datei-API – Aktionsbegründung zum Herabstufen einer Vertraulichkeitsbezeichnung in einer Datei (C#)

In diesem Schnellstart wird das Herabstufen einer Bezeichnung behandelt, wenn die Bezeichnungsrichtlinie eine Begründung erfordert. Dabei wird die Schnittstelle `IFileHandler` zum Ändern der Bezeichnungen einer Datei verwendet. Weitere Informationen finden Sie in der [API-Referenz](/dotnet/api/?term=microsoft.informationprotection).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart zum Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C#)](quick-file-set-get-label-csharp.md) ab. Darin wird eine einfache Visual Studio-Projektmappe zum Auflisten der Vertraulichkeitsbezeichnungen einer Organisation erstellt, mit der Vertraulichkeitsbezeichnungen in einer Datei festgelegt oder aus dieser gelesen werden können. Dieser Schnellstart zum Herabstufen oder Entfernen einer Bezeichnung mit erforderlicher Begründung in C# baut auf dem vorherigen auf.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MIP-SDK](concept-handler-file-cpp.md) durch.

## <a name="add-logic-to-set-a-lower-label-to-a-protected-file"></a>Hinzufügen von Logik zum Festlegen einer niedrigeren Bezeichnung für eine geschützte Datei

Fügen Sie Logik hinzu, um eine Vertraulichkeitsbezeichnung für eine Datei mit dem FileHandler-Objekt festzulegen.

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C#)“ erstellt haben.

2. Öffnen Sie im Projektmappen-Explorer die CS-Datei des Projekts, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Aktualisieren Sie den `<label-id>`-Wert aus dem vorherigen Schnellstart auf eine Vertraulichkeitsbezeichnung, die eine Begründung für die Herabstufung voraussetzt. Während dieses Schnellstarts legen Sie diese Bezeichnung zunächst fest und versuchen dann, sie in weiteren Schritten über Codeausschnitte herabzustufen.

4. Fügen Sie gegen Ende des `Main()`-Bereichs zwischen `Console.ReadKey()` und dem oben aufgeführten Block zum Herunterfahren der Anwendung (wo Sie im vorherigen Schnellstart aufgehört haben) den folgenden Code ein:

    ```csharp
    //Set paths and label ID
    string lowerInput = actualOutputFilePath;
    string lowerActualInput = lowerInput;
    string newLabelId = "<new-label-id>";
    string lowerOutput = "<downgraded-labled-output>";
    string lowerActualOutput = lowerOutput;

    //Create a file handler for that file
    var downgradeHandler = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(lowerInput, lowerActualInput, true)).Result;

    //Set Labeling Options
    LabelingOptions options = new LabelingOptions()
    {
        AssignmentMethod = AssignmentMethod.Standard
    };

    try
    {
        //Try to set new label
        downgradeHandler.SetLabel(fileEngine.GetLabelById(newLabelId), options, new ProtectionSettings());
    }

    catch (Microsoft.InformationProtection.Exceptions.JustificationRequiredException)
    {
        //Request justification from user
        Console.Write("Please provide justification for downgrading a label: ");
        string justification = Console.ReadLine();

        options.IsDowngradeJustified = true;
        options.JustificationMessage = justification;

        //Set new label
        downgradeHandler.SetLabel(fileEngine.GetLabelById(newLabelId), options, new ProtectionSettings());
    }

    // Commit changes, save as outputFilePath
    var downgradedResult = Task.Run(async () => await downgradeHandler.CommitAsync(lowerActualOutput)).Result;

    // Create a new handler to read the labeled file metadata
    var commitHandler = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(lowerOutput, lowerActualOutput, true)).Result;

    // Get the label from output file
    var newContentLabel = commitHandler.Label;
    Console.WriteLine(string.Format("Getting the new label committed to file: {0}", lowerOutput));
    Console.WriteLine(string.Format("File Label: {0} \r\nIsProtected: {1}", newContentLabel.Label.Name, newContentLabel.IsProtectionAppliedFromLabel.ToString()));
    Console.WriteLine("Press a key to continue.");
    Console.ReadKey();

    ```

5. Suchen Sie am Ende der Main()-Methode den Block zum Herunterfahren der Anwendung, den Sie im vorherigen Schnellstart erstellt haben, und fügen Sie die folgenden Handlerzeilen zum Freigeben der Ressourcen hinzu:

    ````csharp
    downgradeHandler = null;
    commitHandler = null;
    ````

6. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<downgraded-labled-output\> | Der Ausgabedateipfad, in dem die geänderte Datei gespeichert werden soll |
   | \<new-label-id\> | Eine Vorlagen-ID, kopiert aus der Konsolenausgabe im vorherigen Schnellstart. Beispiel: `bb7ed207-046a-4caf-9826-647cff56b990`. Stellen Sie sicher, dass die Vertraulichkeit niedriger als die der vorherigen Bezeichnung der geschützten Datei ist. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B (**Projektmappe erstellen**), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, *kann* die Anwendung Sie jedes Mal zur Authentifizierung über ADAL auffordern, wenn das SDK Ihre `AcquireToken()`-Methode aufruft. Wenn bereits zwischengespeicherte Anmeldeinformationen vorhanden sind, werden Sie nicht zur Anmeldung aufgefordert. Die Liste der Bezeichnungen mit den Informationen zur angewendeten Bezeichnung und der geänderten Datei wird sofort angezeigt.

  ```console
    Personal : 73c47c6a-eb00-4a6a-8e19-efaada66dee6
    Public : 73254501-3d5b-4426-979a-657881dfcb1e
    General : da480625-e536-430a-9a9e-028d16a29c59
    Confidential : 569af77e-61ea-4deb-b7e6-79dc73653959
    Highly Confidential : 905845d6-b548-439c-9ce5-73b2e06be157
    Press a key to continue.

    Getting the label committed to file: c:\Test\Test_labeled.docx
    Name: Confidential
    IsProtected: True
    Press any key to continue . . .

    Please provide justification for downgrading a label: Lower label approved.
    Getting the new label committed to file: c:\Test\Test_downgraded.docx
    File Label: General
    IsProtected: False
    Press a key to continue.
   ```

Falls für die Bezeichnung, die aus einer Datei gelöscht wird, gemäß der Bezeichnungsrichtlinie eine Begründung erforderlich ist, sollten Sie einen ähnlichen Ansatz für den `DeleteLabel()`-Vorgang befolgen. Die `DeleteLabel()`-Funktion löst eine `JustificationRequiredException`-Ausnahme aus, und das `IsDowngradeJustified`-Flag sollte in der Ausnahmebehandlung auf TRUE festgelegt werden, bevor eine Bezeichnung gelöscht wird.