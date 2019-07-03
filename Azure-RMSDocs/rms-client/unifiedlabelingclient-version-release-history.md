---
title: Azure Information Protection – einheitliche bezeichnungs-Client – Verlauf und Support-Richtlinie für Anwendungsversion
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: maayan
ms.suite: ems
ms.openlocfilehash: 1e59e864c86ded6433e5edd89748cd794a3d6410
ms.sourcegitcommit: a2542aec8cd2bf96e94923740bf396badff36b6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67535174"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection unified - Clientversion Bezeichnung Versionsgeschichte und Supportrichtlinie

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


Sie können den einheitlichen Azure Information Protection-Bezeichnung-Client aus der [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Nach einer kurzen Verzögerung von in der Regel ein paar Wochen, ist die neueste allgemein verfügbare Version auch im Microsoft Update-Katalogs mit dem Produktnamen enthalten **Microsoft Azure Information Protection**  >  **Microsoft Azure Information Protection Unified Bezeichnung-Client**, und die Klassifizierung der **Updates**. Diese Aufnahme in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Softwarebereitstellungsmechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [aktualisieren und Verwalten von Azure Information Protection unified bezeichnungs Client](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version der allgemein verfügbar (GA) des Azure Information Protection unified bezeichnungs-Clients wird für bis zu sechs Monate nach der Veröffentlichung von der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

> [!NOTE]
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

### <a name="release-information"></a>Informationen zum Release

Verwenden Sie die folgende Informationen, um anzuzeigen, was für die allgemein verfügbare Version des Azure Information Protection unified bezeichnungs-Clients unterstützt wird.

Dieser Client installiert ein Office-Add-On für Windows-Computer, eine Erweiterung für den Datei-Explorer und ein PowerShell-Modul. Es gelten die gleichen [Voraussetzungen](../requirements.md) wie für den Azure Information Protection-Client, der Richtlinien aus Azure herunterlädt.

Um Features und Funktionen, mit dem Azure Information Protection-Client vergleichen zu können, finden Sie unter [vergleichen Sie die Clients](use-client.md#compare-the-clients).

## <a name="versions-later-than-207790"></a>Höhere Versionen als 2.0.779.0

**Veröffentlicht**: 06/20/2019

Wenn Sie eine Version 2 des Clients, die nach 2.0.779.0 liegt verfügen, ist es sich um einen vorschaubuild für Test-und Evaluierungszwecke. 

**Neue Funktionen:**

- Unterstützung für [Erweiterte Einstellungen](clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie für Security & Compliance Center mit PowerShell konfigurieren.
    
    Diese erweiterte Einstellungen unterstützen die folgenden Anpassungen:
     - [Information Protection-Leiste in Office-Apps anzeigen](clientv2-admin-guide-customizations.md#display-the-information-protection-bar-in-office-apps)
    - [Die empfohlene Klassifizierung in Outlook aktivieren](clientv2-admin-guide-customizations.md#enable-recommended-classification-in-outlook)
    - [Festlegen einer anderen Standardbezeichnung für Outlook](clientv2-admin-guide-customizations.md#set-a-different-default-label-for-outlook)
    - [Deaktivieren der Option „Nicht jetzt“ für Dokumente bei Verwendung der obligatorischen Bezeichnung](clientv2-admin-guide-customizations.md#remove-not-now-for-documents-when-you-use-mandatory-labeling)
    - [Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen](clientv2-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)
    - [Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer](clientv2-admin-guide-customizations.md#disable-custom-permissions-in-file-explorer)
    - [Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien](clientv2-admin-guide-customizations.md#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer)
    - [Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](clientv2-admin-guide-customizations.md#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
    - [Add "Report an Issue" for users](clientv2-admin-guide-customizations.md#add-report-an-issue-for-users) ("Problem melden" für Benutzer hinzufügen)
    - [Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](clientv2-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
    - [Deaktiviert das Senden von ermittelten vertraulichen Informationen in Dokumenten mit Azure Information Protection-analytics](clientv2-admin-guide-customizations.md#disable-sending-discovered-sensitive-information-in-documents-to-azure-information-protection-analytics)
    - [Deaktivieren der Übereinstimmungen des Sendeinformationstyps für eine Teilmenge von Benutzern](clientv2-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users)
    - [Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](clientv2-admin-guide-customizations.md#migrate-labels-from-secure-islands-and-other-labeling-solutions)
    - [Wenden Sie eine benutzerdefinierte Eigenschaft an, wenn eine Bezeichnung angewendet wird](clientv2-admin-guide-customizations.md#apply-a-custom-property-when-a-label-is-applied)
    - [Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](clientv2-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)
    - [Geben Sie eine standardmäßige untergeordnete Bezeichnung für eine übergeordnete Bezeichnung](clientv2-admin-guide-customizations.md#specify-a-default-sublabel-for-a-parent-label)
    - [Geben Sie eine Farbe für die Bezeichnung](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)

- Unterstützung für Bezeichnungen, die für benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint und Datei-Explorer konfiguriert sind:
    - Wenn Sie Bezeichnungen mit dieser Konfiguration über das Azure-Portal haben, werden sie jetzt durch die einheitliche bezeichnungs-Client unterstützt, aber es derzeit keine entsprechende Konfiguration in das Admin Center gibt.
    - Wenn ein Benutzer eine Bezeichnung mit dieser Konfiguration auswählt, werden sie aufgefordert, Benutzer und die schutzeinstellungen für das Dokument auswählen.

- PowerShell-Änderungen in das Modul "azureinformationprotection":
    - Neues Cmdlet: [New-AIPCustomPermissions](/powershell/module/azureinformationprotection/New-AIPCustomPermissions) -New-RMSProtectionLicense zum Erstellen einer Ad-hoc-Richtlinie für benutzerdefinierte Berechtigungen ersetzt
    - Neue Parameter:
        -  *CustomPermissions* und *RemoveProtection* – hinzugefügt [Set-AIPFileLabel](/powershell/module/azureinformationprotection/Set-AIPFileLabel)
        -  *"Onbehalfof"* – hinzugefügt [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), um anstelle von verwendet werden die *Token* -Parameter für nicht interaktive Sitzungen
        -  *"WhatIf"* und *DiscoveryInfoTypes* – hinzugefügt [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification), damit dieses Cmdlet im Suchmodus ausführen kann, ohne das Anwenden von Bezeichnern
    - Veralteten Cmdlets: Clear-RMSAuthentication, Get-RMSFileStatus, Get-RMSServer, Get-RMSServerAuthentication, Get-RMSTemplate, Protect-RMSFile, Set-RMSServerAuthentication, Unprotect-RMSFile


**Behoben:**

- Wenn die automatische Kennzeichnung konfiguriert ist, wendet die Bezeichnung beim ersten ein Dokument gespeichert wird.

- Standardmäßig bezeichnungs-unterstützt über untergeordnete Bezeichnungen.

## <a name="version-207790"></a>Version 2.0.779.0

**Veröffentlicht**: 05/01/2019

Diese Version enthält eine einzelne Lösung für die ein Race-Bedingung-Problem zu beheben, in denen in einigen Fällen keine Bezeichnungen in Office-apps oder Datei-Explorer angezeigt.

## <a name="version-207780"></a>Version 2.0.778.0

**Veröffentlicht**: 04/16/2019

Unterstützt über 11/01/2019

Diese erste allgemein verfügbare Version des Azure Information Protection unified bezeichnungs-Clients für Windows unterstützt die folgenden Features: 

- Upgrade vom Azure Information Protection-Client.

- Manuelle, automatische und empfohlene Klassifizierung: Weitere Informationen zur Konfiguration der automatischen und empfohlenen Klassifizierung für diesen Client finden Sie unter [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf den Inhalt](/Office365/SecurityCompliance/apply-sensitivity-label-automatically).

- Datei-Explorer, Rechtsklickaktionen zum Klassifizieren und Schützen von Dateien, Entfernen des Schutzes und Anwenden von benutzerdefinierten Berechtigungen.

- Ein Viewer für geschützten Text und geschützte Bilddateien, geschützte PDF-Dateien und Dateien die generisch geschützt werden.

- PowerShell-Befehle für Folgendes:
    - [Festlegen oder Entfernen einer Bezeichnung in einem Dokument](/powershell/module/azureinformationprotection/set-aipfilelabel)
    - [Hinzufügen einer Bezeichnung zu einem Dokument nach Untersuchen des Inhalts](/powershell/module/azureinformationprotection/set-aipfileclassification)
    - [Lesen von Informationen zu einer auf ein Dokument angewendeten Bezeichnung](/powershell/module/azureinformationprotection/get-aipfilestatus)
    - [Authentifizieren der Unterstützung unbeaufsichtigter PowerShell-Sitzungen](/powershell/module/azureinformationprotection/set-aipauthentication)

- Überwachung von Daten und der Endpunkt-Discovery-Unterstützung für die zentrale Berichterstattung mithilfe [Analytics für Azure Information Protection](../reports-aip.md).

- Folgende Einstellungen für Bezeichnungen und Richtlinien:
    - Optische Kennzeichnung (Kopfzeile, Fußzeile und Wasserzeichen)
    - Standard-Bezeichnungen – aktuell eingeschränkt auf Bezeichnungen ohne untergeordnete Bezeichnungen
    - Bezeichnungen, die „Nicht weiterleiten“ anwenden und nur in Outlook angezeigt werden
    - Aufforderung zur Angabe einer Begründung, wenn ein Benutzer eine Klassifizierungsstufe senkt oder eine Bezeichnung entfernt
    - Farben für die Bezeichnungen

- Aktualisieren der Richtlinie über die Admin Center:
    - Bei jedem Start einer Office-App und alle vier Stunden
    - Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen
    - Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz

- Die Dialogfelder „Hilfe“ und „Feedback“, die Einstellungen zum Zurücksetzen und Exportprotokolle umfassen.


## <a name="next-steps"></a>Nächste Schritte

Ausführliche Informationen finden Sie in den [Vergleichstabellen](use-client.md#compare-the-clients).

Weitere Informationen zum Installieren und verwenden dieses Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection – einheitliche bezeichnungs Client – Administratorhandbuch](clientv2-admin-guide.md)

