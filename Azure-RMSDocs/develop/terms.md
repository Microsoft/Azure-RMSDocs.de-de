---
title: Begriffe | Azure RMS
description: "Sammlung mit Terminologiedefinitionen, die speziell für Rights Management Services gelten."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 8d6a7553123d36f5a08665949e6417d83bd3912e


---

# <a name="terms"></a>Nutzungsbedingungen

Sammlung mit Terminologiedefinitionen, die speziell für Rights Management Services gelten.

**Veralteter Algorithmus**  
Eine modale Einstellung, mit der ein älteres Inhaltsschutzschema implementiert wird, bei dem speziell auf den Electronic Codebook-Verschlüsselungsmodus (Electronic Codebook cipher mode; ECB) verwiesen wird. Die Einstellung ermöglicht es Ihnen in diesem SDK, Lizenzen zu generieren, die mit der vom [AD Rights Management Services SDK](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx) verwendeten MSDRM-Bibliothek kompatibel sind.

Diese Einstellung kann dazu führen, dass Inhalt von Ihrer Anwendung mit einem Verfahren geschützt wird, das den Kundenstandards für den Inhaltsschutz nicht entspricht.

Mit der Einstellung wird verhindert, dass Ihre Anwendung von den kryptografischen Erweiterungen profitiert, die dem Microsoft Rights Management SDK 3.0 oder höher hinzugefügt werden.

**Microsoft Protected File-Format**

Wird auch als PFile-Format bezeichnet. Es ist das Standardformat für AD RMS und fungiert als Standard für alle RMS-fähigen Anwendungen.

Das PFile-Format ist für den Anwendungsentwickler transparent, da es in den Entwurf des Microsoft Rights Management SDK 4.2 eingebettet ist.

 

 






<!--HONumber=Nov16_HO2-->


