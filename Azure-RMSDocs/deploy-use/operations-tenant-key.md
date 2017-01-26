---
title: "Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel | Azure Information Protection"
description: "Lernen Sie die verschiedenen Steuerungs- und Zuständigkeitsebenen kennen, die für Ihren Azure Information Protection-Mandantenschlüssel zur Verfügung stehen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 0e10e5d5aba51f96ab1e29e42ae39929c321f563


---

# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel

>*Gilt für: Azure Information Protection, Office 365*

Abhängig von der Mandantenschlüsseltopologie (von Microsoft oder vom Kunden verwaltet) verfügen Sie über verschiedene Ebenen der Steuerung und Zuständigkeit für Ihren Azure Information Protection-Mandantenschlüssel, nachdem dieser implementiert wurde.

Wenn Sie Ihren eigenen Mandantenschlüssel in Azure Key Vault verwalten, wird dies häufig als „Bring Your Own Key“ (BYOK) bezeichnet. Weitere Informationen zu diesem Szenario und zur Wahl zwischen den beiden Mandantenschlüssel-Topologien finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

In der folgenden Tabelle sind die Vorgänge aufgeführt, die Sie in der jeweiligen Topologie, die Sie für Ihren Azure Information Protection-Mandantenschlüssel ausgewählt haben, ausführen können.

|Lebenszyklusvorgang|Von Microsoft verwaltet (Standard)|Kundenverwaltet (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Widerrufen Ihres Mandantenschlüssels|Nein (automatisch)|Ja|
|Neuvergabe (Rollover) Ihres Mandantenschlüssels|Ja |Ja|
|Sicherung und Wiederherstellung Ihres Mandantenschlüssels|Nein|Ja|
|Exportieren Ihres Mandantenschlüssels|Ja|Nein|
|Reaktion auf eine Sicherheitsverletzung|Ja|Ja|

Nachdem Sie die implementierte Topologie ermittelt haben, können Sie auf einen der folgenden Links klicken, um weitere Informationen zu diesen Vorgängen für Ihren Azure Information Protection-Mandantenschlüssel zu erhalten:


- [Von Microsoft verwalteter Mandantenschlüssel](operations-microsoft-managed-tenant-key.md)
- [Vom Kunden verwalteter Mandantenschlüssel](operations-customer-managed-tenant-key.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


