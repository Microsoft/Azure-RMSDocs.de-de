---
title: 'Gewusst wie: Neuveröffentlichen des Szenarios C #'
description: In diesem Artikel erfahren Sie, wie Sie das Szenario für die Wiederverwendung des Schutz Handlers für das erneute Veröffentlichen von Szenarien verstehen.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: conceptual
ms.date: 05/01/2020
ms.author: v-anikep
ms.openlocfilehash: 2b6e0b866144c4883ece29936c1a23cc946c5976
ms.sourcegitcommit: 36413b0451ae28045193c04cbe2d3fb2270e9773
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403339"
---
# <a name="microsoft-information-protection-sdk---file-api-republishing-quickstart-c"></a>Schnellstart: Microsoft Information Protection SDK-Datei-API-Wiederveröffentlichung (c#)

## <a name="overview"></a>Übersicht

Eine Übersicht zu diesem Szenario und zu seiner Verwendung finden Sie unter [Veröffentlichen im MIP SDK](concept-republishing.md).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Vervollständigen der [Schnellstartanleitung: Set/Get sensisensilabels (c#)](quick-file-set-get-label-csharp.md) First, das eine Starter-Visual Studio-Projekt Mappe erstellt, um die Vertraulichkeits Bezeichnungen einer Organisation aufzulisten und Vertraulichkeits Bezeichnungen in einer Datei festzulegen und zu lesen. Diese Schnellstartanleitung zum erneuten Veröffentlichen einer geschützten Datei-c# basiert auf der vorherigen Schnellstartanleitung.
- Optional: Überprüfen von [Datei Handlern](concept-handler-file-cpp.md) in den MIP SDK-Konzepten.
- Optional: Überprüfen Sie die [Schutz Handler](concept-handler-protection-cpp.md) in den MIP SDK-Konzepten.

## <a name="add-logic-to-edit-and-republish-a-protected-file"></a>Hinzufügen von Logik zum Bearbeiten und erneuten Veröffentlichen einer geschützten Datei

1. Öffnen Sie die Visual Studio-Projekt Mappe, die Sie im vorherigen Artikel "Schnellstart: Set/Get sensisensilabels (c#)" erstellt haben.

2. Öffnen Sie im Projektmappen-Explorer die CS-Datei des Projekts, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. `Main()` `Console.ReadKey()` Fügen Sie den folgenden Code am Ende des Texts unter und über den Block "Herunterfahren der Anwendung" (wo Sie im vorherigen Schnellstart aufgehört haben) hinzu.

```csharp
string protectedFilePath = "<protected-file-path>" // Originally protected file's path from previous quickstart.

//Create a fileHandler for consumption for the Protected File.
var protectedFileHandler = Task.Run(async () => 
                            await fileEngine.CreateFileHandlerAsync(protectedFilePath,// inputFilePath
                                                                    protectedFilePath,// actualFilePath
                                                                    false, //isAuditDiscoveryEnabled
                                                                    null)).Result; // fileExecutionState

// Store protection handler from file
var protectionHandler = protectedFileHandler.Protection;

//Check if the user has the 'Edit' right to the file
if (protectionHandler.AccessCheck("Edit"))
{
    // Decrypt file to temp path
    var tempPath = Task.Run(async () => await protectedFileHandler.GetDecryptedTemporaryFileAsync()).Result;

    /*
        Your own application code to edit the decrypted file belongs here. 
    */

    /// Follow steps below for re-protecting the edited file. ///
    // Create a new file handler using the temporary file path.
    var republishHandler = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(tempPath, tempPath, false)).Result;

    // Set protection using the ProtectionHandler from the original consumption operation.
    republishHandler.SetProtection(protectionHandler);

    // New file path to save the edited file
    string reprotectedFilePath = "<reprotected-file-path>" // New file path for saving reprotected file.

    // Write changes
    var reprotectedResult = Task.Run(async () => await republishHandler.CommitAsync(reprotectedFilePath)).Result;

    var protectedLabel = protectedFileHandler.Label;
    Console.WriteLine(string.Format("Originally protected file: {0}", protectedFilePath));
    Console.WriteLine(string.Format("File LabelID: {0} \r\nProtectionOwner: {1} \r\nIsProtected: {2}", 
                        protectedLabel.Label.Id, 
                        protectedFileHandler.Protection.Owner, 
                        protectedLabel.IsProtectionAppliedFromLabel.ToString()));
    var reprotectedLabel = republishHandler.Label;
    Console.WriteLine(string.Format("Reprotected file: {0}", reprotectedFilePath));
    Console.WriteLine(string.Format("File LabelID: {0} \r\nProtectionOwner: {1} \r\nIsProtected: {2}", 
                        reprotectedLabel.Label.Id, 
                        republishHandler.Protection.Owner, 
                        reprotectedLabel.IsProtectionAppliedFromLabel.ToString()));
    Console.WriteLine("Press a key to continue.");
    Console.ReadKey();
}
```

4. Am Ende von Main () finden Sie den Block für das Herunterfahren der Anwendung, der im vorherigen Schnellstart erstellt wurde

    ````csharp
        protectedFileHandler = null;
        protectionHandler = null;
    ````

5. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<protected-file-path\> | Geschützte Datei aus vorheriger Schnellstartanleitung. |
   | \<reprotected-file-path\> | Der Ausgabe Dateipfad für die geänderte Datei, die erneut veröffentlicht werden soll. |

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

    Getting the label committed to file: C:\Test\Test_protected.docx
    File Label: Confidential
    IsProtected: True
    Press a key to continue.
    Originally protected file: C:\Test\Test_protected.docx
    File LabelID: 569af77e-61ea-4deb-b7e6-79dc73653959
    ProtectionOwner: User1@Contoso.OnMicrosoft.com
    IsProtected: True
    Reprotected file: C:\Test\Test_reprotected.docx
    File LabelID: 569af77e-61ea-4deb-b7e6-79dc73653959
    ProtectionOwner: User1@Contoso.OnMicrosoft.com
    IsProtected: True
    Press a key to continue.
   ```