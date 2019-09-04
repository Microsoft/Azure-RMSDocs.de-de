---
title: Azure Information Protection vereinheitlichte Bezeichnung für den Client Versionsverlauf & Unterstützungs Richtlinie
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 614435c39458462449f71955215e9e6adef06754
ms.sourcegitcommit: 8cd708f3f45d3f49d0c84fc56fec9c7bdcd08ba7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70214098"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection Unified Bezeichnungs Verlauf des Client Versions Verlaufs und der Support Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Unified Bezeichnung-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


Sie können den Azure Information Protection Unified Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen.

Nach einer kurzen Verzögerung von in der Regel einige Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog mit dem Produktnamen **Microsoft Azure Information Protection** > **Microsoft Azure Informationen enthalten. Schutz einheitlicher**Bezeichnungs Client und die Klassifizierung von **Updates**. Diese Aufnahme in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Softwarebereitstellungsmechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [aktualisieren und Verwalten des Azure Information Protection Unified Bezeichnung-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede allgemein verfügbare Version des Azure Information Protection Unified Bezeichnung-Clients wird bis zu sechs Monate nach der Veröffentlichung der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

> [!NOTE]
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

### <a name="release-information"></a>Informationen zum Release

Verwenden Sie die folgenden Informationen, um zu erfahren, was für eine unterstützte Version des Azure Information Protection Unified Bezeichnung-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn Sie also ein Problem mit dem Unified-Bezeichnungs Client haben, sollten Sie überprüfen, ob es mit der neuesten GA-Version behoben wurde. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

Dieser Client ersetzt den Azure Information Protection Client (klassisch). Informationen zum Vergleichen von Features und Funktionen mit dem klassischen Client finden Sie unter [vergleichen der Clients](use-client.md#compare-the-clients).

## <a name="version-22210"></a>Version 2.2.21.0

**Veröffentlicht**: 09/03/2019

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
    - [Deaktivieren der Übereinstimmungen des Sendeinformationstyps für eine Teilmenge von Benutzern](clientv2-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users)
    - [Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](clientv2-admin-guide-customizations.md#migrate-labels-from-secure-islands-and-other-labeling-solutions)
    - [Anwenden einer benutzerdefinierten Eigenschaft, wenn eine Bezeichnung angewendet wird](clientv2-admin-guide-customizations.md#apply-a-custom-property-when-a-label-is-applied)
    - [Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](clientv2-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)
    - [Festlegen einer Standard untergeordneten Bezeichnung für eine übergeordnete Bezeichnung](clientv2-admin-guide-customizations.md#specify-a-default-sublabel-for-a-parent-label)
    - [Farbe für die Bezeichnung angeben](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)

- Unterstützung für Bezeichnungen, die für benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer konfiguriert sind:
    - Wenn Sie über Bezeichnungen mit dieser Konfiguration aus dem Azure-Portal verfügen, werden Sie jetzt vom Unified Label-Client unterstützt, obwohl derzeit keine äquivalente Konfiguration in den Admin Centers vorhanden ist.
    - Wenn ein Benutzer eine Bezeichnung mit dieser Konfiguration auswählt, wird er aufgefordert, Benutzer und Schutzeinstellungen für das Dokument auszuwählen.

- PowerShell-Änderungen im azureinformationprotection-Modul:
    - Neues Cmdlet: [New-aipcustomberechti-](/powershell/module/azureinformationprotection/New-AIPCustomPermissions) ersetzt New-rmsprotectionlicense zum Erstellen einer Ad-hoc-Richtlinie für benutzerdefinierte Berechtigungen.
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

## <a name="version-207780"></a>Version 2.0.778.0

**Veröffentlicht**: 04/16/2019

Unterstützt durch 11/01/2019

Diese erste Version der allgemeinen Verfügbarkeit des Azure Information Protection Unified Bezeichnung-Clients für Windows unterstützt die folgenden Features: 

- Upgrade vom Azure Information Protection-Client.

- Manuelle, automatische und empfohlene Klassifizierung: Weitere Informationen zur Konfiguration der automatischen und empfohlenen Klassifizierung für diesen Client finden Sie unter [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf den Inhalt](/Office365/SecurityCompliance/apply-sensitivity-label-automatically).

- Datei-Explorer, Rechtsklickaktionen zum Klassifizieren und Schützen von Dateien, Entfernen des Schutzes und Anwenden von benutzerdefinierten Berechtigungen.

- Ein Viewer für geschützten Text und geschützte Bilddateien, geschützte PDF-Dateien und Dateien die generisch geschützt werden.

- PowerShell-Befehle für Folgendes:
    - [Festlegen oder Entfernen einer Bezeichnung in einem Dokument](/powershell/module/azureinformationprotection/set-aipfilelabel)
    - [Hinzufügen einer Bezeichnung zu einem Dokument nach Untersuchen des Inhalts](/powershell/module/azureinformationprotection/set-aipfileclassification)
    - [Lesen von Informationen zu einer auf ein Dokument angewendeten Bezeichnung](/powershell/module/azureinformationprotection/get-aipfilestatus)
    - [Authentifizieren der Unterstützung unbeaufsichtigter PowerShell-Sitzungen](/powershell/module/azureinformationprotection/set-aipauthentication)

- Überwachen von Daten und Endpunkt Ermittlungs Unterstützung für Zentrale Berichterstellung mithilfe von [Azure Information Protection Analytics](../reports-aip.md).

- Folgende Einstellungen für Bezeichnungen und Richtlinien:
    - Optische Kennzeichnung (Kopfzeile, Fußzeile und Wasserzeichen)
    - Standard Bezeichnung: derzeit beschränkt auf Bezeichnungen ohne untergeordnete Bezeichnungen
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

Weitere Informationen zum Installieren und verwenden dieses Clients finden Sie unter: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection Unified Bezeichnung-Client Administrator Handbuch](clientv2-admin-guide.md)

