---
title: "Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 44408fd8f9da73d8050e0938aa1cc9bc76688bed


---

# Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel

*Gilt für: Azure Rights Management, Office 365*

Abhängig von der Mandantenschlüsseltopologie (von Microsoft oder vom Kunden verwaltet), besitzen Sie verschiedene Stufen der Kontrolle und Verantwortlichkeit für Ihren Microsoft Azure Rights Management-Mandantenschlüssel (Azure RMS), nachdem er implementiert wurde.

Wenn Sie Ihren eigenen Mandantenschlüssel verwalten, wird dies häufig als „Bring Your Own Key“ (BYOK) bezeichnet. Weitere Informationen zu diesem Szenario und zur Wahl zwischen den beiden Mandantenschlüssel-Topologien finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

In der folgenden Tabelle werden die Vorgänge identifiziert, die Sie in der jeweiligen Topologie, die Sie für Ihren Azure RMS-Mandantenschlüssel ausgewählt haben, ausführen können.

|Lebenszyklusvorgang|Von Microsoft verwaltet (Standard)|Kundenverwaltet (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Widerrufen Ihres Mandantenschlüssels|Nein (automatisch)|Nein (automatisch)|
|Neuvergabe (Rollover) Ihres Mandantenschlüssels|Ja |Ja|
|Sicherung und Wiederherstellung Ihres Mandantenschlüssels|Nein|Ja|
|Exportieren Ihres Mandantenschlüssels|Ja|Nein|
|Reaktion auf eine Sicherheitsverletzung|Ja|Ja|

Nachdem Sie identifiziert haben, welche Topologie Sie implementiert haben, können Sie einen der folgenden Punkte auswählen, um weitere Informationen zu diesen Vorgängen für Ihren Azure RMS-Mandantenschlüssel zu erhalten:


- [Von Microsoft verwalteter Mandantenschlüssel](operations-microsoft-managed-tenant-key.md)
- [Vom Kunden verwalteter Mandantenschlüssel](operations-customer-managed-tenant-key.md)







<!--HONumber=Jun16_HO4-->


