---
title: Was ist Azure Information Protection (AIP)?
description: Azure Information Protection (AIP) erweitert das Microsoft Information Protection-Framework (MIP), um die von Microsoft 365 bereitgestellten Bezeichnungs- und Klassifizierungsfunktionen zu erweitern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/09/2020
ms.topic: overview
ms.collection: M365-security-compliance
ms.service: information-protection
Customer intent: As an administrator, I want to extend Microsoft 365's labeling and classification functionality to the File Explorer, PowerShell, third party apps and services, and more.
ms.custom: contperfq2
search.appverid:
- MET150
ms.openlocfilehash: 4a945f07532786c268886a44de23430be9a78700
ms.sourcegitcommit: 822b23024cfd01ea41ac6ae9370489193782f078
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634698"
---
# <a name="what-is-azure-information-protection"></a>Was ist Azure Information Protection?

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection (AIP) ist eine cloudbasierte Lösung, die Organisationen das Erkennen, Klassifizieren und Schützen von Dokumenten und E-Mails durch Anwendung von Bezeichnungen auf Inhalte ermöglicht.

AIP gehört zur Microsoft Information Protection-Lösung (MIP) und erweitert die Bezeichnungs- und Klassifizierungsfunktionen von Microsoft 365.

Die folgende Abbildung zeigt die Erweiterungen von Azure Information Protection für MIP, einschließlich des [Clients für einheitliche Bezeichnungen](#aip-unified-labeling-client), dem [Scanner](#aip-on-premises-scanner) und dem [SDK](#microsoft-information-protection-sdk).

:::image type="content" source="media/what-is-mip.png" alt-text="Die Azure Information Protection-Bereiche des Microsoft Information Protection-Frameworks":::

Microsoft Information Protection ist der allgemeine Stack zum Schutz von Informationen, der vom AIP-Client für einheitliche Bezeichnungen genutzt wird. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/protect-information).

## <a name="aip-unified-labeling-client"></a>AIP-Client für einheitliche Bezeichnungen

Der Azure Information Protection-Client für einheitliche Bezeichnungen erweitert die Bezeichnungs-, Klassifizierungs- und Schutzfunktionen auf zusätzliche Dateitypen sowie auf den Datei-Explorer und PowerShell. 

Klicken Sie z. B. im Datei-Explorer mit der rechten Maustaste auf mindestens eine Datei, und wählen Sie **Klassifizieren und schützen** aus, um die AIP-Funktionen für die ausgewählten Dateien zu bearbeiten.

:::image type="content" source="media/protect-from-file-explorer.png" alt-text="Klassifizieren und Schützen über den Datei-Explorer":::

Ausführliche Informationen zu den neuesten Features und zur öffentlichen Vorschauversion des Clients für einheitliche Bezeichnungen finden Sie unter [Azure Information Protection unified labeling client - Version release history and support policy](rms-client/unifiedlabelingclient-version-release-history.md) (Azure Information Protection-Client für einheitliche Bezeichnungen: Versionsverlauf und Supportrichtlinie).

Laden Sie den Client von der [Microsoft Azure Information Protection-Downloadseite](https://www.microsoft.com/download/details.aspx?id=53018) herunter.
    
## <a name="aip-on-premises-scanner"></a>Lokaler AIP-Scanner

Der lokale Azure Information Protection-Scanner ermöglicht es Administratoren, ihre Netzwerke und lokalen Dateirepositorys auf vertrauliche Inhalte zu überprüfen, die bezeichnet, klassifiziert und/oder geschützt werden müssen.

Der lokale Scanner wird mit PowerShell-Cmdlets als Bestandteil des Clients für einheitliche Bezeichnungen installiert und kann mit PowerShell und über den Azure Information Protection-Bereich im Azure-Portal verwaltet werden.

Verwenden Sie beispielsweise die im Azure-Portal angezeigten Scannerdaten, um Repositorys in Ihrem Netzwerk zu finden, in denen möglicherweise vertrauliche Inhalte riskant sind:

:::image type="content" source="media/risky-repos-small.png" alt-text="Durchsicht überprüfter Netzwerke auf riskante Repositorys" lightbox="media/risky-repos.png":::

Weitere Informationen finden Sie in folgenden Quellen:

- [Was ist der AIP-Scanner für einheitliche Bezeichnungen?](deploy-aip-scanner.md)
- Die Abschnitte zum Scanner im [Versionsverlauf zum AIP-Client für einheitliche Bezeichnungen](rms-client/unifiedlabelingclient-version-release-history.md)

Laden Sie die Scannerinstallationsdatei zusammen mit dem Client von der [Microsoft Azure Information Protection-Downloadseite](https://www.microsoft.com/download/details.aspx?id=53018) herunter.


## <a name="microsoft-information-protection-sdk"></a>Microsoft Information Protection SDK

Das Microsoft Information Protection-SDK erweitert Vertraulichkeitsbezeichnungen auf Anwendungen und Dienste von Drittanbietern. Entwickler können das SDK verwenden, um native Unterstützung für das Anwenden von Bezeichnungen und Schutz auf Dateien zu erstellen.

Sie können beispielsweise das MIP-SDK für Folgendes verwenden:

- Eine Branchenanwendung, die Klassifizierungsbezeichnungen beim Exportieren auf Dateien anwendet.
- Eine CAD-/CAM-Entwurfsanwendung stellt native Unterstützung für Bezeichnungen von Microsoft Information Protection bereit.
- Ein Sicherheitsbroker für Cloudzugriff oder eine Lösung für das Verhindern von Datenverlust argumentiert über Daten hinweg, die mit Azure Information Protection verschlüsselt wurden.

Weitere Informationen finden Sie in der [Übersicht zum Microsoft Information Protection-SDK](/information-protection/develop/overview).

## <a name="next-steps"></a>Nächste Schritte

**Für die ersten Schritte mit AIP** laden Sie den Client und den Scanner für einheitliche Bezeichnungen herunter und installieren diese.

- [Registrieren für eine kostenlose Testversion](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)  (Enterprise Mobility + Security E5)
- [Herunterladen des Clients](https://www.microsoft.com/download/details.aspx?id=53018)
- [Schnellstart: Bereitstellen des Clients für einheitliche Bezeichnungen](quickstart-deploy-client.md)

**Machen Sie sich mit AIP vertraut**, indem Sie erste Tutorials absolvieren:

- [Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen](tutorial-install-scanner.md)
- [Tutorial: Erkennen vertraulicher Inhalte mit dem Azure Information Protection-Scanner (AIP)](tutorial-scan-networks-and-content.md)
- [Tutorial: Verhindern übermäßiger Freigaben in Outlook mit Azure Information Protection (AIP)](tutorial-preventing-oversharing.md)

**Wenn Sie soweit sind und AIP weiter anpassen möchten**, finden Sie weitere Informationen im [Admin Guide: Custom configurations for the Azure Information Protection unified labeling client](rms-client/clientv2-admin-guide-customizations.md) (Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client für einheitliche Bezeichnungen).

**Informationen zu den ersten Schritten mit dem MIP-SDK** finden Sie unter [Microsoft Information Protection (MIP) SDK: Setup und Konfiguration](/information-protection/develop/setup-configure-mip).

### <a name="additional-resources"></a>Zusätzliche Ressourcen

|Ressource  |Links und Beschreibung  |
|---------|---------|
|**Abonnementoptionen und Preise**     |    [Azure Information Protection – Preise](https://azure.microsoft.com/pricing/details/information-protection)     |
|**Häufig gestellte Fragen und bekannte Probleme**     | [Häufig gestellte Fragen zu Azure Information Protection](faqs.md) </br> [Bekannte Probleme: Azure Information Protection](known-issues.md)       |
|**Supportoptionen**     | [Supportoptionen für Azure Information Protection](information-support.md)        |
|**Yammer**     |  [Azure Information Protection](https://www.yammer.com/AskIPTeam)       |
|**Ignite 2020**     |  - [Übergreifender Informationsschutz und Governance in der Cloud, lokal, über Endpunkte und Remotearbeitsumgebungen](https://myignite.microsoft.com/sessions/ceba117f-9bc7-4426-9ebc-753d94c6a476)</br>- [Mit intelligenten Datenschutz- und Compliancelösungen zum Helden des Risikomanagements](https://myignite.microsoft.com/sessions/9a1e2716-55f5-4c3e-8626-0cb77e60eb87)</br>- [Datenkenntnis, Schützen Ihrer Daten und Verhindern von Datenschutz mit Microsoft Information Protection](https://myignite.microsoft.com/sessions/46ff69cf-2c8f-4e61-a923-f72f5740f02f)</br>- [Fragen Sie den Experten: Fragen zur Microsoft-Compliance: Information Protection und Governance, Insiderrisiken, Complianceverwaltung und viel mehr](https://myignite.microsoft.com/sessions/5ce48b36-9827-4d60-8540-90546333063d)       |
|**Neuigkeiten**     | Achten Sie auf neue Features für AIP im Microsoft 365 und SharePoint Admin Center:   </br>- [Neuerungen in Microsoft 365 Admin Center](/microsoft-365/admin/whats-new-in-preview) </br>- [Neuerungen in SharePoint Admin Center](/sharepoint/what-s-new-in-admin-center)     |
|     |         |

## <a name="aips-classic-client"></a>Der klassische AIP-Client

Mit dem klassischen Azure Information Protection-Client, der früheren Version von AIP, können Administratoren Klassifizierungsbezeichnungen direkt im Azure-Portal verwalten.

Im Azure-Portal verwaltete AIP-Bezeichnungen werden *nicht* von der Plattform für einheitliche Bezeichnungen unterstützt. Sie funktionieren nur mit dem Azure Information Protection-Client und -Scanner sowie Microsoft Cloud App Security. 

Die Migration auf einheitliche Bezeichnungen wird empfohlen, um diese Features sowie SharePoint, Microsoft 365-Apps, Outlook für das Web und mobile Geräte, PowerBI-Datenschutz und mehr zu unterstützen. Weitere Informationen finden Sie unter [Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen](tutorial-migrating-to-ul.md).

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. 
>
> Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Lösung für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
