---
title: Verwendung von Azure RMS-AIP durch Windows-Dateiserver, die FCI unterstützen
description: Verwendung der Windows Server-Dateiklassifizierungsinfrastruktur mit Azure RMS, wenn Sie den RMS-Connector für den automatischen Schutz von Office-Dokumenten bereitstellen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.subservice: fci
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 4e3c194be533adce625d1a15ad3fdfcd863da279
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384331"
---
# <a name="how-windows-file-servers-that-use-fci-support-azure-rights-management"></a>Wie Windows-Dateiserver, die FCI verwenden, Azure Rights Management unterstützen

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [Azure Information Protection klassischer Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn Sie Windows Server für die Verwendung der Dateiklassifizierungsinfrastruktur konfigurieren, kann dieses „Ressourcen-Manager für Dateiserver“-Feature lokale Dateien untersuchen und bestimmen, ob sie sensible Daten enthalten. 

Dateien, die diese Kriterien erfüllen, werden mit Klassifizierungs Eigenschaften gekennzeichnet, die ein Administrator definiert. Die Dateiklassifizierungsinfrastruktur kann dann automatisch entsprechend der Klassifizierung Aktionen vornehmen. 

Eine dieser Aktionen umfasst das Anwenden von Informationsschutz mithilfe von Azure Rights Management und die Bereitstellung des Rights Management-Connector (auch als RMS-Connector bezeichnet). Office-Dateien werden von Azure RMS dann automatisch geschützt.

> [!TIP]
> Zum Schützen aller Dateitypen verwenden Sie nicht den RMS-Verbindungsdienst, sondern führen stattdessen ein Windows PowerShell-Skript aus, das Cmdlets aus dem [Azure Information Protection-Modul](./rms-client/client-admin-guide-powershell.md) verwendet.
> 

Die Klassifizierungsrichtlinien sind vollständig konfigurierbar und in hohem Maße erweiterbar, sodass Sie potenzielle Datenlecks durch nicht autorisierte und autorisierte Benutzer verhindern können. Sie können damit sogar das Risiko potenzieller Datenlecks durch Netzwerkadministratoren verringern, weil Sie Richtlinien konfigurieren können, die nicht erfordern, dass diese Administratoren Zugriff auf die Dateien haben.

Anweisungen zum Bereitstellen und Konfigurieren des RMS-Verbindungs-Connector für Office-Dateien finden Sie unter Bereitstellen [des Azure Rights Management-Verbindungs-Connector](deploy-rms-connector.md)

Anweisungen zum Verwenden des Windows PowerShell-Skripts für alle Dateitypen finden Sie unter. 

- [RMS-Schutz mit Windows Server-Datei Klassifizierungs Infrastruktur &#40;FCI&#41;](./rms-client/configure-fci.md)
- [Windows PowerShell-Skript für Azure RMS Schutz mithilfe von Datei Server Ressourcen-Manager FCI](rms-client/fci-script.md)


## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie erfahren haben, wie Azure RMS von Anwendungen und Diensten unterstützt wird, ist es für Sie unter Umständen interessant, Azure RMS mit der lokalen Version von Rights Management, also Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS), zu vergleichen. Einen Vergleich der Features, Anforderungen und Sicherheitskontrollen finden Sie unter [Vergleich von Azure Rights Management und AD RMS](compare-on-premise.md).


