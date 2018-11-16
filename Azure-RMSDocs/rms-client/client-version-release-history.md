---
title: 'Der Azure Information Protection-Client: Versionsgeschichte und Supportrichtlinie'
description: Erfahren Sie, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde, und erhalten Sie Informationen zum Support der Lifecycle-Richtlinie.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d4b9419ee12dfef0db29604dc7a396eedd7225fc
ms.sourcegitcommit: a547dee247e4961e8f7c1f08e39b03dff710a74c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51628070"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Der Azure Information Protection-Client: Verlauf der Releases und Supportrichtlinie

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Das Azure Information Protection-Team aktualisiert den Azure Information Protection-Client regelmäßig, um Korrekturen und neue Funktionen zu implementieren. 

Sie können das neueste allgemein verfügbare Release und die aktuelle Vorschauversion (sofern verfügbar) im [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. Die allgemein verfügbare Version ist außerdem im Microsoft Update-Katalog (Kategorie: **Azure Information Protection**) enthalten, sodass Sie ein Upgrade des Client über WSUS, den Konfigurationsmanager oder andere Mechanismen zur Bereitstellung von Software durchführen können, die Microsoft Update verwenden.

Weitere Informationen finden Sie unter [Upgraden und Verwalten des Azure Information Protection-Clients](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version des Azure Information Protection-Clients mit allgemeiner Verfügbarkeit wird bis zu sechs Monate nach dem Release der nächsten Version mit allgemeiner Verfügbarkeit unterstützt. Nicht unterstützte Versionen des Clients sind nicht auf dieser Seite enthalten. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

### <a name="release-history"></a>Verlauf der Releases

Im Folgenden wird erläutert, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. 

> [!NOTE]
> Kleinere Korrekturen werden nicht aufgelistet. Wenn also ein Problem mit dem Azure Information Protection-Client auftreten sollte, wird empfohlen, dass Sie zuerst überprüfen, ob dieses Problem mit dem neusten allgemein verfügbaren Release behoben wird. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion.
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

## <a name="versions-later-than-137190"></a>Versionen ab 1.37.19.0

Wenn Ihre Clientversion höher als 1 ist, handelt es sich um eine Vorschauversion für Test- und Evaluierungszwecke. 

> [!TIP]
> Sind würden den Azure Information Protection-Client für einheitliche Bezeichnungen gerne bewerten, da Ihre Bezeichnungen vom Office 365 Security & Compliance Center veröffentlicht werden? Hier finden Sie weitere Informationen dazu: [Azure Information Protection-Client für einheitliche Bezeichnungen: Informationen zum Release](unifiedlabelingclient-version-release-history.md).

**Veröffentlicht**: 20.9.2018

**Neue Funktionen:**

- Unterstützung für die [zentrale Berichterstellung](../reports-aip.md) für die auf der Microsoft Ignite angekündigte Azure Information Protection-Analysefunktion

**Zusätzliche Informationen:**

Nur für diese Vorschauversion, speziell für die Überprüfung:

- Installationsschritte für die Überprüfung:
    
    1. Installieren Sie die aktuelle GA-Version (1.37.19.0) des Clients.
    2. Installieren und konfigurieren Sie die Überprüfung.
    3. Starten Sie die Überprüfung.
    4. Führen Sie ein Upgrade für den Azure Information Protection-Client auf die Vorschauversion aus.
    5. Starten Sie die Überprüfung.

- Bekannte Probleme beim Überprüfen von großen Datasets:
    
    Mit dieser Vorschauversion können Sie die Anzahl von zu überprüfenden Dateien schrittweise erhöhen und den Fortschritt überwachen. Wenn der Status meldet, dass die Überprüfung ausgeführt wird, aber neue Dateien nicht überprüft werden, reduzieren Sie die Anzahl von zu überprüfenden Dateien, und starten Sie die Überprüfung neu. 

Sie benötigen Anweisungen zum Installieren, Konfigurieren und Starten der Überprüfung. Diese finden Sie unter [Bereitstellen der Azure Rights Management-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](../deploy-aip-scanner.md).

## <a name="version-137190"></a>Version 1.37.19.0

**Veröffentlicht**: 17.9.2018

Diese Version umfasst die MSIPC-Version 1.0.3592.627 des RMS-Clients.

**Neue Features**: 

- Unterstützung des ISO-Standards für die PDF-Verschlüsselung durch Konfiguration einer neuen [erweiterten Clientkonfiguration](client-admin-guide-customizations.md#protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Wenn diese Option konfiguriert wird, behalten PDF-Dokumente, die Sie schützen, ihre Erweiterung bei (anstelle einer Änderung in PPDF) und können von PDF-Readern geöffnet werden, die diesen ISO-Standard unterstützen. Derzeit müssen Sie Benutzer anweisen, diese geschützten PDF-Dateien manuell über den Azure Information Protection-Viewer zu öffnen. Damit Benutzern dabei zur Seite zu stehen, wird beim Öffnen dieser geschützten Dateien eine Seite mit Symbolen angezeigt, aus denen Sie ihr Betriebssystem auswählen können.

- Unterstützung neuer Typen vertraulicher Informationen, die beim Klassifizieren von Dokumenten helfen, die personenbezogene Informationen enthalten. [Weitere Informationen](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) 

- Bezeichnungen, die Schutz anwenden, werden jetzt in Office 2016-Apps (ab Version 1805, Build 9330.2078) angezeigt, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“) zugewiesen wurde.

- Unterstützung von Bezeichnungen für das Dokumentformat **Strict Open XML** in Word-, Excel- und PowerPoint- Dateien. Weitere Informationen zu den Open XML-Formaten finden Sie im Office-Blogbeitrag [New file format options in the new Office (Neue Dateiformate in der neuen Version von Office)](https://www.microsoft.com/en-us/microsoft-365/blog/2012/08/13/new-file-format-options-in-the-new-office/). 

- Unterstützung für Dateien, die von Secure Islands geschützt werden, wenn diese Dateien keine PDF- oder Office-Dokumente sind. Zum Beispiel geschützte Text- und Bilddateien oder Dateien mit der Erweiterung PFILE. Diese Unterstützung ermöglicht neue Szenarios, z.B. dass die Azure Information Protection-Überprüfung diese Dateien auf vertrauliche Informationen prüfen kann und diesen automatisch Bezeichnungen für Azure Information Protection hinzufügt. [Weitere Informationen](client-admin-guide-customizations.md#support-for-files-protected-by-secure-islands)

- Neue erweiterte Clienteinstellungen zum Entfernen von Kopf- und Fußzeilen, die von anderen Bezeichnungslösungen auf Dokumente angewendet wurden. [Weitere Informationen](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)

- Für die Azure Information Protection-Überprüfung:

    - Das neue Cmdlet [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner): Muss nach dem Upgrade von der aktuellen allgemein verfügbaren Version (1.29.5.0) oder früher einmalig ausgeführt werden.
    
    - Das neue Cmdlet [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus): Ruft den aktuellen Status des Diensts für die Überprüfung ab.  
    
    - Das neue Cmdlet [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan): Weist die Überprüfung an, eine einmalige Überprüfungszyklus zu starten, wenn der Zeitplan auf „manuell“ festgelegt ist.
    
    - SharePoint Server 2010 wird für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.
    
- Unterstützung für das neue Blatt **Azure Information Protection – Knoten (Vorschau)** im Azure-Portal, mit dem Sie die Überprüfung von einer zentralen Stelle aus verwalten können. Die Informationen von den bereitgestellten Überprüfungen, die mit Azure verbunden sind, werden alle fünf Minuten aktualisiert. Auf diesem Blatt können Sie eine einmalige Überprüfung starten, alle Dateien erneut überprüfen, den Status einer Überprüfung prüfen und die Überprüfungsgeschwindigkeit anzeigen.

**Fehlerbehebungen**

- Für die Azure Information Protection-Überprüfung:
    
    - Bei Dokumenten, die in SharePoint-Bibliotheken geschützt werden, wenn der Parameter *DefaultOwner* nicht für das Datenrepository verwendet wird, wird nun der Wert des SharePoint-Editors anstelle des Autorenwerts als Standardwert verwendet.
    
    - Die Überprüfungsberichte enthalten nun „Zuletzt geändert von“ für Office-Dokumente.
    
    - Sie können nun beim Bearbeiten der Registrierung alle Dateitypen mit dem Platzhalter `*` schützen, wie im Abschnitt [Bearbeiten der Registrierung für die Überprüfung](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) beschrieben.

- Das Anzeigen von E-Mails mithilfe der Pfeilsymbole „Nächstes Element“ und „Vorheriges Element“ auf der Symbolleiste für den Schnellzugriff zeigt nun die richtige Bezeichnung für die jeweilige E-Mail an.

- Benutzerdefinierte Berechtigungen unterstützen nun Empfänger-E-Mail-Adressen, die ein Apostroph enthalten.

- Die Computerumgebung wird erfolgreich gestartet (Bootstrap), wenn diese Aktion durch Öffnen eines geschützten Dokuments gestartet wird, das in SharePoint Online gespeichert ist.

- Wenn Sie den Client für den Rechtsklick auf den Datei-Explorer, PowerShell oder den Scanner verwenden, wird die Bezeichnung für Dateien in WebDav-Positionen blockiert, da es sich hierbei um ein nicht unterstütztes Szenario handelt.

- Das Symbol zum Löschen einer Bezeichnung wird in Client-Apps nicht angezeigt (Word, Excel, PowerPoint und Outlook), wenn Sie die [Richtlinieneinstellung](../configure-policy-settings.md) der Option **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen über eine Bezeichnung verfügen) konfigurieren.

**Weitere Änderungen**:

- Bei [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration):
    
    - **OneTime**, **Continuous** und **Never** (Einmalig, Fortlaufend und Nie) sind nicht mehr Werte für den Parameter *Schedule*. Stattdessen gibt es nun die Werte **Manual** (Manuell) und **Always** (Immer).
        
    - Der Parameter *Type* wurde entfernt, d.h. er wurde auch aus der Ausgabe entfernt, wenn Sie [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration) ausführen. Standardmäßig werden nach dem ersten Überprüfungszyklus nur neue oder geänderte Dateien untersucht. Wenn Sie zuvor für den *Typ*-Parameter **Vollständig** festgelegt haben, um alle Dateien erneut zu überprüfen, führen Sie nun [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan) mit dem *Zurücksetzen*-Parameter aus. Die Überprüfung muss auch für einen manuellen Zeitplan konfiguriert sein, was voraussetzt, dass für den *Zeitplan*-Parameter mit [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) die Option **Manuell** festgelegt wird.
    
- Die Standardausschlussliste des Clients und der Überprüfung umfasst nun MSG-, RAR- und ZIP-Dateien. Die Überprüfung schließt auch RTF-Dateien aus. [Weitere Informationen](client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)

- Die Richtlinienversion wurde in 1.4 geändert. Das Identifizieren der Versionsnummer ist zum [Konfigurieren nicht verbundener Computer](client-admin-guide-customizations.md#support-for-disconnected-computers) erforderlich.

- Der Link **Feedback senden** im Dialogfeld **Hilfe und Feedback** wurde entfernt. Er wurde vorübergehend durch **Problem melden** ersetzt, doch dieser Link wird nur noch in Vorschauversionen angezeigt. Standardmäßig sendet diese Option eine E-Mail an Microsoft, aber Sie können die E-Mail-Adresse in eine beliebige HTTP-Zeichenfolge ändern. Beispiele dafür sind eine benutzerdefinierte Webseite, über die Benutzer Probleme melden, oder eine E-Mail-Adresse, die E-Mails an Ihren Helpdesk weiterleitet. Verwenden Sie eine [erweiterte Clienteinstellung](client-admin-guide-customizations.md#modify-the-email-address-for-the-report-an-issue-link), um diese Adresse zu ändern.

## <a name="version-12950"></a>Version 1.29.5.0 

**Veröffentlicht:** 26.6.2018

Diese Version umfasst die MSIPC-Version 1.0.3403.1224 des RMS-Clients.

**Fixes**:

- Für die Office-Versionen 16.0.9324.1000 und höher (Klick-und-Los) unterstützt die Azure Information Protection-Leiste die neuesten Anzeigeoptionen für Monitore. Bisher konnte es passieren, dass die Leiste außerhalb der Outlook-Anwendung angezeigt wurde.

- Optische Kennzeichnungen, die Sie [pro Office-Anwendungstyp](../configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook) konfigurieren können, ersetzen eine Kopf- und Fußzeile, die zuvor von einer Azure Information Protection-Bezeichnung angewendet wurde.

- Wenn eine Excel-Datei bereits bezeichnet wurde und die Bezeichnung optische Kennzeichnungen anwendet, werden diese optischen Kennzeichnungen jetzt auch auf neue Tabellenblätter angewendet.

- Wenn Sie die erweiterte Clienteinstellung verwenden, um einem [Office-Dokument über eine bereits bestehende benutzerdefinierte Eigenschaft eine Bezeichnung hinzuzufügen](client-admin-guide-customizations.md#label-an-office-document-by-using-an-existing-custom-property), setzt die automatische Bezeichnung nicht die manuelle Bezeichnung außer Kraft.

## <a name="version-127480"></a>Version 1.27.48.0

**Veröffentlicht:** 30.5.2018

Diese Version umfasst die MSIPC-Version 1.0.3403.1224 des RMS-Clients.

**Neue Features**: 

- Für die Azure Information Protection-Überprüfung:
    
    - Sie können eine Liste mit Dateitypen angeben, die in die Überprüfung eingeschlossen oder von ihr ausgeschlossen werden sollen. Verwenden Sie zum Angeben der Liste [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes). Nachdem Sie die Liste mit Dateitypen angegeben haben, können Sie mithilfe von [Add-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes) einen neuen Dateityp zur Liste hinzufügen. Mit [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes) kann ein Dateityp aus der Liste entfernt werden.
    
    - Mithilfe der Standardbezeichnung können Sie Dateien bezeichnen, ohne deren Inhalt zu überprüfen. Verwenden Sie hierzu das Cmdlet [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/Set-AIPScannerRepository), und legen Sie den Parameter *MatchPolicy* auf **Off** fest. 
    
    - Dateien mit vertraulichen Informationstypen können Sie ohne Konfiguration der Bezeichnungen für die automatische Klassifizierung ermitteln. Verwenden Sie hierzu das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration), und legen Sie den Parameter *DiscoverInformationTypes* auf **All** fest.
    
    - Standardmäßig werden nur Office-Dokumenttypen geschützt. Sie können weitere Dateitypen schützen, indem Sie diese in der Registrierung definieren. Weitere Informationen hierzu finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](../develop/file-api-configuration.md).
    
    - Standardmäßig wird die Überprüfung für eine höhere Sicherheit mit einer niedrigen Integritätsebene ausgeführt. Dies gilt für den Fall, dass die Überprüfung mit einem Konto ausgeführt wird, das über privilegierte Rechte verfügt. Wenn das Dienstkonto, das die Überprüfung ausführt, nur über die unter [Voraussetzungen für die Azure Information Protection-Überprüfung](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner) dokumentierten Rechte verfügt, ist eine niedrige Integritätsebene weder erforderlich noch empfehlenswert, da sie sich negativ auf die Leistung auswirkt. Sie können die niedrige Integritätsebene mithilfe der erweiterten Clienteinstellung deaktivieren. [Weitere Informationen](client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) 
    
- Für [Get-AIPFileStatus](/powershell/module/azureinformationprotection/Get-AIPFileStatus) beinhaltet die Ausgabe jetzt den Rights Management-Besitzer und den Rights Management-Aussteller sowie das Datum, an dem der Inhalt geschützt wurde.
 
**Weitere Änderungen**:

- Für die Azure Information Protection-Überprüfung: 
    
    - Wenn Sie eine frühere Version der Überprüfung installiert haben, führen Sie nach dem Upgrade des Azure Information Protection-Clients den Befehl zur Installation der Überprüfung mit [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) erneut aus. Ihre Konfigurationseinstellungen für Überprüfung und Repositorys werden beibehalten. Die Neuinstallation der Überprüfung gewährt dem Überprüfungsdienstkonto Berechtigungen zum Löschen für die Überprüfungsdatenbank, die für Berichte benötigt werden.    
    
    - Der Parameter *ScanMode* von [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) wurde in **Enforce** umbenannt und kann die Werte Off und On enthalten.
    
    - Wenn Sie eine Standardbezeichnung verwenden möchten, müssen Sie diese nicht mehr als Richtlinieneinstellung konfigurieren. Sie können die Standardbezeichnung stattdessen mit der Repositorykonfiguration angeben. 

- Die Seiten „Herzlichen Glückwunsch!“ sowie „Neuigkeiten in Azure Information Protection“, die bei der ersten Verwendung in Office-Anwendungen angezeigt wurden, wurden entfernt.

## <a name="version-12660"></a>Version 1.26.6.0

**Veröffentlicht:** 17.4.2018

Diese Version umfasst die MSIPC-Version 1.0.3403.1224 des RMS-Clients.

**Neue Features**:

- Azure Information Protection-Überprüfung: Das im Client enthaltene PowerShell-Modul verfügt über neue Cmdlets zum Installieren und Konfigurieren des Überprüfungsmoduls, mit denen Sie Dateien in Ihren lokalen Datenspeichern ermitteln, klassifizieren und schützen können. Eine Anleitung hierzu finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](../deploy-aip-scanner.md). 
- Sie haben jetzt die Möglichkeit, verschiedene optische Kennzeichnungen für Word, Excel, PowerPoint und Outlook festzulegen, indem Sie die Variablenanweisung „If.App“ in der Textzeichenfolge verwenden und den Anwendungstyp identifizieren. [Weitere Informationen]configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Unterstützung der [Richtlinieneinstellung](../configure-policy-settings.md), **Information Protection-Leiste in Office-Apps anzeigen**. Wenn diese Einstellung deaktiviert ist, wählen Benutzer Bezeichnungen über die Schaltfläche **Schützen** im Menüband aus.

- Eine neue erweiterte Clienteinstellung (noch in der Vorschau), mit der Sie die Klassifizierung aktivieren können, die fortlaufend im Hintergrund ausgeführt wird. Ist diese Einstellung aktiviert, wird für Office-Apps die automatische und empfohlene Klassifizierung ständig im Hintergrund ausgeführt, anstatt beim Speichern von Dokumenten. Aufgrund dieses veränderten Verhaltens können Sie jetzt eine automatische und empfohlene Klassifizierung auf Dokumente anwenden, die in SharePoint Online gespeichert sind. [Weitere Informationen](client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background)

- Eine neue erweiterte Clienteinstellung, mit der verhindert wird, dass Outlook die Standardbezeichnung anwendet, die in der Azure Information Protection-Richtlinie konfiguriert ist. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden. [Weitere Informationen](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Für Office-Apps können Sie beim Angeben von benutzerdefinierten Berechtigungen über ein Adressbuchsymbol jetzt nach Benutzern suchen und diese auswählen. Diese Option sorgt für Parität auf der Benutzeroberfläche, wenn Sie benutzerdefinierte Berechtigungen mit dem Datei-Explorer angeben.

- Unterstützung einer Authentifizierungsmethode ganz ohne Interaktion für Dienstkonten, für die PowerShell genutzt wird und denen das Recht für **Lokales Anmelden** nicht gewährt werden kann. Bei dieser Authentifizierungsmethode ist es erforderlich, dass Sie den neuen Parameter *Token* mit [Set-AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication) verwenden und ein PowerShell-Skript als Aufgabe ausführen. [Weitere Informationen](client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

- Neuer Parameter *IntegratedAuth* für [Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication). Dieser Parameter unterstützt den Servermodus für AD RMS, der benötigt wird, damit Windows Server FCI von AD RMS unterstützt werden kann.


**Fixes**:

Fixes für Stabilität und für bestimmte Szenarios, die Folgendes umfassen:

- Für die Office-Versionen 16.0.8628.2010 und höher (Klick-und-Los) unterstützt die Azure Information Protection-Leiste die neuesten Anzeigeoptionen für Monitore. Bisher konnte es passieren, dass die Leiste außerhalb von Office-Anwendungen angezeigt wurde.

- Wenn zwei Organisationen Dokumente und E-Mails über eine Azure Information Protection-Freigabe verwenden, werden jeweils die eigenen Bezeichnungen beibehalten und nicht durch die Bezeichnungen der anderen Organisation ersetzt.

- Für Excel:
        
    - Unterstützung für die Änderung von Office- oder Windows-Designs. Bisher wurden in Excel nach dem Ändern des Designs keine Daten angezeigt.
        
    - Unterstützung für Zellen in Excel, die Querverweise enthalten. Bisher konnte es in diesen Zellen zu einer Beschädigung des Texts kommen.
    
    - Unterstützung für die Eingabe von japanischen, chinesischen und koreanischen Zeichen, was zuvor dazu führte, dass ein Fenster geschlossen wurde, sodass diese Zeichen nicht ausgewählt werden konnten.
    
    - Unterstützung für Kommentare, zuvor wurde der Kommentar während der Eingabe geschlossen.

- Für PowerPoint: Unterstützung für Mitverfasser, was zuvor zu Datenverlust führen konnte.

- Dateien mit der Dateinamenerweiterung „.xml“ können jetzt für die empfohlene bzw. automatische Klassifizierung untersucht werden.

- Mit dem Viewer können jetzt geschützte textbasierte Dateien (PTXT und PXML) geöffnet werden, die größer als 20 MB sind. 
- Es wird verhindert, dass Outlook hängt, wenn Outlook-Erinnerungen genutzt werden.

- Bootstrap funktioniert für die 64-Bit-Version von Office, sodass Sie Dokumente und E-Mails schützen können.

- Sie können für Word, Excel, PowerPoint und den Datei-Explorer jetzt eine Bezeichnung für benutzerdefinierte Berechtigungen konfigurieren und außerdem die erweiterte Clienteinstellung verwenden, um die Optionen für die benutzerdefinierten Berechtigungen auszublenden. [Weitere Informationen](client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) 

- Fallback auf die Schriftart Calibri, wenn optische Kennzeichnungen in der Azure Information Protection-Richtlinie für einen Schriftartnamen konfiguriert sind, der auf dem Client nicht installiert ist.

- Verhinderung von Office-Abstürzen nach einem Upgrade des Azure Information Protection-Clients.

- Verbesserung der Leistung und der Arbeitsspeichernutzung für Office-Apps.

- Wenn Sie eine Bezeichnung für benutzerdefinierte Berechtigungen und die Schutzart „HYOK (AD RMS)“ konfigurieren, wird für den Schutz nicht mehr fälschlicherweise der Azure Rights Management-Dienst genutzt.

- Unterbezeichnungen erben keine optischen Kennzeichnungen und Schutzeinstellungen von der übergeordneten Bezeichnung mehr, um die Verwaltungsumgebung einheitlicher zu gestalten.

**Weitere Änderungen**:

- Für die [Protokollierung der Clientnutzung](client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client ): Die Ereignis-IDs 102 und ID 103 werden durch Ereignis-ID 101 ersetzt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren und Verwenden des Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)


