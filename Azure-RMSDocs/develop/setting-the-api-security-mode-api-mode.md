---
title: 'Gewusst wie: Festlegen des API-Sicherheitsmodus | Azure RMS'
description: Erfahren Sie, wie Sie den API-Sicherheitsmodus mithilfe der ipcsetglobalproperty-Funktion festlegen, um auszuwählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 942192690e06422246fa0ed7a4fb2d1d3ccf6cd6
ms.sourcegitcommit: dc50f9a6c2f66544893278a7fd16dff38eef88c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88563599"
---
# <a name="how-to-set-the-api-security-mode"></a>Exemplarische Vorgehensweise: Festlegen des API-Sicherheitsmodus

Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)-Funktion verwenden.

Rufen Sie zum Initialisieren der Anwendung für die Ausführung im *Servermodus* die [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)-Funktion auf, und legen Sie den Sicherheitsmodus auf [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx) fest. Standardmäßig wird Ihre Anwendung im *Client Modus*, **IPC \_ API \_ Mode \_ Client**, ausgeführt.

Weitere Informationen zum *Servermodus* finden Sie unter [Anwendungstypen](application-types.md).

**Wichtig**    Der Sicherheitsmodus sollte festgelegt werden, bevor eine andere Rights Management Services SDK 2,1-Funktion aufgerufen wird. Nachdem der Sicherheitsmodus festgelegt wurde, kann er für den aktuellen Prozess nicht mehr geändert werden.

## <a name="related-topics"></a>Zugehörige Themen

* [Anwendungstypen](application-types.md)
* [API mode values (API-Moduswerte)](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
