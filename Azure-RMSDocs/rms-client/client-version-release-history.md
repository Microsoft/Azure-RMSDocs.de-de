---
title: Azure Information Protection von Client Versionsverlauf & Unterstützungs Richtlinie
description: Erfahren Sie, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde, und erhalten Sie Informationen zum Support der Lifecycle-Richtlinie.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/05/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v1client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e9fc95f47273b6d604ba6a1151106ae64298fce0
ms.sourcegitcommit: 3b50727cb50a612b12f248a5d18b00175aa775f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75743639"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Der Azure Information Protection-Client: Verlauf der Releases und Supportrichtlinie


>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*



Sie können das neueste allgemein verfügbare Release und die aktuelle Vorschauversion (sofern verfügbar) im [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. 

Nach einer kurzen Verzögerung von in der Regel einige Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog mit dem Produktnamen **Microsoft Azure Information Protection** > **Microsoft Azure Information Protection Client**und der Klassifizierung der **Updates**enthalten. Diese Aufnahme in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Softwarebereitstellungsmechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [Upgraden und Verwalten des Azure Information Protection-Clients](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

> [!TIP]
> Sie sind daran interessiert, den Azure Information Protection Unified Label-Client zu verwenden, da ihre Bezeichnungen aus Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center veröffentlicht werden? Wenn Sie den Unified-Bezeichnungs Client aus dem Microsoft Download Center herunterladen und anschließend installieren, können Sie das Upgrade Ihres Azure Information Protection-Clients auf den Unified-Bezeichnungs [Client](unifiedlabelingclient-version-release-history.md)durchführen.

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version des Azure Information Protection-Clients mit allgemeiner Verfügbarkeit wird bis zu sechs Monate nach dem Release der nächsten Version mit allgemeiner Verfügbarkeit unterstützt. Mit Ausnahme dieses Abschnitts enthält die Dokumentation keine Informationen zu nicht unterstützten Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

##### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden:

|Clientversion|Datum der Veröffentlichung|
|--------------|-------------|
|1.41.51.0|27.11.2018|
|1.37.19.0|17.9.2018|
|1.29.5.0|26.6.2018|
|1.27.48.0|30.5.2018|
|1.26.6.0|04/17/2018|
|1.10.56.0|09/18/2017|
|1.7.210.0|06/06/2017|
|1.4.21.0|15.03.2017|
|1.3.155.2|02/08/2017|
|1.2.4.0.0|27.10.2016|
|1.1.23.0|10/01/2016|

Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

Ab 6/2/2019 ist für den Bezeichnungs Dienst für Azure Information Protection Verbindungen erforderlich, die TLS 1,2 verwenden.

Alle Client Versionen von 1.4.21.0 veröffentlicht 03/15/2017 unterstützen TLS 1,2. Client Versionen **1.3.155.2**, **1.2.4.0**und **1.1.23.0** verwenden nicht TLS 1,2 und können daher die Azure Information Protection Richtlinie nicht mehr herunterladen.

### <a name="release-history"></a>Verlauf der Releases

Im Folgenden wird erläutert, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt.

> [!NOTE]
> Kleinere Korrekturen werden nicht aufgelistet. Wenn also ein Problem mit dem Azure Information Protection-Client auftreten sollte, wird empfohlen, dass Sie zuerst überprüfen, ob dieses Problem mit dem neusten allgemein verfügbaren Release behoben wird. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.


## <a name="version-154330"></a>Version 1.54.33.0

**Veröffentlicht**: 10/23/2019

Diese Version umfasst die msipc-Version 1.0.4008.0813 des RMS-Clients.

Diese Version enthält allgemeine Korrekturen für Stabilität und Leistung.

## <a name="version-153100"></a>Version 1.53.10.0

**Veröffentlicht**: 07/15/2019

Unterstützt durch 04/23/2020

Diese Version umfasst die msipc-Version 1.0.3889.0419 des RMS-Clients.

**Neue Funktionen:**

- Neue erweiterte Client Einstellung zum Ausschließen von Outlook-Nachrichten aus der Richtlinien Einstellung **alle Dokumente und e-Mails müssen eine Bezeichnung aufweisen**. [Weitere Informationen](client-admin-guide-customizations.md#exempt-outlook-messages-from-mandatory-labeling)

- Neue erweiterte Client Einstellung zur weiteren Anpassung der Einstellungen, mit denen Popup Meldungen in Outlook implementiert werden, die gesendete e-Mails warnen, rechtfertigen oder blockieren. Mit dieser neuen erweiterten Einstellung können Sie eine andere Aktion für e-Mail-Nachrichten ohne Anlagen festlegen. [Weitere Informationen](client-admin-guide-customizations.md#to-specify-a-different-action-for-email-messages-without-attachments)

**Fixes**:

- Wenn Sie den Datei-Explorer verwenden, klicken Sie mit der rechten Maustaste auf die Bezeichnung einer Datei, für die der Schutz unabhängig von einer Bezeichnung angewendet wurde. dieser Schutz wird beibehalten. Ein Benutzer hat z. b. benutzerdefinierte Berechtigungen auf eine Datei angewendet.

- Wenn Sie die Option "nicht weiterleiten" in einem e-Mail-Thread durch eine Bezeichnung ersetzen, die für benutzerdefinierte Berechtigungen konfiguriert ist und nicht weiterleiten, können die ursprünglichen Empfänger die e-Mail-Nachricht weiterhin öffnen.

- Im folgenden Szenario wird ein Benutzer in der QuickInfo-QuickInfo nicht mehr angezeigt, dass die Bezeichnung automatisch von Ihnen festgelegt wurde: ein Benutzer erhält eine geschützte e-Mail mit einem angefügten Dokument, das nicht gekennzeichnet ist, aber automatisch geschützt wird. Wenn der Benutzer aus derselben Organisation wie der Absender das Dokument öffnet, wird die entsprechende Bezeichnung für die Schutzeinstellungen auf das Dokument angewendet.

- Das minimale [Nutzungsrecht](../configure-usage-rights.md#usage-rights-and-descriptions) zum Ausführen des Cmdlets " [Unprotect-rmsfile](/powershell/module/azureinformationprotection/unprotect-rmsfile) " lautet jetzt " **Speichern unter", "Exportieren** (exportieren)" und nicht " **Kopieren** " (extrahieren).

## <a name="version-1482040"></a>Version 1.48.204.0

**Veröffentlicht**: 04/16/2019

Unterstützt durch 01/15/2020

Diese Version umfasst die MSIPC-Version 1.0.3592.627 des RMS-Clients.

**Neue Funktionen:**

- Der Azure Information Protection Scanner wird jetzt über die Azure-Portal konfiguriert, nicht mithilfe von PowerShell.
    
    Wenn Sie eine allgemein verfügbare Version des Scanner upgraden, unterscheidet sich der Upgradevorgang von früheren Versionen. Informationen hierzu finden Sie unter [Upgrade der Azure Information Protection-Überprüfung](client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

- Der Scanner unterstützt jetzt mehrere Konfigurations Datenbanken auf derselben SQL Server-Instanz, wenn Sie einen Profilnamen angeben.

- Unterstützung für die folgenden Typen vertraulicher Informationen, mit deren Hilfe Anmeldeinformationen in Dokumenten und E-Mails erkannt werden:
    - Azure Service Bus-Verbindungszeichenfolge
    - Azure IoT Verbindungszeichenfolge
    - Azure Storage-Konto
    - Azure IAAS-Datenbankverbindungszeichenfolge und Azure SQL-Verbindungszeichenfolge
    - Azure Redis Cache-Verbindungszeichenfolge
    - Azure SAS
    - SQL Server-Verbindungszeichenfolge
    - Azure DocumentDB-Authentifizierungsschlüssel
    - Kennwort für Azure-Veröffentlichungseinstellungen
    - Schlüssel für Azure Storage-Konto (allgemein)

- Unterstützung der Endpunkt Ermittlung für [Azure Information Protection Analytics](../reports-aip.md), um vertrauliche Informationen zu melden, die beim ersten Speichern eines Office-Dokuments (mithilfe von Desktop-Apps für Word, Excel und PowerPoint) gefunden wurden:
    - Um diese Informationen zu ermitteln, müssen die Dokumente nicht beschriftet werden.
    - Vertrauliche Informationen werden durch vordefinierte und benutzerdefinierte Informationstypen identifiziert.
    - Wenn Sie nicht möchten, dass die Typen der sensiblen Informationen an Azure Information Protection Analytics gesendet werden, können Sie die Endpunkt Ermittlung mit einer [erweiterten Client Einstellung](client-admin-guide-customizations.md#disable-sending-discovered-sensitive-information-in-documents-to-azure-information-protection-analytics)deaktivieren.

- Neue erweiterte Clienteinstellungen, die Popupmeldungen in Outlook implementieren, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben. [Weitere Informationen](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
    
    Beachten Sie Folgendes: Wenn Sie die Eigenschaft "Erweiterter Client" von "outlookcollaborationtreuddomains" für die Vorschauversion konfiguriert haben, wird diese Einstellung nun durch drei neue Einstellungen ersetzt, sodass Domänen pro Aktion ausgenommen werden können: outlookwarntreuhänddomains, Outlookjustifytreuhänddomains und outlookblocktreuhänddomains.

- Wenn Sie Dateien mit dem Cmdlet [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel) bezeichnen und schützen, können Sie den Parameter *EnableTracking* verwenden, um die Dateien bei der Website zur Dokumentnachverfolgung zu registrieren. [Weitere Informationen](client-admin-guide-document-tracking.md#using-powershell-to-register-labeled-documents-with-the-document-tracking-site)

- Eine neue erweiterte Client Einstellung für [Azure Information Protection Analytics](../reports-aip.md), um das Senden von Informationstypen Übereinstimmungen für eine Teilmenge von Benutzern zu verhindern, wenn Sie das Kontrollkästchen im Azure-Portal aktiviert haben, das eine tiefere Analyse Ihrer sensiblen Daten ermöglicht. Diese Einstellung gilt für den Client und den Scanner. [Weitere Informationen](client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users)

- Neue erweiterte Client Einstellung, die nur anwendbar ist, wenn Sie die Richtlinien Einstellung so konfigurieren, dass benutzerdefinierte Berechtigungen nicht angezeigt werden: Wenn eine Datei vorhanden ist, die mit benutzerdefinierten Berechtigungen geschützt ist, können Sie die Option benutzerdefinierte Berechtigungen im Datei-Explorer anzeigen, damit Benutzer Folgendes sehen: und ändern Sie diese (wenn Sie über Berechtigungen zum Ändern der Schutzeinstellungen verfügen). [Weitere Informationen](client-admin-guide-customizations.md#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer)


**Fixes**:

- In Pfaden und Dateinamen werden in der Azure Information Protection-Analyse anstelle von Nicht-ASCII-Zeichen keine Fragezeichen ( **?** ) angezeigt, wenn das Gebietsschema des Ausgangsbetriebssystems Englisch ist.

- Neue optische Kennzeichnungen werden konsistent angewendet, wenn ein Benutzer einem Word-Dokument neue Abschnitte hinzufügt und das Dokument anschließend mit einer neuen Bezeichnung versieht.

- Der Azure Information Protection-Client entfernt den Schutz ordnungsgemäß von einem PDF-Dokument, das durch die Rights Management-Freigabeanwendung geschützt wurde.

- Untergeordnete Bezeichnungen werden von PowerShell und vom Scanner ordnungsgemäß angewendet, wenn die übergeordnete Bezeichnung für benutzerdefinierte Berechtigungen konfiguriert wurde.

- Vom Azure Information Protection-Client werden Bezeichnungen ordnungsgemäß angezeigt, die von [Clients angewendet wurden, die einheitliche Bezeichnungen unterstützen](../configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

- Dokumente werden in Office ordnungsgemäß ohne Wiederherstellungsmeldung geöffnet, nachdem der Schutz durch Datei-Explorer entfernt und mit der rechten Maustaste auf PowerShell oder den Scanner geklickt wurde.

- Wenn Sie die erweiterte Clienteinstellung verwenden, um eine [Standardbezeichnung für Outlook](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) festzulegen, können Sie eine übergeordnete Bezeichnung anwenden, die Unterbezeichnungen hat, wenn alle diese Unterbezeichnungen für den Benutzer deaktiviert sind.

- Wenn Sie die [Richtlinien Einstellung](../configure-policy-settings.md) **für e-Mail-Nachrichten mit Anlagen verwenden, wenden Sie eine Bezeichnung an, die der höchsten Klassifizierung dieser Anlagen entspricht** , und die Bezeichnung mit der höchsten Klassifizierung ist für benutzerdefinierte Berechtigungen konfiguriert. das Ergebnis war zuvor, dass die Bezeichnung auf die e-Mail angewendet wurde, der Schutz jedoch nicht war. Jetzt:
    - Wenn die benutzerdefinierten Berechtigungen der Bezeichnung Outlook einschließen (nicht weiterleiten): wenden Sie diese Bezeichnung und deren nicht weiterleiten-Schutz auf die e-Mail an.
    - Wenn die benutzerdefinierten Berechtigungen der Bezeichnung nur für Word, Excel, PowerPoint und den Datei-Explorer gelten: wenden Sie die Bezeichnung nicht an, und wenden Sie keinen Schutz auf die e-Mail an.

**Weitere Änderungen**:

- Die folgenden sensiblen Informationstypen werden [nicht mehr für Bezeichnungen unterstützt](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) , die Sie für die empfohlene oder automatische Klassifizierung konfigurieren:
    - EU Phone Number (EU-Telefonnummer)
    - EU GPS Coordinates (EU-GPS-Koordinaten)

- Da der Azure Information Protections-Scanner über das Azure-Portal konfiguriert wird, sind die folgenden Cmdlets inzwischen veraltet und können nicht zum Konfigurieren von Datenrepositorys oder der Dateitypenliste verwendet werden:
    - Add-AIPScannerRepository
    - Add-AIPScannerScannedFileTypes
    - Get-AIPScannerRepository
    - Remove-AIPScannerRepository
    - Remove-AIPScannerScannedFileTypes
    - Set-AIPScannerRepository
    - Set-AIPScannerScannedFileTypes

- Ein neues PowerShell-Cmdlet [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) für Szenarios, in denen der Azure Information Protection-Scanner die entsprechende Konfiguration vom Azure-Portal nicht herunterladen kann.

- Vom Azure Information Protection-Scanner werden ZIP-Dateien nicht mehr standardmäßig ausgeschlossen. Informationen zum Überprüfen und Bezeichnen von ZIP-Dateien finden Sie im Abschnitt [Überprüfen von ZIP-Dateien](client-admin-guide-file-types.md#to-inspect-zip-files) des Administratorhandbuchs.

- Die [Richtlinien Einstellung](../configure-policy-settings.md) **Benutzer müssen eine Begründung angeben, um eine niedrigere Klassifizierungs Bezeichnung festzulegen, eine Bezeichnung zu entfernen oder den Schutz zu entfernen** , gilt nicht mehr für den Scanner. Die Überprüfung führt diese Aktionen aus, wenn Sie die Einstellung neu bezeichnen **von** **Dateien** im Überprüfungs Profil auf ein festlegen, und aktivieren Sie dann das Kontrollkästchen Herabstufung der **Bezeichnung zulassen** .

## <a name="next-steps"></a>Nächste Schritte

Nicht sicher, ob dies der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen des zu verwendenden Kunden für Windows-Computer](use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

Weitere Informationen zum Installieren und Verwenden des Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)
