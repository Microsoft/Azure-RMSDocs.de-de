---
title: 'Vorgehensweise: Erneutes Veröffentlichen in C#'
description: In diesem Artikel erfahren Sie, wie Sie den Schutzhandler zum erneuten Veröffentlichen wiederverwenden.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 05/01/2020
ms.author: v-anikep
ms.openlocfilehash: c72d284363c1ca988692d18b7007a88c88d808b5
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91421189"
---
# <a name="microsoft-information-protection-sdk---file-api-republishing-quickstart-c"></a>Microsoft Information Protection SDK: Schnellstart für die Wiederveröffentlichung der Datei-API (C#)

## <a name="overview"></a>Übersicht

Eine Übersicht zu diesem Szenario und dessen Verwendung finden Sie unter [Erneutes Veröffentlichen mit dem MIP SDK](concept-republishing.md).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart zum Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C#)](quick-file-set-get-label-csharp.md) ab. Darin wird eine Visual Studio-Startprojektmappe zum Auflisten der Vertraulichkeitsbezeichnungen einer Organisation erstellt, mit der Vertraulichkeitsbezeichnungen in einer Datei festgelegt oder aus dieser gelesen werden können. Diese Schnellstartanleitung zum erneuten Veröffentlichen einer geschützten Datei in C# baut auf der vorherigen Anleitung auf.
- Optional: Lesen Sie sich die Konzepte zu [Dateihandlern im MIP SDK](concept-handler-file-cpp.md) durch.
- Optional: Sehen Sie sich die Konzepte unter [ProtectionHandler im MIP SDK](concept-handler-protection-cpp.md) an.

## <a name="add-logic-to-edit-and-republish-a-protected-file"></a>Hinzufügen von Logik zum Bearbeiten und erneuten Veröffentlichen einer geschützten Datei

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Festlegen und Abrufen von Vertraulichkeitsbezeichnungen (C#)“ erstellt haben.

2. Öffnen Sie im Projektmappen-Explorer die CS-Datei des Projekts, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Fügen Sie gegen Ende des `Main()`-Bereichs zwischen `Console.ReadKey()` und dem oben aufgeführten Block zum Herunterfahren der Anwendung (wo Sie im vorherigen Schnellstart aufgehört haben) den folgenden Code ein:

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

4. Suchen Sie am Ende der Main()-Methode den Block zum Herunterfahren der Anwendung, den Sie im vorherigen Schnellstart erstellt haben, und fügen Sie die folgenden Handlerzeilen zum Freigeben der Ressourcen hinzu:

    ````csharp
        protectedFileHandler = null;
        protectionHandler = null;
    ````

5. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<protected-file-path\> | Dies ist die geschützte Datei aus der vorherigen Schnellstartanleitung. |
   | \<reprotected-file-path\> | Dies ist der Ausgabedateipfad für die erneute Veröffentlichung der angepassten Datei. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B ( **Projektmappe erstellen** ), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 ( **Debuggen starten** ) zum Ausführen der Anwendung.

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