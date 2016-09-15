---
title: "Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel | Azure RMS"
description: "Identifizieren Sie die verschiedenen Steuerungs- und Zuständigkeitsebenen, die Sie für Ihren Azure RMS-Mandantenschlüssel (Azure Rights Management) vorgesehen haben."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad32910b482ca9d92b4ac8f3f123eda195db29cd
ms.openlocfilehash: d496a99c4b05e0cf0ba5929f44cdbd1906d31341


---

# Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel

>*Gilt für: Azure Rights Management, Office 365*

Abhängig von der Mandantenschlüsseltopologie (von Microsoft oder vom Kunden verwaltet), besitzen Sie verschiedene Stufen der Kontrolle und Verantwortlichkeit für Ihren Microsoft Azure Rights Management-Mandantenschlüssel (Azure RMS), nachdem er implementiert wurde.

Wenn Sie Ihren eigenen Mandantenschlüssel in Azure Key Vault verwalten, wird dies häufig als „Bring Your Own Key“ (BYOK) bezeichnet. Weitere Informationen zu diesem Szenario und zur Wahl zwischen den beiden Mandantenschlüssel-Topologien finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

In der folgenden Tabelle werden die Vorgänge identifiziert, die Sie in der jeweiligen Topologie, die Sie für Ihren Azure RMS-Mandantenschlüssel ausgewählt haben, ausführen können.

|Lebenszyklusvorgang|Von Microsoft verwaltet (Standard)|Kundenverwaltet (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Widerrufen Ihres Mandantenschlüssels|Nein (automatisch)|Ja|
|Neuvergabe (Rollover) Ihres Mandantenschlüssels|Ja |Ja|
|Sicherung und Wiederherstellung Ihres Mandantenschlüssels|Nein|Ja|
|Exportieren Ihres Mandantenschlüssels|Ja|Nein|
|Reaktion auf eine Sicherheitsverletzung|Ja|Ja|

Nachdem Sie identifiziert haben, welche Topologie Sie implementiert haben, können Sie einen der folgenden Punkte auswählen, um weitere Informationen zu diesen Vorgängen für Ihren Azure RMS-Mandantenschlüssel zu erhalten:


- [Von Microsoft verwalteter Mandantenschlüssel](operations-microsoft-managed-tenant-key.md)
- [Vom Kunden verwalteter Mandantenschlüssel](operations-customer-managed-tenant-key.md)







<!--HONumber=Aug16_HO4-->


