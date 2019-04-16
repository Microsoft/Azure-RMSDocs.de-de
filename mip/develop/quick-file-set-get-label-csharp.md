---
title: 'Schnellstart: Satz an, und erhalten Sie eine sensible Beschriftung auf eine Datei mit den C# MIP SDK'
description: Einen Schnellstart zeigt Ihnen, wie Sie mit der Microsoft Informationen Protection SDK .NET Wrapper zum Festlegen und Abrufen eine sensible Beschriftung für eine Datei.
services: information-protection
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.date: 01/09/2019
ms.author: mbaldwin
ms.openlocfilehash: 395c46ce1979b2ef670aa27e9329c5219ca63e13
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573759"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>Schnellstart: Festlegen und Abrufen einer vertraulichkeitsbezeichnung (C#)

In diesem Schnellstart wird gezeigt, wie Sie weitere MIP-Datei-APIs nutzen. Durch Verwendung einer der Vertraulichkeitsbezeichnungen, die Sie im vorherigen Schnellstart aufgelistet haben, verwenden Sie einen Dateihandler zum Festlegen/Abrufen der Bezeichnung für eine Datei. Die Dateihandlerklasse macht verschiedene Vorgänge für das Festlegen/Abrufen von Bezeichnungen oder Schutz für unterstützte Dateitypen verfügbar.

## <a name="prerequisites"></a>Vorraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Vollständige [Schnellstart: Liste der vertraulichkeitsbezeichnungen (C#)](quick-file-list-labels-csharp.md) erste, die eine Starter-Visual Studio-Projektmappe, um die Liste der vertraulichkeitsbezeichnungen einer Organisation erstellt. Dieser Schnellstart „Festlegen und Abrufen einer Vertraulichkeitsbezeichnung“ baut auf den vorherigen auf.
- Optional: Überprüfen Sie [Datei Handler das MIP SDK](concept-handler-file-cpp.md) Konzepte.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>Hinzufügen von Logik zum Festlegen und Abrufen einer Vertraulichkeitsbezeichnung

Fügen Sie Logik hinzu, um eine Vertraulichkeitsbezeichnung für eine Datei mit dem Datei-Engine-Objekt festzulegen oder abzurufen. 

1. Mithilfe von **Projektmappen-Explorer**, öffnen Sie die CS-Datei im Projekt, das die Implementierung der Main() enthält "Methode. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben. 

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
          ActionSource = ActionSource.Manual,
          AssignmentMethod = AssignmentMethod.Standard
     };

     // Set a label on input file
     handler.SetLabel(labelId, labelingOptions);

     // Commit changes, save as outputFilePath
     var result = Task.Run(async () => await handler.CommitAsync(outputFilePath)).Result;

     // Create a new handler to read the labeled file metadata
     var handlerModified = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(outputFilePath, actualOutputFilePath, true)).Result;

     // Get the label from output file
     var contentLabel = handlerModified.Label;
     Console.WriteLine(string.Format("Getting the label committed to file: {0}", outputFilePath));
     Console.WriteLine(string.Format("File Label: {0} \r\nIsProtected: {1}", contentLabel.Label, contentLabel.IsProtectionAppliedFromLabel.ToString()));
     Console.WriteLine("Press a key to continue.");
     Console.ReadKey();
   ```

3. Ersetzen Sie die Platzhalterwerte in dem Quellcode, den Sie gerade eingefügt haben, durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<input-file-path\> | Der vollständige Pfad zu einer Testeingabedatei. Beispiel: `c:\\Test\\Test.docx`. |
   | \<label-id\> | Eine Vertraulichkeitsbezeichnungs-ID, die aus der Konsolenausgabe im vorherigen Schnellstart kopiert wird. Beispiel: `f42a3342-8706-4288-bd31-ebb85995028z`. |
   | \<output-file-path\> | Der vollständige Pfad zur Ausgabedatei, die eine bezeichnete Kopie der Eingabedatei ist. Beispiel: `c:\\Test\\Test_labeled.docx`. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung. 

1. Verwenden Sie STRG + UMSCHALT + B (**Projektmappe**) zum Erstellen der Clientanwendung. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn Ihr Projekt erstellt und ausgeführt wird, auf die Anwendung *möglicherweise* Aufforderung zur Authentifizierung über ADAL jedes Mal die SDK-Aufrufe Ihrer `AcquireToken()` Methode. Wenn zwischengespeicherte Anmeldeinformationen bereits vorhanden, Sie nicht aufgefordert, melden Sie sich, und finden Sie unter der Liste der Bezeichnungen gefolgt von den Informationen auf die angewendete Bezeichnung und -Datei geändert.

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
