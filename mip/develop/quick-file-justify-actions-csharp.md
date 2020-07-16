---
title: 'Vorgehensweise: Herabstufen/entfernen einer Bezeichnung, die eine Begründung erfordert (c#)'
description: In diesem Artikel erfahren Sie, wie Sie eine Bezeichnung herabstufen oder entfernen, für die eine Begründung erforderlich ist.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: conceptual
ms.date: 05/01/2020
ms.author: v-anikep
ms.openlocfilehash: 88c55d973dde25e1571750e51e36f5fa726770f5
ms.sourcegitcommit: 36413b0451ae28045193c04cbe2d3fb2270e9773
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403220"
---
# <a name="microsoft-information-protection-sdk-file-api---action-justification-for-lowering-a-sensitivity-label-on-a-file-c"></a>Microsoft Information Protection SDK-Datei-API-Aktions Begründung für das Herabstufen einer Vertraulichkeits Bezeichnung in einer Datei (c#)

In diesem Schnellstart wird die Behandlung eines Vorgangs für eine Herabstufung der Bezeichnung behandelt, wenn die Bezeichnungs Richtlinie eine Begründung Hier wird `IFileHandler` die-Schnittstelle zum Ändern der Bezeichnungen einer Datei verwendet. Weitere Informationen finden Sie in der [API-Referenz](/dotnet/api/?term=microsoft.informationprotection).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Vervollständigen des [Schnellstarts: Set/Get Sensitivität Labels (c#)](quick-file-set-get-label-csharp.md) , mit dem eine Starter-Visual Studio-Projekt Mappe erstellt wird, um die Vertraulichkeits Bezeichnungen einer Organisation aufzulisten und Vertraulichkeits Bezeichnungen festzulegen und aus einer Datei zu lesen. Die Schnellstartanleitung "Gewusst wie: Herabstufen/entfernen einer Bezeichnung, die eine Begründung erfordert c#" basiert auf der vorherigen Version.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MIP-SDK](concept-handler-file-cpp.md) durch.

## <a name="add-logic-to-set-a-lower-label-to-a-protected-file"></a>Hinzufügen von Logik zum Festlegen einer niedrigeren Bezeichnung für eine geschützte Datei

Fügen Sie Logik hinzu, um mithilfe des dateihandlerobjekts eine Vertraulichkeits Bezeichnung für eine Datei festzulegen.

1. Öffnen Sie die Visual Studio-Projekt Mappe, die Sie im vorherigen Abschnitt "Schnellstart: Set/Get Sensitivitäts Labels (c#)" erstellt haben.

2. Öffnen Sie im Projektmappen-Explorer die CS-Datei des Projekts, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Aktualisieren Sie den `<label-id>`-Wert aus dem vorherigen Schnellstart auf eine Vertraulichkeitsbezeichnung, die eine Begründung für die Herabstufung voraussetzt. Während dieses Schnellstarts legen Sie diese Bezeichnung zunächst fest und versuchen dann, sie in weiteren Schritten über Codeausschnitte herabzustufen.

4. `Main()` `Console.ReadKey()` Fügen Sie den folgenden Code am Ende des Texts unter und über den Block "Herunterfahren der Anwendung" (wo Sie im vorherigen Schnellstart aufgehört haben) hinzu.

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

5. Am Ende von Main () finden Sie den Block "Herunterfahren der Anwendung", der in der vorherigen Schnellstartanleitung erstellt wurde

    ````csharp
    downgradeHandler = null;
    commitHandler = null;
    ````

6. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<downgraded-labled-output\> | Der Ausgabedateipfad, in dem die geänderte Datei gespeichert werden soll |
   | \<new-label-id\> | Eine Vorlagen-ID, die aus der Konsolenausgabe im vorherigen Schnellstart kopiert wurde, z `bb7ed207-046a-4caf-9826-647cff56b990` . b.:. Stellen Sie sicher, dass die Vertraulichkeit niedriger als die der vorherigen Bezeichnung der geschützten Datei ist. |

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

Beachten Sie, dass ein ähnlicher Ansatz auch für `DeleteLabel()` den-Vorgang gilt, wenn die Bezeichnung, die aus einer Datei gelöscht wird, gemäß der Bezeichnung Richtlinie eine Begründung erfordert.`DeleteLabel()` die Funktion löst eine `JustificationRequiredException` Ausnahme `IsDowngradeJustified` aus, und das Flag sollte in der Ausnahmebehandlung auf true festgelegt werden, bevor eine Bezeichnung erfolgreich gelöscht wird.