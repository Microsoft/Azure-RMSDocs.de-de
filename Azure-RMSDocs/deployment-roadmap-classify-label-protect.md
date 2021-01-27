---
title: Bereitstellen von Azure Information Protection (AIP) für Klassifizierung, Bezeichnung und Schutz
description: Verwenden Sie diese Schritte, um Azure Information Protection (AIP) für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten, wenn Sie Ihre Daten klassifizieren, bezeichnen und schützen möchten.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 6612500a86f8a84c5f5762e91933c3f9cf743678
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809522"
---
# <a name="aip-deployment-roadmap-for-classification-labeling-and-protection"></a>Leitfaden zur AIP-Bereitstellung für Klassifizierung, Bezeichnung und Schutz

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Verwenden Sie die folgenden Schritte als Empfehlungen, die Sie beim vorbereiten, implementieren und Verwalten von Azure Information Protection für Ihre Organisation unterstützen, wenn Sie Ihre Daten klassifizieren, bezeichnen und schützen möchten.

Diese Roadmap wird für alle Kunden mit einem unterstützenden Abonnement empfohlen. Zu den zusätzlichen Funktionen zählen das Erkennen von vertraulichen Informationen und das bezeichnen von Dokumenten und e-Mails für die Klassifizierung. 

Bezeichnungen können auch Schutz anwenden, um diesen Schritt für Ihre Benutzer zu vereinfachen. 

> [!TIP]
> Alternativ können Sie einen der folgenden Artikel suchen:
> - [AIP-Roadmap nur zum Schutz von Daten](deployment-roadmap-protect-only.md)
> - [Schrittanleitungen für häufige Szenarien, in denen Azure Information Protection verwendet wird](how-to-guides.md)
> - [Azure Information Protection releaseroadmap](information-support.md#information-about-new-releases-and-updates)

## <a name="deployment-process"></a>Bereitstellungsprozess

Führen Sie die folgenden Schritte aus:

1. [Bestätigen Ihres Abonnements und Zuweisen von Benutzerlizenzen](#confirm-your-subscription-and-assign-user-licenses)
1. [Vorbereiten Ihres Mandanten für Azure Information Protection](#prepare-your-tenant-to-use-azure-information-protection)
1. [Konfigurieren und Bereitstellen von Klassifizierungen und Bezeichnungen](#configure-and-deploy-classification-and-labeling)
1. [Vorbereitung auf den Datenschutz](#prepare-for-data-protection)
1. [Konfigurieren von Bezeichnungen und Einstellungen, Anwendungen und Diensten für den Schutz von Daten](#configure-labels-and-settings-applications-and-services-for-data-protection)
1. [Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten](#use-and-monitor-your-data-protection-solutions)
1. [Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto](#administer-the-protection-service-for-your-tenant-account-as-needed)

> [!TIP]
> Verwenden Sie bereits die Schutzfunktion von Azure Information Protection? Sie können viele dieser Schritte überspringen und sich auf die Schritte [3](#configure-and-deploy-classification-and-labeling) und [5,1](#configure-labels-and-settings-applications-and-services-for-data-protection)konzentrieren.

## <a name="confirm-your-subscription-and-assign-user-licenses"></a>Bestätigen Ihres Abonnements und Zuweisen von Benutzerlizenzen

Vergewissern Sie sich, dass Ihre Organisation über ein Abonnement verfügt, das die von Ihnen erwarteten Funktionen und Features umfasst. Diese Details finden Sie auf der Seite [Azure Information Protection Preise](https://azure.microsoft.com/pricing/details/information-protection) .

Weisen Sie anschließend jedem Benutzer in Ihrer Organisation, der Klassifizierungen und Bezeichnung vornehmen und Dokumente und E-Mails schützen soll, eine Lizenz aus diesem Abonnement zu.

> [!IMPORTANT]
> Weisen Sie Benutzerlizenzen nicht manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht, um den Azure Rights Management-Dienst für Ihre Organisation zu verwalten. 
>
> Für diese Lizenzen wird im Microsoft 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](/previous-versions/azure/dn194118(v=azure.100))**RIGHTSMANAGEMENT_ADHOC** angezeigt. 
>
> Weitere Informationen finden Sie unter [RMS for Individuals und Azure Information Protection](./rms-for-individuals.md).
> 
## <a name="prepare-your-tenant-to-use-azure-information-protection"></a>Vorbereiten Ihres Mandanten für Azure Information Protection

Bevor Sie Azure Information Protection verwenden, stellen Sie sicher, dass Sie über Benutzerkonten und Gruppen in Microsoft 365 oder Azure Active Directory verfügen, die AIP zum Authentifizieren und autorisieren Ihrer Benutzer verwenden kann.

Erstellen Sie bei Bedarf diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. 

Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

## <a name="configure-and-deploy-classification-and-labeling"></a>Konfigurieren und Bereitstellen von Klassifizierungen und Bezeichnungen

Führen Sie die folgenden Schritte aus:

1. **Dateien scannen (optional, jedoch empfohlen)**

    Stellen Sie [den Azure Information Protection-Client](quickstart-deploy-client.md)bereit, und [Installieren](tutorial-install-scanner.md) und führen Sie dann [den Scanner](tutorial-scan-networks-and-content.md) aus, um die vertraulichen Informationen zu ermitteln, die Sie in Ihren lokalen Daten speichern haben. 

    Die Informationen, die der Scanner findet, können Ihnen bei Ihrer Klassifizierungstaxonomie helfen und wertvolle Informationen darüber liefern, welche Bezeichnungen Sie benötigen und welche Dateien geschützt werden müssen.

    Der Überprüfungs **Modus für** Scanner erfordert keine Bezeichnungs Konfiguration oder Taxonomie und ist daher in dieser frühen Phase der Bereitstellung geeignet. Sie können diese Scannerkonfiguration auch parallel mit den folgenden Bereitstellungs Schritten verwenden, bis Sie die empfohlene oder automatische Bezeichnung konfigurieren.

1. **Anpassen der AIP-Standard Richtlinie**.

    Wenn Sie noch nicht über eine Klassifizierungs Strategie verfügen, verwenden Sie eine Standard Richtlinie als Grundlage für die Bestimmung der Bezeichnungen, die Sie für Ihre Daten benötigen. Passen Sie diese Bezeichnungen nach Bedarf an Ihre Anforderungen an.

    Beispielsweise können Sie Ihre Bezeichnungen mit den folgenden Details neu konfigurieren:

    - Stellen Sie sicher, dass ihre Bezeichnungen ihre Klassifizierungs Entscheidungen unterstützen.
    - Konfigurieren von Richtlinien für die manuelle Bezeichnung durch Benutzer
    - Schreiben Sie einen Benutzer Leit Faden, um zu erläutern, welche Bezeichnung in jedem Szenario angewendet werden sollte.
    - Wenn Ihre Standard Richtlinie mit Bezeichnungen erstellt wurde, die den Schutz automatisch anwenden, können Sie die Schutzeinstellungen vorübergehend entfernen oder die Bezeichnung deaktivieren, während Sie die Einstellungen testen. 

    Vertraulichkeits Bezeichnungen und Beschriftungs Richtlinien für den Unified Label-Client werden im Microsoft 365 Security Center, Microsoft 365 Compliance Center oder im Microsoft 365 Security & Compliance Center konfiguriert. Weitere Informationen finden Sie unter Informationen [zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels).

1. **Bereitstellen des Clients für Ihre Benutzer**

    Nachdem Sie eine Richtlinie konfiguriert haben, stellen Sie den Azure Information Protection Client für Ihre Benutzer bereit. Bereitstellen von Benutzer Schulungen und spezifischen Anweisungen, wann die Bezeichnungen ausgewählt werden sollen. 

    Weitere Informationen finden Sie im Unified Bezeichnungs [Client-Administrator Handbuch](./rms-client/clientv2-admin-guide.md).

1. **Erweiterte Konfigurationen einführen**

    Warten Sie, bis Ihre Benutzer mit Bezeichnungen in Ihren Dokumenten und e-Mails vertraut werden. Wenn Sie bereit sind, führen Sie erweiterte Konfigurationen ein, z. b.:

    - Anwenden von Standard Bezeichnungen
    - Benutzer werden zur Begründung aufgefordert, wenn Sie eine Bezeichnung mit einer niedrigeren Klassifizierungs Ebene ausgewählt haben oder eine Bezeichnung entfernen
    - Es wird geprüft, ob alle Dokumente und e-Mails eine Bezeichnung aufweisen.
    - Anpassen von Kopfzeilen, Fußzeilen oder Wasserzeichen
    - Empfohlene und automatische Bezeichnung

    Weitere Informationen finden Sie unter [Administrator Handbuch: benutzerdefinierte Konfigurationen](rms-client/client-admin-guide-customizations.md).
     
    > [!TIP]
    > Wenn Sie Bezeichnungen für die automatische Bezeichnung konfiguriert haben, führen Sie den [Azure Information Protection Scanner](deploy-aip-scanner-manage.md) erneut in Ihren lokalen Daten speichern im Ermittlungs Modus aus, und passen Sie Ihre Richtlinie an. 
    > 
    > Wenn Sie die Überprüfung im Ermittlungs Modus ausführen, können Sie feststellen, welche Bezeichnungen auf Dateien angewendet werden. Dadurch können Sie die Bezeichnung ihrer Bezeichnung optimieren und Sie auf eine Massen Klassifizierung und den Schutz von Dateien vorbereiten. 
    > 

## <a name="prepare-for-data-protection"></a>Vorbereitung auf den Datenschutz

Stellen Sie Datenschutz für Ihre empfindlichsten Daten bereit, sobald die Benutzer mit dem bezeichnen von Dokumenten und e-Mails vertraut sind.

Führen Sie die folgenden Schritte aus, um den Schutz der Daten zu vorbereiten:

1. Legen **Sie fest, wie Sie Ihren Mandanten Schlüssel verwalten möchten**.

    Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). 
 
    Weitere Informationen und Optionen für zusätzlichen lokalen Schutz finden [Sie unter Planning and Implementierungs your Azure Information Protection Tenant Key](plan-implement-tenant-key.md).

1. **Installieren Sie PowerShell für AIP**.

    Installieren Sie das PowerShell-Modul für **aipservice** auf mindestens einem Computer, der über Internet Zugriff verfügt. Sie können diesen Schritt jetzt oder später durchführen. 

    Weitere Informationen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](./install-powershell.md).

1. **Nur AD RMS**: Migrieren Sie Ihre Schlüssel, Vorlagen und URLs in die Cloud.

    Wenn Sie zurzeit AD RMS verwenden, führen Sie eine Migration aus, um die Schlüssel, Vorlagen und URLs in die Cloud zu verschieben. 
    
    Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

1. **Aktivieren** Sie den Schutz.

    Stellen Sie sicher, dass der Schutzdienst aktiviert ist, damit Sie mit dem Schützen von Dokumenten und E-Mails beginnen können. Wenn Sie in mehreren Phasen bereitstellen, konfigurieren Sie die Onboarding-Steuerelemente für Benutzer, um die Fähigkeit der Benutzer einzuschränken, Schutz anzuwenden. 

    Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](./activate-service.md).

1. **Beachten Sie die Verwendungs Protokollierung (optional)**.

    Protokollieren Sie die Verwendung, um zu überwachen, wie Ihre Organisation den Schutzdienst verwendet. Sie können diesen Schritt jetzt oder später durchführen. 

    Weitere Informationen finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md).

## <a name="configure-labels-and-settings-applications-and-services-for-data-protection"></a>Konfigurieren von Bezeichnungen und Einstellungen, Anwendungen und Diensten für den Schutz von Daten

Führen Sie die folgenden Schritte aus:

1. **Aktualisieren ihrer Bezeichnungen zum Anwenden des Schutzes**
    
    Weitere Informationen finden Sie unter [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/encryption-sensitivity-labels).

    > [!IMPORTANT]
    > Benutzer können Bezeichnungen in Outlook anwenden, die Rights Management Schutz auch dann gelten, wenn Exchange nicht für die Verwaltung von Informationsrechten (Information Rights Management, unm) konfiguriert ist. 
    > 
    > Allerdings bietet Ihre Organisation keine vollständige Funktionalität für die Verwendung von Azure Rights Management Protection mit Exchange, bis Exchange für die Faim-oder [Microsoft 365 Nachrichten Verschlüsselung mit neuen Funktionen](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)konfiguriert ist. Diese zusätzliche Konfiguration ist in der folgenden Liste enthalten (2 für Exchange Online und 5 für lokales Exchange). 
    > 
    
1. **Konfigurieren von Office-Anwendungen und -Diensten**
    
    Konfigurieren Sie Office-Anwendungen und-Dienste für die Features zur Verwaltung von Informationsrechten (Information Rights Management, unm) in Microsoft SharePoint oder Exchange Online. 

    Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md).

1. **Konfigurieren des Administratorfeatures für die Datenwiederherstellung**
    
    Wenn vorhandene IT-Dienste von Azure Information Protection geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen, Gateways zur Inhaltsverschlüsselung und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. 

    Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](./configure-super-users.md).

1. **Massenklassifizierung und -schützen vorhandener Dateien**
    
    Führen Sie nun für Ihre lokalen Datenspeicher den [Azure Information Protection-Scanner](deploy-aip-scanner.md) im Erzwingungsmodus aus, sodass Dateien automatisch mit einer Bezeichnung versehen werden.
    
    Verwenden Sie für Dateien auf PCs PowerShell-Cmdlets, um Dateien zu klassifizieren und zu schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide-powershell.md).

    Verwenden Sie für cloudbasierte Datenspeicher [Azure Cloud App Security](/cloud-app-security). 

    > [!TIP]
    > Obwohl das klassifizieren und schützen vorhandener Dateien in einem Massen Vorgang nicht zu den Haupt Anwendungsfällen von Cloud App Security gehört, können Sie mithilfe von [dokumentierten](/cloud-app-security/azip-integration#enable-azure-information-protection) Problem Umgehungen Ihre Dateien klassifizieren und schützen.

6. **Bereitstellen des Connectors für durch IRM geschützte Bibliotheken unter SharePoint Server und durch IRM geschützte E-Mails für Exchange lokal**
    
    Wenn Sie SharePoint und Exchange lokal verwenden und deren Funktionen zur Verwaltung von Informationsrechten (IRM) nutzen möchten, installieren und konfigurieren Sie den Rights Management-Connector. 

    Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](./deploy-rms-connector.md).

## <a name="use-and-monitor-your-data-protection-solutions"></a>Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten

Nun können Sie überwachen, wie Ihre Organisation die von Ihnen konfigurierten Bezeichnungen verwendet, und sicherstellen, dass vertrauliche Informationen geschützt werden. 

Weitere Informationen finden Sie auf den folgenden Seiten:

- [Zentrale Berichterstellung für Azure Information Protection](reports-aip.md) (derzeit in der Vorschau)
- [Protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md)

## <a name="administer-the-protection-service-for-your-tenant-account-as-needed"></a>Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto

Wenn Sie mit der Verwendung des Schutzdiensts beginnen, kann PowerShell nützlich sein, um administrative Änderungen skriptgestützt oder automatisiert durchzuführen. PowerShell kann ebenfalls für einige der erweiterten Konfigurationen erforderlich sein. 

Weitere Informationen finden Sie unter [Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](./administer-powershell.md).

## <a name="references-for-classic-client-environments"></a>Verweise für klassische Client Umgebungen

**Relevant für**: nur AIP Classic Client

Wenn Sie den klassischen Client verwenden, verwenden Sie anstelle der oben verknüpften Verweise die folgenden Verweise:

- Stellen Sie die mit dem klassischen Client bereitgestellte Überprüfung bereit, **und führen** Sie Sie aus. Weitere Informationen finden Sie unter [Was ist der Azure Information Protection klassischen Scanner?](deploy-aip-scanner-classic.md)

- **Konfigurieren Sie die Richtlinie im Azure-Portal.** Weitere Informationen finden Sie unter [Konfigurieren Azure Information Protection Richtlinie](./configure-policy.md) und [Konfigurieren einer Bezeichnung für Rights Management Schutz](./configure-policy-protection.md).

- Stellen **Sie Ihren Client für Benutzer** bereit, indem Sie das [klassische Client Administrator Handbuch](./rms-client/client-admin-guide.md) und die [benutzerdefinierten Konfigurations Anweisungen für den klassischen Client](rms-client/client-admin-guide-customizations.md)verwenden.

- **PowerShell-Anweisungen**: [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md)

- **Lokale Überwachung**: [Protokollierung der lokalen Verwendung mit Windows-Ereignis Monitor](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-classic-client)

> [!TIP]
> Möglicherweise interessieren Sie sich auch für die [Azure Information Protection Bereitstellungs Roadmap für den Schutz](deployment-roadmap-protect-only.md), die nur für den klassischen Client unterstützt wird.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie Azure Information Protection bereitstellen, ist es möglicherweise hilfreich, die [häufig gestellten Fragen](faqs.md), [bekannten Probleme](known-issues.md)und die Seite [Informationen und Support](information-support.md) für weitere Ressourcen zu überprüfen.