---
title: 'Schnellstart: Bereitstellen des Azure Information Protection-Clients (AIP) für einheitliche Bezeichnungen'
description: Eine schnelle Einführung in das Bereitstellen des Azure Information Protection-Clients (AIP) für einheitliche Bezeichnungen
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/09/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: fa795fa29e39bc9fe5abc9a68febcd168a5bb502
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97386337"
---
# <a name="quickstart-deploying-the-azure-information-protection-aip-unified-labeling-client"></a>Schnellstart: Bereitstellen des Azure Information Protection-Clients (AIP) für einheitliche Bezeichnungen

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> ***Relevant für:** [Azure Information Protection-Client für einheitliche Bezeichnungen für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Der Azure Information Protection-Client (AIP) für einheitliche Bezeichnungen gehört zur [Microsoft Information Protection](https://aka.ms/MIPdocs)-Lösung und erweitert die von Microsoft 365 bereitgestellten integrierten Funktionen für die Vertraulichkeitsbezeichnung. 

Der Client bietet Endbenutzerunterstützung für Bezeichnung und Schutz in Office-Anwendungen sowie im Datei-Explorer und in PowerShell. Der mit dem Client für einheitliche Bezeichnungen bereitgestellte Scanner ermöglicht Administratoren die Überprüfung von Netzwerken und Freigaben auf vertrauliche Inhalte. 

Für Organisationen ohne Informationsschutzplattform bietet der Client einen Viewer für Inhalte, die von anderen Organisationen mithilfe von Microsoft Information Protection geschützt werden.

## <a name="review-aip-client-prerequisites"></a>Überprüfen der Voraussetzungen für den AIP-Client

Lesen Sie die unten verknüpften Artikel, um mehr über die Voraussetzungen für die Bereitstellung des Azure Information Protection-Clients für einheitliche Bezeichnungen in Ihrer Organisation zu erfahren:

- **[Anforderungen an Azure Information Protection](requirements.md).** Beschreibt die detaillierten Systemanforderungen für die Bereitstellung des AIP-Clients in Ihrer Organisation, wie ein Azure Information Protection-Abonnement und Azure Active Directory. Außerdem werden die unterstützten Clientgeräte und Anwendungen aufgeführt.

- **[Voraussetzungen für den Client für einheitliche Bezeichnungen](rms-client/clientv2-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-unified-labeling-client).** Listet die Systemanforderungen für jeden Computer auf, auf dem der AIP-Client installiert ist.

## <a name="install-the-aip-client"></a>Installieren des AIP-Clients

AIP bietet folgende Clientinstallationsoptionen:

- **[Herunterladen und Ausführen der EXE-Datei](rms-client/clientv2-admin-guide-install.md#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-executable-installer).** Für die meisten Anwendungsfälle wird diese Installation empfohlen. Die Installation kann interaktiv oder im Hintergrund ausgeführt werden.

    Wenn die Installation beendet ist, werden Sie möglicherweise aufgefordert, den Computer oder die Office-Software neu zu starten. Starten Sie bei Bedarf neu, um fortzufahren.

- **[Herunterladen und Ausführen der MSI-Datei](rms-client/clientv2-admin-guide-install.md#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-msi-installer).** Wird für Installationen im Hintergrund unterstützt, die einen zentralen Bereitstellungsmechanismus verwenden, z. B. Gruppenrichtlinien, Configuration Manager oder Microsoft Intune.

Die AIP-Clientinstallationsdateien sind auf der [Microsoft-Downloadwebsite](https://www.microsoft.com/download/details.aspx?id=53018) verfügbar. 

Weitere Informationen finden Sie unter [Optionen zum Installieren des AIP-Clients](rms-client/clientv2-admin-guide-install.md#options-to-install-the-azure-information-protection-unified-labeling-client-for-users).

> [!TIP]
> Um die neuesten Features für den AIP-Client zu testen, stellen Sie die öffentliche Vorschauversion auf einem Testsystem bereit. Weitere Informationen finden Sie in den [Informationen zum Versionsverlauf](rms-client/unifiedlabelingclient-version-release-history.md) zum AIP-Client für einheitliche Bezeichnungen.
> 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den ersten Schritten mit dem Azure Information-Client finden Sie in den folgenden Schnellstarts und Tutorials:

- [Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen](tutorial-install-scanner.md)
- [Tutorial: Erkennen vertraulicher Inhalte mit dem Azure Information Protection-Scanner (AIP)](tutorial-scan-networks-and-content.md)
- [Tutorial: Verhindern übermäßiger Freigaben mit Azure Information Protection (AIP)](tutorial-preventing-oversharing.md)
- [Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen](tutorial-migrating-to-ul.md) 

**Siehe auch**:

- [Bekannte Probleme: Azure Information Protection](known-issues.md) 
- [Häufig gestellte Fragen zu Azure Information Protection](faqs.md) 
- [Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client für einheitliche Bezeichnungen](rms-client/clientv2-admin-guide-customizations.md)        
    
