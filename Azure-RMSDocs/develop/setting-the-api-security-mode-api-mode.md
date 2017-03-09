---
title: 'Gewusst wie: Festlegen des API-Sicherheitsmodus | Azure RMS'
description: "Wählen Sie aus, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 49e87a8bf7ec5e628cf76c6ec82df2bb1b0835a3


---

# <a name="how-to-set-the-api-security-mode"></a>Exemplarische Vorgehensweise: Festlegen des API-Sicherheitsmodus

Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)-Funktion verwenden.

Rufen Sie zum Initialisieren der Anwendung für die Ausführung im *Servermodus* die [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)-Funktion auf, und legen Sie den Sicherheitsmodus auf [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx) fest. Standardmäßig wird die Anwendung im *Clientmodus* (**IPC\_API\_MODE\_CLIENT**) ausgeführt.

Weitere Informationen zum *Servermodus* finden Sie unter [Anwendungstypen](application-types.md).

**Wichtig**: Der Sicherheitsmodus sollte festgelegt werden, bevor andere Funktionen des Rights Management Services SDK 2.1 aufgerufen werden. Nachdem der Sicherheitsmodus festgelegt wurde, kann er für den aktuellen Prozess nicht mehr geändert werden.

## <a name="related-topics"></a>Verwandte Themen

* [Anwendungstypen](application-types.md)
* [API mode values (API-Moduswerte)](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


