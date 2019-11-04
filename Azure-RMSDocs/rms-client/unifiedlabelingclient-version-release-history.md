---
title: Azure Information Protection vereinheitlichte Bezeichnung für den Client Versionsverlauf & Unterstützungs Richtlinie
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: cabailey
ms.author: cabailey
manager: rkarlin
ms.date: 11/02/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 0ee20b6063dffd18b5067663de05c2d7a25cabd4
ms.sourcegitcommit: ee897f9dc3580269395b63fb9aeccbd8a547fff1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73446037"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection Unified Bezeichnungs Verlauf des Client Versions Verlaufs und der Support Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


Sie können den Azure Information Protection Unified Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen.

Nach einer kurzen Verzögerung von in der Regel einige Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog mit dem Produktnamen **Microsoft Azure Information Protection** > **Microsoft Azure Informationen enthalten. Schutz einheitlicher**Bezeichnungs Client und die Klassifizierung von **Updates**. Diese Aufnahme in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Softwarebereitstellungsmechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [aktualisieren und Verwalten des Azure Information Protection Unified Bezeichnung-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede allgemein verfügbare Version des Azure Information Protection Unified Bezeichnung-Clients wird bis zu sechs Monate nach der Veröffentlichung der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

##### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden:

|Client Version|Datum der Veröffentlichung|
|--------------|-------------|
|2.0.778.0|04/16/2019|

Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.


### <a name="release-information"></a>Informationen zum Release

Verwenden Sie die folgenden Informationen, um zu erfahren, was für eine unterstützte Version des Azure Information Protection Unified Bezeichnung-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn Sie also ein Problem mit dem Unified-Bezeichnungs Client haben, sollten Sie überprüfen, ob es mit der neuesten GA-Version behoben wurde. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

Dieser Client ersetzt den Azure Information Protection Client (klassisch). Informationen zum Vergleichen von Features und Funktionen mit dem klassischen Client finden Sie unter [vergleichen der Bezeichnung für Clients für Windows-Computer](use-client.md##compare-the-labeling-clients-for-windows-computers).

## <a name="version-25330"></a>Version 2.5.33.0

**Veröffentlicht**: 10/23/2019

**Neue Funktionen:**

- Vorschauversion des [Scanners](../deploy-aip-scanner.md), um lokale Datenspeicher zu überprüfen und zu bezeichnen. Mit dieser Version des Scanners:
    
    - Wenn Sie die Scanner für die Verwendung desselben Scanner-Profils konfigurieren, können mehrere Scanner dieselbe SQL Server Datenbank gemeinsam nutzen. Diese Konfiguration erleichtert die Verwaltung mehrerer Scanner und führt zu schnelleren Scanzeiten. Wenn Sie diese Konfiguration verwenden, warten Sie immer, bis die Installation eines Scanners abgeschlossen ist, bevor Sie einen weiteren Scanner mit dem gleichen Profil installieren.
    
    - Sie müssen ein Profil angeben, wenn Sie den Scanner installieren, und die Scannerdatenbank hat den Namen **AIPScannerUL_\<profile_name >** . Der Parameter " *profile* " ist auch für "Set-aipscanner" obligatorisch.
    
    - Sie können in allen Dokumenten eine Standard Bezeichnung festlegen, auch wenn Dokumente bereits mit der Bezeichnung versehen sind. Legen Sie in den Überprüfungs Profil-oder Repository-Einstellungen die Option **Dateien** neu bezeichnen auf ein fest **, und aktivieren** Sie das Kontrollkästchen neue **Bezeichnung Standard Bezeichnung erzwingen** .
    
    - Sie können vorhandene Bezeichnungen aus allen Dokumenten entfernen, und dieser Vorgang umfasst das Entfernen des Schutzes, wenn dieser zuvor durch eine Bezeichnung angewendet wurde. Der Schutz, der unabhängig von einer Bezeichnung angewendet wird, wird beibehalten. Diese Scannerkonfiguration wird in den Einstellungen für das Scanner-Profil oder im Repository mit den folgenden Einstellungen erreicht:
        - Bezeichnungs **Dateien basierend auf dem Inhalt**: **Off**
        - **Standard Bezeichnung**: **keine**
        - **Dateien**neu bezeichnen: **aktivieren** Sie das Kontrollkästchen **Standard Bezeichnung erzwingen** ausgewählt haben.
    
    - Wie bei der Überprüfung des klassischen Clients schützt der Scanner standardmäßig Office-Dateien und PDF-Dateien. Sie können andere Dateitypen schützen, wenn Sie eine [Erweiterte PowerShell-Einstellung](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect)verwenden.
    
    - Ereignis-IDs für die Start-und Beendigungs Zyklen der Scanner werden nicht in das Windows-Ereignisprotokoll geschrieben. Verwenden Sie stattdessen die Azure-Portal für diese Informationen.
    
    - Bekanntes Problem: neue und umbenannte Bezeichnungen können nicht als Standard Bezeichnung für das Scanner-Profil oder die Repository-Einstellungen ausgewählt werden. Problem Umgehungen
        - Für neue Bezeichnungen: Fügen Sie im Azure-Portal [die Bezeichnung](../configure-policy-add-remove-label.md) , die Sie verwenden möchten, der globalen Richtlinie oder einer Bereichs bezogenen Richtlinie hinzu.
        - Umbenannte Bezeichnungen: Schließen Sie die Azure-Portal, und öffnen Sie Sie erneut.
    
    Sie können Scanner über den Azure Information Protection-Client (klassisch) aktualisieren. Nach dem Upgrade, mit dem eine neue Datenbank erstellt wird, werden bei der ersten Ausführung des Scanners alle Dateien neu erstellt. Anweisungen finden Sie unter [Aktualisieren des Azure Information Protection Scanners](clientv2-admin-guide.md#upgrading-the-azure-information-protection-scanner) im Administrator Handbuch.
    
    Weitere Informationen finden Sie im Blogbeitrag Ankündigung: [Unified-Bezeichnung AIP Scanner Preview sorgt für horizontales hochskalieren und mehr.](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Unified-labeling-AIP-scanner-preview-brings-scaling-out-and-more/ba-p/862552)

- Das PowerShell-Cmdlet " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " verfügt über neue Parameter ("*AppID*", " *appsecret*", " *tenantid*", " *delegateduser*" und " *onbehalfof*"), wenn Sie Dateien nicht interaktiv bezeichnen möchten, und auch ein neues Verfahren zum Registrieren einer APP in Azure AD. Beispiele für Szenarien sind der Scanner und automatisierte PowerShell-Skripts zum bezeichnen von Dokumenten. Anweisungen finden Sie unter Vorgehens [Weise beim nicht interaktiven bezeichnen von Dateien](clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) im Administrator Handbuch.
    
    Beachten Sie, dass *delegateduser* ein neuer Parameter seit der letzten Vorschauversion des Unified-Bezeichnungs Clients ist und dass die API-Berechtigungen für die registrierte App folglich geändert wurden.

- Neue PowerShell-Bezeichnung für erweiterte Einstellungen, um [die zu schützenden Dateitypen zu ändern](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect).

- Neue PowerShell-Bezeichnung für erweiterte Einstellungen, um [die Regeln für die Bezeichnung Migration auf SharePoint-Eigenschaften auszuweiten](clientv2-admin-guide-customizations.md#extend-your-label-migration-rules-to-sharepoint-properties).

- Übereinstimmende benutzerdefinierte vertrauliche Informationstypen werden an [Azure Information Protection Analytics](../reports-aip.md)gesendet.

- Die angewendete Bezeichnung zeigt die konfigurierte Farbe für die Bezeichnung an, wenn eine [Farbe konfiguriert](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)wurde.

- Beim Hinzufügen oder Ändern von Schutzeinstellungen zu einer Bezeichnung wird die Bezeichnung vom Client erneut mit den neuesten Schutzeinstellungen angewendet, wenn das Dokument das nächste Mal gespeichert wird. Auf ähnliche Weise wendet der Scanner die Bezeichnung erneut mit diesen aktuellen Schutzeinstellungen an, wenn das Dokument im Erzwingungs Modus das nächste Mal gescannt wird.

- [Unterstützung für nicht verbundene Computer](clientv2-admin-guide-customizations.md#support-for-disconnected-computers) durch Exportieren von Dateien von einem Client und manuelles Kopieren der Computer auf den getrennten Computer. Beachten Sie, dass diese Konfiguration für die Bezeichnung mit dem Datei-Explorer, PowerShell und dem Scanner unterstützt wird. Diese Konfiguration wird für die Bezeichnung mit Office-Apps nicht unterstützt.

- Neues Cmdlet " [Export-aiplogs](https://docs.microsoft.com/powershell/module/azureinformationprotection/export-aiplogs)", um alle Protokolldateien aus "%LocalAppData%\microsoft\msip\logs" zu erfassen und Sie in einer einzelnen komprimierten Datei mit dem ZIP-Format zu speichern. Diese Datei kann dann an Microsoft-Support gesendet werden, wenn Sie zum Untersuchen eines gemeldeten Problems aufgefordert werden, Protokolldateien zu senden.

**Fixes**

- Sie können mit dem Datei-Explorer erfolgreich Änderungen an einer geschützten Datei vornehmen und mit der rechten Maustaste klicken, nachdem ein Kennwort für die Datei entfernt wurde.

- Sie können nativ geschützte Dateien im Viewer öffnen, ohne dass das [Nutzungsrecht](../configure-usage-rights.md#usage-rights-and-descriptions)"Speichern unter", "exportieren (exportieren)" erforderlich ist.

- Bezeichnungen und Richtlinien Einstellungen werden erwartungsgemäß aktualisiert, ohne dass " [Clear-aipauthentication](/powershell/module/azureinformationprotection/clear-aipauthentication?)" ausgeführt werden muss, oder Sie müssen den Ordner "%LocalAppData%\microsoft\msip\mip" manuell löschen.

**Weitere Änderungen**

- Wenn Sie [Einstellungen zurücksetzen](clientv2-admin-guide.md#more-information-about-the-reset-settings-option) , werden die\>Ordner%LocalAppData%\microsoft\msip\mip\\ *\<ProcessName. exe* anstelle von%LocalAppData%\microsoft\msip\mip\\ *\<ProcessName\>* \mip gelöscht. Pfalz.

- " [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) " enthält jetzt die Inhalts-ID für ein geschütztes Dokument.

## <a name="version-22210"></a>Version 2.2.21.0

**Veröffentlicht**: 09/03/2020

Unterstützt durch 04/23/2020

**Fixes**

- Wenn Sie die erweiterte Einstellung [outlookdefaultlabel](clientv2-admin-guide-customizations.md#set-a-different-default-label-for-outlook) verwenden, um eine andere Standard Bezeichnung für Outlook festzulegen, und die angegebene Bezeichnung keine Unterbezeichnungen für die Bezeichnungs Richtlinie hat, wird die Bezeichnung ordnungsgemäß angewendet.

- Wenn der Azure Information Protection-Client in einer Office-App verwendet wird, wird ein Benutzer mit einem Active Directory Konto, das nicht für Single Sign-On konfiguriert ist, aufgefordert, sich für Azure Information Protection zu authentifizieren. Nach der erfolgreichen Authentifizierung wird der Client Status ordnungsgemäß in Online geändert, wodurch Bezeichnungs Funktionen aktiviert werden.

## <a name="version-22190"></a>Version 2.2.19.0

**Veröffentlicht**: 08/06/2019

Unterstützt durch 03/03/2020

**Fixes**

- Der Client kann seine Richtlinie herunterladen und die aktuellen Vertraulichkeits Bezeichnungen anzeigen. Diese Korrektur ist nach dem Upgrade von einer früheren Version erforderlich, und Sie haben keine benutzerdefinierten Informationstypen in Ihrem Beschriftungs Center konfiguriert.

- Allgemeine Verbesserungen der Leistung und Stabilität.

## <a name="version-22140"></a>Version 2.2.14.0

**Veröffentlicht**: 07/15/2019

Unterstützt durch 02/06/2020

**Neue Funktionen:**

- Unterstützung für [Erweiterte Einstellungen](clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mit PowerShell für die Security & Compliance Center konfigurieren.
    
    Diese erweiterten Einstellungen unterstützen die folgenden Anpassungen:
     - [Information Protection-Leiste in Office-Apps anzeigen](clientv2-admin-guide-customizations.md#display-the-information-protection-bar-in-office-apps)
    - [Ausschließen von Outlook-Nachrichten von der obligatorischen Bezeichnung](clientv2-admin-guide-customizations.md#exempt-outlook-messages-from-mandatory-labeling)
    - [Die empfohlene Klassifizierung in Outlook aktivieren](clientv2-admin-guide-customizations.md#enable-recommended-classification-in-outlook)
    - [Festlegen einer anderen Standardbezeichnung für Outlook](clientv2-admin-guide-customizations.md#set-a-different-default-label-for-outlook)
    - [Deaktivieren der Option „Nicht jetzt“ für Dokumente bei Verwendung der obligatorischen Bezeichnung](clientv2-admin-guide-customizations.md#remove-not-now-for-documents-when-you-use-mandatory-labeling)
    - [Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen](clientv2-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)
    - [Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer](clientv2-admin-guide-customizations.md#disable-custom-permissions-in-file-explorer)
    - [Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien](clientv2-admin-guide-customizations.md#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer)
    - [Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](clientv2-admin-guide-customizations.md#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
    - [Add "Report an Issue" for users](clientv2-admin-guide-customizations.md#add-report-an-issue-for-users) ("Problem melden" für Benutzer hinzufügen)
    - [Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](clientv2-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
    - [Hiermit wird das Senden von ermittelten sensiblen Informationen in Dokumenten an Azure Information Protection Analytics deaktiviert.](clientv2-admin-guide-customizations.md#disable-sending-discovered-sensitive-information-in-documents-to-azure-information-protection-analytics)
    - [Senden von Informationstypen Übereinstimmungen an Azure Information Protection Analytics](clientv2-admin-guide-customizations.md#send-information-type-matches-to-azure-information-protection-analytics)
    - [Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](clientv2-admin-guide-customizations.md#migrate-labels-from-secure-islands-and-other-labeling-solutions)
    - [Anwenden einer benutzerdefinierten Eigenschaft, wenn eine Bezeichnung angewendet wird](clientv2-admin-guide-customizations.md#apply-a-custom-property-when-a-label-is-applied)
    - [Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](clientv2-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)
    - [Festlegen einer Standard untergeordneten Bezeichnung für eine übergeordnete Bezeichnung](clientv2-admin-guide-customizations.md#specify-a-default-sublabel-for-a-parent-label)
    - [Farbe für die Bezeichnung angeben](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)

- Unterstützung für Bezeichnungen, die für benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer konfiguriert sind. Weitere Informationen finden Sie im Abschnitt [erlauben Sie Benutzern das Zuweisen von Berechtigungen](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions) in der Office-Dokumentation.

- PowerShell-Änderungen im azureinformationprotection-Modul:
    - Neues Cmdlet: [New-aipcustomberechti-](/powershell/module/azureinformationprotection/New-AIPCustomPermissions) ersetzt New-rmsprotectionlicense zum Erstellen einer Ad-hoc-Richtlinie für benutzerdefinierte Berechtigungen
    - Neue Parameter:
        -  " *Custom-Berechtigungen* " und " *removeprotection* ": " [Set-aipfilelabel](/powershell/module/azureinformationprotection/Set-AIPFileLabel) " hinzugefügt
        -  " *Onbehalfof* ": " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication)" wurde hinzugefügt und anstelle des *tokenparameters* für nicht interaktive Sitzungen verwendet.
        -  " *WhatIf* " und " *discoveryinfotypes* ": " [Set-aipfileclassification](/powershell/module/azureinformationprotection/set-aipfileclassification)" wurde hinzugefügt, sodass dieses Cmdlet im Ermittlungs Modus ohne Anwenden von Bezeichnungen ausgeführt werden kann.
    - Als veraltet markierte Cmdlets, die eine direkte Verbindung mit einem Schutzdienst herstellen: Clear-rmsauthentication, Get-rmsfilestatus, Get-rmsserver, Get-rmsserverauthentication, Get-RMSTemplate, Protect-rmsfile, Set-rmsserverauthentication, Unprotect-rmsfile


**Fixes**

- Unterstützung für [Inhalts Übereinstimmungen](../reports-aip.md#content-matches-for-deeper-analysis) für Analytics und [Set-aipfileclassification](https://docs.microsoft.com/powershell/module/azureinformationprotection/set-aipfileclassification?view=azureipps) mit dem *discoveryinfotypes* -Parameter.

- Nachdem Sie zu einem alternativen Gebiets Schema in Windows gewechselt haben, können Sie trotzdem eine Bezeichnung mit Schutz auf ein PDF-Dokument anwenden.

- Wenn eine Bezeichnung aus dem Inhalt entfernt wird, wird der Schutz auch nur dann entfernt, wenn er als Teil der Bezeichnung konfiguriert wurde. Wenn der Schutz unabhängig von der Bezeichnung angewendet wurde, wird dieser Schutz beibehalten. Ein Benutzer hat z. b. benutzerdefinierte Berechtigungen auf eine Datei angewendet.

- Wenn die automatische Bezeichnung konfiguriert ist, wird die Bezeichnung beim ersten Speichern eines Dokuments angewendet.

- Die Standard Bezeichnung unterstützt untergeordnete Bezeichnungen.

## <a name="version-207790"></a>Version 2.0.779.0

**Veröffentlicht**: 05/01/2019

Unterstützt durch 02/15/2020

Diese Version bietet eine einzige Lösung zum Beheben eines racebedingungs Problems, bei dem manchmal keine Bezeichnungen in Office-Apps oder im Datei-Explorer angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Nicht sicher, ob dies der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen des zu verwendenden Kunden für Windows-Computer](use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

Weitere Informationen zum Installieren und verwenden dieses Clients finden Sie unter: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection Unified-Bezeichnung Client Administrator Handbuch](clientv2-admin-guide.md)

