---
title: 'Der Azure Information Protection-Client: Versionsgeschichte und Supportrichtlinie'
description: Erfahren Sie, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde, und erhalten Sie Informationen zum Support der Lifecycle-Richtlinie.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4ff64b5bb4f73533352aa5497a98263c86842800
ms.sourcegitcommit: c41490096af48e778947739e320e0dc8511f6c68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2018
ms.locfileid: "34423254"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Der Azure Information Protection-Client: Verlauf der Releases und Supportrichtlinie

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Das Azure Information Protection-Team aktualisiert den Azure Information Protection-Client regelmäßig, um Korrekturen und neue Funktionen zu implementieren. 

Sie können das neuste allgemein verfügbare Release und die aktuelle Vorschauversion im [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. Diese Versionen sind außerdem im Microsoft Update-Katalog (Kategorie: **Azure Information Protection**) enthalten, damit Sie den Client über WSUS, den Konfigurationsmanager oder andere Mechanismen zur Bereitstellung von Software bereitstellen können, die Microsoft Update verwenden.

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version des Azure Information Protection-Clients mit allgemeiner Verfügbarkeit wird bis zu sechs Monate nach dem Release der nächsten Version mit allgemeiner Verfügbarkeit unterstützt. Nicht unterstützte Versionen des Clients sind nicht auf dieser Seite enthalten. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

### <a name="release-history"></a>Verlauf der Releases

Im Folgenden wird erläutert, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. 

> [!NOTE]
> Kleinere Korrekturen werden nicht aufgelistet. Wenn also ein Problem mit dem Azure Information Protection-Client auftreten sollte, wird empfohlen, dass Sie zuerst überprüfen, ob dieses Problem mit dem neusten allgemein verfügbaren Release behoben wird. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion.
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../get-started/information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

## <a name="versions-later-than-12660"></a>Versionen ab 1.26.6.0

Wenn Ihre Version des Clients höher als 1.26.6.0 ist, handelt es sich um eine Vorabversion für Test- und Evaluierungszwecke. 
 
**Veröffentlicht:** 21.5.2018 

Die aktuelle Version lautet **1.27.48.0** und weist seit der aktuellen allgemein verfügbaren Version des Clients die unten angegebenen Änderungen auf.  

**Neue Features**: 

- Für die Azure Information Protection-Überprüfung:
    
    - Sie können eine Liste mit Dateitypen angeben, die in die Überprüfung eingeschlossen oder von ihr ausgeschlossen werden sollen. Verwenden Sie zum Angeben der Liste [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes). Nachdem Sie die Liste mit Dateitypen angegeben haben, können Sie mithilfe von [Add-AIPScannerScannedFileType](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileType) einen neuen Dateityp zur Liste hinzufügen. Mit [Remove-AIPScannerScannedFileType](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileType) kann ein Dateityp aus der Liste entfernt werden.
    
    - Mithilfe der Standardbezeichnung können Sie Dateien bezeichnen, ohne deren Inhalt zu überprüfen. Verwenden Sie hierzu das Cmdlet [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/Set-AIPScannerRepository), und legen Sie den Parameter *MatchPolicy* auf **Off** fest. 
    
    - Dateien mit vertraulichen Informationstypen können Sie ohne Konfiguration der Bezeichnungen für die automatische Klassifizierung ermitteln. Verwenden Sie hierzu das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration), und legen Sie den Parameter *DiscoverInformationTypes* auf **All** fest.
    
    - Standardmäßig werden nur Office-Dokumenttypen geschützt. Sie können weitere Dateitypen schützen, indem Sie diese in der Registrierung definieren. Weitere Informationen hierzu finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](../develop/file-api-configuration.md).
    
    - Standardmäßig wird die Überprüfung für eine höhere Sicherheit mit einer niedrigen Integritätsebene ausgeführt. Dies gilt für den Fall, dass die Überprüfung mit einem Konto ausgeführt wird, das über privilegierte Rechte verfügt. Wenn das Dienstkonto, das die Überprüfung ausführt, nur über die unter [Voraussetzungen für die Azure Information Protection-Überprüfung](../deploy-use/deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner) dokumentierten Rechte verfügt, ist eine niedrige Integritätsebene weder erforderlich noch empfehlenswert, da sie sich negativ auf die Leistung auswirkt. Sie können die niedrige Integritätsebene mithilfe der erweiterten Clienteinstellung deaktivieren. [Weitere Informationen](../rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) 
    
- Für [Get-AIPFileStatus](/powershell/module/azureinformationprotection/Get-AIPFileStatus) beinhaltet die Ausgabe jetzt den Rights Management-Besitzer und den Rights Management-Aussteller sowie das Datum, an dem der Inhalt geschützt wurde.
 
**Weitere Änderungen**:

- Für die Azure Information Protection-Überprüfung: 
    
    - Der Parameter *ScanMode* von [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) wurde in **Enforce** umbenannt und kann die Werte Off und On enthalten.
    
    - Wenn Sie eine Standardbezeichnung verwenden möchten, müssen Sie diese nicht mehr als Richtlinieneinstellung konfigurieren. Sie können die Standardbezeichnung stattdessen mit der Repositorykonfiguration angeben. 

- Die Seiten „Herzlichen Glückwunsch!“ sowie „Neuigkeiten in Azure Information Protection“, die bei der ersten Verwendung in Office-Anwendungen angezeigt wurden, wurden entfernt.

## <a name="version-12660"></a>Version 1.26.6.0

**Veröffentlicht:** 17.4.2018

Diese Version umfasst die MSIPC-Version 1.0.3403.1224 des RMS-Clients.

**Neue Features**:

- Azure Information Protection-Überprüfung: Das im Client enthaltene PowerShell-Modul verfügt über neue Cmdlets zum Installieren und Konfigurieren des Überprüfungsmoduls, mit denen Sie Dateien in Ihren lokalen Datenspeichern ermitteln, klassifizieren und schützen können. Eine Anleitung hierzu finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](../deploy-use/deploy-aip-scanner.md). 

- Sie haben jetzt die Möglichkeit, verschiedene optische Kennzeichnungen für Word, Excel, PowerPoint und Outlook festzulegen, indem Sie die Variablenanweisung „If.App“ in der Textzeichenfolge verwenden und den Anwendungstyp identifizieren. [Weitere Informationen](../deploy-use/configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Unterstützung der [Richtlinieneinstellung](../deploy-use/configure-policy-settings.md), **Information Protection-Leiste in Office-Apps anzeigen**. Wenn diese Einstellung deaktiviert ist, wählen Benutzer Bezeichnungen über die Schaltfläche **Schützen** im Menüband aus.

- Eine neue erweiterte Clienteinstellung (noch in der Vorschau), mit der Sie die Klassifizierung aktivieren können, die fortlaufend im Hintergrund ausgeführt wird. Ist diese Einstellung aktiviert, wird für Office-Apps die automatische und empfohlene Klassifizierung ständig im Hintergrund ausgeführt, anstatt beim Speichern von Dokumenten. Aufgrund dieses veränderten Verhaltens können Sie jetzt eine automatische und empfohlene Klassifizierung auf Dokumente anwenden, die in SharePoint Online gespeichert sind. [Weitere Informationen](client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background)

- Eine neue erweiterte Clienteinstellung, mit der verhindert wird, dass Outlook die Standardbezeichnung anwendet, die in der Azure Information Protection-Richtlinie konfiguriert ist. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden. [Weitere Informationen](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Für Office-Apps können Sie beim Angeben von benutzerdefinierten Berechtigungen über ein Adressbuchsymbol jetzt nach Benutzern suchen und diese auswählen. Diese Option sorgt für Parität auf der Benutzeroberfläche, wenn Sie benutzerdefinierte Berechtigungen mit dem Datei-Explorer angeben.

- Unterstützung einer Authentifizierungsmethode ganz ohne Interaktion für Dienstkonten, für die PowerShell genutzt wird und denen das Recht für **Lokales Anmelden** nicht gewährt werden kann. Bei dieser Authentifizierungsmethode ist es erforderlich, dass Sie den neuen Parameter *Token* mit [Set-AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication) verwenden und ein PowerShell-Skript als Aufgabe ausführen. [Weitere Informationen](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

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

- Sie können für Word, Excel, PowerPoint und den Datei-Explorer jetzt eine Bezeichnung für benutzerdefinierte Berechtigungen konfigurieren und außerdem die erweiterte Clienteinstellung verwenden, um die Optionen zu den benutzerdefinierten Berechtigungen auszublenden. [Weitere Informationen](client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) 

- Fallback auf die Schriftart Calibri, wenn optische Kennzeichnungen in der Azure Information Protection-Richtlinie für einen Schriftartnamen konfiguriert sind, der auf dem Client nicht installiert ist.

- Verhinderung von Office-Abstürzen nach einem Upgrade des Azure Information Protection-Clients.

- Verbesserung der Leistung und der Arbeitsspeichernutzung für Office-Apps.

- Wenn Sie eine Bezeichnung für benutzerdefinierte Berechtigungen und die Schutzart „HYOK (AD RMS)“ konfigurieren, wird für den Schutz nicht mehr fälschlicherweise der Azure Rights Management-Dienst genutzt.

- Unterbezeichnungen erben keine optischen Kennzeichnungen und Schutzeinstellungen von der übergeordneten Bezeichnung mehr, um die Verwaltungsumgebung einheitlicher zu gestalten.


## <a name="version-110560"></a>Version 1.10.56.0

**Veröffentlicht**: 18.9.2017

Diese Version umfasst die MSIPC-Version 1.0.3219.0619 des RMS-Clients.

**Neue Features**:

- Unterstützung für die neuen Office 365-DLP-Bedingungen, die Sie für eine Bezeichnung konfigurieren können. Weitere Informationen finden Sie unter [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](../deploy-use/configure-policy-classification.md).

- Unterstützung für Bezeichnungen, für die benutzerdefinierte Aktionen konfiguriert sind. Bei Outlook wendet diese Bezeichnung automatisch die Outlook-Option „Nicht weiterleiten“ an. Bei Word, Excel, PowerPoint und dem Datei-Explorer fordert diese Bezeichnung den Benutzer dazu auf, benutzerdefinierte Berechtigungen anzugeben. Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](../deploy-use/configure-policy-protection.md).

- Bezeichnungen unterstützen mehrere Sprachen. Ab dem 30. August 2017 enthält die [Standardrichtlinie](../deploy-use/configure-policy-default.md) Unterstützung für mehrere Sprachen, die den Benutzern in dieser Clientversion angezeigt werden. Unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection](../deploy-use/configure-policy-languages.md) finden Sie Informationen darüber, wie Benutzer vor diesem Datum Bezeichnungen aus einer Standardrichtlinie bzw. die von Ihnen konfigurierten Bezeichnungen in ihrer bevorzugten Sprache anzeigen können.

- Bezeichnungen werden zusätzlich zu der Anzeige auf der Information Protection-Leiste über die Schaltfläche **Schützen** auf dem Office-Menüband angezeigt. 

- Nativer Schutz für folgende Visio-Dateitypen: VSDM, VSDX, VSSM, VSSX, VSTM, VSTX

- Unterstützung für erweiterte Clientkonfigurationen, die Sie im Azure-Portal konfigurieren können. Diese Konfigurationen umfassen Folgendes:
    
    - [Ausblenden der Schaltfläche „Nicht weiterleiten“ in Outlook](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook)
    
    - [Verfügbar- oder Nicht-Verfügbarmachen der Optionen für benutzerdefinierte Berechtigungen für Benutzer](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users)
    
    - [Die Azure Information Protection-Leiste dauerhaft ausblenden](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar)
    
    - [Die empfohlene Klassifizierung in Outlook aktivieren](../rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook)

- Bei PowerShell: Unterstützung für die nicht interaktive Bezeichnung von Dateien unter Verwendung der neuen PowerShell-Cmdlets [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) und [Clear-AIPAuthentication](/powershell/module/azureinformationprotection/clear-aipauthentication). Weitere Informationen zur Verwendung dieser Cmdlets finden Sie im [PowerShell-Abschnitt](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) des Administratorhandbuchs.

- Für die PowerShell-Cmdlets [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) und [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification) gibt es die neuen Parameter **Owner** und **PreserveFileDetails**. Mit diesen Parametern können Sie eine E-Mail-Adresse für die benutzerdefinierte Eigenschaft „Owner“ angeben und das Datum für Dokumente, die Sie bezeichnen, unverändert lassen.

**Fixes**:

Fixes für Stabilität und für bestimmte Szenarios, die Folgendes umfassen:

- Unterstützung für den generischen Schutz von großen Dateien, die zuvor bei einer Größe von über 1 GB zu Beschädigungen führen konnten. Nun ist die Dateigröße nur durch den verfügbaren Festplattenspeicherplatz und Arbeitsspeicherplatz eingeschränkt. Weitere Informationen zu Einschränkungen bei der Dateigröße finden Sie unter [Für den Schutz unterstützte Dateigrößen](client-admin-guide-file-types.md#file-sizes-supported-for-protection) im Administratorhandbuch.

- Die Anzeige des Azure Information Protection-Clients öffnet geschützte PDF-Dateien (.ppdf) schreibgeschützt.

- Unterstützung für die Bezeichnung und den Schutz von Dateien, die auf dem SharePoint-Server gespeichert sind.

- Wasserzeichen unterstützen jetzt mehrere Zeilen. Darüber hinaus werden visuelle Kennzeichnungen jetzt [nur beim ersten Speichern](../deploy-use/configure-policy-markings.md#when-visual-markings-are-applied) angewendet, anstatt jedes Mal, wenn ein Dokument gespeichert wird.

- Die Option **Diagnose ausführen** im Dialogfeld **Hilfe und Feedback** wird durch **Einstellungen zum Zurücksetzen** ersetzt. Das Verhalten für diese Aktion wurde geändert, sodass das Abmelden des Benutzers und das Löschen der Azure Information Protection-Richtlinie mit eingeschlossen ist. Weitere Informationen finden Sie unter [Weitere Informationen über die Zurücksetzungsoption für die aktuelle Vorschauversion des Azure Information Protection-Clients](..\rms-client\client-admin-guide.md#more-information-about-the-reset-settings-option) im Administratorhandbuch.

- Unterstützung für die Proxyauthentifizierung.

Fixes für eine bessere Benutzererfahrung, die Folgendes umfassen:

- E-Mail-Validierung, wenn Benutzer benutzerdefinierte Berechtigungen angeben. Darüber hinaus können jetzt durch Drücken der EINGABETASTE mehrere E-Mail-Adressen angegeben werden.

- Die übergeordnete Bezeichnung wird nicht angezeigt, wenn für ihre untergeordneten Bezeichnungen Schutz konfiguriert ist und der Client nicht über eine Edition von Office verfügt, die den Schutz unterstützt. 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren und Verwenden des Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
