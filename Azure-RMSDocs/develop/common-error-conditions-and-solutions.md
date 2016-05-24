---
# required metadata

title: Häufige Fehlerbedingungen und Lösungen | Azure RMS
description: Dieses Thema umfasst die häufigsten Fehlermeldungen, die auftreten können, wenn Sie die RMS SDK 2.1-Entwicklertools verwenden.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: A5B95EB8-3528-4CFF-86FC-166613A5F4A3
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Häufige Fehlerbedingungen und Lösungen
Dieses Thema umfasst die häufigsten Fehlermeldungen, die auftreten können, wenn Sie die Rights Management Services SDK 2.1-Entwicklertools verwenden. Darüber hinaus stellt es eine empfohlene Aktion zum Beheben des Fehlers bereit, sofern zutreffend.

**Wichtig** – Verwenden Sie für die Verarbeitung von Fehlerbedingung immer einen Aufruf von [IpcGetErrorMessageText](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) direkt nach dem Fehler eines SDK-API-Aufrufs, daher Sie umfassende Informationen über die Art des Fehlers erhalten.

 

## Fehler und Aktion ##
Die nachstehende Liste enthält Fehlerkonstanten, deren zugeordnete Beschreibung und eine empfohlene Aktion zum Beheben der Fehlerbedingung.

**FEHLER** – *IPCERROR_DEBUGGER_DETECTED* – Ein Debugger wurde von RMS SDK 2.1 erkannt.

**AKTION** – Die Entwicklerversion von RMS SDK 2.1 überprüft das Vorhandensein eines Debuggers nicht. Wenn möglich, debuggen Sie die Anwendung mit dieser Version von RMS SDK 2.1.
Wenn Sie die Produktionsversion von RMS SDK 2.1 debuggen müssen, verwenden Sie die folgende Anleitung.

Einige RMS SDK 2.1-Funktionen sollen unter einem Debugger fehlschlagen:
- [IpcGetKey</strong>](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
- [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
- [IpcGetTemplateIssuerList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)

Um nach diesen Funktionsaufrufen Code zu debuggen, müssen Sie den Prozess unterbrechen und einen Debugger anfügen, nachdem die Funktionsaufrufe abgeschlossen wurden. Dazu können Sie u. a. eine Assert-Anweisung verwenden, um den Debugger zu unterbrechen. Das ASSERTE-Makro ist Bestandteil des *Crtdbg.h*-Headers.
Weitere Informationen zu \_ASSERTE, finden Sie unter [\_ASSERT-, \_ASSERTE-Makros](https://msdn.microsoft.com/en-us/library/ezb1wyez.aspx)

**FEHLER** – *IPCERROR_BROKEN_CERT_CHAIN* – Zertifikatkette stimmt nicht überein.

**AKTION** – Stellen Sie sicher, dass der Hierarchieschlüssel den richtigen Wert basierend auf dem Schlüssel enthält, den Sie verwendet haben, um das AD RMS-Anwendungsmanifest zu signieren.
Dies sind die Signaturschlüssel und die zugehörigen Werte (Hierarchie **DWORD**):
- ISV – 1
- Produktion – 0 oder nicht vorhanden

**FEHLER** – *IPCERROR_MACHINE_CERT_NOT_TRUSTED* – Sie verwenden eine Anwendung, die mit dem ISV-Signaturschlüssel signiert wurde, die aber versucht, mit einem AD RMS-Produktionsserver (oder umgekehrt) zu kommunizieren.

- Wenn Sie die Entwicklerversion des AD RMS-Servers verwenden, stellen Sie sicher, dass Sie den ISV-Signaturschlüssel zum Signieren der Anwendung verwenden.
- Wenn Sie die Produktionsversion des AD RMS-Servers verwenden, stellen Sie sicher, dass Sie den ISV-Produktionssignaturschlüssel zum Signieren der Anwendung verwenden.

**FEHLER** – *IPCERROR_APPLICATION_AUTH_ERROR_MANIFEST* – Das Anwendungsmanifest ist ungültig. Dies kann verursacht werden, wenn die Binärdatei (Anwendung) neu erstellt und das Manifest nicht neu generiert wurde.

**AKTION** – Stellen Sie sicher, dass Sie das Anwendungsmanifest jedes Mal, wenn Sie Ihre Anwendung neu erstellen, neu generieren.

## Verwandte Themen ##
* [Hinweise für Entwickler](developer-notes.md)
* [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [IpcGetTemplateIssuerList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [\_ASSERT-, \_ASSERTE-Makros](https://msdn.microsoft.com/en-us/library/ezb1wyez.aspx)
 

 


<!--HONumber=Apr16_HO4-->


