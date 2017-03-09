---
title: Testen der Anwendung | Azure RMS
description: Anweisungen zum Einrichten der Anwendung zum Testen.
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 65ac5120e58ea6a212c09f7c2dd278356d0778b1


---

# <a name="testing-your-application"></a>Testen der Anwendung

Dieses Thema enthält Anleitungen zum Einrichten der Anwendung zum Testen.

## <a name="instructions"></a>Anweisungen

### <a name="step-1-setup-for-testing"></a>Schritt 1: Einrichten für Tests

Sie können Tests entweder mit Azure RMS oder mit einem RMS-Server unter Windows Server ausführen. Wir empfehlen, dass Sie Tests zunächst unter Azure RMS und anschließend (sofern dies für Ihre Bereitstellung erforderlich ist) mit einem RMS-Server ausführen.

1. Informationen zum Testen mit Azure RMS finden Sie unter [Gewusst wie: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md).
2. Informationen zum Testen mit einem RMS-Server finden Sie unter [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md).
3. Im Folgenden wird beschrieben, wie die Developer-Laufzeit installiert wird.

   Sie müssen den Rights Management Service Client 2.1 auf dem Computer installieren, auf dem Sie die Anwendung testen.
   - Wenn Sie Ihre Anwendung auf einem anderen Computer als Ihrem Entwicklungscomputer testen, installieren Sie den RMS-Client 2.1 von der [AD RMS-Client-Downloadseite](http://www.microsoft.com/en-us/download/details.aspx?id=38396) auf diesem Computer.
   - Wenn Sie Ihre Anwendung auf Ihrem Entwicklungscomputer testen, dann sollte das Rights Management Services SDK 2.1 bereits installiert sein. Der RMS-Client 2.1 wurde zu diesem Zeitpunkt im Hintergrund installiert.

    Informationen zum Installieren des RMS SDK 2.1 finden Sie unter [Installieren des SDK](install-the-rms-sdk.md).

## <a name="remarks"></a>Hinweise

Die Anleitung in diesem Thema ist nicht vollständig. Detaillierte Informationen zum Konfigurieren des RMS-Clients 2.1 finden Sie unter [Hinweise zur Bereitstellung des RMS-Clients 2.1](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx).

### <a name="related-topics"></a>Verwandte Themen

* [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md)
* [Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md)
* [Installieren des SDK](install-the-rms-sdk.md)
* [Hinweise zur Bereitstellung des RMS-Clients 2.1](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


