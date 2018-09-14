---
title: AIP-Entwicklerterminologie | Microsoft-Dokumentation
description: Sammlung mit Terminologiedefinitionen für Entwickler, die speziell für Rights Management Services gelten.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8ddf0b8722111ff2cd4c433337c4e0c930b02009
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151555"
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

