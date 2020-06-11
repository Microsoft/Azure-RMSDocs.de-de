---
title: RMS SDK 4,2-Hinweis zur Veraltung
description: RMS SDK 4,2-Hinweis zur Veraltung
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
ms.date: 03/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 51af06c37e6ee23a762f35791b0796b93b52e83b
ms.sourcegitcommit: f32928f7dcc03111fc72d958cda9933d15065a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2020
ms.locfileid: "84665808"
---
# <a name="rms-sdk-42-deprecation-notice"></a>RMS SDK 4,2-Hinweis zur Veraltung 

*Gilt für alle Versionen von RMS SDK 4,2 Versionen vor dem 2020. März*

Am 3. März 2020 wurde ein Update der RMS SDK 4,2 für Android, IOS und OSX über das Microsoft Download Center veröffentlicht. Dieses Update ist für alle Anwendungen obligatorisch, die diese RMS SDK Plattformen heute verwenden.  

Am Dienstag, 15. September, werden 2020 Versionen der RMS SDK, die vor dem März 2020 veröffentlicht wurden, keine Verbindung mit dem Azure Rights Management-Dienst Endpunkt herstellen. Anwendungen, die RMS SDK 4,2 verwenden, müssen vor diesem Datum aktualisiert werden. 

## <a name="reason-for-change"></a>Grund für Änderungen 

In früheren Versionen des-RMS SDK wird das Fixieren von Zertifikaten verwendet, um sicherzustellen, dass der RMS-fähige Client mit dem RMS-Dienst kommuniziert und ein Zertifikat empfängt, das mit einer bestimmten, erwarteten Stamm Zertifizierungsstelle verkettet ist.  

Moderne Browser verwenden Zertifikat Transparenz Protokolle, um zu überprüfen, ob Zertifikate für berechtigte Domänen Besitzer ausgestellt wurden und dass diese Zertifikate von vertrauenswürdigen Stamm Zertifizierungsstellen ausgestellt werden.  

Um moderne Browser besser unterstützen zu können, aktualisiert Microsoft am 15. September 2020 das Zertifikat für `https://api.aadrm.com` auf ein neues Zertifikat, das von einer global vertrauenswürdigen Stamm Zertifizierungsstelle ausgestellt wurde, die ausgestellte Zertifikate für Zertifikat Transparenz Protokolle ausgibt, die von modernen Browsern als vertrauenswürdig eingestuft werden. Wenn diese Änderung vollständig ist, können ältere Versionen von RMS SDK, die versuchen, das Zertifikat an das erwartete Stamm Zertifikat anzuhependen, dieses Zertifikat nicht finden. die Verbindung kann nicht hergestellt werden.  

## <a name="client-impact"></a>Client Auswirkung 

Die folgenden Microsoft-Anwendungen verwenden heute die RMS SDI. Updates werden für diese Plattformen zur Verfügung gestellt, und die Geräte sollten vor dem Stichtag für September aktualisiert werden. 

- Office 2019 für Mac 
- Office 2016 für Mac 
- Word, Excel und PowerPoint für IOS 
- Word, Excel und PowerPoint für Android 

Ressourcen 

- Android: https://www.microsoft.com/download/details.aspx?id=43673
- iOS: https://www.microsoft.com/download/details.aspx?id=43674 
- macOS: https://www.microsoft.com/download/details.aspx?id=43675 
- Linux: https://azuread.github.io/rms-sdk-for-cpp/annotated.html