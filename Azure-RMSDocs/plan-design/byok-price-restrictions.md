---
title: "BYOK – Preise und Einschränkungen | Azure RMS"
description: "Lernen Sie die Einschränkungen bei Verwendung kundenverwalteter Schlüssel (bekannt als „Bring Your Own Key“, BYOK) mit Azure RMS kennen."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ada00b6f6298e7d359c73eb38dfdac169eacb708
ms.openlocfilehash: d704f3d9357993bdb01a38cda6f434ab1583b627


---

# BYOK – Preise und Einschränkungen

>*Gilt für: Azure Rights Management, Office 365*


Organisationen mit einem Abonnement, das Azure Rights Management umfasst, können kundenverwaltete Schlüssel (BYOK) in Azure Key Vault verwenden und die Nutzung ohne Aufpreis protokollieren. Um Azure Key Vault verwenden zu können, müssen Sie jedoch über ein Azure-Abonnement verfügen, das Key Vault mit HSM-geschützten Schlüsseln unterstützt. Für die Verwendung eines Schlüssels in Azure Key Vault fällt eine monatliche Gebühr an. Weitere Informationen finden Sie auf der [Seite mit den Azure Key Vault-Preisen](https://azure.microsoft.com/en-us/pricing/details/key-vault/).

Wenn Benutzer sich über RMS for Individuals für ein kostenloses Konto registriert haben, können Sie BYOK und die Verwendungsprotokollierung nicht nutzen, da in dieser Konfiguration kein Mandantenadministrator zum Konfigurieren dieser Features vorhanden ist.


> [!NOTE]
> Weitere Informationen zu RMS for Individuals finden Sie unter [RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md).

![BYOK unterstützt Exchange Online nicht.](../media/RMS_BYOK_noExchange.png)

BYOK und die Verwendungsprotokollierung arbeiten nahtlos mit jeder Anwendung zusammen, die in Azure RMS integriert wird. Dazu gehören Clouddienste wie SharePoint Online, lokale Server mit Exchange und SharePoint, für die Azure RMS unter Verwendung des RMS-Connectors eingesetzt wird, sowie Clientanwendungen wie Office 2016 und Office 2013. Sie erhalten Protokolle der Schlüsselnutzung unabhängig davon, welche Anwendung Anforderungen an Azure RMS stellt.

Es gibt eine Ausnahme: Derzeit ist **Azure RMS BYOK nicht mit Exchange Online kompatibel**. Wenn Sie Exchange Online verwenden möchten, empfehlen wir, dass Sie Azure RMS jetzt im Standard-Schlüsselverwaltungsmodus bereitstellen, in dem Microsoft Ihren Schlüssel generiert und verwaltet. Sie können später zu BYOK wechseln, beispielsweise wenn Exchange Online Azure RMS BYOK unterstützt. Wenn Sie jedoch nicht warten können, haben Sie jetzt die Möglichkeit, Azure RMS mit BYOK mit eingeschränkter RMS-Funktionalität für Exchange Online bereitzustellen (ungeschützte E-Mails und Anlagen bleiben dabei voll funktionsfähig):

-   Geschützte E-Mails oder Anlagen in Outlook Web Access können nicht angezeigt werden.

-   Geschützte E-Mails auf mobilen Geräten, die Exchange ActiveSync IRM verwenden, können nicht angezeigt werden.

-   Die Transport- (z. B. zum Scannen nach Schadsoftware) und Journalentschlüsselung sind nicht möglich, sodass geschützte E-Mails und Anlagen übersprungen werden.

-   Transportschutzregeln und die Verhinderung von Datenverlust (Data Loss Prevention, DLP), die IRM-Richtlinien erzwingen, sind nicht möglich, sodass der RMS-Schutz mit diesen Methoden nicht angewendet werden kann.

-   Serverbasierte Suche für geschützte E-Mails, sodass geschützte E-Mails übersprungen werden.

Bei der Verwendung von Azure RMS BYOK mit eingeschränkter RMS-Funktionalität für Exchange Online funktioniert RMS mit E-Mail-Clients in Outlook auf Windows- und Mac-Computern und mit anderen E-Mail-Clients, die Exchange ActiveSync IRM nicht verwenden.

Wenn Sie von AD RMS zu Azure RMS migrieren, haben Sie möglicherweise Ihren Schlüssel als vertrauenswürdige Veröffentlichungsdomäne (TPD) in Exchange Online importiert (in der Exchange-Terminologie auch als BYOK bezeichnet, was sich von Azure Key Vault BYOK unterscheidet). In diesem Szenario müssen Sie die vertrauenswürdige Veröffentlichungsdomäne aus Exchange Online entfernen, um in Konflikt stehende Vorlagen und Richtlinien zu vermeiden. Weitere Informationen finden Sie unter [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) in der Cmdlets-Bibliothek für Exchange Online.

In einigen Fällen stellt die Azure RMS BYOK-Ausnahme in der Praxis kein Problem für Exchange Online dar. Beispielsweise führen Organisationen, die BYOK und Protokollierung benötigen, ihre Datenanwendungen (Exchange, SharePoint, Office) lokal aus und verwenden Azure RMS für Funktionen, die bei lokalem AD RMS nicht einfach verfügbar sind (z. B. Zusammenarbeit mit anderen Unternehmen und Zugriff von mobilen Clients aus). Sowohl BYOK als auch die Protokollierung funktionieren gut in diesem Szenario und gestatten der Organisation die Übernahme der vollständigen Kontrolle über ihr Azure RMS-Abonnement.

## Nächste Schritte

Wenn Sie sich für die Verwaltung Ihres eigenen Schlüssels entschieden haben, helfen Ihnen die Informationen unter [Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) weiter.

Wenn Sie sich für die Standardkonfiguration entschieden haben, bei der Ihr Mandantenschlüssel von Microsoft verwaltet wird, helfen Ihnen die Informationen im Abschnitt [Nächste Schritte](plan-implement-tenant-key.md#next-steps) des Artikels „Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels“ weiter.




<!--HONumber=Aug16_HO4-->


