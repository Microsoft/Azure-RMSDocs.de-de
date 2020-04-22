---
title: 'Schnellstart: Festlegen und Abrufen einer Vertraulichkeitsbezeichnung für eine Datei mit dem MSIP SDK für C#'
description: In diesem Schnellstart wird veranschaulicht, wie Sie mit dem .NET-Wrapper für das Microsoft Information Protection SDK eine Vertraulichkeitsbezeichnung für eine Datei festlegen und abrufen können.
services: information-protection
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: c081d20ba3cfffdc1db06ade5d918230f3b9eff8
ms.sourcegitcommit: a3f901e479abbe056f8936a96b7253f0826d1415
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "75554989"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>Schnellstart: Festlegen und Abrufen einer Vertraulichkeitsbezeichnung (C#)

In diesem Schnellstart wird gezeigt, wie Sie weitere MIP-Datei-APIs nutzen. Durch Verwendung einer der Vertraulichkeitsbezeichnungen, die Sie im vorherigen Schnellstart aufgelistet haben, verwenden Sie einen Dateihandler zum Festlegen/Abrufen der Bezeichnung für eine Datei. Die Dateihandlerklasse macht verschiedene Vorgänge für das Festlegen/Abrufen von Bezeichnungen oder Schutz für unterstützte Dateitypen verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart Auflisten von Vertraulichkeitsbezeichnungen (C#)](quick-file-list-labels-csharp.md) ab. Darin wird eine Visual Studio-Startprojektmappe zum Auflisten der Vertraulichkeitsbezeichnungen einer Organisation erstellt. Dieser Schnellstart „Festlegen und Abrufen einer Vertraulichkeitsbezeichnung“ baut auf den vorherigen auf.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MSIP SDK](concept-handler-file-cpp.md) durch.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>Hinzufügen von Logik zum Festlegen und Abrufen einer Vertraulichkeitsbezeichnung

Fügen Sie Logik hinzu, um eine Vertraulichkeitsbezeichnung für eine Datei mit dem Datei-Engine-Objekt festzulegen oder abzurufen. 

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CS-Datei im Projekt, die die Implementierung der Main()-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben. 

2. Fügen Sie gegen Ende des `Main()`-Texts, zwischen `Console.ReadKey()` und `}` (wo Sie im vorherigen Schnellstart aufgehört haben) den folgenden Code ein:

   ```csharp
     //Set paths and label ID
     string inputFilePath = "<input-file-path>";
     string actualFilePath = inputFilePath;
     string labelId = "<label-id>";
     string outputFilePath = "<output-file-path>";
     string actualOutputFilePath = outputFilePath;

     //Create a file handler for that file
     //Note: the 2nd inputFilePath is used to provide a human-readable content identifier for admin auditing. 
     var handler = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(inputFilePath, actualFilePath, true)).Result;

     //Set Labeling Options
     LabelingOptions labelingOptions = new LabelingOptions()
     {
          AssignmentMethod = AssignmentMethod.Standard
     };

     // Set a label on input file
     handler.SetLabel(engine.GetLabelById(labelId), labelingOptions, new ProtectionSettings());

     // Commit changes, save as outputFilePath
     var result = Task.Run(async () => await handler.CommitAsync(outputFilePath)).Result;

     // Create a new handler to read the labeled file metadata
     var handlerModified = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(outputFilePath, actualOutputFilePath, true)).Result;

     // Get the label from output file
     var contentLabel = handlerModified.Label;
     Console.WriteLine(string.Format("Getting the label committed to file: {0}", outputFilePath));
     Console.WriteLine(string.Format("File Label: {0} \r\nIsProtected: {1}", contentLabel.Label.Name, contentLabel.IsProtectionAppliedFromLabel.ToString()));
     Console.WriteLine("Press a key to continue.");
     Console.ReadKey();
   ```

3. Suchen Sie am Ende von `Main()` den Block zum Herunterfahren der Anwendung, den Sie in der ersten Schnellstartanleitung erstellt haben, und heben Sie die Auskommentierung der Zeile für den Handler auf:

   ```csharp
   // Application Shutdown
   handler = null;
   fileEngine = null;
   fileProfile = null;
   mipContext = null;
   ```

4. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<input-file-path\> | Der vollständige Pfad zu einer Testeingabedatei. Beispiel: `c:\\Test\\Test.docx`. |
   | \<label-id\> | Eine Vertraulichkeitsbezeichnungs-ID, die aus der Konsolenausgabe im vorherigen Schnellstart kopiert wird. Beispiel: `f42a3342-8706-4288-bd31-ebb85995028z`. |
   | \<output-file-path\> | Der vollständige Pfad zur Ausgabedatei, die eine bezeichnete Kopie der Eingabedatei ist. Beispiel: `c:\\Test\\Test_labeled.docx`. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung. 

1. Drücken Sie STRG+UMSCHALT+B (**Projektmappe erstellen**), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, *kann* die Anwendung Sie jedes Mal zur Authentifizierung über ADAL auffordern, wenn das SDK Ihre `AcquireToken()`-Methode aufruft. Wenn bereits zwischengespeicherte Anmeldeinformationen vorhanden sind, werden Sie nicht zur Anmeldung aufgefordert. Die Liste der Bezeichnungen mit den Informationen zur angewendeten Bezeichnung und der geänderten Datei wird sofort angezeigt.

  ```console   
  Personal : 73c47c6a-eb00-4a6a-8e19-efaada66dee6
  Public : 73254501-3d5b-4426-979a-657881dfcb1e
  General : da480625-e536-430a-9a9e-028d16a29c59
  Confidential : 569af77e-61ea-4deb-b7e6-79dc73653959
        Recipients Only (C) : d98c4267-727b-430e-a2d9-4181ca5265b0
        All Employees (C) : 2096f6a2-d2f7-48be-b329-b73aaa526e5d
        Anyone (not protected) (C) : 63a945ec-1131-420d-80da-2fedd15d3bc0
  Highly Confidential : 905845d6-b548-439c-9ce5-73b2e06be157
        Recipients Only : 05ee72d9-1a75-441f-94e2-dca5cacfe012
        All Employees : 922b06ef-044b-44a3-a8aa-df12509d1bfe
        Anyone (not protected) : c83fc820-961d-40d4-ba12-c63f72a970a3
  Press a key to continue.

   Applying Label ID 074e457c-5848-4542-9a6f-34a182080e7z to c:\Test\Test.docx
   Committing changes
   
   Label committed to file: c:\Test\Test_labeled.docx
   Press any key to continue . . .
  
   Getting the label committed to file: c:\Test\Test_labeled.docx
   Name: Confidential
   Id: 074e457c-5848-4542-9a6f-34a182080e7z
   Press any key to continue . . .
   ```

Sie können die Anwendung der Bezeichnung verifizieren, indem Sie die Ausgabedatei öffnen und die Information Protection-Einstellungen des Dokuments visuell überprüfen.

> [!NOTE]
> Wenn Sie ein Office-Dokument mit einer Bezeichnung versehen, sich aber nicht mit einem Konto des Azure Active Directory-Mandanten angemeldet haben, von dem das Zugriffstoken abgerufen wurde, werden Sie (wenn Vertraulichkeitsbezeichnungen konfiguriert sind) möglicherweise aufgefordert, sich anzumelden, bevor Sie das bezeichnete Dokument öffnen können. 
