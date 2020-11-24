---
title: Testen der Anwendung | Azure RMS
description: Erfahren Sie, wie Sie sich mit Azure RMS oder einem RMS-Server, der unter Windows Server ausgeführt wird, auf Anwendungstests vorbereiten.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: c4c6ac4e2f8463e7d17f8ebd609a1276edbce1f7
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568195"
---
# <a name="testing-your-application"></a>Testen Ihrer Anwendung

Hier erfahren Sie, wie Sie das Testen einer Anwendung vorbereiten.

## <a name="instructions"></a>Instructions

Sie können mit Azure RMS oder mit einem RMS-Server Tests durchführen, der unter Windows Server läuft.  Testen Sie zuerst mit Azure RMS und dann mit dem RMS-Server (falls für Ihre Bereitstellung erforderlich).

- Informationen zum Testen mit Azure RMS finden Sie unter [Gewusst wie: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md).
- Informationen zum Testen mit einem RMS-Server finden Sie unter [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md).
- Installieren der Developer-Runtime

   Sie müssen den Rights Management Service Client 2.1 auf dem Computer installieren, auf dem Sie die Anwendung testen.
  - Um Ihre Anwendung auf einem anderen Computer als Ihrem Entwicklungscomputer zu testen, installieren Sie den RMS-Client 2.1 von der [AD RMS-Client-Downloadseite](https://www.microsoft.com/download/details.aspx?id=38396) auf diesem Computer.
  - Auf Ihrem Entwicklungscomputer sollte bereits vorher das Rights Management Services SDK 2.1 installiert worden sein.

    Hilfe zur Installation des RMS SDK 2.1 finden Sie unter [Install the SDK (Installieren des SDK)](install-the-rms-sdk.md).

## <a name="remarks"></a>Bemerkungen

Diese Anleitung geht nicht auf Details ein. Informationen zum Konfigurieren des RMS-Clients 2.1 finden Sie unter [Anmerkungen zur Bereitstellung des RMS-Clients 2.1](../rms-client/client-deployment-notes.md).

## <a name="related-topics"></a>Verwandte Themen

* [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md)
* [Vorgehensweise: Verwenden der Adal-Authentifizierung](how-to-use-adal-authentication.md)
* [Installieren des SDKs](install-the-rms-sdk.md)
* [Hinweise zur Bereitstellung des RMS-Clients 2.1](../rms-client/client-deployment-notes.md)