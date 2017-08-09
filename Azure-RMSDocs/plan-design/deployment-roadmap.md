---
title: "Roadmap für die Bereitstellung von Azure Information Protection"
description: "Führen Sie diese Schritte aus, um Azure Information Protection für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: fabb31e2945b47cda688129d7ecd7cc3c26fd802
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2017
---
# <a name="azure-information-protection-deployment-roadmap"></a>Roadmap für die Bereitstellung von Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Führen Sie die folgenden Schritte aus, um Azure Information Protection für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten.

Falls Sie Azure Information Protection einmal schnell selbst ausprobieren möchten, anstatt die Anwendung in eine Produktionsumgebung einzuführen, helfen Ihnen die Informationen unter [Schnellstarttutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md) weiter.

> [!IMPORTANT]
> Lesen Sie sich vor dem Ausführen der folgenden Schritte den Artikel [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md) durch.

Wählen Sie eine Roadmap für die Bereitstellung aus, die für Ihre Organisation anwendbar ist und die [Abonnementfunktionen und -features](https://www.microsoft.com/cloud-platform/azure-information-protection-features) umfasst, die Sie benötigen:

- [Klassifizierung, Bezeichnung und Schutz](#deployment-roadmap-for-classification-labeling-and-protection)

- [Ausschließlicher Schutz von Daten](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Roadmap für die Bereitstellung von Klassifizierung, Bezeichnung und Schutz

> [!NOTE]
> Verwenden Sie bereits den Azure Rights Management-Dienst für den Schutz von Daten? Sie können viele dieser Schritte überspringen und sich auf die Schritte 3 und 5.1 konzentrieren.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Schritt 1: Bestätigen Ihres Abonnements und Zuweisen von Benutzerlizenzen
Überprüfen Sie anhand der [Abonnementinformationen](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) und der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website, ob Ihre Organisation über ein Abonnement verfügt, das diese Funktionen und Features umfasst. Weisen Sie anschließend jedem Benutzer in Ihrer Organisation, der Klassifizierungen und Bezeichnung vornehmen und Dokumente und E-Mails schützen soll, eine Lizenz aus diesem Abonnement zu.

Hinweis: Weisen Sie keine Benutzerlizenzen manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht zum Verwalten des Azure Rights Management-Diensts für Ihre Organisation. Für diese Lizenzen wird im Office 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) **RIGHTSMANAGEMENT_ADHOC** angezeigt. Weitere Informationen dazu, wie das RMS for Individuals-Abonnement automatisch gewährt und Benutzern zugewiesen wird, finden Sie unter [RMS for Individuals und Azure Information Protection](../understand-explore/rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Schritt 2: Vorbereiten Ihres Mandanten für Azure Information Protection
Führen Sie die folgende Vorbereitungsschritte aus, bevor Sie mit der Verwendung von Azure Information Protection beginnen:

- Stellen Sie sicher, dass Sie über Benutzerkonten und -gruppen in Office 365 oder Azure Active Directory verfügen, die von Azure Information Protection zum Authentifizieren und Autorisieren von Benutzern in Ihrer Organisation verwendet werden. Falls erforderlich, erstellen Sie diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Schritt 3: Konfigurieren und Bereitstellen von Klassifizierungen und Bezeichnungen

Wenn Sie nicht bereits über eine Klassifizierungsstrategie verfügen, lesen Sie die [Azure Information Protection-Standardrichtlinie](../deploy-use/configure-policy-default.md), und verwenden Sie diese als Grundlage für die Entscheidung, welche Klassifizierungsbezeichnungen Sie den Daten in Ihrer Organisation zuweisen möchten. Sie können diese an Ihre geschäftlichen Anforderungen anpassen. 

Konfigurieren Sie die Standardbezeichnungen von Azure Information Protection, um Änderungen vorzunehmen, die Ihre Klassifizierungsentscheidungen unterstützen. Konfigurieren Sie die Richtlinie für das manuelle Bezeichnen von Benutzern, und verfassen Sie Anleitungen für Benutzer dazu, welche Bezeichnung wann anzuwenden sind. Weitere Informationen zum Konfigurieren der Azure Information Protection-Richtlinie finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](../deploy-use/configure-policy.md).

Stellen Sie anschließend den Azure Information Protection-Client für Benutzer bereit, und bieten Sie Benutzerschulungen und Anleitungen für die Auswahl der Bezeichnungen an. Weitere Informationen zum Installieren und Unterstützen des Clients finden Sie im [Azure Information Protection-Client – Administratorhandbuch](../rms-client/client-admin-guide.md).

Wenn die Benutzer nach einer Weile mit dem Bezeichnen ihrer Dokumente und E-Mails vertraut sind, können Sie weitere Konfigurationen einführen. Dazu zählt unter anderem Folgendes:

- Anwenden einer Standardbezeichnung

- Auffordern von Benutzern, eine Begründung anzugeben, wenn sie eine Bezeichnung mit einer niedrigeren Klassifizierungsebene ausgewählt haben

- Vorschreiben, dass alle Dokumente und E-Mails eine Bezeichnung benötigen

- Benutzerdefinierte Kopfzeilen, Fußzeilen und Wasserzeichen

- Bedingungen zur Unterstützung von Empfehlungen und automatische Bezeichnung

Wählen Sie zu diesem Zeitpunkt nicht die Option für den Schutz der Dokumente und E-Mails aus.

### <a name="step-4-prepare-for-rights-management-data-protection"></a>Schritt 4: Vorbereiten für den Schutz von Daten durch Rights Management

Wenn Benutzer mit dem Bezeichnen von Dokumenten und E-Mails vertraut sind, können Sie mit der Einführung des Schutzes von Daten für Ihre vertraulichsten Daten beginnen. Diese Phase erfordert die folgenden Vorbereitungsschritte für den Azure Rights Management-Dienst:

1. Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Beachten Sie, dass Sie derzeit BYOK nicht verwenden können, wenn Sie Exchange Online nutzen. Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

2. Installieren Sie das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] auf mindestens einem Computer, der Zugang zum Internet hat. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell für den Azure Rights Management-Dienst](../deploy-use/install-powershell.md).

3. Wenn Sie derzeit lokale Rights Management Services verwenden: Führen Sie eine Migration durch, um die Schlüssel, Vorlagen und URLs in die Cloud zu verschieben. Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Aktivieren Sie den Azure Rights Management-Dienst, damit Sie mit dem Schützen von Dokumenten und E-Mails beginnen können. Wenn eine Bereitstellung in Phasen erforderlich ist, konfigurieren Sie benutzerbezogene Steuerungsrichtlinien für die Einbindung (Onboarding), um die Nutzung auf bestimmte Benutzer zu beschränken. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

Erwägen Sie optional die Konfigurierung folgender Funktionen:

-   Benutzerdefinierte Vorlagen, wenn die Standardvorlagen für Rechterichtlinien für Ihre Organisation nicht ausreichend sind. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](../deploy-use/configure-policy-templates.md).

-   Nutzungsprotokollierung, sodass Sie überwachen können, wie Ihre Organisation Rights Management verwendet. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-rights-management-data-protection"></a>Schritt 5: Konfigurieren der Azure Information Protection-Richtlinie sowie von Anwendungen und Diensten für den Schutz von Daten durch Rights Management

1. Aktualisieren Ihrer Azure Information Protection-Richtlinie für den Schutz von Daten
    
    Ändern Sie Ihre Azure Information Protection-Richtlinie so, dass eine oder mehrere Bezeichnungen den Rights Management-Schutz anwenden. Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](../deploy-use/configure-policy-protection.md).
    
    Beachten Sie, dass Benutzer Bezeichnungen für die Anwendung des Rights Management-Schutzes auch dann in Outlook verwenden können, wenn Exchange nicht für Information Rights Management (IRM) konfiguriert ist. Ihre Organisation kann jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn Exchange für IRM konfiguriert ist. Diese zusätzliche Konfiguration ist in der folgenden Liste enthalten (2 für Exchange Online und 5 für lokales Exchange). 

2. Konfigurieren von Office-Anwendungen und -Diensten für IRM
    
    Konfigurieren Sie die Office-Anwendungen und -Dienste für die IRM-Features (Information Rights Management) in SharePoint Online oder Exchange Online. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

3. Konfigurieren des Administratorfeatures für die Datenwiederherstellung
    
    Wenn vorhandene IT-Dienste von Azure Rights Management geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen, Gateways zur Inhaltsverschlüsselung und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md).

4. Massenweises Klassifizieren und Schützen von Dateien – Bei Bedarf
    
    Die PowerShell-Cmdlets, mit denen Sie Dateien klassifizieren und schützen (als auch die Klassifizierung und den Schutz entfernen), werden automatisch mit dem Azure Information Protection-Client installiert. Weitere Informationen finden Sie im Administratorhandbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](..\rms-client\client-admin-guide-powershell.md).

6. Bereitstellen des Connectors für lokale Server
    
    Wenn Sie über lokale Dienste verfügen, die Sie mit dem Azure Rights Management-Dienst verwenden möchten, installieren und konfigurieren Sie den Rights Management-Connector. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>Schritt 6: Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten
Sie sind jetzt bereit, Ihre Daten zu schützen und dabei zu protokollieren, wie die von Ihnen konfigurierten Bezeichnungen und der Rights Management-Datenschutz in Ihrem Unternehmen verwendet werden. Weitere Informationen zur Unterstützung dieser Phase der Bereitstellung finden Sie unter:

- [Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](../deploy-use/help-users.md)

-  [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md)

- [Clientdateien und Nutzungsprotokollierung](../rms-client/client-admin-guide-files-and-logging.md)

Wenn Sie sich für den automatischen Schutz von Dateien mithilfe der Dateiklassifizierungsinfrastruktur auf einem Windows-basierten Dateiserver interessieren, lesen Sie den Artikel [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](../rms-client/configure-fci.md).

### <a name="step-7-administer-the-rights-management-service-for-your-tenant-account-as-needed"></a>Schritt 7: Bedarfsgesteuertes Verwalten des Rights Management-Diensts für Ihr Mandantenkonto
Wenn Sie mit der Verwendung des Azure Rights Management-Diensts beginnen, kann Windows PowerShell nützlich sein, um administrative Änderungen skriptgesteuert oder automatisiert durchzuführen. Weitere Informationen finden Sie unter [Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell](../deploy-use/administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Roadmap für die Bereitstellung zum ausschließlichen Schutz von Daten

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-azure-rights-management"></a>Schritt 1: Sicherstellen, dass Sie über ein Abonnement verfügen, das Azure Rights Management umfasst
Überprüfen Sie anhand der [Abonnementinformationen](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) und der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website, ob Ihre Organisation über ein Abonnement verfügt, das diese Funktionen und Features umfasst. Weisen Sie anschließend jedem Benutzer in Ihrer Organisation, der Dokumente und E-Mails mit dem Azure Rights Management-Dienst schützen soll, eine Lizenz aus diesem Abonnement zu.

Hinweis: Weisen Sie keine Benutzerlizenzen manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht zum Verwalten des Azure Rights Management-Diensts für Ihre Organisation. Für diese Lizenzen wird im Office 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) **RIGHTSMANAGEMENT_ADHOC** angezeigt. Weitere Informationen dazu, wie das RMS for Individuals-Abonnement automatisch gewährt und Benutzern zugewiesen wird, finden Sie unter [RMS for Individuals und Azure Information Protection](../understand-explore/rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-the-azure-rights-management-service"></a>Schritt 2: Vorbereiten Ihres Mandanten für die Verwendung des Azure Rights Management-Diensts
Bevor Sie mit der Verwendung von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] beginnen, führen Sie folgende Vorbereitungsschritte aus:

1.  Stellen Sie sicher, dass Ihr Office 365-Mandant die Benutzerkonten und -gruppen enthält, die Azure Information Protection zum Authentifizieren und Autorisieren von Benutzern in Ihrer Organisation verwendet. Falls erforderlich, erstellen Sie diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

2. Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Beachten Sie, dass Sie derzeit BYOK nicht verwenden können, wenn Sie Exchange Online nutzen. Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

3. Installieren Sie das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] auf mindestens einem Computer, der Zugang zum Internet hat. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

4. Wenn Sie derzeit lokale Rights Management Services verwenden: Führen Sie eine Migration durch, um die Schlüssel, Vorlagen und URLs in die Cloud zu verschieben. Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Aktivieren Sie Rights Management, damit Sie mit der Verwendung des Diensts beginnen können. Wenn eine Bereitstellung in Phasen erforderlich ist, konfigurieren Sie benutzerbezogene Steuerungsrichtlinien für die Einbindung (Onboarding), um die Nutzung auf bestimmte Benutzer zu beschränken. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

Erwägen Sie optional die Konfigurierung folgender Funktionen:

-   Benutzerdefinierte Vorlagen, wenn die Standardvorlagen für Ihre Organisation nicht ausreichend sind. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](../deploy-use/configure-policy-templates.md).

-   Nutzungsprotokollierung, sodass Sie überwachen können, wie Ihre Organisation Rights Management verwendet. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).

### <a name="step-3-install-the-client-and-configure-applications-and-services-for-rights-management"></a>Schritt 3: Installieren des Clients und Konfigurieren von Anwendungen und Diensten für Rights Management

1. Bereitstellen des Azure Information Protection-Clients
    
    Installieren Sie Azure Information Protection für Benutzer, um Office 2010 zu unterstützen, andere Dateien als Office-Dokumente und E-Mails zu schützen und geschützte Dokumente nachzuverfolgen. Bieten Sie Benutzerschulungen für diesen Client an. Weitere Informationen finden Sie unter [Azure Information Protection-Client für Windows](../rms-client/aip-client.md).

2. Konfigurieren von Office-Anwendungen und -Diensten für IRM
    
    Konfigurieren Sie die Office-Anwendungen und -Dienste für die IRM-Features (Information Rights Management) in SharePoint Online oder Exchange Online. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

3. Konfigurieren des Administratorfeatures für die Datenwiederherstellung
    
    Wenn vorhandene IT-Dienste von Azure Rights Management geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen, Gateways zur Inhaltsverschlüsselung und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md).

4. Massenweises Schützen von Dateien – Bei Bedarf 
    
    Die PowerShell-Cmdlets, mit denen Sie mehrere Dateitypen massenweise schützen oder deren Schutz aufheben können, werden automatisch mit dem Azure Information Protection-Client installiert. Weitere Informationen finden Sie im Administratorhandbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](..\rms-client\client-admin-guide-powershell.md).

5. Bereitstellen des Connectors für lokale Server
    
    Wenn Sie über lokale Dienste verfügen, die Sie mit dem Azure Rights Management-Dienst verwenden möchten, installieren und konfigurieren Sie den Rights Management-Connector. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).


### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Schritt 4: Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten
Sie können jetzt Ihre Daten schützen und die Nutzung von Rights Management durch Ihre Organisation protokollieren. Weitere Informationen zu dieser Bereitstellungsphase finden Sie unter [Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](../deploy-use/help-users.md) und [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).

Wenn Sie sich für den automatischen Schutz von Dateien mithilfe der Dateiklassifizierungsinfrastruktur auf einem Windows-basierten Dateiserver interessieren, lesen Sie den Artikel [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](../rms-client/configure-fci.md).

### <a name="step-5-administer-the-rights-management-service-for-your-tenant-account-as-needed"></a>Schritt 5: bedarfsgesteuertes Verwalten des Rights Management-Diensts für Ihr Mandantenkonto
Wenn Sie mit der Verwendung des Azure Rights Management-Diensts beginnen, kann Windows PowerShell nützlich sein, um administrative Änderungen skriptgesteuert oder automatisiert durchzuführen. Weitere Informationen finden Sie unter [Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell](../deploy-use/administer-powershell.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
