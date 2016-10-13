---
title: 'Gewusst wie: Festlegen des API-Sicherheitsmodus | Azure RMS'
description: "Wählen Sie aus, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: f10129cb907cafa0e0c717b02153bbcdea012959


---

# Exemplarische Vorgehensweise: Festlegen des API-Sicherheitsmodus

Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [**IpcSetGlobalProperty**](/information-protection/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)-Funktion verwenden.

Rufen Sie zum Initialisieren der Anwendung für die Ausführung im *Servermodus* die [**IpcSetGlobalProperty**](/information-protection/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)-Funktion auf, und legen Sie den Sicherheitsmodus auf [**IPC\_API\_MODE\_SERVER**](/information-protection/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER) fest. Standardmäßig wird die Anwendung im *Clientmodus* (**IPC\_API\_MODE\_CLIENT**) ausgeführt.

Weitere Informationen zum *Servermodus* finden Sie unter [Anwendungstypen](application-types.md).

**Wichtig**: Der Sicherheitsmodus sollte festgelegt werden, bevor andere Funktionen des Rights Management Services SDK 2.1 aufgerufen werden. Nachdem der Sicherheitsmodus festgelegt wurde, kann er für den aktuellen Prozess nicht mehr geändert werden.

## Verwandte Themen

* [Anwendungstypen](application-types.md)
* [**API-Moduswerte**](/information-protection/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER)
* [**IpcSetGlobalProperty**](/information-protection/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
 

 



<!--HONumber=Sep16_HO5-->


