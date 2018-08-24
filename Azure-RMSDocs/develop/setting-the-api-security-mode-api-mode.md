---
title: 'Gewusst wie: Festlegen des API-Sicherheitsmodus | Azure RMS'
description: Wählen Sie aus, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: c6e7d29ac65e9f8494e6aaba8d5e3e2564bd3305
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808411"
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
