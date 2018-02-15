---
title: Der Azure Information Protection-Client&colon; Verlauf der Releases und Supportrichtlinie
description: "Erfahren Sie, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde, und erhalten Sie Informationen zum Support der Lifecycle-Richtlinie."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/06/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 19390c05719ebfee7e3442437d3f5bdfd303c652
ms.sourcegitcommit: d32d1f5afa5ee9501615a6ecc4af8a4cd4901eae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Der Azure Information Protection-Client: Verlauf der Releases und Supportrichtlinie

>*Gilt für: Azure Information Protection*

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

## <a name="versions-later-than-110560"></a>1.10.56.0 und spätere Versionen

Wenn Ihre Version des Clients höher als 1.10.56.0 ist, handelt es sich um einen Vorschaubuild für Test- und Auswertungszwecke.

Die aktuelle Version lautet **1.21.203.0** und weist seit der aktuellen GA-Version des Clients die unten angegebenen Änderungen auf.

Diese Version umfasst die MSIPC-Version 1.0.3403.1224 des RMS-Clients.

**Neue Features**:

- Azure Information Protection-Überprüfung: Das im Client enthaltene PowerShell-Modul verfügt über neue Cmdlets zum Installieren und Konfigurieren des Überprüfungsmoduls, mit denen Sie Dateien in Ihren lokalen Datenspeichern ermitteln, klassifizieren und schützen können. Eine Anleitung hierzu finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](../deploy-use/deploy-aip-scanner.md). 

- Für Office-Apps wird die automatische und empfohlene Klassifizierung ständig im Hintergrund ausgeführt, anstatt beim Speichern von Dokumenten. Aufgrund dieses veränderten Verhaltens können Sie jetzt eine automatische und empfohlene Klassifizierung auf Dokumente anwenden, die in SharePoint Online gespeichert sind. [Weitere Informationen](../deploy-use/configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) 

- Sie haben jetzt die Möglichkeit, verschiedene optische Kennzeichnungen für Word, Excel, PowerPoint und Outlook festzulegen, indem Sie die Variablenanweisung „If.App“ in der Textzeichenfolge verwenden und den Anwendungstyp identifizieren. [Weitere Informationen](../deploy-use/configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Unterstützung der [Richtlinieneinstellung](../deploy-use/configure-policy-settings.md), **Information Protection-Leiste in Office-Apps anzeigen**. Wenn diese Einstellung deaktiviert ist, wählen Benutzer Bezeichnungen über die Schaltfläche **Schützen** im Menüband aus.

- Eine neue erweiterte Clienteinstellung, mit der verhindert wird, dass Outlook die Standardbezeichnung anwendet, die in der Azure Information Protection-Richtlinie konfiguriert ist. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden. [Weitere Informationen](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Für Office-Apps können Sie beim Angeben von benutzerdefinierten Berechtigungen über ein Adressbuchsymbol jetzt nach Benutzern suchen und diese auswählen. Diese Option sorgt für Parität auf der Benutzeroberfläche, wenn Sie benutzerdefinierte Berechtigungen mit dem Datei-Explorer angeben.

- Unterstützung einer Authentifizierungsmethode ganz ohne Interaktion für Dienstkonten, für die PowerShell genutzt wird und denen das Recht für **Lokales Anmelden** nicht gewährt werden kann. Bei dieser Authentifizierungsmethode ist es erforderlich, dass Sie den neuen Parameter *Token* mit [Set-AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication) verwenden und ein PowerShell-Skript als Aufgabe ausführen. [Weitere Informationen](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

- Neuer Parameter *IntegratedAuth* für [Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication). Dieser Parameter unterstützt den Servermodus für AD RMS, der benötigt wird, damit Windows Server FCI von AD RMS unterstützt werden kann.


**Fixes**:

Fixes für Stabilität und für bestimmte Szenarios, die Folgendes umfassen:

- Für die Office-Versionen 16.0.8628.2010 und höher (Klick-und-Los) unterstützt die Azure Information Protection-Leiste die neuesten Anzeigeoptionen für Monitore. Bisher konnte es passieren, dass die Leiste außerhalb von Office-Anwendungen angezeigt wurde.

- Wenn zwei Organisationen Dokumente und E-Mails über eine Azure Information Protection-Freigabe verwenden, werden jeweils die eigenen Bezeichnungen beibehalten und nicht durch die Bezeichnungen der anderen Organisation ersetzt.

- Unterstützung für Zellen in Excel, die Querverweise enthalten. Bisher konnte es in diesen Zellen zu einer Beschädigung des Texts kommen.

- Unterstützung für die Änderung von Office- oder Windows-Designs. Bisher wurden in Excel nach dem Ändern des Designs keine Daten angezeigt.

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

## <a name="version-172100"></a>Version 1.7.210.0

**Veröffentlicht**: 06.06.2017

Diese Version umfasst die MSIPC-Version 1.0.2217.1 des RMS-Clients.

**Neue Features**:

- Neues PowerShell-Cmdlet [Set-AIPFileClassification](/powershell/module/azureinformationprotection/Set-AIPFileClassification). Wenn Sie dieses Cmdlet ausführen, werden die Dateiinhalte überprüft und die Bezeichnungen werden gemäß den Bedingungen, die Sie in der Azure Information Protection-Richtlinie angeben, automatisch auf nicht bezeichnete Dateien angewendet.

**Fixes**:

- Alle Bezeichnungs- und Klassifizierungs-Cmdlets werden nun auf Computern unterstützt, die nicht mit dem Internet verbunden sind, aber eine gültige Azure Information Protection-Richtlinie aufweisen.

- Aus Konsistenzgründen wird ein Ausgabeparameter des Cmdlets [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) von britischem Englisch (**IsLabelled**) in amerikanisches Englisch (**IsLabeled**) geändert. Wenn Sie Skripts oder automatisierte Prozesse verwenden, die nach diesem Parameter suchen, aktualisieren Sie die Schreibweise dieses Parameters.

- Die allgemeinen Fehlerbehebungen zur Verbesserung der Stabilität umfassen Folgende:

    - Für Outlook: Fehlerbehebungen für Abstürze, hohen Speicherverbrauch und Anzeigeprobleme bei Menüs.
    
    - Für Word, Excel und PowerPoint: Fehlerbehebungen für hohe CPU-Auslastung, Anzeigeprobleme beim Speichern großer Excel-Dateien oder keine Reaktion der Anwendung. 
    
    Um die Leistung von Office 2016 bei SharePoint Online und OneDrive for Business zu verbessern, werden bei diesen Anwendungen außerdem automatische und empfohlene Bezeichnungen beim Schließen der Datei statt beim Speichern (beim automatischen Speichern oder Speichervorgang durch den Benutzer) angewendet. Gleichermaßen gilt: Wenn die Einstellung **All documents and email must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung haben) aktiviert ist, werden Benutzer erst aufgefordert, eine Bezeichnung auszuwählen, wenn die Datei geschlossen wird. Die Ausnahme gilt für Word 2016 und Excel 2016, wenn der Benutzer die Option **Speichern unter** wählt. Diese Aktion löst dann diese Bezeichnungsverhalten aus, sofern diese konfiguriert sind. 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren und Verwenden des Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
