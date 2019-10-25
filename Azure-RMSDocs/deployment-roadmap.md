---
title: Roadmap für die Bereitstellung von Azure Information Protection
description: Führen Sie diese Schritte aus, um Azure Information Protection für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: d304664bb3573bc1a90989f11927264450d01c0d
ms.sourcegitcommit: 47d5765e1b76309a81aaf5e660256f2fb30eb2b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72805568"
---
# <a name="azure-information-protection-deployment-roadmap"></a>Roadmap für die Bereitstellung von Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Führen Sie die folgenden Schritte aus (empfohlen), um Azure Information Protection für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten.

Alternativ 

- Suchen Sie nach einer szenariobasierten Anweisung für Azure Information Protection? [Allgemeine Szenarien, in denen Azure Information Protection verwendet wird, finden Sie unter Anleitungen](how-to-guides.md).

- Suchen Sie nach der Roadmap für die Azure Information Protection-Version? Weitere Informationen finden Sie unter [Informationen zu neuen Releases und Updates](information-support.md#information-about-new-releases-and-updates).

### <a name="identify-your-deployment-roadmap"></a>Identifizieren Ihrer Bereitstellungsroadmap

Lesen Sie vor dem Durchführen der folgenden Schritte zum Bereitstellen von Azure Information Protection den Artikel [Anforderungen für Azure Information Protection](./requirements.md).

Wählen Sie dann eine Roadmap für die Bereitstellung aus, die für Ihre Organisation anwendbar ist und die [Abonnementfunktionen und -features](https://azure.microsoft.com/pricing/details/information-protection/) umfasst, die Sie benötigen:

- [Klassifizierung, Bezeichnung und Schutz](#deployment-roadmap-for-classification-labeling-and-protection)
    
    Der empfohlene Pfad, wenn Sie über ein unterstützendes Abonnement verfügen, da die zusätzlichen Funktionen das ermitteln sensibler Informationen unterstützen und Dokumente und e-Mails für die Klassifizierung bezeichnen. Die Bezeichnungen können auch Schutz anwenden, um diese Komplexität von Benutzern zu abstrahieren.
    
    Die Bereitstellungs Schritte eignen sich für Azure Information Protection Bezeichnungen und Vertraulichkeits Bezeichnungen, die die [einheitliche Beschriftungs Plattform](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)verwenden.

- [Ausschließlicher Schutz von Daten](#deployment-roadmap-for-data-protection-only)
    
    Der Pfad, der verwendet werden soll, wenn Sie über kein Abonnement verfügen, das Klassifizierungen und Bezeichnungen unterstützt, aber Schutz ohne Bezeichnungen unterstützt.

## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Roadmap für die Bereitstellung von Klassifizierung, Bezeichnung und Schutz

> [!NOTE]
> Verwenden Sie bereits die Schutzfunktion von Azure Information Protection? Sie können viele dieser Schritte überspringen und sich auf die Schritte 3 und 5.1 konzentrieren.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Schritt 1: Bestätigen Ihres Abonnements und Zuweisen von Benutzerlizenzen
Überprüfen Sie anhand der Abonnementinformationen und der Featureliste auf der [Azure Information Protection-Preisseite](https://azure.microsoft.com/pricing/details/information-protection), ob Ihre Organisation über ein Abonnement verfügt, das diese Funktionen und Features umfasst. Weisen Sie anschließend jedem Benutzer in Ihrer Organisation, der Klassifizierungen und Bezeichnung vornehmen und Dokumente und E-Mails schützen soll, eine Lizenz aus diesem Abonnement zu.

Hinweis: Weisen Sie keine Benutzerlizenzen manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht zum Verwalten des Azure Rights Management-Diensts für Ihre Organisation. Für diese Lizenzen wird im Microsoft 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) **RIGHTSMANAGEMENT_ADHOC** angezeigt. Weitere Informationen dazu, wie das RMS for Individuals-Abonnement automatisch gewährt und Benutzern zugewiesen wird, finden Sie unter [RMS for Individuals und Azure Information Protection](./rms-for-individuals.md).

### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Schritt 2: Vorbereiten Ihres Mandanten für Azure Information Protection

Bevor Sie mit der Verwendung von Azure Information Protection beginnen, stellen Sie sicher, dass Sie über Benutzerkonten und Gruppen in Office 365 oder Azure Active Directory verfügen. Diese Benutzerkonten und Gruppen werden von Azure Information Protection verwendet, um Benutzer aus Ihrer Organisation zu authentifizieren und zu autorisieren. Falls erforderlich, erstellen Sie diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. 

Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Schritt 3: Konfigurieren und Bereitstellen von Klassifizierungen und Bezeichnungen

Legen Sie vor dem Konfigurieren von Bezeichnungen und Richtlinien Einstellungen fest, welche Azure Information Protection Client Sie verwenden möchten: der klassische Client oder der Unified Label-Client. Möglicherweise benötigen Sie aber auch beide Clients. Diese Client Entscheidung wird jetzt benötigt, sodass Sie wissen, welches Verwaltungs Portal zum Konfigurieren von Bezeichnungen und Richtlinien Einstellungen verwendet werden soll. Weitere Informationen und Hilfe bei dieser Entscheidung finden Sie unter Auswählen des [zu verwendenden Azure Information Protection Clients](./rms-client/use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

> [!TIP]
> **Optional, aber empfohlen**: Verwenden Sie den [Schnellstart für Scanner](quickstart-findsensitiveinfo.md) , um zu ermitteln, welche sensiblen Informationen Sie in Ihren lokalen Daten speichern haben. Die Informationen, die der Scanner findet, können Ihnen bei Ihrer Klassifizierungstaxonomie helfen und wertvolle Informationen darüber liefern, welche Bezeichnungen Sie benötigen und welche Dateien geschützt werden müssen.
> 
> Da der Überprüfungs Modus für die Überprüfung nicht erfordert, dass Bezeichnungen konfiguriert werden oder die Klassifizierungs Taxonomie definiert ist, ist die Ausführung des Scanners auf diese Weise für diese sehr frühe Bereitstellung geeignet. Sie können diese Konfiguration des Scanners auch parallel mit den folgenden Bereitstellungs Schritten verwenden, bis Sie die empfohlene oder automatische Bezeichnung konfigurieren.

Wenn Sie noch nicht über eine Klassifizierungs Strategie verfügen, überprüfen Sie die [Standard-Azure Information Protection Richtlinie](./configure-policy-default.md) , und verwenden Sie diese als Grundlage für die Entscheidung, welche Klassifizierungs Bezeichnungen ihren Organisationsdaten zugewiesen werden sollen. Sie können diese an Ihre geschäftlichen Anforderungen anpassen.

Konfigurieren Sie Ihre Bezeichnungen neu, um Änderungen vorzunehmen, die Sie zur Unterstützung ihrer Klassifizierungs Entscheidungen benötigen. Konfigurieren Sie die Richtlinie für das manuelle Bezeichnen von Benutzern, und verfassen Sie Anleitungen für Benutzer dazu, welche Bezeichnung wann anzuwenden sind. Wenn Ihre Standardrichtlinie mit Bezeichnungen erstellt wurde, die Schutz automatisch anwenden, entfernen Sie die Schutzeinstellungen vorübergehend, oder deaktivieren Sie die Bezeichnung. Weitere Informationen zum Konfigurieren der Bezeichnungen und Richtlinien Einstellungen finden Sie in der folgenden Dokumentation:

- Azure Information Protection Bezeichnungen für den klassischen Client: [Konfigurieren Azure Information Protection Richtlinie](./configure-policy.md)

- Vertraulichkeits Bezeichnungen für den Unified Label-Client: [Übersicht über Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)

Stellen Sie dann den Azure Information Protection Client (klassisch) oder den Azure Information Protection Unified-Beschriftungs Client für Benutzer bereit. Bereitstellen von Benutzer Schulungen und spezifischen Anweisungen, wann die Bezeichnungen ausgewählt werden sollen. Weitere Informationen zum Installieren und unterstützen von Clients finden Sie in den Administrator Handbüchern:

- [Azure Information Protection-Client – Administratorhandbuch](./rms-client/client-admin-guide.md)

- [Azure Information Protection Unified Bezeichnung-Client Administrator Handbuch](./rms-client/clientv2-admin-guide.md)

Wenn die Benutzer nach einer Weile mit dem Bezeichnen ihrer Dokumente und E-Mails vertraut sind, können Sie weitere Konfigurationen einführen. Dazu zählt unter anderem Folgendes:

- Anwenden einer Standardbezeichnung

- Auffordern von Benutzern, eine Begründung anzugeben, wenn sie eine Bezeichnung mit einer niedrigeren Klassifizierungsebene ausgewählt haben, oder Entfernen einer Bezeichnung

- Vorschreiben, dass alle Dokumente und E-Mails eine Bezeichnung benötigen

- Benutzerdefinierte Kopfzeilen, Fußzeilen und Wasserzeichen

- Empfohlene und automatische Bezeichnung

Wählen Sie zu diesem Zeitpunkt nicht die Option für den Schutz der Dokumente und E-Mails aus. Nachdem Sie Bezeichnungen für das automatische Bezeichnen konfiguriert haben, führen Sie jedoch den [Azure Information Protection-Scanner](deploy-aip-scanner.md) für Ihre lokalen Datenspeicher im Erkennungsmodus aus, um Ihre Richtlinie zu erfüllen. Wenn Sie den Scanner mit dieser Konfiguration ausführen, erfahren Sie, welche Bezeichnungen auf Dateien angewendet würden. Diese Informationen helfen Ihnen bei der Feinabstimmung Ihrer Bezeichnungskonfiguration und bereiten Sie auf die Massenklassifizierung und den Schutz von großen Dateimengen vor. 

### <a name="step-4-prepare-for-data-protection"></a>Schritt 4: Vorbereitung auf den Datenschutz

Wenn Benutzer mit dem Bezeichnen von Dokumenten und E-Mails vertraut sind, können Sie mit der Einführung des Schutzes von Daten für Ihre vertraulichsten Daten beginnen. Für diese Phase sind folgende Vorbereitungen notwendig:

1. Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

2. Installieren Sie das PowerShell-Modul für aipservice auf mindestens einem Computer, der über Internet Zugriff verfügt. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](./install-powershell.md).

3. Wenn Sie derzeit AD RMS verwenden: Führen Sie eine Migration durch, um die Schlüssel, Vorlagen und URLs in die Cloud zu verschieben. Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Stellen Sie sicher, dass der Schutzdienst aktiviert ist, damit Sie mit dem Schützen von Dokumenten und E-Mails beginnen können. Wenn eine Bereitstellung in Phasen erforderlich ist, konfigurieren Sie benutzerbezogene Steuerungsrichtlinien für die Einbindung (Onboarding), um die Möglichkeiten von Benutzern zum Anwenden von Schutz zu beschränken. Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](./activate-service.md).

Erwägen Sie optional die Konfigurierung folgender Funktionen:

- Nutzungsprotokollierung, sodass Sie überwachen können, wie Ihre Organisation den Schutzdienst verwendet. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md).

### <a name="step-5-configure-labels-and-settings-applications-and-services-for-data-protection"></a>Schritt 5: Konfigurieren von Bezeichnungen und Einstellungen, Anwendungen und Diensten für den Schutz von Daten

1. Aktualisieren ihrer Bezeichnungen zum Anwenden des Schutzes
    
    Informationen zum Azure Information Protection-Client (klassisch) finden [Sie unter Konfigurieren einer Bezeichnung für Rights Management Schutz](./configure-policy-protection.md).
    
    Informationen zum Azure Information Protection Unified Label-Client finden [Sie unter Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Sensitivitäts Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels).
    
    Beachten Sie, dass Benutzer Bezeichnungen für die Anwendung des Rights Management-Schutzes auch dann in Outlook verwenden können, wenn Exchange nicht für Information Rights Management (IRM) konfiguriert ist. Ihre Organisation kann jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn Exchange für IRM oder die [Office 365-Nachrichtenverschlüsselung mit neuen Funktionen](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist. Diese zusätzliche Konfiguration ist in der folgenden Liste enthalten (2 für Exchange Online und 5 für lokales Exchange). 

2. Konfigurieren von Office-Anwendungen und -Diensten
    
    Konfigurieren Sie die Office-Anwendungen und -Dienste für die IRM-Features (Information Rights Management) in SharePoint Online oder Exchange Online. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md).

3. Konfigurieren des Administratorfeatures für die Datenwiederherstellung
    
    Wenn vorhandene IT-Dienste von Azure Information Protection geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen – Data Leak Prevention, Gateways zur Inhaltsverschlüsselung (Content Encryption Gateways, CEG) und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](./configure-super-users.md).

4. Massenklassifizierung und -schützen vorhandener Dateien
    
    Führen Sie nun für Ihre lokalen Datenspeicher den [Azure Information Protection-Scanner](deploy-aip-scanner.md) im Erzwingungsmodus aus, sodass Dateien automatisch mit einer Bezeichnung versehen werden. Verwenden Sie für cloudbasierte Datenspeicher [Azure Cloud App Security](https://docs.microsoft.com/cloud-app-security).
    
    Für Dateien auf PCs können Sie PowerShell-Cmdlets verwenden, um Dateien zu klassifizieren und zu schützen. Weitere Informationen finden Sie in den folgenden Administrator Handbüchern:
    
    - Azure Information Protection-Client (klassisch): [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md)
    
    - Azure Information Protection Unified-Bezeichnungs Client: [Verwenden von PowerShell mit dem Azure Information Protection Unified-Beschriftungs Client](./rms-client/clientv2-admin-guide-powershell.md)

6. Bereitstellen des Connectors für durch IRM geschützte Bibliotheken unter SharePoint Server und durch IRM geschützte E-Mails für Exchange lokal
    
    Wenn Sie SharePoint und Exchange lokal verwenden und deren Funktionen zur Verwaltung von Informationsrechten (IRM) nutzen möchten, installieren und konfigurieren Sie den Rights Management-Connector. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](./deploy-rms-connector.md).

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>Schritt 6: Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten
Sie sind nun bereit, die Verwendung der von Ihnen konfigurierten Bezeichnungen in Ihrem Unternehmen zu überwachen und zu bestätigen, dass Sie sensible Informationen schützen. Weitere Informationen zur Unterstützung dieser Phase der Bereitstellung finden Sie unter:

- [Zentrale Berichterstellung für Azure Information Protection](reports-aip.md) (derzeit in der Vorschau)

- [Lokale Verwendungs Protokollierung mit Windows-Ereignis Monitor](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client) für den Azure Information Protection-Client (klassisch)

- [Protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md)

### <a name="step-7-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Schritt 7: Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto

Wenn Sie mit der Verwendung des Schutzdiensts beginnen, kann PowerShell nützlich sein, um administrative Änderungen skriptgestützt oder automatisiert durchzuführen. PowerShell kann ebenfalls für einige der erweiterten Konfigurationen erforderlich sein. 

Weitere Informationen finden Sie unter [Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](./administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Roadmap für die Bereitstellung zum ausschließlichen Schutz von Daten

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-the-protection-service-from-azure-information-protection"></a>Schritt 1: Bestätigen, dass Sie ein Abonnement besitzen, das den Schutzdienst von Azure Information Protection enthält

Überprüfen Sie anhand der Abonnementinformationen und der Featureliste auf der [Azure Information Protection-Preisseite](https://azure.microsoft.com/pricing/details/information-protection), ob Ihre Organisation über ein Abonnement verfügt, das diese Funktionen und Features umfasst. Weisen Sie anschließend jedem Benutzer in Ihrer Organisation, der Dokumente und E-Mails schützen soll, eine Lizenz aus diesem Abonnement zu.

Hinweis: Weisen Sie keine Benutzerlizenzen manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht zum Verwalten des Azure Rights Management-Diensts für Ihre Organisation. Für diese Lizenzen wird im Microsoft 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) **RIGHTSMANAGEMENT_ADHOC** angezeigt. Weitere Informationen dazu, wie das RMS for Individuals-Abonnement automatisch gewährt und Benutzern zugewiesen wird, finden Sie unter [RMS for Individuals und Azure Information Protection](./rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Schritt 2: Vorbereiten Ihres Mandanten für Azure Information Protection

Führen Sie die folgende Vorbereitungsschritte aus, bevor Sie mit der Verwendung des Schutzdiensts von Azure Information Protection beginnen:

1. Stellen Sie sicher, dass Ihr Office 365-Mandant die Benutzerkonten und -gruppen enthält, die Azure Information Protection zum Authentifizieren und Autorisieren von Benutzern in Ihrer Organisation verwendet. Falls erforderlich, erstellen Sie diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

2. Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

3. Installieren Sie das PowerShell-Modul für aipservice auf mindestens einem Computer, der über Internet Zugriff verfügt. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](./install-powershell.md).

4. Wenn Sie derzeit AD RMS verwenden: Führen Sie eine Migration durch, um die Schlüssel, Vorlagen und URLs in die Cloud zu verschieben. Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Stellen Sie sicher, dass der Schutzdienst aktiviert ist, damit Sie mit dem Schützen von Dokumenten und E-Mails beginnen können. Wenn eine Bereitstellung in Phasen erforderlich ist, konfigurieren Sie benutzerbezogene Steuerungsrichtlinien für die Einbindung (Onboarding), um die Möglichkeiten von Benutzern zum Anwenden von Schutz zu beschränken. Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](./activate-service.md).

Erwägen Sie optional die Konfigurierung folgender Funktionen:

- Benutzerdefinierte Vorlagen für die Schutzeinstellungen, wenn die Standardvorlagen für Ihre Organisation nicht ausreichend sind. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](./configure-policy-templates.md).

- Nutzungsprotokollierung, sodass Sie überwachen können, wie Ihre Organisation den Schutzdienst verwendet. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md).

### <a name="step-3-install-the-azure-information-protection-client-classic-and-configure-applications-and-services-for-rights-management"></a>Schritt 3: Installieren des Azure Information Protection-Clients (klassisch) und Konfigurieren von Anwendungen und Diensten für Rights Management

1. Bereitstellen des Azure Information Protection Clients (klassisch)
    
    Installieren Sie den klassischen Client für Benutzer, um Office 2010 zu unterstützen, um andere Dateien als Office-Dokumente und e-Mails zu schützen und geschützte Dokumente zu verfolgen. Bieten Sie Benutzerschulungen für diesen Client an. Weitere Informationen finden Sie unter [Azure Information Protection-Client für Windows](./rms-client/aip-client.md).

2. Konfigurieren von Office-Anwendungen und -Diensten
    
    Konfigurieren Sie die Office-Anwendungen und -Dienste für die IRM-Features (Information Rights Management) in SharePoint Online oder Exchange Online. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](./configure-applications.md).

3. Konfigurieren des Administratorfeatures für die Datenwiederherstellung
    
    Wenn vorhandene IT-Dienste von Azure Information Protection geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen – Data Leak Prevention, Gateways zur Inhaltsverschlüsselung (Content Encryption Gateways, CEG) und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](./configure-super-users.md).

4. Massenschützen vorhandener Dateien 
    
    Sie können PowerShell-Cmdlets verwenden, um mehrere Dateitypen massenzuschützen oder den Schutz aufzuheben. Weitere Informationen finden Sie im Administratorhandbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).
    
    Für Dateien auf Windows-basierten Dateiservern können Sie diese Cmdlets mit einem Skript und der Windows Server-Dateiklassifizierungsinfrastruktur verwenden. Weitere Informationen finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](./rms-client/configure-fci.md).

5. Bereitstellen des Connectors für lokale Server
    
    Wenn Sie über lokale Dienste verfügen, die Sie mit dem Schutzdienst verwenden möchten, installieren und konfigurieren Sie den Rights Management-Connector. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](./deploy-rms-connector.md).

### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Schritt 4: Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten

Sie können jetzt Ihre Daten schützen und die Nutzung des Schutzdiensts durch Ihre Organisation protokollieren. Weitere Informationen zur Unterstützung dieser Bereitstellungs Phase finden Sie unter unterstützen von [Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](./help-users.md) und [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md).

### <a name="step-5-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Schritt 5: Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto

Wenn Sie mit der Verwendung des Schutzdiensts beginnen, kann PowerShell nützlich sein, um administrative Änderungen skriptgestützt oder automatisiert durchzuführen. PowerShell kann ebenfalls für einige der erweiterten Konfigurationen erforderlich sein. 

Weitere Informationen finden Sie unter [Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](./administer-powershell.md).

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie Azure Information Protection bereitstellen, ist es möglicherweise hilfreich, die [häufig gestellten Fragen](faqs.md)und die Seite [Informationen und Support](information-support.md) für weitere Ressourcen zu überprüfen.