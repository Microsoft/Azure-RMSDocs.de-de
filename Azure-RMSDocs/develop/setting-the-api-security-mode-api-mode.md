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
ms.openlocfilehash: 5061a3a4375333224989f9a690c22a317e827fac
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568270"
---
# <a name="how-to-set-the-api-security-mode"></a>Exemplarische Vorgehensweise: Festlegen des API-Sicherheitsmodus

Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [IpcSetGlobalProperty](/previous-versions/windows/desktop/msipc/ipcsetglobalproperty)-Funktion verwenden.

Rufen Sie zum Initialisieren der Anwendung für die Ausführung im *Servermodus* die [IpcSetGlobalProperty](/previous-versions/windows/desktop/msipc/ipcsetglobalproperty)-Funktion auf, und legen Sie den Sicherheitsmodus auf [IPC\_API\_MODE\_SERVER](/previous-versions/windows/desktop/msipc/api-mode-values) fest. Standardmäßig wird Ihre Anwendung im *Client Modus*, **IPC \_ API \_ Mode \_ Client**, ausgeführt.

Weitere Informationen zum *Servermodus* finden Sie unter [Anwendungstypen](application-types.md).

**Wichtig**    Der Sicherheitsmodus sollte festgelegt werden, bevor eine andere Rights Management Services SDK 2,1-Funktion aufgerufen wird. Nachdem der Sicherheitsmodus festgelegt wurde, kann er für den aktuellen Prozess nicht mehr geändert werden.

## <a name="related-topics"></a>Verwandte Themen

* [Anwendungstypen](application-types.md)
* [API mode values (API-Moduswerte)](/previous-versions/windows/desktop/msipc/api-mode-values)
* [IpcSetGlobalProperty](/previous-versions/windows/desktop/msipc/ipcsetglobalproperty)