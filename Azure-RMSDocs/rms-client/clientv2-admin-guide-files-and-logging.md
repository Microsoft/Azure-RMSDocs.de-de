---
title: Azure Information Protection unified bezeichnungs-Clientdateien und verwendungsprotokollierung
description: Informationen zu den Clientdateien und verwendungsprotokollierung für Azure Information Protection unified bezeichnungs-Client für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: f49495ae79dbd61e85406957c0fb7864be7116ac
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60181292"
---
# <a name="admin-guide-azure-information-protection-unified-labeling-client-files-and-client-usage-logging"></a>Administratorhandbuch: Azure Information Protection unified bezeichnungs-Clientdateien und clientverwendungsprotokollierung

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anleitungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Nachdem Sie den Azure Information Protection unified bezeichnungs-Client installiert haben, müssen Sie wissen, wo die Dateien gespeichert sind, und überwachen, wie der Client verwendet wird.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Dateispeicherorte für den Azure Information Protection-Client

Clientdateien:   

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Client-Protokolldateien:

- Für 64-Bit- und 32-Bit-Betriebssysteme: **%localappdata%\Microsoft\MSIP**


## <a name="next-steps"></a>Nächste Schritte
Nun, da Sie alle Protokolldateien verknüpft ist, mit dem Azure Information Protection unified bezeichnungs-Client ermittelt haben, finden Sie in der folgenden zusätzlichen Informationen, Sie zur Unterstützung dieses Clients müssen eventuell:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)

