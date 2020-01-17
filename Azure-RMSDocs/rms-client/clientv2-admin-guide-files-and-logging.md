---
title: Azure Information Protection vereinheitlichte Bezeichnung von Client Dateien und Verwendungs Protokollierung
description: Informationen zu den Client Dateien und Verwendungs Protokollierung für den Azure Information Protection Unified-Bezeichnungs Client für Windows.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/13/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 2983f346ba29bed30d1ceb2b055e4cdd1e152d4e
ms.sourcegitcommit: ad3e55f8dfccf1bc263364990c1420459c78423b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76117543"
---
# <a name="admin-guide-azure-information-protection-unified-labeling-client-files-and-client-usage-logging"></a>Administrator Handbuch: Azure Information Protection vereinheitlichte Bezeichnung für Client Dateien und Client Verwendungs Protokollierung

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Nachdem Sie den Azure Information Protection Unified Bezeichnung-Client installiert haben, müssen Sie möglicherweise wissen, wo sich Dateien befinden, und überwachen, wie der Client verwendet wird.

## <a name="file-locations-for-the-azure-information-protection-unified-labeling-client"></a>Dateispeicher Orte für den Azure Information Protection Unified-Bezeichnungs Client

Clientdateien:   

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Client Protokolldateien und aktuell installierte Richtlinien Dateien:

- Für 64-Bit- und 32-Bit-Betriebssysteme: **%localappdata%\Microsoft\MSIP**


## <a name="usage-logging-for-the-azure-information-protection-unified-labeling-client"></a>Verwendungs Protokollierung für den Azure Information Protection Unified-Bezeichnungs Client

Der Unified-Bezeichnungs Client protokolliert keine Benutzeraktivität im lokalen Windows-Ereignisprotokoll. Verwenden Sie stattdessen das [zentrale Berichterstattungs](../reports-aip.md) Feature von Azure Information Protection. 


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie alle Protokolldateien identifiziert haben, die dem Azure Information Protection Unified Bezeichnung-Client zugeordnet sind, finden Sie hier weitere Informationen, die Sie möglicherweise zur Unterstützung dieses Clients benötigen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)

