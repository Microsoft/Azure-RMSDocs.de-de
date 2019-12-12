---
title: Testen der Anwendung | Azure RMS
description: Anweisungen zum Einrichten der Anwendung zum Testen.
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
ms.custom: dev
ms.openlocfilehash: 8744ea8dfd7213030c741e6e760c506e0d795db4
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "68792263"
---
# <a name="testing-your-application"></a>Testen der Anwendung

Hier erfahren Sie, wie Sie das Testen einer Anwendung vorbereiten.

## <a name="instructions"></a>Anweisungen

Sie können mit Azure RMS oder mit einem RMS-Server Tests durchführen, der unter Windows Server läuft.  Testen Sie zuerst mit Azure RMS und dann mit dem RMS-Server (falls für Ihre Bereitstellung erforderlich).

- Informationen zum Testen mit Azure RMS finden Sie unter [Gewusst wie: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md).
- Informationen zum Testen mit einem RMS-Server finden Sie unter [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md).
- Installieren der Developer-Runtime

   Sie müssen den Rights Management Service Client 2.1 auf dem Computer installieren, auf dem Sie die Anwendung testen.
  - Um Ihre Anwendung auf einem anderen Computer als Ihrem Entwicklungscomputer zu testen, installieren Sie den RMS-Client 2.1 von der [AD RMS-Client-Downloadseite](https://www.microsoft.com/download/details.aspx?id=38396) auf diesem Computer.
  - Auf Ihrem Entwicklungscomputer sollte bereits vorher das Rights Management Services SDK 2.1 installiert worden sein.

    Hilfe zur Installation des RMS SDK 2.1 finden Sie unter [Install the SDK (Installieren des SDK)](install-the-rms-sdk.md).

## <a name="remarks"></a>Hinweise

Diese Anleitung geht nicht auf Details ein. Informationen zum Konfigurieren des RMS-Clients 2.1 finden Sie unter [Anmerkungen zur Bereitstellung des RMS-Clients 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx).

## <a name="related-topics"></a>Zugehörige Themen

* [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md)
* [Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md)
* [Installieren des SDK](install-the-rms-sdk.md)
* [Hinweise zur Bereitstellung des RMS-Clients 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx)

