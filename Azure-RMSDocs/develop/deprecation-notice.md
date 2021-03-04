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
ms.openlocfilehash: dbf96e317f70e41e76223cf6512eaa32427ff4c9
ms.sourcegitcommit: 7420cf0200c90687996124424a254c289b11a26f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844301"
---
# <a name="rms-sdk-42-deprecation-notice"></a>RMS SDK 4,2-Hinweis zur Veraltung 

*Gilt für alle Versionen von RMS SDK 4,2 Versionen vor dem 2020. März*

Am 3. März 2020 wurde ein Update der RMS SDK 4,2 für Android, IOS und OSX über das Microsoft Download Center veröffentlicht. Dieses Update ist für alle Anwendungen obligatorisch, die diese RMS SDK Plattformen heute verwenden.  

Ab Januar 2021 können Versionen der RMS SDK, die vor dem März 2020 veröffentlicht wurden, keine Verbindung mit dem Azure Rights Management-Dienst Endpunkt herstellen. Anwendungen, die noch nicht aktualisiert wurden, können keine TLS-Verbindung mit dem Azure Rights Management-Dienst herstellen. 

## <a name="reason-for-change"></a>Grund für Änderungen 

In früheren Versionen des-RMS SDK wird das Fixieren von Zertifikaten verwendet, um sicherzustellen, dass der RMS-fähige Client mit dem RMS-Dienst kommuniziert und ein Zertifikat empfängt, das mit einer bestimmten, erwarteten Stamm Zertifizierungsstelle verkettet ist.  

Moderne Browser verwenden Zertifikat Transparenz Protokolle, um zu überprüfen, ob Zertifikate für berechtigte Domänen Besitzer ausgestellt wurden und dass diese Zertifikate von vertrauenswürdigen Stamm Zertifizierungsstellen ausgestellt werden.  

Um moderne Browser besser zu unterstützen, aktualisiert Microsoft am 1. Dezember 2020 das Zertifikat für `https://api.aadrm.com` auf ein neues Zertifikat, das von einer global vertrauenswürdigen Stamm Zertifizierungsstelle ausgestellt wurde, die ausgestellte Zertifikate für Zertifikat Transparenz Protokolle meldet, denen moderne Browser vertraut sind. Wenn diese Änderung vollständig ist, können ältere Versionen von RMS SDK, die versuchen, das Zertifikat an das erwartete Stamm Zertifikat anzuhependen, dieses Zertifikat nicht finden. die Verbindung kann nicht hergestellt werden.  

## <a name="client-impact"></a>Client Auswirkung 

Die folgenden Microsoft-Anwendungen verwenden heute die RMS SDI. Für diese Plattformen wurden Updates zur Verfügung gestellt, und die Geräte sollten vor dem Stichtag für Dezember aktualisiert werden. 

- Office Pro Plus/2019 für Mac, Version 16,40 oder höher.
- Office 2016 für Mac, Version 16.16.27 oder höher.
- Word, Excel und PowerPoint für IOS, Version 2.40.20071600 oder höher.
- Word, Excel und PowerPoint für Android, Version 16.0.12827.20140 oder höher.

Ressourcen 

- Android: https://www.microsoft.com/download/details.aspx?id=43673
- iOS: https://www.microsoft.com/download/details.aspx?id=43674 
- macOS: https://www.microsoft.com/download/details.aspx?id=43675 
- Linux: https://azuread.github.io/rms-sdk-for-cpp/annotated.html
