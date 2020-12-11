---
title: 'Schnellstart: Verschlüsseln/Entschlüsseln von Text mit der Schutz-API im MIP SDK für C#'
description: Dieser Schnellstart zeigt die Verwendung des .NET-Wrappers im Microsoft Information Protection SDK für C#, um Ad-hoc-Text mithilfe einer Schutzvorlage zu verschlüsseln und zu entschlüsseln (C#).
services: information-protection
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 03/30/2020
ms.author: v-anikep
ms.custom: has-adal-ref
ms.openlocfilehash: 5fae5837ab26c4fce20ac120293eff3823dd9b70
ms.sourcegitcommit: 6322f840388067edbe3642661e313ff225be5563
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96535823"
---
# <a name="quickstart-encryptdecrypt-text-using-mip-sdk-c"></a>Schnellstart: Verschlüsseln/Entschlüsseln von Text mit dem MIP SDK (C#)

In diesem Schnellstart wird gezeigt, wie Sie weitere MIP-Schutz-APIs nutzen. Sie verwenden eine der im vorherigen Schnellstart aufgelisteten Schutzvorlagen, um mit einem Schutzhandler Ad-hoc-Text zu verschlüsseln. Die Schutzhandlerklasse macht verschiedene Vorgänge zum Anwenden/Entfernen von Schutz verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Bearbeiten Sie zunächst den [Schnellstart: Auflisten von Schutzvorlagen (C#)](quick-protection-list-templates-csharp.md), in dem eine Visual Studio-Startprojektmappe erstellt wird, um die Schutzvorlagen aufzulisten, die einem authentifizierten Benutzer zur Verfügung stehen. Der vorliegende Schnellstart zum Verschlüsseln/Entschlüsseln von Text baut auf dem vorherigen Schnellstart auf.
- Optional: Sehen Sie sich die Konzepte unter [ProtectionHandler im MIP SDK](concept-handler-protection-cpp.md) an.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>Hinzufügen von Logik zum Festlegen und Abrufen einer Vertraulichkeitsbezeichnung

Fügen Sie mit dem Schutz-Engine-Objekt Logik zum Verschlüsseln von Ad-hoc-Text hinzu.

1. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CS-Datei im Projekt, die die Implementierung der Main()-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

2. Fügen Sie gegen Ende des `Main()`-Texts – an der Stelle, an der Sie im vorherigen Schnellstart aufgehört haben – den folgenden Code ein:

   ```csharp
   //Set text to encrypt and template ID
   string inputText = "<Sample-text>";
   string templateId = "<template-id>";
   //Create a template based publishing descriptor
   ProtectionDescriptor protectionDescriptor = new ProtectionDescriptor(templateId);

   //Create publishing settings using protection descriptor
   PublishingSettings publishingSettings = new PublishingSettings(protectionDescriptor);

   //Generate Protection Handler for publishing
   var publishingHandler = Task.Run(async() => await protectionEngine.CreateProtectionHandlerForPublishingAsync(publishingSettings)).Result;

   //Encrypt text using Publishing handler
   long bufferSize = publishingHandler.GetProtectedContentLength(inputText.Length, true);
   byte[] inputTextBuffer = Encoding.ASCII.GetBytes(inputText);
   byte[] encryptedTextBuffer = new byte[bufferSize];
   publishingHandler.EncryptBuffer(0, inputTextBuffer, encryptedTextBuffer, true);
   Console.WriteLine("Original text: {0}", inputText);
   Console.WriteLine("Encrypted text: {0}", Encoding.UTF8.GetString(encryptedTextBuffer));

   //Create a Protection handler for consumption using the same publishing licence
   var serializedPublishingLicense = publishingHandler.GetSerializedPublishingLicense();
   PublishingLicenseInfo plInfo = PublishingLicenseInfo.GetPublishingLicenseInfo(serializedPublishingLicense);
   ConsumptionSettings consumptionSettings = new ConsumptionSettings(plInfo);
   var consumptionHandler = protectionEngine.CreateProtectionHandlerForConsumption(consumptionSettings);

   //Use the handler to decrypt the encrypted text
   long buffersize = encryptedTextBuffer.Length;
   byte[] decryptedBuffer = new byte[bufferSize];
   var bytesDecrypted = consumptionHandler.DecryptBuffer(0, encryptedTextBuffer, decryptedBuffer, true);
   byte[] OutputBuffer = new byte[bytesDecrypted];
   for (int i = 0; i < bytesDecrypted; i++){
      OutputBuffer[i] = decryptedBuffer[i];
   }

   Console.WriteLine("Decrypted content: {0}", Encoding.UTF8.GetString(OutputBuffer));
   Console.WriteLine("Press a key to quit.");
   Console.ReadKey();

   ```

3. Suchen Sie am Ende von `Main()` den Block zum Herunterfahren der Anwendung, den Sie im ersten Schnellstart erstellt haben, und fügen Sie die Handlerzeilen ein:

   ```csharp
   // Application Shutdown
   publishingHandler = null;
   consumptionHandler = null;
   protectionEngine = null;
   protectionProfile = null;
   mipContext = null;
   ```

4. Ersetzen Sie die Platzhalterwerte im Quellcode durch die folgenden Werte:

   | Platzhalter | Wert |
   |:----------- |:----- |
   | \<sample-text\> | Beispieltext, den Sie verschlüsseln möchten. Beispiel: `My secure text`. |
   | \<template-id\> | Eine Vorlagen-ID, kopiert aus der Konsolenausgabe im vorherigen Schnellstart. Beispiel: `bb7ed207-046a-4caf-9826-647cff56b990`. |

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B (**Projektmappe erstellen**), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, *kann* die Anwendung Sie jedes Mal zur Authentifizierung über ADAL auffordern, wenn das SDK Ihre `AcquireToken()`-Methode aufruft. Wenn bereits zwischengespeicherte Anmeldeinformationen vorhanden sind, werden Sie nicht zur Anmeldung aufgefordert. Die Liste der Bezeichnungen mit den Informationen zur angewendeten Bezeichnung und der geänderten Datei wird sofort angezeigt.

  ```console
   Original content: My secure text
   Encrypted content: c?_hp???Q??+<?
   Decrypted content: My secure text
   Press a key to quit.
   ```
