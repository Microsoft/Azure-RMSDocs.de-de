---
title: Azure Information Protection vereinheitlichte Bezeichnung von Client Dateien und Verwendungs Protokollierung
description: Informationen zu den Client Dateien und Verwendungs Protokollierung für den Azure Information Protection Unified-Bezeichnungs Client für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 0658eda00dbbb2fa90038dcfefba00684a2919d2
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68789966"
---
# <a name="admin-guide-azure-information-protection-unified-labeling-client-files-and-client-usage-logging"></a>Administratorhandbuch: Azure Information Protection vereinheitlichte Bezeichnung von Client Dateien und Client Verwendungs Protokollierung

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Unified Bezeichnung-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Nachdem Sie den Azure Information Protection Unified Bezeichnung-Client installiert haben, müssen Sie möglicherweise wissen, wo sich Dateien befinden, und überwachen, wie der Client verwendet wird.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Dateispeicherorte für den Azure Information Protection-Client

Clientdateien:   

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Client Protokolldateien:

- Für 64-Bit-und 32-Bit-Betriebssysteme: **%LocalAppData%\microsoft\msip\logs**


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie alle Protokolldateien identifiziert haben, die dem Azure Information Protection Unified Bezeichnung-Client zugeordnet sind, finden Sie hier weitere Informationen, die Sie möglicherweise zur Unterstützung dieses Clients benötigen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)

