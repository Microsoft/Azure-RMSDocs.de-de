---
title: Roadmap für die Bereitstellung von Azure Information Protection
description: Führen Sie diese Schritte aus, um Azure Information Protection für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: dd88cc456337398e9ac95ffafec8514f93cc6598
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60179826"
---
# <a name="azure-information-protection-deployment-roadmap"></a>Roadmap für die Bereitstellung von Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Führen Sie die folgenden Schritte aus (empfohlen), um Azure Information Protection für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten.

Wenn Sie allerdings nach szenariobasierten Anweisungen suchen, lesen Sie [Schrittanleitungen für häufige Szenarien mit Azure Information Protection](how-to-guides.md).

> [!NOTE]
> Wenn Sie nach einer Roadmap für Produktreleases suchen, lesen Sie den Abschnitt [Informationen zu neuen Releases und Updates](information-support.md#information-about-new-releases-and-updates).

### <a name="identify-your-deployment-roadmap"></a>Identifizieren Ihrer Bereitstellungsroadmap

Lesen Sie vor dem Durchführen der folgenden Schritte zum Bereitstellen von Azure Information Protection den Artikel [Anforderungen für Azure Information Protection](./requirements.md).

Wählen Sie dann eine Roadmap für die Bereitstellung aus, die für Ihre Organisation anwendbar ist und die [Abonnementfunktionen und -features](https://azure.microsoft.com/pricing/details/information-protection/) umfasst, die Sie benötigen:

- [Klassifizierung, Bezeichnung und Schutz](#deployment-roadmap-for-classification-labeling-and-protection)

- [Ausschließlicher Schutz von Daten](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Roadmap für die Bereitstellung von Klassifizierung, Bezeichnung und Schutz

> [!NOTE]
> Verwenden Sie bereits die Schutzfunktion von Azure Information Protection? Sie können viele dieser Schritte überspringen und sich auf die Schritte 3 und 5.1 konzentrieren.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Schritt 1: Bestätigen Ihres Abonnements und Zuweisen von Benutzerlizenzen
Überprüfen Sie anhand der Abonnementinformationen und der Featureliste auf der [Azure Information Protection-Preisseite](https://azure.microsoft.com/pricing/details/information-protection), ob Ihre Organisation über ein Abonnement verfügt, das diese Funktionen und Features umfasst. Weisen Sie anschließend jedem Benutzer in Ihrer Organisation, der Klassifizierungen und Bezeichnung vornehmen und Dokumente und E-Mails schützen soll, eine Lizenz aus diesem Abonnement zu.

Hinweis: Weisen Sie keine Benutzerlizenzen manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht zum Verwalten des Azure Rights Management-Diensts für Ihre Organisation. Für diese Lizenzen wird im Microsoft 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) **RIGHTSMANAGEMENT_ADHOC** angezeigt. Weitere Informationen dazu, wie das RMS for Individuals-Abonnement automatisch gewährt und Benutzern zugewiesen wird, finden Sie unter [RMS for Individuals und Azure Information Protection](./rms-for-individuals.md).

### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Schritt 2: Vorbereiten Ihres Mandanten für Azure Information Protection

Bevor Sie mit der Verwendung von Azure Information Protection beginnen, stellen Sie sicher, dass Sie über Benutzerkonten und Gruppen in Office 365 oder Azure Active Directory verfügen. Diese Benutzerkonten und Gruppen werden von Azure Information Protection verwendet, um Benutzer aus Ihrer Organisation zu authentifizieren und zu autorisieren. Falls erforderlich, erstellen Sie diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. 

Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Schritt 3: Konfigurieren und Bereitstellen von Klassifizierungen und Bezeichnungen

> [!TIP]
> **Optional, aber empfohlen**: Erwägen Sie, den Azure Information Protection-Scanner einzusetzen, um herauszufinden, welche vertraulichen Informationen Sie in Ihren lokalen Datenspeichern gespeichert haben. Dieses Szenario wird in [diesem Schnellstart](quickstart-findsensitiveinfo.md) behandelt. Die Informationen, die der Scanner findet, können Ihnen bei Ihrer Klassifizierungstaxonomie helfen und wertvolle Informationen darüber liefern, welche Bezeichnungen Sie benötigen und welche Dateien geschützt werden müssen.
> 
> Der Scanner kann so konfiguriert werden, dass er nach bekannten vertraulichen Informationstypen in lokalen Dateien in Windows Server, Dateien in Netzwerkfreigaben und Dateien in lokalen Versionen von SharePoint sucht. Da diese Konfiguration nicht erfordert, dass Sie Bezeichnungen konfigurieren oder gar Ihre Klassifizierungstaxonomie definieren müssen, ist eine derartige Ausführung des Scanners für dieses sehr frühe Stadium Ihrer Bereitstellung geeignet. Sie können diese Konfiguration des Scanners auch parallel zu den folgenden Bereitstellungsschritten verwenden, bis Sie die Bedingungen für Ihre Bezeichnungen konfigurieren.

Wenn Sie nicht bereits über eine Klassifizierungsstrategie verfügen, lesen Sie die [Azure Information Protection-Standardrichtlinie](./configure-policy-default.md), und verwenden Sie diese als Grundlage für die Entscheidung, welche Klassifizierungsbezeichnungen Sie den Daten in Ihrer Organisation zuweisen möchten. Sie können diese an Ihre geschäftlichen Anforderungen anpassen.

Konfigurieren Sie die Standardbezeichnungen von Azure Information Protection, um Änderungen vorzunehmen, die Ihre Klassifizierungsentscheidungen unterstützen. Konfigurieren Sie die Richtlinie für das manuelle Bezeichnen von Benutzern, und verfassen Sie Anleitungen für Benutzer dazu, welche Bezeichnung wann anzuwenden sind. Wenn Ihre Standardrichtlinie mit Bezeichnungen erstellt wurde, die Schutz automatisch anwenden, entfernen Sie die Schutzeinstellungen vorübergehend, oder deaktivieren Sie die Bezeichnung. Weitere Informationen zum Konfigurieren der Azure Information Protection-Richtlinie finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](./configure-policy.md).

Bereitstellen der [Azure Information Protection-Client oder des einheitlichen Azure Information Protection-Bezeichnung-Clients für Benutzer](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client) für Benutzer, und geben Sie die Schulung von Benutzern und spezifische Anweisungen Wenn die Bezeichnungen auswählen. Weitere Informationen zum Installieren und unterstützen des Clients finden Sie unter den Admin-Handbüchern:

- [Azure Information Protection-Client – Administratorhandbuch](./rms-client/client-admin-guide.md)

- [Azure Information Protection – einheitliche bezeichnungs Client – Administratorhandbuch](./rms-client/clientv2-admin-guide.md)

Wenn die Benutzer nach einer Weile mit dem Bezeichnen ihrer Dokumente und E-Mails vertraut sind, können Sie weitere Konfigurationen einführen. Dazu zählt unter anderem Folgendes:

- Anwenden einer Standardbezeichnung

- Auffordern von Benutzern, eine Begründung anzugeben, wenn sie eine Bezeichnung mit einer niedrigeren Klassifizierungsebene ausgewählt haben, oder Entfernen einer Bezeichnung

- Vorschreiben, dass alle Dokumente und E-Mails eine Bezeichnung benötigen

- Benutzerdefinierte Kopfzeilen, Fußzeilen und Wasserzeichen

- Bedingungen zur Unterstützung von Empfehlungen und automatische Bezeichnung

Wählen Sie zu diesem Zeitpunkt nicht die Option für den Schutz der Dokumente und E-Mails aus. Nachdem Sie Bezeichnungen für das automatische Bezeichnen konfiguriert haben, führen Sie jedoch den [Azure Information Protection-Scanner](deploy-aip-scanner.md) für Ihre lokalen Datenspeicher im Erkennungsmodus aus, um Ihre Richtlinie zu erfüllen. Wenn Sie den Scanner mit dieser Konfiguration ausführen, erfahren Sie, welche Bezeichnungen auf Dateien angewendet würden. Diese Informationen helfen Ihnen bei der Feinabstimmung Ihrer Bezeichnungskonfiguration und bereiten Sie auf die Massenklassifizierung und den Schutz von großen Dateimengen vor. 

### <a name="step-4-prepare-for-data-protection"></a>Schritt 4: Vorbereitung auf den Datenschutz

Wenn Benutzer mit dem Bezeichnen von Dokumenten und E-Mails vertraut sind, können Sie mit der Einführung des Schutzes von Daten für Ihre vertraulichsten Daten beginnen. Für diese Phase sind folgende Vorbereitungen notwendig:

1. Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

2. Installieren Sie das PowerShell-Modul für AADRM auf mindestens einem Computer, der Zugang zum Internet hat. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Installieren des AADRM-PowerShell-Moduls](./install-powershell.md).

3. Wenn Sie zurzeit AD RMS verwenden: Führen Sie eine Migration aus, um die Schlüssel, Vorlagen und URLs in die Cloud verschieben. Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Stellen Sie sicher, dass der Schutzdienst aktiviert ist, damit Sie mit dem Schützen von Dokumenten und E-Mails beginnen können. Wenn eine Bereitstellung in Phasen erforderlich ist, konfigurieren Sie benutzerbezogene Steuerungsrichtlinien für die Einbindung (Onboarding), um die Möglichkeiten von Benutzern zum Anwenden von Schutz zu beschränken. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](./activate-service.md).

Erwägen Sie optional die Konfigurierung folgender Funktionen:

- Nutzungsprotokollierung, sodass Sie überwachen können, wie Ihre Organisation den Schutzdienst verwendet. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](./log-analyze-usage.md).

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-data-protection"></a>Schritt 5: Konfigurieren der Azure Information Protection-Richtlinie sowie von Anwendungen und Diensten für den Schutz von Daten

1. Aktualisieren Sie Ihre Bezeichnungen aus, um den Schutz anzuwenden
    
    Für den Azure Information Protection-Client finden Sie unter [Gewusst wie: Konfigurieren einer Bezeichnung für Rights Management-Schutz](./configure-policy-protection.md).
    
    Die Azure Information Protection die Bezeichnung Client unified, finden Sie unter [Beschränken des Zugriffs auf Inhalte mithilfe von Verschlüsselung in vertraulichkeitsbezeichnungen](https://docs.microsoft.com/Office365/SecurityCompliance/encryption-sensitivity-labels).
    
    Beachten Sie, dass Benutzer Bezeichnungen für die Anwendung des Rights Management-Schutzes auch dann in Outlook verwenden können, wenn Exchange nicht für Information Rights Management (IRM) konfiguriert ist. Ihre Organisation kann jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn Exchange für IRM oder die [Office 365-Nachrichtenverschlüsselung mit neuen Funktionen](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist. Diese zusätzliche Konfiguration ist in der folgenden Liste enthalten (2 für Exchange Online und 5 für lokales Exchange). 

2. Konfigurieren von Office-Anwendungen und -Diensten
    
    Konfigurieren Sie die Office-Anwendungen und -Dienste für die IRM-Features (Information Rights Management) in SharePoint Online oder Exchange Online. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md).

3. Konfigurieren des Administratorfeatures für die Datenwiederherstellung
    
    Wenn vorhandene IT-Dienste von Azure Information Protection geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen – Data Leak Prevention, Gateways zur Inhaltsverschlüsselung (Content Encryption Gateways, CEG) und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](./configure-super-users.md).

4. Massenklassifizierung und -schützen vorhandener Dateien
    
    Führen Sie nun für Ihre lokalen Datenspeicher den [Azure Information Protection-Scanner](deploy-aip-scanner.md) im Erzwingungsmodus aus, sodass Dateien automatisch mit einer Bezeichnung versehen werden. Verwenden Sie für cloudbasierte Datenspeicher [Azure Cloud App Security](https://docs.microsoft.com/cloud-app-security).
    
    Für Dateien auf PCs können Sie PowerShell-Cmdlets verwenden, um Dateien zu klassifizieren und zu schützen. Weitere Informationen finden Sie im Administratorhandbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).

6. Bereitstellen des Connectors für durch IRM geschützte Bibliotheken unter SharePoint Server und durch IRM geschützte E-Mails für Exchange lokal
    
    Wenn Sie SharePoint und Exchange lokal verwenden und deren Funktionen zur Verwaltung von Informationsrechten (IRM) nutzen möchten, installieren und konfigurieren Sie den Rights Management-Connector. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](./deploy-rms-connector.md).

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>Schritt 6: Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten
Sie sind nun bereit, die Verwendung der von Ihnen konfigurierten Bezeichnungen in Ihrem Unternehmen zu überwachen und zu bestätigen, dass Sie sensible Informationen schützen. Weitere Informationen zur Unterstützung dieser Phase der Bereitstellung finden Sie unter:

- [Berichterstellung für Azure Information Protection](reports-aip.md): zurzeit in der Vorschau

- Clientdateien und verwendungsprotokollierung für den [Azure Information Protection-Client](./rms-client/client-admin-guide-files-and-logging.md)

- [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](./log-analyze-usage.md)

### <a name="step-7-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Schritt 7: Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto

Wenn Sie mit der Verwendung des Schutzdiensts beginnen, kann PowerShell nützlich sein, um administrative Änderungen skriptgestützt oder automatisiert durchzuführen. PowerShell kann ebenfalls für einige der erweiterten Konfigurationen erforderlich sein. 

Weitere Informationen finden Sie unter [Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell](./administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Roadmap für die Bereitstellung zum ausschließlichen Schutz von Daten

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-the-protection-service-from-azure-information-protection"></a>Schritt 1: Bestätigen, dass Sie ein Abonnement besitzen, das den Schutzdienst von Azure Information Protection enthält

Überprüfen Sie anhand der Abonnementinformationen und der Featureliste auf der [Azure Information Protection-Preisseite](https://azure.microsoft.com/pricing/details/information-protection), ob Ihre Organisation über ein Abonnement verfügt, das diese Funktionen und Features umfasst. Weisen Sie anschließend jedem Benutzer in Ihrer Organisation, der Dokumente und E-Mails schützen soll, eine Lizenz aus diesem Abonnement zu.

Hinweis: Weisen Sie keine Benutzerlizenzen manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht zum Verwalten des Azure Rights Management-Diensts für Ihre Organisation. Für diese Lizenzen wird im Microsoft 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) **RIGHTSMANAGEMENT_ADHOC** angezeigt. Weitere Informationen dazu, wie das RMS for Individuals-Abonnement automatisch gewährt und Benutzern zugewiesen wird, finden Sie unter [RMS for Individuals und Azure Information Protection](./rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Schritt 2: Vorbereiten Ihres Mandanten für Azure Information Protection

Führen Sie die folgende Vorbereitungsschritte aus, bevor Sie mit der Verwendung des Schutzdiensts von Azure Information Protection beginnen:

1. Stellen Sie sicher, dass Ihr Office 365-Mandant die Benutzerkonten und -gruppen enthält, die Azure Information Protection zum Authentifizieren und Autorisieren von Benutzern in Ihrer Organisation verwendet. Falls erforderlich, erstellen Sie diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

2. Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

3. Installieren Sie das PowerShell-Modul für AADRM auf mindestens einem Computer, der Zugang zum Internet hat. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Installieren des AADRM-PowerShell-Moduls](./install-powershell.md).

4. Wenn Sie zurzeit AD RMS verwenden: Führen Sie eine Migration aus, um die Schlüssel, Vorlagen und URLs in die Cloud verschieben. Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Stellen Sie sicher, dass der Schutzdienst aktiviert ist, damit Sie mit dem Schützen von Dokumenten und E-Mails beginnen können. Wenn eine Bereitstellung in Phasen erforderlich ist, konfigurieren Sie benutzerbezogene Steuerungsrichtlinien für die Einbindung (Onboarding), um die Möglichkeiten von Benutzern zum Anwenden von Schutz zu beschränken. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](./activate-service.md).

Erwägen Sie optional die Konfigurierung folgender Funktionen:

- Benutzerdefinierte Vorlagen für die Schutzeinstellungen, wenn die Standardvorlagen für Ihre Organisation nicht ausreichend sind. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](./configure-policy-templates.md).

- Nutzungsprotokollierung, sodass Sie überwachen können, wie Ihre Organisation den Schutzdienst verwendet. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](./log-analyze-usage.md).

### <a name="step-3-install-the-azure-information-protection-client-and-configure-applications-and-services-for-rights-management"></a>Schritt 3: Den Azure Information Protection-Client installieren und Konfigurieren von Anwendungen und Dienste für Rights Management

1. Bereitstellen des Azure Information Protection-Clients
    
    Installieren Sie Azure Information Protection für Benutzer, um Office 2010 zu unterstützen, andere Dateien als Office-Dokumente und E-Mails zu schützen und geschützte Dokumente nachzuverfolgen. Bieten Sie Benutzerschulungen für diesen Client an. Weitere Informationen finden Sie unter [Azure Information Protection-Client für Windows](./rms-client/aip-client.md).

2. Konfigurieren von Office-Anwendungen und -Diensten
    
    Konfigurieren Sie die Office-Anwendungen und -Dienste für die IRM-Features (Information Rights Management) in SharePoint Online oder Exchange Online. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](./configure-applications.md).

3. Konfigurieren des Administratorfeatures für die Datenwiederherstellung
    
    Wenn vorhandene IT-Dienste von Azure Information Protection geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen – Data Leak Prevention, Gateways zur Inhaltsverschlüsselung (Content Encryption Gateways, CEG) und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](./configure-super-users.md).

4. Massenschützen vorhandener Dateien 
    
    Sie können PowerShell-Cmdlets verwenden, um mehrere Dateitypen massenzuschützen oder den Schutz aufzuheben. Weitere Informationen finden Sie im Administratorhandbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).
    
    Für Dateien auf Windows-basierten Dateiservern können Sie diese Cmdlets mit einem Skript und der Windows Server-Dateiklassifizierungsinfrastruktur verwenden. Weitere Informationen finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](./rms-client/configure-fci.md).

5. Bereitstellen des Connectors für lokale Server
    
    Wenn Sie über lokale Dienste verfügen, die Sie mit dem Schutzdienst verwenden möchten, installieren und konfigurieren Sie den Rights Management-Connector. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](./deploy-rms-connector.md).

### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Schritt 4: Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten

Sie können jetzt Ihre Daten schützen und die Nutzung des Schutzdiensts durch Ihre Organisation protokollieren. Weitere Informationen zu dieser Bereitstellungsphase finden Sie unter [Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](./help-users.md) und [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](./log-analyze-usage.md).

### <a name="step-5-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Schritt 5: Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto

Wenn Sie mit der Verwendung des Schutzdiensts beginnen, kann PowerShell nützlich sein, um administrative Änderungen skriptgestützt oder automatisiert durchzuführen. PowerShell kann ebenfalls für einige der erweiterten Konfigurationen erforderlich sein. 

Weitere Informationen finden Sie unter [Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell](./administer-powershell.md).