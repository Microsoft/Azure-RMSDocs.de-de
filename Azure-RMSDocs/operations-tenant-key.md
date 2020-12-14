---
title: Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel
description: Lernen Sie die verschiedenen Steuerungs- und Zuständigkeitsebenen kennen, die für Ihren Azure Information Protection-Mandantenschlüssel zur Verfügung stehen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 7d6cf57f75cdb3e60371dfae26509bd7f2e847c5
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97386473"
---
# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel

>**Gilt für*: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Je nach Mandantenschlüsseltopologie für Azure Information Protection stehen unterschiedliche Kontroll- und Zuständigkeitsebenen für Ihren Azure Information Protection-Mandantenschlüssel zur Verfügung. Es gibt zwei Schlüsseltopologien: **von Microsoft verwaltete** und **kundenverwaltete**.

Wenn Sie Ihren eigenen Mandantenschlüssel in Azure Key Vault verwalten, wird dies häufig als „Bring Your Own Key“ (BYOK) bezeichnet. Weitere Informationen zu diesem Szenario und zur Wahl zwischen den beiden Mandantenschlüsseltopologien finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

In der folgenden Tabelle sind die Vorgänge aufgeführt, die Sie in der jeweiligen Topologie, die Sie für Ihren Azure Information Protection-Mandantenschlüssel ausgewählt haben, ausführen können.

|Lebenszyklusvorgang|Von Microsoft verwaltet (Standard)|Kundenverwaltet (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Widerrufen Ihres Mandantenschlüssels|Nein (automatisch)|Ja|
|Neuerstellung Ihres Mandantenschlüssels|Ja|Ja|
|Sicherung und Wiederherstellung Ihres Mandantenschlüssels|Nein |Ja|
|Exportieren Ihres Mandantenschlüssels|Ja|Nein |
|Reaktion auf eine Sicherheitsverletzung|Ja|Ja|

Nachdem Sie die implementierte Topologie ermittelt haben, können Sie auf einen der folgenden Links klicken, um weitere Informationen zu diesen Vorgängen für Ihren Azure Information Protection-Mandantenschlüssel zu erhalten:

- [Von Microsoft verwalteter Mandantenschlüssel](operations-microsoft-managed-tenant-key.md)
- [Vom Kunden verwalteter Mandantenschlüssel](operations-customer-managed-tenant-key.md)

Wenn Sie jedoch einen Mandantenschlüssel für Azure Information Protection erstellen möchten, indem Sie eine vertrauenswürdige Veröffentlichungsdomäne (TPD) aus Active Directory Rights Management Services importieren, ist dieser Importvorgang jedoch Teil der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).  

