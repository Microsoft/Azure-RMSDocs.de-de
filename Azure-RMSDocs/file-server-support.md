---
title: So unterstützen Dateiserver, die FCI verwenden, Azure RMS von AIP
description: Verwendung der Windows Server-Dateiklassifizierungsinfrastruktur mit Azure RMS, wenn Sie den RMS-Connector für den automatischen Schutz von Office-Dokumenten bereitstellen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/12/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 81754d9f7ac0ff1351d4298f23da31afcf8ed900
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254406"
---
# <a name="how-file-servers-that-run-windows-server-and-use-file-classification-infrastructure-fci-support-azure-rights-management"></a>So schützen Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden Azure Rights Management

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Wenn Sie Windows Server für die Verwendung der Dateiklassifizierungsinfrastruktur konfigurieren, kann dieses „Ressourcen-Manager für Dateiserver“-Feature lokale Dateien untersuchen und bestimmen, ob sie sensible Daten enthalten. Dateien, die diese Kriterien erfüllen, werden mit Klassifizierungseigenschaften gekennzeichnet, die ein Administrator definiert. Die Dateiklassifizierungsinfrastruktur kann dann automatisch entsprechend der Klassifizierung Aktionen vornehmen. Eine dieser Aktionen umfasst die Anwendung von Informationsschutz mithilfe von Azure Rights Management sowie die Bereitstellung des Rights Management-Connectors (auch als RMS-Connector bezeichnet). Office-Dateien werden von Azure RMS dann automatisch geschützt.

Zum Schützen aller Dateitypen verwenden Sie nicht den RMS-Verbindungsdienst, sondern führen stattdessen ein Windows PowerShell-Skript aus, das Cmdlets aus dem [Azure Information Protection-Modul](./rms-client/client-admin-guide-powershell.md) verwendet.

Die Klassifizierungsrichtlinien sind vollständig konfigurierbar und in hohem Maße erweiterbar, sodass Sie potenzielle Datenlecks durch nicht autorisierte und autorisierte Benutzer verhindern können. Sie können damit sogar das Risiko potenzieller Datenlecks durch Netzwerkadministratoren verringern, weil Sie Richtlinien konfigurieren können, die nicht erfordern, dass diese Administratoren Zugriff auf die Dateien haben.

Eine Anleitung zum Bereitstellen und Konfigurieren des RMS-Connectors für Office-Dateien finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

Eine Anleitung zur Verwendung des Windows PowerShell-Skripts für alle Dateitypen finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure)](./rms-client/configure-fci.md).



## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie erfahren haben, wie Azure RMS von Anwendungen und Diensten unterstützt wird, ist es für Sie unter Umständen interessant, Azure RMS mit der lokalen Version von Rights Management, also Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS), zu vergleichen. Einen Vergleich der Features, Anforderungen und Sicherheitssteuerungen finden Sie unter [Vergleich zwischen Azure Rights Management und AD RMS](compare-on-premise.md).


