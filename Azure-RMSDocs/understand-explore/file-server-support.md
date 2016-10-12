---
title: "Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden | Azure Information Protection"
description: "Verwendung der Windows Server-Dateiklassifizierungsinfrastruktur mit Azure RMS, wenn Sie den RMS-Connector für den automatischen Schutz von Office-Dokumenten bereitstellen."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2c0f3b58a2f1b5233c262bb67cc4a485557ba997
ms.openlocfilehash: 64c718f91d1d2f516bcac6dd949eef5ef379a306


---


# Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden

>*Gilt für: Azure Information Protection, Office 365*


Wenn Sie Windows Server für die Verwendung der Dateiklassifizierungsinfrastruktur konfigurieren, kann dieses „Ressourcen-Manager für Dateiserver“-Feature lokale Dateien untersuchen und bestimmen, ob sie sensible Daten enthalten. Dateien, die diese Kriterien erfüllen, werden mit Klassifizierungseigenschaften gekennzeichnet, die ein Administrator definiert. Die Dateiklassifizierungsinfrastruktur kann dann automatisch entsprechend der Klassifizierung Aktionen vornehmen. Eine dieser Aktionen umfasst die Anwendung von Informationsschutz mithilfe von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] sowie die Bereitstellung des Rights Management-Connectors (auch als RMS-Verbindungsdienst bezeichnet). Office-Dateien werden von Azure RMS dann automatisch geschützt.

Zum Schützen aller Dateitypen verwenden Sie nicht den RMS-Verbindungsdienst, sondern führen stattdessen ein Windows PowerShell-Skript aus, das Cmdlets aus dem [RMS Protection-Tool](https://www.microsoft.com/en-us/download/details.aspx?id=47256) verwendet.

Die Klassifizierungsrichtlinien sind vollständig konfigurierbar und in hohem Maße erweiterbar, sodass Sie potenzielle Datenlecks durch nicht autorisierte und autorisierte Benutzer verhindern können. Sie können damit sogar das Risiko potenzieller Datenlecks durch Netzwerkadministratoren verringern, weil Sie Richtlinien konfigurieren können, die nicht erfordern, dass diese Administratoren Zugriff auf die Dateien haben.

Eine Anleitung zum Bereitstellen und Konfigurieren des RMS-Connectors für Office-Dateien finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

Eine Anleitung zur Verwendung des Windows PowerShell-Skripts für alle Dateitypen finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure)](../rms-client/configure-fci.md).



## Nächste Schritte
Nachdem Sie erfahren haben, wie Azure RMS von Anwendungen und Diensten unterstützt wird, ist es für Sie unter Umständen interessant, Azure RMS mit der lokalen Version von Rights Management, also Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS), zu vergleichen. Einen Vergleich der Features, Anforderungen und Sicherheitssteuerungen finden Sie unter [Vergleich zwischen Azure Rights Management und AD RMS](compare-azure-rms-ad-rms.md).





<!--HONumber=Sep16_HO4-->


