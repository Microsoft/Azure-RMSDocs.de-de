---
# required metadata

title: Festlegen des API-Sicherheitsmodus | Azure RMS
description: Wählen Sie aus, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Dieser SDK-Inhalt ist nicht aktuell. Für kurze Zeit finden Sie die [aktuelle Version](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) der Dokumentation auf MSDN. **
# Festlegen des API-Sicherheitsmodus

Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)-Funktion verwenden.

Rufen Sie zum Initialisieren der Anwendung für die Ausführung im *Servermodus* die [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)-Funktion auf, und legen Sie den Sicherheitsmodus auf [**IPC\_API\_MODE\_SERVER**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER) fest. Standardmäßig wird die Anwendung im *Clientmodus* (**IPC\_API\_MODE\_CLIENT**) ausgeführt.

Weitere Informationen zum *Servermodus* finden Sie unter [Anwendungstypen](application-types.md).

**Wichtig**: Der Sicherheitsmodus sollte festgelegt werden, bevor andere Funktionen des Rights Management Services SDK 2.1 aufgerufen werden. Nachdem der Sicherheitsmodus festgelegt wurde, kann er für den aktuellen Prozess nicht mehr geändert werden.

 

## Verwandte Themen

* [Anwendungstypen](application-types.md)
* [Entwicklerkonzepte](ad-rms-concepts-nav.md)
* [**API-Moduswerte**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
 

 





<!--HONumber=Jun16_HO1-->

