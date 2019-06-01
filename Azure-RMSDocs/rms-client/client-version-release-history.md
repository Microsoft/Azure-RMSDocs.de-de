---
title: Azure Information Protection-Client - Version-Verlauf und Support-Richtlinie
description: Erfahren Sie, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde, und erhalten Sie Informationen zum Support der Lifecycle-Richtlinie.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 05/31/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 201716f5d33b79223100d1751c555899aa5958ca
ms.sourcegitcommit: 9c0bc68fa036749e20aa67660d96278efbeb6a49
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448048"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Azure Information Protection-Client: Versionsveröffentlichungsverlauf und Supportrichtlinie

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Das Azure Information Protection-Team aktualisiert den Azure Information Protection-Client regelmäßig, um Korrekturen und neue Funktionen zu implementieren. 

Sie können das neueste allgemein verfügbare Release und die aktuelle Vorschauversion (sofern verfügbar) im [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. 

Nach einer kurzen Verzögerung von in der Regel ein paar Wochen, ist die neueste allgemein verfügbare Version auch im Microsoft Update-Katalogs mit dem Produktnamen enthalten **Microsoft Azure Information Protection**  >  **Microsoft Azure Information Protection-Client**, und die Klassifizierung der **Updates**. Diese Aufnahme in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Softwarebereitstellungsmechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [Upgraden und Verwalten des Azure Information Protection-Clients](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

> [!TIP]
> Verwendung von unified Azure Information Protection bezeichnungs-Client, da Ihre Bezeichnungen von der Office 365 Security & Compliance Center, Microsoft 365-Security-Center oder Microsoft 365 Compliance Center veröffentlicht werden? Wenn Sie herunterladen und Sie dann die einheitlichen bezeichnungs-Client aus dem Microsoft Download Center installieren, können Sie Ihren Azure Information Protection-Client aktualisieren, zu diesem [einheitliche bezeichnungs Client](unifiedlabelingclient-version-release-history.md).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version des Azure Information Protection-Clients mit allgemeiner Verfügbarkeit wird bis zu sechs Monate nach dem Release der nächsten Version mit allgemeiner Verfügbarkeit unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

### <a name="release-history"></a>Verlauf der Releases

Im Folgenden wird erläutert, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. 

> [!NOTE]
> Kleinere Korrekturen werden nicht aufgelistet. Wenn also ein Problem mit dem Azure Information Protection-Client auftreten sollte, wird empfohlen, dass Sie zuerst überprüfen, ob dieses Problem mit dem neusten allgemein verfügbaren Release behoben wird. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (sofern verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

## <a name="version-1482040"></a>Version 1.48.204.0

**Veröffentlicht**: 04/16/2019

Diese Version umfasst die MSIPC-Version 1.0.3592.627 des RMS-Clients.

**Neue Funktionen:**

- Der Azure Information Protection-Scanner ist jetzt im Azure-Portal und nicht mithilfe von PowerShell konfiguriert werden.
    
    Wenn Sie eine allgemein verfügbare Version des Scanner upgraden, unterscheidet sich der Upgradevorgang von früheren Versionen. Informationen hierzu finden Sie unter [Upgrade der Azure Information Protection-Überprüfung](client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

- Die Überprüfung unterstützt nun mehrere Konfigurationsdatenbanken auf derselben SQL Server-Instanz ein, wenn Sie einen Profilnamen ein angeben.

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

- Neue erweiterte Clienteinstellungen, die Popupmeldungen in Outlook implementieren, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben. [Weitere Informationen](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
    
    Beachten Sie, dass wenn Sie die erweiterten Clients-Eigenschaft für die Vorschauversion der OutlookCollaborationTrustedDomains konfiguriert haben, wird diese Einstellung jetzt durch drei neue Einstellungen ersetzt, damit Domänen pro Aktion ausgeschlossen werden können: OutlookWarnTrustedDomains OutlookJustifyTrustedDomains und OutlookBlockTrustedDomains.

- Wenn Sie Dateien mit dem Cmdlet [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel) bezeichnen und schützen, können Sie den Parameter *EnableTracking* verwenden, um die Dateien bei der Website zur Dokumentnachverfolgung zu registrieren. [Weitere Informationen](client-admin-guide-document-tracking.md#using-powershell-to-register-labeled-documents-with-the-document-tracking-site)

- Neue erweiterte Clienteinstellung, die nur angewendet wird, wenn Sie die Richtlinieneinstellung so konfigurieren, dass keine benutzerdefinierten Berechtigungen angezeigt werden: Wenn es eine Datei gibt, die mit benutzerdefinierten Berechtigungen geschützt wurde, blenden Sie die Option „Benutzerdefinierte Berechtigungen“ im Dateiexplorer ein, sodass Benutzer diese sehen und ändern können (wenn diese die Berechtigungen haben, um Schutzeinstellungen ändern zu können). [Weitere Informationen](client-admin-guide-customizations.md#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer)

- Ermittlung von Dienstendpunkten für [Analytics für Azure Information Protection](../reports-aip.md).
    
- Zwei neue erweiterte Client-Einstellungen für die Analyse, für die folgenden Szenarien:
    
    - Verhindert das Senden von Übereinstimmungen zwischen Informationstypen für eine Teilmenge von Benutzern, wenn Sie das Kontrollkästchen zum Sammeln von Übereinstimmungen zwischen Inhalten im Azure-Portal aktiviert haben. [Weitere Informationen](client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users)
    - Für die **Datenermittlung** melden, zeigt an, ob Dateien vertrauliche Informationen enthalten. [Weitere Informationen](client-admin-guide-customizations.md#enable-azure-information-protection-analytics-to-discover-sensitive-information-in-documents)

**Fixes**:

- In Pfaden und Dateinamen werden in der Azure Information Protection-Analyse anstelle von Nicht-ASCII-Zeichen keine Fragezeichen ( **?** ) angezeigt, wenn das Gebietsschema des Ausgangsbetriebssystems Englisch ist.

- Neue optische Kennzeichnungen werden konsistent angewendet, wenn ein Benutzer einem Word-Dokument neue Abschnitte hinzufügt und das Dokument anschließend mit einer neuen Bezeichnung versieht.

- Der Azure Information Protection-Client entfernt den Schutz ordnungsgemäß von einem PDF-Dokument, das durch die Rights Management-Freigabeanwendung geschützt wurde.

- Untergeordnete Bezeichnungen werden von PowerShell und vom Scanner ordnungsgemäß angewendet, wenn die übergeordnete Bezeichnung für benutzerdefinierte Berechtigungen konfiguriert wurde.

- Vom Azure Information Protection-Client werden Bezeichnungen ordnungsgemäß angezeigt, die von [Clients angewendet wurden, die einheitliche Bezeichnungen unterstützen](../configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

- Dokumente werden in Office ordnungsgemäß ohne Wiederherstellungsmeldung geöffnet, nachdem der Schutz durch Datei-Explorer entfernt und mit der rechten Maustaste auf PowerShell oder den Scanner geklickt wurde.

- Wenn Sie die erweiterte Clienteinstellung verwenden, um eine [Standardbezeichnung für Outlook](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) festzulegen, können Sie eine übergeordnete Bezeichnung anwenden, die Unterbezeichnungen hat, wenn alle diese Unterbezeichnungen für den Benutzer deaktiviert sind.

- Wenn Sie die [Richtlinieneinstellung](../configure-policy-settings.md) **Wenden Sie für E-Mails mit Anlagen eine Bezeichnung an, die der höchsten Klassifizierung dieser Anlagen entspricht.** verwenden und die Bezeichnung mit der höchsten Klassifizierung für benutzerdefinierte Berechtigungen konfiguriert ist, war das Ergebnis bisher, dass die Bezeichnung auf die E-Mail angewendet wurde, der Schutz jedoch nicht. Jetzt:
    - Wenn die benutzerdefinierten Berechtigungen einer Bezeichnung Outlook einschließen (Nicht weiterleiten): Die Bezeichnung und ihr „Nicht weiterleiten“-Schutz werden auf die E-Mail angewendet.
    - Wenn die benutzerdefinierten Berechtigungen einer Bezeichnung nur für Word, Excel, PowerPoint und den Dateiexplorer gelten: Die Bezeichnung wird nicht angewendet, und für die E-Mail wird kein Schutz angewendet.

**Weitere Änderungen**:

- Die folgenden Typen für vertrauliche Informationen sind [nicht mehr unterstützt](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) für Bezeichnungen, die Sie konfigurieren, empfohlen oder automatische Klassifizierung:
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

- Die [Richtlinieneinstellung](../configure-policy-settings.md) **Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung festlegen, eine Bezeichnung oder den Schutz entfernen möchten** gilt für den Scanner nicht mehr. Vom Scanner werden diese Aktionen durchgeführt, wenn Sie die Einstellung **Dateien neu bezeichnen** im Scannerprofil mit **Ein** konfigurieren.

## <a name="version-141510"></a>Version 1.41.51.0

**Veröffentlicht**: 27.11.2018

Diese Version umfasst die MSIPC-Version 1.0.3592.627 des RMS-Clients.

**Neue Funktionen:**

- Der Azure Information Protection-Client schützt jetzt standardmäßig PDF-Dateien mit dem ISO-Standard für die Verschlüsselung von PDF-Datei. Bisher mussten Sie diese Unterstützung mit einer erweiterten Clienteinstellung aktivieren.
    
    Wenn Sie möchten, dass der Client zum Schutz von PDF-Dateien mit der .ppdf-Erweiterung zurückkehrt, verwenden Sie die gleiche [erweiterte Clienteinstellung](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption), aber geben Sie **False** an.

- Unterstützung der Überwachung [zentralen reporting](../reports-aip.md) mithilfe von Azure Information Protection-Analyse, die auf der Microsoft Ignite 2018 angekündigt.

- Excel unterstützt jetzt auch [optische Kennzeichnungen](../configure-policy-markings.md) in unterschiedlichen Farben.

- Bei vorhandenen S/MIME-Bereitstellungen eine neue erweiterte Clienteinstellung zum Konfigurieren einer Bezeichnung zum automatischen Anwenden des S/MIME-Schutzes in Outlook. [Weitere Informationen](client-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)

- Eine neue erweiterte Clienteinstellung als Alternative zum Bearbeiten der Registrierung, um Anmeldeaufforderungen für den Azure Information Protection-Dienst für [getrennte Computer](client-admin-guide-customizations.md#support-for-disconnected-computers) zu verhindern.

- Eine neue erweiterte Clienteinstellung zur [Unterstützung der Reihenfolge der untergeordneten Bezeichnungen](client-admin-guide-customizations.md#enable-order-support-for-sublabels-on-attachments) bei Verwendung der folgenden Richtlinieneinstellung:
    - **Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht**

**Fixes**:

- Der Azure Information Protection-Client schließt die Dateinamenerweiterungen ZIP, RAR und MSG nicht mehr für den Datei-Explorer (Rechtsklick) und PowerShell-Befehle aus. Diese Erweiterungen bleiben jedoch in der Standardeinstellung für die Überprüfung ausgeschlossen. 

- Der Azure Information Protection-Client kann den Schutz mehrerer Dateien (Mehrfachauswahl und ein Ordner mit geschützten Dateien) mit Rechtsklick aufheben, wenn Sie den Datei-Explorer verwenden.

- Für Excel:
    
    - Optische Kennzeichnungen werden jetzt angewendet, wenn Sie das Arbeitsblatt während der Bearbeitung einer Zelle speichern.
    
    - Excel 2010: Wenn ein Arbeitsblatt mithilfe der Mitautor-[Berechtigungsebene](../configure-usage-rights.md#rights-included-in-permissions-levels) geschützt ist, ist die Schaltfläche **Bezeichnung löschen** jetzt verfügbar, wenn Sie mit der rechten Maustaste auf die Datei klicken und **Klassifizieren und schützen** auswählen.

- Die erweiterten Clienteinstellungen, die [Kopf- und Fußzeilen aus anderen Bezeichnungslösungen entfernen](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions) können, unterstützen jetzt benutzerdefinierte Layouts.

**Weitere Änderungen**:

- Wenn die Überprüfung des Zeitplans auf **Immer** festgelegt ist, entsteht jetzt eine Verzögerung von 30 Sekunden zwischen Überprüfungen.

- Die Überprüfung ändert den Rights Management-Besitzer nicht mehr für Dateien, die er bezeichnet, wenn die Datei bereits geschützt ist.

## <a name="version-137190"></a>Version 1.37.19.0

**Veröffentlicht**: 17.9.2018

Diese Version umfasst die MSIPC-Version 1.0.3592.627 des RMS-Clients.

**Neue Features**: 

- Unterstützung des ISO-Standards für die PDF-Verschlüsselung durch Konfiguration einer neuen [erweiterten Clientkonfiguration](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Wenn diese Option auf **True** gesetzt wird, behalten PDF-Dokumente, die Sie schützen, ihre Erweiterung bei (anstelle einer Änderung in PPDF) und können von PDF-Readern geöffnet werden, die diesen ISO-Standard unterstützen. Derzeit müssen Sie Benutzer anweisen, diese geschützten PDF-Dateien manuell über den Azure Information Protection-Viewer zu öffnen. Damit Benutzern dabei zur Seite zu stehen, wird beim Öffnen dieser geschützten Dateien eine Seite mit Symbolen angezeigt, aus denen Sie ihr Betriebssystem auswählen können.

- Unterstützung neuer Typen vertraulicher Informationen, die beim Klassifizieren von Dokumenten helfen, die personenbezogene Informationen enthalten. [Weitere Informationen](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) 

- Bezeichnungen, die Schutz anwenden, werden jetzt in Office 365-Apps von Office 365 Business oder Microsoft 365 Business angezeigt, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.

- Unterstützung von Bezeichnungen für das Dokumentformat **Strict Open XML** in Word-, Excel- und PowerPoint- Dateien. Weitere Informationen zu den Open XML-Formaten finden Sie im Office-Blogbeitrag [New file format options in the new Office (Neue Dateiformate in der neuen Version von Office)](https://www.microsoft.com/en-us/microsoft-365/blog/2012/08/13/new-file-format-options-in-the-new-office/). 

- Unterstützung für Dateien, die von Secure Islands geschützt werden, wenn diese Dateien keine PDF- oder Office-Dokumente sind. Zum Beispiel geschützte Text- und Bilddateien oder Dateien mit der Erweiterung PFILE. Diese Unterstützung ermöglicht neue Szenarios, z.B. dass die Azure Information Protection-Überprüfung diese Dateien auf vertrauliche Informationen prüfen kann und diesen automatisch Bezeichnungen für Azure Information Protection hinzufügt. [Weitere Informationen](client-admin-guide-customizations.md#support-for-files-protected-by-secure-islands)

- Neue erweiterte Clienteinstellungen zum Entfernen von Kopf- und Fußzeilen, die von anderen Bezeichnungslösungen auf Dokumente angewendet wurden. [Weitere Informationen](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)

- Für die Azure Information Protection-Überprüfung:

    - Neues Cmdlet, [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner): Muss nach dem Upgrade von der aktuellen allgemein verfügbaren Version (1.29.5.0) oder früher einmalig ausgeführt werden.
    
    - Neues Cmdlet, [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus): Ruft den aktuellen Status des Diensts für die Überprüfung ab.  
    
    - Neues Cmdlet, [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan): Weist die Überprüfung an, einen einmaligen Überprüfungszyklus zu starten, wenn der Zeitplan auf „manuell“ festgelegt ist.
    
    - PDF-Dokumente sind nun standardmäßig geschützt, wenn Sie den ISO-Standard für die PDF-Verschlüsselung verwenden.
    
    - SharePoint Server 2010 wird für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.
    
- Unterstützung für das neue Blatt **Azure Information Protection – Knoten (Vorschau)** im Azure-Portal, mit dem Sie die Überprüfung von einer zentralen Stelle aus verwalten können. Die Informationen von den bereitgestellten Überprüfungen, die mit Azure verbunden sind, werden alle fünf Minuten aktualisiert. Auf diesem Blatt können Sie eine einmalige Überprüfung starten, alle Dateien erneut überprüfen, den Status einer Überprüfung prüfen und die Überprüfungsgeschwindigkeit anzeigen.

**Fehlerbehebungen**

- Für die Azure Information Protection-Überprüfung:
    
    - Bei Dokumenten, die in SharePoint-Bibliotheken geschützt werden, wenn der Parameter *DefaultOwner* nicht für das Datenrepository verwendet wird, wird nun der Wert des SharePoint-Editors anstelle des Autorenwerts als Standardwert verwendet.
    
    - Die Überprüfungsberichte enthalten nun „Zuletzt geändert von“ für Office-Dokumente.
    
    - Sie können nun beim Bearbeiten der Registrierung alle Dateitypen mit dem Platzhalter `*` schützen, wie im Abschnitt [Bearbeiten der Registrierung für die Überprüfung](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) beschrieben.

- Das Anzeigen von E-Mails mithilfe der Pfeilsymbole „Nächstes Element“ und „Vorheriges Element“ auf der Symbolleiste für den Schnellzugriff zeigt nun die richtige Bezeichnung für die jeweilige E-Mail an.

- Wenn Sie PowerShell, den Datei-Explorer oder die Überprüfung zum Klassifizieren oder Schützen verwenden, werden die Metadaten des Office-Dokuments weder entfernt noch verschlüsselt.

- Benutzerdefinierte Berechtigungen unterstützen nun Empfänger-E-Mail-Adressen, die einen Apostroph enthalten.

- Die Computerumgebung wird erfolgreich gestartet (Bootstrap), wenn diese Aktion durch Öffnen eines geschützten Dokuments gestartet wird, das in SharePoint Online gespeichert ist.

- Wenn Sie den Client für den Rechtsklick auf den Datei-Explorer, PowerShell oder den Scanner verwenden, wird die Bezeichnung für Dateien in WebDav-Positionen blockiert, da es sich hierbei um ein nicht unterstütztes Szenario handelt.

- Das Symbol zum Löschen einer Bezeichnung wird in Client-Apps nicht angezeigt (Word, Excel, PowerPoint und Outlook), wenn Sie die [Richtlinieneinstellung](../configure-policy-settings.md) der Option **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen über eine Bezeichnung verfügen) konfigurieren.

**Weitere Änderungen**:

- Bei [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration):
    
    - **OneTime**, **Continuous** und **Never** (Einmalig, Fortlaufend und Nie) sind nicht mehr Werte für den Parameter *Schedule*. Stattdessen gibt es nun die Werte **Manual** (Manuell) und **Always** (Immer).
        
    - Der Parameter *Type* wurde entfernt, d.h. er wurde auch aus der Ausgabe entfernt, wenn Sie [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration) ausführen. Standardmäßig werden nach dem ersten Überprüfungszyklus nur neue oder geänderte Dateien untersucht. Wenn Sie zuvor für den *Typ*-Parameter **Vollständig** festgelegt haben, um alle Dateien erneut zu überprüfen, führen Sie nun [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan) mit dem *Zurücksetzen*-Parameter aus. Die Überprüfung muss auch für einen manuellen Zeitplan konfiguriert sein, was voraussetzt, dass für den *Zeitplan*-Parameter mit [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) die Option **Manuell** festgelegt wird.
    
- Die Standardausschlussliste des Clients und der Überprüfung umfasst nun MSG-, RAR- und ZIP-Dateien. Die Überprüfung schließt auch RTF-Dateien aus. [Weitere Informationen](client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)

- Die Richtlinienversion wurde in 1.4 geändert. Das Identifizieren der Versionsnummer ist zum [Konfigurieren nicht verbundener Computer](client-admin-guide-customizations.md#support-for-disconnected-computers) erforderlich.

- Der Link **Feedback senden** im Dialogfeld **Hilfe und Feedback** wurde entfernt. Er wurde temporär ersetzt durch die Option **Problem melden**, mit der standardmäßig eine E-Mail an Microsoft gesendet wurde. Seit Dezember 2018 wird die Option **Problem melden** nicht mehr standardmäßig angezeigt. Sie kann aber mit einer [erweiterten Clienteinstellung](client-admin-guide-customizations.md#add-report-an-issue-for-users), in der Sie eine HTTP-Zeichenfolge für den Link angeben, hinzugefügt werden. Beispiele dafür sind eine benutzerdefinierte Webseite, über die Benutzer Probleme melden, oder eine E-Mail-Adresse, die E-Mails an Ihren Helpdesk weiterleitet. 


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren und Verwenden des Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)
