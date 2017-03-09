---
title: AIP-Entwicklerterminologie | Microsoft-Dokumentation
description: "Sammlung mit Terminologiedefinitionen für Entwickler, die speziell für Rights Management Services gelten."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9c0977c57ea8e85b6750fe1f5a063059ee343db9
ms.openlocfilehash: 4ecf686d8e7e26909c8bda4a2d0df7fc61f413bb


---

# <a name="terms"></a>Nutzungsbedingungen

Sammlung mit Terminologiedefinitionen für Entwickler, die speziell für Azure Information Protection gelten.

**Veralteter Algorithmus**  
Eine modale Einstellung, mit der ein älteres Inhaltsschutzschema implementiert wird, bei dem speziell auf den Electronic Codebook-Verschlüsselungsmodus (Electronic Codebook cipher mode; ECB) verwiesen wird. Die Einstellung ermöglicht es Ihnen in diesem SDK, Lizenzen zu generieren, die mit der vom [AD Rights Management Services SDK](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx) verwendeten MSDRM-Bibliothek kompatibel sind.

Diese Einstellung kann dazu führen, dass Inhalt von Ihrer Anwendung mit einem Verfahren geschützt wird, das den Kundenstandards für den Inhaltsschutz nicht entspricht.

Mit der Einstellung wird verhindert, dass Ihre Anwendung von den kryptografischen Erweiterungen profitiert, die dem Microsoft Rights Management SDK 3.0 oder höher hinzugefügt werden.

**Microsoft Protected File-Format**

Wird auch als PFile-Format bezeichnet. Es ist das Standardformat für AD RMS und fungiert als Standard für alle RMS-fähigen Anwendungen.

Das PFile-Format ist für den Anwendungsentwickler transparent, da es in den Entwurf des Microsoft Rights Management SDK 4.2 eingebettet ist.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


