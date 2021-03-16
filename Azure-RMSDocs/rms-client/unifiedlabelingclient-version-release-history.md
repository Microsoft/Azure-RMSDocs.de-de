---
title: 'Neues in Azure Information Protection (AIP): Versionsverlauf & Unterstützungs Richtlinie'
description: Hier finden Sie Informationen zu den Neuerungen beim Unified-Bezeichnung-Client (Azure Information Protection) für Windows.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/07/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: cf639e1a0e8b68ed58aadb2404c15fd385320bcb
ms.sourcegitcommit: 99f1a1ab40eea7802e6c4f98724958409ee779ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2021
ms.locfileid: "103558140"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection Unified Bezeichnungs Verlauf des Client Versions Verlaufs und der Support Richtlinie

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen unter [AIP und ältere Windows-und Office-Versionen](../known-issues.md#aip-and-legacy-windows-and-office-versions).*
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie [unter AIP Classic Client Version Release History und Support Policy](client-version-release-history.md). *

Dieser Artikel beschreibt die neuen Features, die für den Unified-Bezeichnungs Client verfügbar sind, sowie Wartungsinformationen und Support Zeitpläne für jede einheitliche AIP-Client Version.

Sie können den Azure Information Protection Unified Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunterladen.

Nach einer kurzen Verzögerung von normalerweise vier Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog enthalten. Azure Information Protection Versionen haben den Produktnamen **Microsoft Azure Information Protection**  >  **Microsoft Azure Information Protection Unified**-Bezeichnungs Client und eine Klassifizierung von **Updates**.

Das Einschließen von Azure Information Protection in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Software Bereitstellungs Mechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [aktualisieren und Verwalten des Azure Information Protection Unified Bezeichnung-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

## <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede allgemein verfügbare Version des Azure Information Protection Unified Bezeichnung-Clients wird bis zu sechs Monate nach der Veröffentlichung der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden

|Clientversion|Datum der Veröffentlichung|
|--------------|-------------|
| 2.7.96  |01/20/2021 |
|2.6.111.0 | 03/09/2020|
|2.5.33.0 |23.10.2019|
|2.2.21.0|09/03/2019|
|2.2.19.0|08/06/2019|
|2.2.14.0|07/15/2019|
|2.0.779.0|05/01/2019|
|2.0.778.0|04/16/2019|
| | |

Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

### <a name="release-information"></a>Informationen zum Release

Verwenden Sie die folgenden Informationen, um zu erfahren, was für eine unterstützte Version des Azure Information Protection Unified Bezeichnung-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

Beachten Sie, Azure Information Protection Features derzeit in der Vorschau Phase sind. Die [ergänzenden Bestimmungen für Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) enthalten zusätzliche rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden bzw. anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind.

> [!NOTE]
> Kleinere Fehlerbehebungen sind nicht immer aufgeführt. Wenn Sie also ein Problem mit dem Unified-Bezeichnungs Client haben, sollten Sie überprüfen, ob es mit der neuesten GA-Version behoben wurde. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

Der Unified-Bezeichnungs Client ersetzt den Azure Information Protection klassischen Client. Informationen zum Vergleichen von Features und Funktionen mit dem klassischen Client finden Sie unter [vergleichen der Beschriftungslösungen für Windows-Computer](use-client.md#compare-the-labeling-solutions-for-windows-computers).

## <a name="version-210460-for-co-authoring-public-preview"></a>Version 2.10.46.0 für die gemeinsamen Erstellung (Public Preview)

Vereinheitlichte Bezeichnung Client Version 2.10.46.0

**Release** 03/02/2021

Diese dedizierte Version von Azure Information Protection bietet eine öffentliche Vorschau der in Microsoft 365 neu unterstützten Funktionen für die gemeinsamen Dokument Erstellung.

Die gemeinsamen Erstellung von Office-Apps ermöglicht mehreren Benutzern das Bearbeiten von Dokumenten, die durch [Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels)gekennzeichnet und verschlüsselt sind.

> [!IMPORTANT]
> Um die Funktionen zur gemeinsamen Erstellung in der öffentlichen Vorschau zu nutzen, müssen Sie die dedizierte Installationsdatei für diese Version herunterladen und installieren. Laden Sie die Datei auf der [Microsoft-Download Website](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunter, und installieren Sie Sie `AzInfoProtection_2.10.46_CoAuthoring_PublicPreview.exe`  .
>
> Ihr System muss außerdem die Versions Anforderungen erfüllen, die in den [Microsoft 365 Voraussetzungen für die gemeinsamen Erstellung](/microsoft-365/compliance/sensitivity-labels-coauthoring#prerequisites)aufgeführt sind.
>

Bevor Sie beginnen, sollten Sie alle zugehörigen Voraussetzungen und Einschränkungen überprüfen. Weitere Informationen finden Sie unter

- [Aktivieren der gemeinsamen Erstellung von Dateien, die mit Vertraulichkeits Bezeichnungen verschlüsselt](/microsoft-365/compliance/sensitivity-labels-coauthoring) sind, in der Microsoft 365-Dokumentation.
- [Bekannte Probleme bei der Co-Erstellung in aip](../known-issues.md#known-issues-for-co-authoring-public-preview)
## <a name="version-210430-for-dlp-policies-public-preview"></a>Version 2.10.43.0 für DLP-Richtlinien (öffentliche Vorschau)

Unified Bezeichnung Scanner-Version 2.10.43.0

**Release** 03/02/2021

Diese dedizierte Version von Azure Information Protection bietet eine öffentliche Vorschau der Unterstützung von Richtlinien zur Verhinderung von Datenverlust (DLP), die von Microsoft 365 unterstützt werden. 

- Die **Verwendung einer DLP-Richtlinie** ermöglicht es dem Scanner, potenzielle Datenverluste zu erkennen, indem er DLP-Regeln mit in Dateifreigaben und SharePoint Server gespeicherten Dateien abschließt. 

- [**Aktivieren Sie DLP-Regeln im Inhalts Überprüfungs Auftrag**](../deploy-aip-scanner-configure-install.md#use-a-dlp-policy-public-preview) , um das verfügbar machen von Dateien zu verringern, die ihren DLP-Richtlinien entsprechen. 

    Der Scanner kann den Dateizugriff nur auf Daten Besitzer reduzieren oder die Gefährdung von Netzwerk weiten Gruppen, wie z. b. **allen** **Benutzern, authentifizierten Benutzern** oder **Domänen Benutzern**, verringern.

- **Durch das Scannen von Dateien mit aktivierten DLP-Regeln werden auch Datei Berechtigungs Berichte erstellt**. Fragen Sie diese Berichte ab, um bestimmte Dateiinformationen zu untersuchen, oder untersuchen Sie die verfügbar machung eines bestimmten Benutzers für überprüfte Dateien

Einstellungen zum erzwingen oder Testen der DLP-Richtlinie werden im [Microsoft 365 Compliance Center](/microsoft-365/compliance/create-test-tune-dlp-policy#turn-on-a-dlp-policy)konfiguriert.

> [!IMPORTANT]
> Um die DLP-Unterstützung in der öffentlichen Vorschau zu nutzen, müssen Sie die dedizierte Installationsdatei für diese Version herunterladen und installieren. Laden Sie die Datei auf der [Microsoft-Download Website](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunter, und installieren Sie Sie `AzInfoProtection_2.10.43_DLP_PublicPreview.exe` .
> 
Weitere Informationen, einschließlich Lizenzierungsanforderungen, finden Sie unter:

- [Konfigurieren einer DLP-Richtlinie im AIP-Scanner](../deploy-aip-scanner-configure-install.md#use-a-dlp-policy-public-preview)
- Informieren Sie sich in der Microsoft 365 Dokumentation [über die Microsoft 365 Verhinderung von Datenverlusten vor Ort](/microsoft-365/compliance/dlp-on-premises-scanner-learn).
- [Beginnen Sie mit dem lokalen Scanner für die Verhinderung von Datenverlust](/microsoft-365/compliance/dlp-on-premises-scanner-get-started)
- [Verwenden des Microsoft 365 für die Verhinderung von Datenverlust vor Ort](/microsoft-365/compliance/dlp-on-premises-scanner-use)



## <a name="version-29116"></a>Version 2.9.116 

Unified-Beschriftungs Scanner und Client Version 2.9.116 

**Veröffentlicht** 02/08/2021

**Behobene Probleme** Benutzer können nun geschützte Dateien wie erwartet in den folgenden Szenarios anzeigen:

- Wenn geschützte Dateien für Benutzer freigegeben werden, die nicht über eine konfigurierte AIP-Richtlinie verfügen, z. b. externe Benutzer. Dieses Problem trat nur bei der [AIP Viewer-App](clientv2-view-use-files.md)auf.

- Wenn Inhalte mit einer Bereichs bezogenen Bezeichnung für Benutzer oder Gruppen freigegeben werden, die nicht im Bereich der Bezeichnung enthalten sind. Dieses Problem trat sowohl bei der [AIP Viewer-App](clientv2-view-use-files.md) als auch beim Anzeigen oder Klassifizierern des freigegebenen Inhalts über den [Datei-Explorer](clientv2-classify-protect.md#using-file-explorer-to-classify-and-protect-files)auf.

Weitere Informationen finden Sie im [Benutzerhandbuch zum AIP Unified Bezeichnung-Client](clientv2-user-guide.md).
## <a name="version-291110"></a>Version 2.9.111.0

Unified-Beschriftungs Scanner und Client Version 2.9.111.0

**Veröffentlicht** 01/13/2021

**Unterstützt durch** 08/08/2021

Diese Version enthält die folgenden neuen Features, Fehlerbehebungen und Verbesserungen für den Unified-Beschriftungs Scanner und-Client:

- **Neue Features für den Scanner**:

    - [PowerShell-Unterstützung für nicht verbundene Scanner-Server](#powershell-support-for-disconnected-scanner-servers)
    - [Unterstützung für NFS-Depots in Inhalts Scan Aufträgen](#support-for-nfs-repositories-in-content-scan-jobs-public-preview) (Public Preview)
    - [Unterstützung für zusätzliche Typen sensibler Informationen hinzugefügt](#added-support-for-additional-sensitive-information-types)

- **Neue Features für den-Client**:

    - Überprüfen des [Dokument Zugriffs und widerrufen des Zugriffs](#track-document-access-and-revoke-access-public-preview) (öffentliche Vorschau)
    - [Unterstützung für zusätzliche Typen sensibler Informationen hinzugefügt](#added-support-for-additional-sensitive-information-types)

- **Korrekturen und Verbesserungen**:

    - [Korrekturen und Verbesserungen für den Unified-Beschriftungs Scanner](#fixes-and-improvements-for-the-unified-labeling-scanner)
    - [Korrekturen und Verbesserungen für den Unified-Bezeichnungs Client](#fixes-and-improvements-for-the-unified-labeling-client)

- **Bekanntes Problem**: in der neuesten GA-Version (2.9.111) wurde ein Problem identifiziert, bei dem einige Benutzer geschützte Dateien in den folgenden Szenarien nicht anzeigen konnten:

    - Wenn geschützte Dateien für Benutzer freigegeben werden, die nicht über eine konfigurierte AIP-Richtlinie verfügen, z. b. externe Benutzer. Dieses Problem tritt nur bei der [AIP Viewer-App](clientv2-view-use-files.md)auf.

    - Wenn Inhalte mit einer Bereichs bezogenen Bezeichnung für Benutzer oder Gruppen freigegeben werden, die nicht im Bereich der Bezeichnung enthalten sind. Dieses Problem tritt sowohl bei der [AIP Viewer-App](clientv2-view-use-files.md) als auch beim Anzeigen oder klassifiziert des freigegebenen Inhalts über den [Datei-Explorer](clientv2-classify-protect.md#using-file-explorer-to-classify-and-protect-files)auf.

### <a name="powershell-support-for-disconnected-scanner-servers"></a>PowerShell-Unterstützung für nicht verbundene Scanner-Server

Der [Azure Information Protection lokale Scanner](../deploy-aip-scanner.md) unterstützt jetzt die Verwaltung von Inhalts Überprüfungs Aufträgen über PowerShell, für Scanner-Server, die keine Verbindung mit dem Internet herstellen können, oder für Scanner in einer [Azure China 21ViaNet-Umgebung (China Sovereign Cloud)](/microsoft-365/admin/services-in-china/parity-between-azure-information-protection#manage-azure-information-protection-content-scan-jobs).

Zur Unterstützung von getrennten oder Azure China 21ViaNet-Scanner-Servern wurden die folgenden neuen Cmdlets hinzugefügt:

|Cmdlet  |BESCHREIBUNG  |
|---------|---------|
|**[Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository)**     | Fügt ihrem inhaltscanauftrag ein neues Repository hinzu.        |
|**[Get-aipscannercontentscanjob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob)**     |      Ruft Details zum inhaltscanauftrag ab.   |
|**[Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository)**     |  Ruft Details zu den für Ihren inhaltscanauftrag definierten Depots ab.       |
|**[Remove-aipscannercontentscanjob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob)**       |    Löscht ihren inhaltscanauftrag.     |
| **[Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository)**    |   Entfernt ein Repository aus Ihrem inhaltscanauftrag.      |
|**[Set-aipscannercontentscanjob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob)**     |   Definiert Einstellungen für Ihren inhaltscanauftrag.      |
**[Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository)**     |   Definiert die Einstellungen für ein vorhandenes Repository in Ihrem inhaltscanauftrag.      |
| | |

Das Cmdlet " [**Set-mipnetworkdiscovery**](/powershell/module/azureinformationprotection/set-mipnetworkdiscovery) " wurde ebenfalls hinzugefügt, um zusätzliche Unterstützung zu bieten, sodass Sie die Installationseinstellungen für den Netzwerk Ermittlungsdienst über PowerShell aktualisieren können.

Weitere Informationen finden Sie unter [Wenn der Überprüfungs Server keine Internet Konnektivität haben kann](../deploy-aip-scanner-prereqs.md#restriction-the-scanner-server-cannot-have-internet-connectivity) und [den Scanner konfigurieren](../deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal).

### <a name="support-for-nfs-repositories-in-content-scan-jobs-public-preview"></a>Unterstützung für NFS-Depots in Inhalts Scan Aufträgen (Public Preview)

Nun können Sie Ihren Inhalts Überprüfungs Aufträgen zusätzlich zu SMB-Dateifreigaben und SharePoint-Depots NFS-Repository hinzufügen.

Dienste für NFS müssen auf dem Überprüfungs Computer bereitgestellt werden, um Scans für NFS-Freigaben zu unterstützen:

1. Navigieren Sie auf Ihrem Computer zum Dialogfeld "Einstellungen" (Windows-Funktionen ein- **oder ausschalten)** .

1. Wählen Sie die folgenden Elemente aus:

    - **Dienste für NFS**
        - **Verwaltungs Tools**
        - **Client für NFS**

Weitere Informationen finden Sie unter [Erstellen eines Inhalts Scan Auftrags](../deploy-aip-scanner-configure-install.md#create-a-content-scan-job).

### <a name="added-support-for-additional-sensitive-information-types"></a>Unterstützung für zusätzliche Typen sensibler Informationen hinzugefügt

Wir haben Unterstützung für zusätzliche vertrauliche Informationstypen in Azure Information Protection hinzugefügt, wie z. b. die **Geschäftsnummer von Australien**, die **australische Firmennummer** oder die **Personal** Ausweisnummer.

Weitere Informationen finden Sie in den [Entitäts Definitionen für sensible Informationen](/microsoft-365/compliance/sensitive-information-type-entity-definitions) in der Microsoft 365-Dokumentation.

### <a name="track-document-access-and-revoke-access-public-preview"></a>Überprüfen des Dokument Zugriffs und widerrufen des Zugriffs (öffentliche Vorschau)

Nachdem Sie ein Upgrade auf Version 2.9.111.0 durchgeführt haben, werden alle geschützten Dokumente, die noch nicht für die Nachverfolgung registriert sind, beim nächsten Öffnen auf einem Computer registriert, auf dem der AIP Unified-Bezeichnungs Client installiert ist. Geschützte Dokumente werden zum Nachverfolgen und widerrufen unterstützt, auch wenn Sie nicht als bezeichnet werden.

Wenn Sie Ihre Dokumente für die Überwachung registriert haben, können Administratoren PowerShell verwenden, um den Zugriff auf Dokumente zu verfolgen und bei Bedarf den Zugriff aufzuheben.

Nachdem Sie das Upgrade ausgeführt haben, können Endbenutzer auch den Zugriff für Dokumente widerrufen, die Sie geschützt haben. Verwenden Sie zum Widerrufen des Zugriffs von Microsoft Office-Apps die neue Option **Zugriff widerrufen** im Menü **Sensitivität** .

Weitere Informationen finden Sie unter

- [Administrator Handbuch: nachverfolgen und widerrufen des Dokumenten Zugriffs mit Azure Information Protection](track-and-revoke-admin.md)
- [Benutzerhandbuch: widerrufen des Dokument Zugriffs mit Azure Information Protection](revoke-access-user.md)
- [Bekannte Probleme beim Nachverfolgen und widerrufen des Zugriffs auf Dokumente](../known-issues.md#known-issues-for-track-and-revoke-features-public-preview)

Wenn Sie über Datenschutzanforderungen in Ihrer Organisation oder Region verfügen, in denen Sie die Funktionen zur dokumentenverfolgung deaktivieren müssen, finden Sie weitere Informationen unter nach [verfolgen und widerrufen von Administrator Verfahren](track-and-revoke-admin.md#turn-off-track-and-revoke-features-for-your-tenant).

**Upgrades vom klassischen Client**

Der klassische AIP-Client unterstützt das verfolgen und widerrufen von Features mithilfe des [Microsoft-Überwachungs Portals](client-track-revoke.md#using-a-web-browser-to-track-and-revoke-documents-that-you-have-registered). Dieses Überwachungs Portal ist bei der Arbeit mit dem Unified-Bezeichnungs Client nicht relevant.
 
Verwenden Sie die PowerShell-Befehle, um nach Verfolgungs Daten mit dem Unified-Bezeichnungs Client anzuzeigen, wie im [Administrator Handbuch](track-and-revoke-admin.md)beschrieben.

### <a name="fixes-and-improvements-for-the-unified-labeling-scanner"></a>Korrekturen und Verbesserungen für den Unified-Beschriftungs Scanner

Die folgenden Korrekturen wurden in Version 2.9.111.0 des [Azure Information Protection Unified-Beschriftungs Scanners](../deploy-aip-scanner.md)übermittelt:

- Unterstützung für Bindestriche ( **-** ) in [Scanner-Datenbanknamen](../deploy-aip-scanner-prereqs.md) hinzugefügt
- Updates in Berichten für den Fall, dass die Option " **[auf Inhalt basierende](../deploy-aip-scanner-configure-install.md#create-a-content-scan-job)** Bezeichnungs Dateien" auf **Off** festgelegt ist
- [Verbesserter Arbeitsspeicher Verbrauch](../deploy-aip-scanner-configure-install.md#optimize-scanner-performance) für eine große Anzahl von Informationstyp Übereinstimmungen
- Unterstützung für [lokale SharePoint-](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) Pfade, die mit einem Schrägstrich ( **/** ) enden
- Erweiterte SharePoint-Scan [Geschwindigkeit](../deploy-aip-scanner-configure-install.md#optimize-scanner-performance)
- Unterstützung für das [vermeiden eines Timeouts](clientv2-admin-guide-customizations.md#avoid-scanner-timeouts-in-sharepoint) beim Scannen eines SharePoint-Servers.

### <a name="fixes-and-improvements-for-the-unified-labeling-client"></a>Korrekturen und Verbesserungen für den Unified-Bezeichnungs Client

- Probleme, die für die [Bezeichnung in e-Mails](clientv2-admin-guide-customizations.md#extend-your-label-migration-rules-to-emails) von Office MSI behoben wurden, z. b. beim Antworten auf oder Weiterleiten einer e-Mail.

- [Newlabel Audit Log](../audit-logs.md#new-label-audit-logs) -Ereignisse enthalten nun die Aktions Quelle für Ereignisse, die von von Outlook gesendeten e-Mails generiert werden.

- Es wurden Probleme behoben, bei denen die Richtlinie manchmal nicht aktualisiert wurde, ohne den Cache zu löschen, nachdem die Bezeichnungs [Richtlinie in Microsoft 365 geändert](/microsoft-365/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy)wurde.

- Der Outlook-Vorschaumodus generiert nun Überwachungs [Protokolle für Ermittlungs Ereignisse](../audit-logs.md#discover-audit-logs) .

- [Empfohlene Bezeichnungen](/microsoft-365/compliance/sensitivity-labels#what-sensitivity-labels-can-do) und [visuelle Kennzeichnung](/microsoft-365/compliance/sensitivity-labels#what-sensitivity-labels-can-do) werden in Outlook erwartungsgemäß angewendet. 

- Unterstützung für das [Auffinden von Empfängern in Outlook-Verteilerlisten](clientv2-admin-guide-customizations.md#expand-outlook-distribution-lists-when-searching-for-email-recipients)hinzugefügt, z. b. wenn die Einstellungen [outlookblocktreuhänder](clientv2-admin-guide-customizations.md#to-exempt-domain-names-for-pop-up-messages-configured-for-specific-labels) und [outlookblockuntreudkollaborationlabel](clientv2-admin-guide-customizations.md#to-implement-the-warn-justify-or-block-pop-up-messages-for-specific-labels) konfiguriert sind.

    Wenn Sie diese Funktion aktivieren, wird empfohlen, dass Sie auch den Standard Timeout Wert erhöhen, wie in der [outlookgetemailadressssestimeoutmsproperty](clientv2-admin-guide-customizations.md#expand-outlook-distribution-lists-when-searching-for-email-recipients) -Einstellung definiert.

- Aktualisierungen der Rangfolge, die verwendet wird, wenn mehrere [Bezeichnungs](clientv2-admin-guide-customizations.md#order-of-precedence---how-conflicting-settings-are-resolved) Richtlinien für einen Benutzer konfiguriert sind, die jeweils in Konflikt stehende Erweiterte Einstellungen haben.

    In solchen Fällen werden die erweiterten Einstellungen der ersten Richtlinie immer entsprechend der Reihenfolge der Richtlinien im Admin Center angewendet. Die Ausnahme für " *outlookdefaultlabel* " wurde jetzt entfernt.

- In einem Szenario, in dem **% AppData% (appdata\roaming)** auf eine nicht standardmäßige Windows-Ordnerstruktur verweist, werden Dateien in Ordnern, die Benutzerverzeichnissen zugeordnet sind, jetzt wie erwartet [aus der Bezeichnung und dem Schutz ausgeschlossen](clientv2-admin-guide-file-types.md#file-types-excluded-from-classification-and-protection) , basierend auf der Konfiguration.

- [Neue erweiterte Client Einstellung](clientv2-admin-guide-customizations.md#remove-all-shapes-of-a-specific-shape-name) (**powerpointremuveallshapesbyshapename**), die zum Entfernen von Formen aus PowerPoint-Kopf-oder-Fußzeilen hinzugefügt wurde, indem der Form Name anstelle des Texts innerhalb einer Form verwendet wird.

## <a name="version-28850"></a>Version 2.8.85.0

Unified-Beschriftungs Scanner und Client Version 2.8.85.0

**Veröffentlicht** 09/22/2020

**Unterstützt durch** 7/13/2021

Diese Version enthält die folgenden neuen Features, Korrekturen und Verbesserungen für den Unified-Beschriftungs Scanner und-Client:

- **Neue Features für den Scanner**:

    - [Optionale vollständige neuänderungen für erkannte Änderungen](#optional-full-rescans-for-changes-detected)
    - [Konfigurieren von SharePoint-Timeouts](#configure-sharepoint-timeouts)
    - [Unterstützung der Netzwerk](#network-discovery-support-public-preview) Ermittlung (Public Preview)

- **Neue Features für den-Client**:

    - [Anpassungen von Administratoren für AIP-Popups in Outlook](#administrator-customizations-for-aip-popups-in-outlook)
    - [Administrator Anpassungen für entsprechende Eingabe Aufforderungen](#administrator-customizations-for-justification-prompts)
    - [Überwachungs Protokoll Updates](#audit-log-updates)
    - [Auf Vorlagen basierende DKE-Beschriftungs Updates](#dke-template-based-labeling-updates)

- **Korrekturen und Verbesserungen:**

    - [Korrekturen und Verbesserungen bei Scanner](#azure-information-protection-scanner-fixed-issues-version-28850)
    - [Client Korrekturen und-Verbesserungen](#azure-information-protection-client-fixed-issues-version-28850)


### <a name="optional-full-rescans-for-changes-detected"></a>Optionale vollständige neuänderungen für erkannte Änderungen

Administratoren können jetzt eine vollständige erneute Überprüfung überspringen, nachdem Sie Änderungen an Richtlinien oder Inhalts Scan Aufträgen vorgenommen haben. Wenn Sie einen vollständigen erneuten Scan überspringen, werden die Änderungen nur auf Dateien angewendet, die seit der letzten Überprüfung geändert oder erstellt wurden.

Beispielsweise können Sie Änderungen vorgenommen haben, die sich nur auf den Endbenutzer auswirken, z. b. in visuellen Markierungen, und nicht die Zeit beanspruchen, die erforderlich ist, um eine vollständige erneute Überprüfung sofort auszuführen.

Überspringen Sie die vollständige, sofortige Neuüberprüfung, und kehren Sie später zurück, um [eine vollständige erneute Überprüfung durchzuführen](../deploy-aip-scanner-manage.md#rescanning-files) und Ihre Änderungen in ihren Depots anzuwenden.

> [!IMPORTANT]
> Administratoren, die Änderungen an Ihren Richtlinien und Inhalts Scan Aufträgen vornehmen, müssen nun die Auswirkungen dieser Änderungen auf den Inhalt verstehen und ermitteln, ob eine vollständige erneute Überprüfung erforderlich ist.
>
> Wenn Sie z. b. die **Vertraulichkeitsrichtlinien** Einstellungen von **erzwingen = aus** in **erzwingen = on** geändert haben, stellen Sie sicher, dass Sie eine vollständige erneute Überprüfung ausführen, um ihre Bezeichnungen auf Ihre Inhalte anzuwenden.
>

### <a name="configure-sharepoint-timeouts"></a>Konfigurieren von SharePoint-Timeouts

Das Standard Timeout für SharePoint-Interaktionen wurde auf zwei Minuten aktualisiert, danach schlägt der versuchte AIP-Vorgang fehl.

AIP-Administratoren können jetzt auch SharePoint-Timeouts für alle Webanforderungen und Datei Webanforderungen separat konfigurieren.

Weitere Informationen finden Sie unter [Konfigurieren von SharePoint-Timeouts](clientv2-admin-guide-customizations.md#configure-sharepoint-timeouts).

### <a name="network-discovery-support-public-preview"></a>Unterstützung der Netzwerk Ermittlung (Public Preview)

Der Unified-Beschriftungs Scanner enthält jetzt einen neuen **Netzwerk** Ermittlungsdienst, mit dem Sie die angegebenen IP-Adressen oder Bereiche für Netzwerkdatei Freigaben überprüfen können, die möglicherweise sensible Inhalte aufweisen.

Der **Netzwerk** Ermittlungsdienst aktualisiert die **Repository** -Berichte mit einer Liste von Freigabe Standorten, die möglicherweise gefährdet sind, basierend auf den ermittelten Berechtigungen und Zugriffsrechten. Überprüfen Sie die aktualisierten **Repository** -Berichte, um sicherzustellen, dass Ihre Inhalts Überprüfungs Aufträge alle zu scannenden Depots enthalten.

> [!TIP]
> Weitere Informationen finden Sie unter [Network Discovery-Cmdlets](#network-discovery-cmdlets-public-preview).

**So verwenden Sie den Netzwerk Ermittlungsdienst**

1. Führen Sie ein Upgrade Ihrer Überprüfungs Version durch, und stellen Sie sicher, dass Ihr Scanner-Cluster richtig konfiguriert ist. Weitere Informationen finden Sie unter
    - [Aktualisieren Ihres Scanners](../deploy-aip-scanner-configure-install.md#upgrade-your-scanner)
    - [Erstellen eines Scanner-Clusters](../deploy-aip-scanner-configure-install.md#create-a-scanner-cluster)

1. Stellen Sie sicher, dass Azure Information Protection Analytics aktiviert ist.

    Wechseln Sie in der Azure-Portal zu **Azure Information Protection > verwalten > configure Analytics (Vorschau)**.

    Weitere Informationen finden Sie unter [Zentrale Berichterstellung für Azure Information Protection (öffentliche Vorschau)](../reports-aip.md).

1. Aktivieren Sie die Netzwerk Ermittlung durch Ausführen des PowerShell-Cmdlets [**install-mipnetworkdiscovery**](/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery) .

    > [!IMPORTANT]
    > Wenn Sie dieses Cmdlet ausführen, stellen Sie sicher, dass Sie einen schwachen Benutzer als Wert für den **standarddomainsuseraccount** -Parameter verwenden, um sicherzustellen, dass alle öffentlichen Zugriffe auf die Repository gemeldet werden.
    >
    > Dieser Benutzer muss nur Mitglied der Gruppe " **Domänen Benutzer** " sein und wird verwendet, um den öffentlichen Zugriff auf die Depots zu simulieren.

1. Wechseln Sie in der Azure-Portal zu Azure Information Protection > **Network Scan-Aufträge** , und [Erstellen Sie Aufträge, um bestimmte Bereiche Ihres Netzwerks zu](../deploy-aip-scanner-configure-install.md#create-a-network-scan-job-public-preview)überprüfen.

1. Verwenden Sie die generierten Berichte im Bereich "neue [**Depots**](../deploy-aip-scanner-configure-install.md#analyze-risky-repositories-found-public-preview) ", um nach zusätzlichen Netzwerkdatei Freigaben zu suchen, die möglicherweise gefährdet sind. Fügen Sie Ihren [Inhalts Überprüfungs Aufträgen](../deploy-aip-scanner-configure-install.md#create-a-content-scan-job) riskante Dateifreigaben hinzu, um die hinzugefügten Depots auf vertrauliche Inhalte zu scannen.

### <a name="network-discovery-cmdlets-public-preview"></a>Cmdlets für die Netzwerk Ermittlung (öffentliche Vorschau)

Folgende PowerShell-Cmdlets sind für die Netzwerk Ermittlung hinzugefügt:

|Cmdlet  |BESCHREIBUNG  |
|---------|---------|
|[**Get-mipnetworkdiscoveryconfiguration**](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryConfiguration)     |   Ruft die aktuelle Einstellung ab, ob der Netzwerk Ermittlungsdienst Netzwerk Scan Daten aus der Standard-, Online-oder Offline Datei abruft, die aus der Azure-Portal exportiert wurde.      |
|[**Get-mipnetworkdiscoveryjobs**](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryJobs)     |    Ruft eine Liste der derzeit konfigurierten Netzwerk Scanaufträge ab.     |
|[**Get-mipnetworkdiscoverystatus**](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryStatus)     |     Ruft den aktuellen Status aller Netzwerk Scanaufträge ab, die in Ihrem Mandanten konfiguriert sind.    |
| [**Import-mipnetworkdiscoveryconfiguration**](/powershell/module/azureinformationprotection/Import-MIPNetworkDiscoveryConfiguration)     |    Importiert die Konfiguration für einen Netzwerk Scanauftrag aus einer Datei.     |
| [**Install-mipnetworkdiscovery**](/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery)| Installiert den Netzwerk Ermittlungsdienst. |
|[**Set-mipnetworkdiscoveryconfiguration**](/powershell/module/azureinformationprotection/Set-MIPNetworkDiscoveryConfiguration)     |   Legt die Konfiguration fest, ob der Netzwerk Ermittlungsdienst Netzwerk Scan Daten aus der Standard-, Online-oder Offline Datei abruft, die aus der Azure-Portal exportiert wurden.      |
|[**Start-mipnetworkdiscovery**](/powershell/module/azureinformationprotection/Start-MIPNetworkDiscovery)     |  Führt sofort einen bestimmten Netzwerk Scanauftrag aus.       |
|[**Deinstallation von mipnetworkdiscovery**](/powershell/module/azureinformationprotection/Uninstall-MIPNetworkDiscovery)     |  Deinstalliert den Netzwerk Ermittlungsdienst.       |
| | |


### <a name="administrator-customizations-for-aip-popups-in-outlook"></a>Anpassungen von Administratoren für AIP-Popups in Outlook

AIP-Administratoren können nun die Popups, die in Outlook angezeigt werden, für Endbenutzer anpassen, z. b. Popups für blockierte e-Mails, Warnmeldungen und einrichtungsoraufforderungen.

Weitere Informationen, einschließlich mehrerer Beispiel Regeln für gängige Anwendungsszenarien, finden Sie unter [Anpassen von Outlook-Popup Nachrichten](clientv2-admin-guide-customizations.md#customize-outlook-popup-messages).

### <a name="administrator-customizations-for-justification-prompts"></a>Administrator Anpassungen für entsprechende Eingabe Aufforderungen

AIP-Administratoren können nun eine der Optionen in den entsprechenden Eingabe Aufforderungen anpassen, die angezeigt werden, wenn Endbenutzer Klassifizierungs Bezeichnungen für Dokumente und e-Mails ändern.

Weitere Informationen finden Sie unter [Anpassen von Eingabe Aufforderungs Texten für geänderte Bezeichnungen](clientv2-admin-guide-customizations.md#customize-justification-prompt-texts-for-modified-labels).

### <a name="audit-log-updates"></a>Überwachungs Protokoll Updates

Überwachungs Protokolle für Zugriffsereignisse vom Unified Label-Client werden nun nur gesendet, wenn Benutzer mit der Bezeichnung oder den geschützten Dateien geöffnet werden, um einen besseren Hinweis auf den Benutzer Zugriff zu erhalten.

Informationstypen werden nicht mehr von Überwachungs [Protokollen für Zugriffsereignisse](../audit-logs.md#access-audit-logs)gesendet und nun nur mit Überwachungs [Protokollen für Ermittlungs Ereignisse](../audit-logs.md#discover-audit-logs)gesendet.

Weitere Informationen finden Sie unter [zugreifen](../audit-logs.md#access-audit-logs)auf Überwachungs Protokolle.

Weitere Informationen finden Sie unter [Azure Information Protection Audit Log Reference](../audit-logs.md).
### <a name="dke-template-based-labeling-updates"></a>Auf Vorlagen basierende DKE-Beschriftungs Updates

Azure Information Protection unterstützt jetzt eine DKE-vorlagenbasierte (Double Key Encryption) vorlagenbasierte Bezeichnung in der Überprüfung sowie die Verwendung des Datei-Explorers und von PowerShell.

Weitere Informationen finden Sie unter

- [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-implement-tenant-key.md)
- [Doppelte Schlüssel Verschlüsselung](/microsoft-365/compliance/double-key-encryption) in den Microsoft 365-Dokumentation

### <a name="azure-information-protection-scanner-fixed-issues-version-28850"></a>Behobene Probleme mit Azure Information Protection Scanner, Version 2.8.85.0

Die folgenden Korrekturen wurden in Version 2.8.85.0 des Azure Information Protection Unified-Beschriftungs Scanners übermittelt:

- Verbesserungen [beim Scannen von Dateien mit langen Pfaden](../deploy-aip-scanner-prereqs.md#file-path-requirements)
- Der AIP-Scanner scannt nun vollständige [SharePoint](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) -Umgebungen, wenn mehrere Content-Datenbanken vorhanden sind.
- Der AIP-Scanner unterstützt jetzt [SharePoint](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) -Dateien mit einem Punkt im Pfad, aber keine Erweiterung. Beispielsweise wird eine Datei mit dem Pfad `https://sharepoint.contoso.com/shared documents/meeting-notes` ohne Erweiterung nun erfolgreich gescannt.
- Der AIP-Scanner unterstützt jetzt [benutzerdefinierte vertrauliche Informationstypen](../deploy-aip-scanner-configure-install.md#identify-all-custom-conditions-and-known-sensitive-information-types) , die im Microsoft Security and Compliance Center erstellt wurden und keiner Richtlinie angehören.

### <a name="azure-information-protection-client-fixed-issues-version-28850"></a>Probleme bei der Azure Information Protection Clients behoben, Version 2.8.85.0

Die folgenden Korrekturen wurden in Version 2.8.85.0 des Azure Information Protection Unified-Bezeichnung Client übermittelt:

- Ein neuer, erzählter Hinweis für alle Elemente, die momentan aus dem Symbolmenü " **Vertraulichkeits** ![Spalten](../media/selected-sensitivity-options.png "Symbol "Spalten"") " in Office-Apps ausgewählt werden. Weitere Informationen finden Sie auf der Seite über [Vertraulichkeits Bezeichnungen in den Microsoft 365](/microsoft-365/compliance/sensitivity-labels#what-sensitivity-labels-can-do)-Dokumentation.
- Korrekturen zum Anzeigen von JPEG-Dateien im [AIP-Viewer](clientv2-view-use-files.md)
- **Das herab** Stufen einer Bezeichnung schließt jetzt automatisch den Schutz Besitzer in Überwachungs [Ereignissen](../audit-logs.md#downgrade-label-audit-logs) ein.
- Änderungs Ereignisse enthalten jetzt das **LastModifiedDate** in den Überwachungs [Protokollen](../audit-logs.md#change-protection-audit-logs) .
- Unterstützung für **Proxy. PAC** -Dateien hinzugefügt, wenn ein Proxy zum Abrufen eines Tokens verwendet wird. Weitere Informationen finden Sie unter [Firewalls und Netzwerkinfrastruktur Anforderungen](../requirements.md#firewalls-and-network-infrastructure).
- Korrekturen für die Authentifizierung beim Aktualisieren von [Richtlinien](../configure-policy.md#making-changes-to-the-policy)
- Korrekturen für [Automatische Inhalte kennzeichnen](../configure-policy-markings.md) von Aktualisierungen für PowerPoint im schreibgeschützten Modus
- Verbesserungen bei Popups und Fehler Texten
- QuickInfo-Updates, um die höchste [Klassifizierung für e-Mail-Anhänge](../faqs-infoprotect.md#when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling)anzuzeigen, wobei sowohl die Klassifizierung der e-Mail als auch die Anlage berücksichtigt werden.
- Fehlerbehebungen für den **Bericht einen Problem** Text beim Ändern von Vertraulichkeits Beschriftungs Richtlinien mithilfe des Cmdlets " [**Set-labelpolicy**](/powershell/module/exchange/set-labelpolicy) "
- Korrekturen in Fehlern, die angezeigt werden, wenn das Cmdlet " [**Set-aipfilelabel**](/powershell/module/azureinformationprotection/set-aipfilelabel) " mit einer ungültigen Bezeichnungs-ID verwendet wird.
- Leistungsfehler Behebungen für das Entschlüsseln von SMIME-e-Mails im Lesebereich von Outlook. Aktivieren Sie die erweiterte [**outlookskipsmimeonleseringpaneenable**](clientv2-admin-guide-customizations.md#prevent-outlook-performance-issues-with-smime-emails) -Eigenschaft, um diese Korrektur zu implementieren.
- Fehlerbehebungen für das [Entschlüsseln von PST-Dateien](clientv2-admin-guide-file-types.md) , die Kenn Wort verschlüsselte Dateien enthalten. Das Entschlüsseln von PST-Dateien schlägt nicht mehr fehl, wenn die PST-Datei eine Kenn Wort geschützte Datei enthält.
- Beim Entfernen einer Schutz Bezeichnung, die nicht in der Bereichs bezogenen Richtlinie enthalten ist, werden nun sowohl die Bezeichnung als auch der Schutz aus dem Inhalt entfernt.

## <a name="version-271010"></a>Version 2.7.101.0

Unified-Beschriftungs Scanner und Client Version 2.7.101.0

**Veröffentlicht** 08/23/2020

**Unterstützt durch** 3/22/2021

**Behebung**:

Das Problem für PPT-, Excel-und Word-Benutzer wurde behoben, das dazu geführt hat, dass Dateien eingefroren, abgestürzt sind oder dass die Speicherung wiederholt werden musste, die mit obligatorischen Bezeichnungen verknüpft war, die mit Schutz, Wasserzeichen und/oder Inhaltsmarkierung

## <a name="version-27990"></a>Version 2.7.99.0

Unified-Beschriftungs Scanner und Client Version 2.7.99.0

**Veröffentlicht** 07/20/2020

**Unterstützt durch** 2/23/2021

**Korrekturen und Verbesserungen**:

Behobene Probleme bei Datei Bezeichnungs Aktionen für **neue Beschriftungs** Überwachungs Protokolle.

Weitere Informationen finden Sie unter [Version 2.7.96.0](#version-27960) und [Azure Information Protection Audit Log Reference (Public Preview)](../audit-logs.md).

## <a name="version-27960"></a>Version 2.7.96.0

Unified-Beschriftungs Scanner und Client Version 2.7.96.0

**Veröffentlicht** 06/29/2020

**Unterstützt durch** 1/20/2021

- [Neue Features für den Unified-Bezeichnungs Client, Version 2.7.96.0](#new-features-for-the-unified-labeling-client-version-27960)
- [Neue Features für den Unified-Bezeichnungs Scanner, Version 2.7.96.0](#new-features-for-the-unified-labeling-scanner-version-27960)
- [Es wurden neue Überwachungs Protokolle für entfernte Dateien generiert.](#new-audit-logs-generated-for-removed-files)
- [Erzwingen von TLS 1.2](#tls-12-enforcement)
- [Korrekturen und Verbesserungen, Version 2.7.96.0](#fixes-and-improvements-version-27960)
### <a name="new-features-for-the-unified-labeling-scanner-version-27960"></a>Neue Features für den Unified-Bezeichnungs Scanner, Version 2.7.96.0

- [Verwenden Sie Scanner, um Bezeichnungen auf der Grundlage der empfohlenen Bedingungen anzuwenden](../deploy-aip-scanner-prereqs.md). AIP-Kunden können nun festlegen, dass nur Dienst seitige Authentifizierung implementiert werden soll. Diese Funktion ermöglicht es AIP-Endbenutzern, immer Empfehlungen anstelle des vorherigen Szenarios zu befolgen, das nur die automatische Bezeichnung auf der Benutzerseite aktiviert hat.

- [Informationen dazu, welche Dateien zuvor von Scanner erkannt wurden, wurden aus dem gescannten Repository gelöscht](../reports-aip.md) Diese gelöschten Dateien wurden zuvor nicht in AIP Analytics gemeldet und sind jetzt im Bericht zur scannerermittlung verfügbar.

- [Berichte aus der Überprüfung bei Fehlern zum Anwenden von Aktions Ereignissen erhalten](../reports-aip.md#friendly-schema-reference-for-event-functions). Verwenden Sie Berichte, um mehr über fehlgeschlagene Aktions Ereignisse und Möglichkeiten zu erfahren, wie Sie zukünftige vorkommen vermeiden.

- Einführung des AIP Scanner Diagnostics Analyzer Tool zur Erkennung und Analyse allgemeiner Scanner-Fehler. Um mit der Verwendung der AIP-Scanner-Diagnose zu beginnen, [führen Sie das Cmdlet **Start-aipscannerdiagnostics**](../deploy-aip-scanner-tsg.md#troubleshooting-using-the-scanner-diagnostic-tool)aus.

- Sie können nun die maximale CPU-Auslastung auf dem Überprüfungs Computer verwalten und begrenzen. Erfahren Sie, wie Sie die CPU-Auslastung von 100% verhindern und die CPU-Auslastung mithilfe der [beiden neuen erweiterten Einstellungen **scannermaxcpu** und **scannermincpu**](./clientv2-admin-guide-customizations.md#limit-cpu-consumption)verwalten.

- Nun können Sie den Unified-Beschriftungs Scanner so konfigurieren, dass bestimmte Dateien abhängig von ihren Dateiattributen übersprungen werden. Hiermit wird die Liste der Dateiattribute definiert, durch die eine Datei mit der neuen **[scannerfsattributestoskip](clientv2-admin-guide-customizations.md#skip-or-ignore-files-during-scans-depending-on-file-attributes)** Advanced-Einstellung übersprungen wird.

### <a name="new-features-for-the-unified-labeling-client-version-27960"></a>Neue Features für den Unified-Bezeichnungs Client, Version 2.7.96.0

- [**Ausrichtungpopups**](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent) werden jetzt für Änderungen angezeigt, die an Standard Bezeichnungen im Unified Label-Client vorgenommen werden.

- Reibungslosere Integration mit visuellen Inhalts Markierungen, die von Office angewendet werden. Weitere Informationen zum Konfigurieren von Inhalts Markierungen in Office-Dokumenten finden [Sie unter Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information](../configure-policy-markings.md)Protection.

- Die neue **wordshapenametoremove** Advanced-Eigenschaft ermöglicht das Entfernen von Inhalts Markierungen in Word-Dokumenten, die von Anwendungen von Drittanbietern erstellt wurden. Erfahren Sie mehr darüber, wie [Sie vorhandene Shape-Namen identifizieren und mithilfe von **wordshapenametoremove** zum Entfernen definieren](./clientv2-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions).

- Unterstützung für **Double Key Encryption (DKE)** (Public Preview).

    Nun können Sie den Unified-Bezeichnungs Client verwenden, um hochgradig sensiblen Inhalt zu schützen, während Sie die vollständige Kontrolle über Ihren Schlüssel behalten. DKE erfordert zwei Schlüssel für den Zugriff auf geschützte Inhalte: ein Schlüssel wird in Azure gespeichert, und der andere Schlüssel wird vom Kunden gespeichert.

    Weitere Informationen zu den standardmäßigen cloudbasierten Mandanten Stamm Schlüsseln finden [Sie unter Planning and Implementierungs your Azure Information Protection Tenant Key](../plan-implement-tenant-key.md). Informationen zum Implementieren der doppelten Schlüssel Verschlüsselung finden Sie unter [doppelte Schlüssel Verschlüsselung](/microsoft-365/compliance/double-key-encryption) in der Microsoft 365-Dokumentation.

### <a name="new-audit-logs-generated-for-removed-files"></a>Es wurden neue Überwachungs Protokolle für entfernte Dateien generiert.

Überwachungs Protokolle werden nun immer generiert, wenn der Scanner erkennt, dass eine zuvor überprüfte Datei entfernt wurde.

Weitere Informationen finden Sie unter

- [Datei entfernte Überwachungs Protokolle](../audit-logs.md#file-removed-audit-logs)
- [Zentrale Berichterstellung für Azure Information Protection](../reports-aip.md)

> [!IMPORTANT]
> In dieser Version generieren Datei Bezeichnungs Aktionen keine neuen Überwachungs Protokolle für die **Bezeichnung** .
> Wenn Sie die Überprüfung im Modus **erzwingen = on** ausführen, wird empfohlen, ein Upgrade auf [Version 2.7.99.0](#version-27990)durchzuführen.
>

### <a name="tls-12-enforcement"></a>Erzwingen von TLS 1.2

Ab dieser Version des Azure Information Protection Clients werden nur die TLS-Versionen 1,2 oder höher unterstützt.

Kunden, die über ein TLS-Setup verfügen, das TLS 1,2 nicht unterstützt, müssen zu einem Setup wechseln, das TLS 1,2 unterstützt, um Azure Information Protection Richtlinien, Token, Überwachung und Schutz zu verwenden und Azure Information Protection-basierte Kommunikation zu empfangen.

Weitere Informationen zu den Anforderungen finden Sie unter [Firewalls und Netzwerkinfrastruktur Anforderungen](../requirements.md#firewalls-and-network-infrastructure).

### <a name="fixes-and-improvements-version-27960"></a>Korrekturen und Verbesserungen, Version 2.7.96.0

- SQL-Verbesserungen für Scanner für
    - Leistung
    - Dateien mit einer großen Anzahl von Informationstypen

- Verbesserungen bei SharePoint-Scans für:
    - Überprüfen der Leistung
    - Dateien mit Sonderzeichen im Pfad
    - Bibliotheken mit großen Dateianzahl

    Eine Schnellstartanleitung für die Verwendung von Azure Information Protection mit SharePoint [finden Sie unter Schnellstart: Ermitteln der sensiblen Informationen, die Sie in lokal gespeicherten Dateien haben](../quickstart-findsensitiveinfo.md).

- Verbesserte Benutzer Benachrichtigungen für fehlende Richtlinien. Weitere Informationen zu Bezeichnungs Richtlinien für den Unified Label-Client finden [Sie unter welche Bezeichnungs Richtlinien können](/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do) in der Microsoft 365-Dokumentation funktionieren.

- [Automatische Bezeichnungen](../configure-policy-classification.md) werden jetzt in Excel für Szenarien angewendet, in denen ein Benutzer mit dem Schließen einer Datei beginnt, ohne zu speichern, genauso wie wenn ein Benutzer eine Datei aktiv speichert.

- Kopf-und Fußzeilen werden erwartungsgemäß entfernt und nicht für jedes Dokument gespeichert, wenn die [externalcontentmarkingtoremove](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions) -Einstellung konfiguriert ist.

- [Dynamische Benutzervariablen](../configure-policy-markings.md#using-variables-in-the-text-string) werden nun wie erwartet in den visuellen Kennzeichnungen eines Dokuments angezeigt.

- Das Problem, dass nur die erste Seite des Inhalts einer PDF-Datei zum Anwenden von Regeln für die automatische Klassifizierung verwendet wurde, ist jetzt aufgelöst, und die automatische Klassifizierung basierend auf dem gesamten Inhalt in der PDF-Datei wird jetzt erwartungsgemäß fortgesetzt. Weitere Informationen zur Klassifizierung und Bezeichnung finden Sie in den häufig gestellten Fragen zur [Klassifizierung und Bezeichnung](../faqs-infoprotect.md).

- Wenn mehrere Exchange-Konten konfiguriert sind und der Azure Information Protection Outlook-Client aktiviert ist, werden die e-Mails wie erwartet vom sekundären Konto gesendet. Weitere Informationen zum Konfigurieren des Unified-Bezeichnungs Clients mit Outlook finden [Sie unter Konfigurieren der Gruppenrichtlinie, um die Deaktivierung von AIP zu verhindern](reqs-ul-client.md#configure-your-group-policy-to-prevent-disabling-aip).

- Wenn ein Dokument mit einer höheren Vertraulichkeits Bezeichnung per Drag and Drop per Drag and Drop in eine e-Mail eingefügt wird, erhält die e-Mail nun automatisch die höhere Vertraulichkeits Bezeichnung wie erwartet. Weitere Informationen zum bezeichnen von Client Funktionen finden Sie in der [Bezeichnung Client Vergleichstabelle](use-client.md#compare-the-labeling-solutions-for-windows-computers).

- Benutzerdefinierte Berechtigungen werden jetzt erwartungsgemäß auf e-Mails angewendet, wenn e-Mail-Adressen sowohl einen Apostroph (') als auch einen Zeitraum (.) enthalten. Weitere Informationen zum Konfigurieren des Unified-Bezeichnungs Clients mit Outlook finden [Sie unter Konfigurieren der Gruppenrichtlinie, um die Deaktivierung von AIP zu verhindern](reqs-ul-client.md#configure-your-group-policy-to-prevent-disabling-aip).


- Standardmäßig geht der NTFS-Besitzer einer Datei verloren, wenn die Datei durch die vereinheitlichte Bezeichnung Scanner, PowerShell oder die Datei-Explorer-Erweiterung gekennzeichnet wird. Nun können Sie das System so konfigurieren, dass der NTFS-Besitzer der Datei beibehalten wird, indem Sie die neue **[usecopyandshandentfsowner](clientv2-admin-guide-customizations.md#preserve-ntfs-owners-during-labeling-public-preview)** Advanced-Einstellung auf " **true**" festlegen.

    Die erweiterte Einstellung **usecopyandkonservierungs entbersowner** erfordert eine geringe Latenz, eine zuverlässige Netzwerkverbindung zwischen dem Scanner und dem gescannten Repository.

## <a name="next-steps"></a>Nächste Schritte

Sie sind nicht sicher, ob Unified Bezeichnung der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen der Windows-Bezeichnung](use-client.md#choose-your-windows-labeling-solution).

Weitere Informationen zum Installieren und Verwenden des Unified-Beschriftungs Clients:

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection Unified-Bezeichnung Client Administrator Handbuch](clientv2-admin-guide.md)
