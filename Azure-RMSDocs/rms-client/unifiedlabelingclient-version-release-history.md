---
title: Azure Information Protection vereinheitlichte Bezeichnung für den Client Versionsverlauf & Unterstützungs Richtlinie
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/02/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: af8998f4a96649c6a14522c5f5beb025527ec556
ms.sourcegitcommit: d519d0326756a389d543b6cd0e607ef5d1d087b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2020
ms.locfileid: "96740621"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection Unified Bezeichnungs Verlauf des Client Versions Verlaufs und der Support Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen [unter AIP für Windows und Office-Versionen unter Erweiterter Support](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support).*
>
> *Anweisungen für: [Azure Information Protection-Client für einheitliche Bezeichnungen für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Sie können den Azure Information Protection Unified Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunterladen.

Nach einer kurzen Verzögerung von in der Regel einige Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog enthalten. Azure Information Protection Versionen haben den Produktnamen **Microsoft Azure Information Protection**  >  **Microsoft Azure Information Protection Unified**-Bezeichnungs Client und eine Klassifizierung von **Updates**. 

Das Einschließen von Azure Information Protection in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Software Bereitstellungs Mechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [aktualisieren und Verwalten des Azure Information Protection Unified Bezeichnung-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede allgemein verfügbare Version des Azure Information Protection Unified Bezeichnung-Clients wird bis zu sechs Monate nach der Veröffentlichung der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Beachten Sie, Azure Information Protection Features derzeit in der Vorschau Phase sind. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

##### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden:

|Clientversion|Datum der Veröffentlichung|
|--------------|-------------|
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

Die neueste Version von Azure Information Protection befindet sich derzeit in der Vorschau Phase. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn Sie also ein Problem mit dem Unified-Bezeichnungs Client haben, sollten Sie überprüfen, ob es mit der neuesten GA-Version behoben wurde. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

Dieser Client ersetzt den Azure Information Protection Client (klassisch). Informationen zum Vergleichen von Features und Funktionen mit dem klassischen Client finden Sie unter [vergleichen der Bezeichnung für Clients für Windows-Computer](use-client.md#compare-the-labeling-clients-for-windows-computers).

## <a name="version-291010-public-preview"></a>Version 2.9.101.0 (öffentliche Vorschau)

Unified Bezeichnung Scanner-Version 2.9.101.0

**Veröffentlicht** 11/30/2020

Die folgenden neuen Features wurden für den lokalen [Scanner für die einheitliche Bezeichnung](../deploy-aip-scanner.md) in Version 2.9.101.0 veröffentlicht:

- [PowerShell-Unterstützung für nicht verbundene Scanner-Server](#powershell-support-for-disconnected-scanner-servers)
- [Unterstützung für NFS-Depots in Inhalts Scan Aufträgen](#support-for-nfs-repositories-in-content-scan-jobs)
- [Unterstützung für sensible Informationstypen hinzugefügt](#added-support-for-sensitive-information-types)
### <a name="powershell-support-for-disconnected-scanner-servers"></a>PowerShell-Unterstützung für nicht verbundene Scanner-Server
Der [Azure Information Protection lokale Scanner](../deploy-aip-scanner.md) unterstützt jetzt die Verwaltung von Inhalts Überprüfungs Aufträgen für Scanner-Server, die keine Verbindung mit dem Internet herstellen können, über PowerShell.

Zur Unterstützung von getrennten Scanner-Servern wurden die folgenden neuen Cmdlets hinzugefügt:

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

### <a name="support-for-nfs-repositories-in-content-scan-jobs"></a>Unterstützung für NFS-Depots in Inhalts Scan Aufträgen

Nun können Sie Ihren Inhalts Überprüfungs Aufträgen zusätzlich zu SMB-Dateifreigaben und SharePoint-Depots NFS-Repository hinzufügen.

Dienste für NFS müssen auf dem Überprüfungs Computer bereitgestellt werden, um Scans für NFS-Freigaben zu unterstützen:

1. Navigieren Sie auf Ihrem Computer zum Dialogfeld "Einstellungen" (Windows-Funktionen ein- **oder ausschalten)** .

1. Wählen Sie die folgenden Elemente aus: 

    - **Dienste für NFS** 
        - **Verwaltungs Tools**
        - **Client für NFS**.

Weitere Informationen finden Sie unter [Erstellen eines Inhalts Scan Auftrags](../deploy-aip-scanner-configure-install.md#create-a-content-scan-job).

### <a name="added-support-for-sensitive-information-types"></a>Unterstützung für sensible Informationstypen hinzugefügt
Wir haben Unterstützung für zusätzliche vertrauliche Informationstypen in Azure Information Protection hinzugefügt, wie z. b. die **Geschäftsnummer von Australien,** die **australische Firmennummer** oder die Personalausweisnummer **.** 

Weitere Informationen finden Sie in den [Entitäts Definitionen für sensible Informationen](/microsoft-365/compliance/sensitive-information-type-entity-definitions) in der Microsoft 365-Dokumentation.
### <a name="fixes-and-improvements"></a>Korrekturen und Verbesserungen

Die folgenden Korrekturen wurden in Version 2.9.101.0 des [Azure Information Protection Unified-Beschriftungs Scanners](../deploy-aip-scanner.md)übermittelt:

- Unterstützung für Bindestriche ( **-** ) in [Scanner-Datenbanknamen](../deploy-aip-scanner-prereqs.md) hinzugefügt
- Updates in Berichten für den Fall, dass die Option " **[auf Inhalt basierende](../deploy-aip-scanner-configure-install.md#create-a-content-scan-job)** Bezeichnungs Dateien" auf **Off** festgelegt ist
- [Verbesserter Arbeitsspeicher Verbrauch](../deploy-aip-scanner-configure-install.md#optimizing-scanner-performance) für eine große Anzahl von Informationstyp Übereinstimmungen
- Unterstützung für [lokale SharePoint-](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) Pfade, die mit einem Schrägstrich ( **/** ) enden
- Erweiterte SharePoint-Scan [Geschwindigkeit](../deploy-aip-scanner-configure-install.md#optimizing-scanner-performance)
- Unterstützung für das [vermeiden eines Timeouts](clientv2-admin-guide-customizations.md#avoid-scanner-timeouts-in-sharepoint) beim Scannen eines SharePoint-Servers.

### <a name="known-issues"></a>Bekannte Probleme
In dieser öffentlichen Vorschauversion wird das Anwenden von Bezeichnungen mit [DKE-Schutz](../plan-implement-tenant-key.md#double-key-encryption-dke-aip-unified-labeling-client-only) von der Überprüfung nicht unterstützt.

## <a name="version-28850"></a>Version 2.8.85.0

Unified-Beschriftungs Scanner und Client Version 2.8.85.0

**Veröffentlicht** 09/22/2020

Diese Version enthält die folgenden neuen Features, Korrekturen und Verbesserungen für den Unified-Beschriftungs Scanner und-Client:

- [Neue Features für den Unified-Beschriftungs Scanner](#new-features-for-the-unified-labeling-scanner-version-28850)
- [Neue Features für den Unified-Bezeichnungs Client](#new-features-for-the-unified-labeling-client-version-28850)
- [Korrekturen und Verbesserungen](#fixes-and-improvements-version-28850)

### <a name="new-features-for-the-unified-labeling-scanner-version-28850"></a>Neue Features für den Unified-Bezeichnungs Scanner, Version 2.8.85.0

- [Optionale vollständige neuänderungen für erkannte Änderungen](#optional-full-rescans-for-changes-detected)
- [Konfigurieren von SharePoint-Timeouts](#configure-sharepoint-timeouts)
- [Unterstützung der Netzwerk Ermittlung](#network-discovery-support) 

#### <a name="optional-full-rescans-for-changes-detected"></a>Optionale vollständige neuänderungen für erkannte Änderungen

Administratoren können jetzt eine vollständige erneute Überprüfung überspringen, nachdem Sie Änderungen an Richtlinien oder Inhalts Scan Aufträgen vorgenommen haben. Wenn Sie einen vollständigen erneuten Scan überspringen, werden die Änderungen nur auf Dateien angewendet, die seit der letzten Überprüfung geändert oder erstellt wurden.

Beispielsweise können Sie Änderungen vorgenommen haben, die sich nur auf den Endbenutzer auswirken, z. b. in visuellen Markierungen, und nicht die Zeit beanspruchen, die erforderlich ist, um eine vollständige erneute Überprüfung sofort auszuführen. 

Überspringen Sie die vollständige, sofortige Neuüberprüfung, und kehren Sie später zurück, um [eine vollständige erneute Überprüfung durchzuführen](../deploy-aip-scanner-manage.md#rescanning-files) und Ihre Änderungen in ihren Depots anzuwenden.

> [!IMPORTANT]
> Administratoren, die Änderungen an Ihren Richtlinien und Inhalts Scan Aufträgen vornehmen, müssen nun die Auswirkungen dieser Änderungen auf den Inhalt verstehen und ermitteln, ob eine vollständige erneute Überprüfung erforderlich ist.
> 
> Wenn Sie beispielsweise die Einstellungen für die **Richtlinien** Erzwingung von **erzwingen = aus** in **erzwingen = on** geändert haben, stellen Sie sicher, dass Sie eine vollständige erneute Überprüfung ausführen, um ihre Bezeichnungen auf Ihre Inhalte anzuwenden.
>

#### <a name="configure-sharepoint-timeouts"></a>Konfigurieren von SharePoint-Timeouts

Das Standard Timeout für SharePoint-Interaktionen wurde auf zwei Minuten aktualisiert, danach schlägt der versuchte AIP-Vorgang fehl.

AIP-Administratoren können jetzt auch SharePoint-Timeouts für alle Webanforderungen und Datei Webanforderungen separat konfigurieren. 

Weitere Informationen finden Sie unter [Konfigurieren von SharePoint-Timeouts](clientv2-admin-guide-customizations.md#configure-sharepoint-timeouts).

#### <a name="network-discovery-support"></a>Unterstützung der Netzwerk Ermittlung

Der Unified-Beschriftungs Scanner enthält jetzt einen neuen **Netzwerk** Ermittlungsdienst, mit dem Sie die angegebenen IP-Adressen oder Bereiche für Netzwerkdatei Freigaben überprüfen können, die möglicherweise sensible Inhalte aufweisen. 

Der **Netzwerk** Ermittlungsdienst aktualisiert die **Repository** -Berichte mit einer Liste von Freigabe Standorten, die möglicherweise gefährdet sind, basierend auf den ermittelten Berechtigungen und Zugriffsrechten. Überprüfen Sie die aktualisierten **Repository** -Berichte, um sicherzustellen, dass Ihre Inhalts Überprüfungs Aufträge alle zu scannenden Depots enthalten.

> [!TIP]
> Weitere Informationen finden Sie unter [Network Discovery-Cmdlets](#network-discovery-cmdlets).

**So verwenden Sie den Netzwerk Ermittlungsdienst**

1. Führen Sie ein Upgrade Ihrer Überprüfungs Version durch, und stellen Sie sicher, dass Ihr Scanner-Cluster richtig konfiguriert ist. Weitere Informationen finden Sie unter
    - [Aktualisieren Ihres Scanners](../deploy-aip-scanner-configure-install.md#upgrading-your-scanner)
    - [Erstellen eines Scanner-Clusters](../deploy-aip-scanner-configure-install.md#create-a-scanner-cluster) 
    
1. Stellen Sie sicher, dass Azure Information Protection Analytics aktiviert ist. 

    Wechseln Sie in der Azure-Portal zu **Azure Information Protection > verwalten > configure Analytics (Vorschau).** 

    Weitere Informationen finden Sie unter [Zentrale Berichterstellung für Azure Information Protection (öffentliche Vorschau)](../reports-aip.md).

1. Aktivieren Sie die Netzwerk Ermittlung durch Ausführen des PowerShell-Cmdlets [**install-mipnetworkdiscovery**](/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery) . 

    > [!IMPORTANT]
    > Wenn Sie dieses Cmdlet ausführen, stellen Sie sicher, dass Sie einen schwachen Benutzer als Wert für den **standarddomainsuseraccount** -Parameter verwenden, um sicherzustellen, dass alle öffentlichen Zugriffe auf die Repository gemeldet werden. 
    >
    > Dieser Benutzer muss nur Mitglied der Gruppe " **Domänen Benutzer** " sein und wird verwendet, um den öffentlichen Zugriff auf die Depots zu simulieren.

1. Wechseln Sie in der Azure-Portal zu Azure Information Protection > **Network Scan-Aufträge** , und [Erstellen Sie Aufträge, um bestimmte Bereiche Ihres Netzwerks zu](../deploy-aip-scanner-configure-install.md#create-a-network-scan-job-public-preview)überprüfen. 

1. Verwenden Sie die generierten Berichte im Bereich "neue [**Depots**](../deploy-aip-scanner-configure-install.md#analyze-risky-repositories-found-public-preview) ", um nach zusätzlichen Netzwerkdatei Freigaben zu suchen, die möglicherweise gefährdet sind. Fügen Sie Ihren [Inhalts Überprüfungs Aufträgen](../deploy-aip-scanner-configure-install.md#create-a-content-scan-job) riskante Dateifreigaben hinzu, um die hinzugefügten Depots auf vertrauliche Inhalte zu scannen.

##### <a name="network-discovery-cmdlets"></a>Cmdlets für die Netzwerk Ermittlung

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

### <a name="new-features-for-the-unified-labeling-client-version-28850"></a>Neue Features für den Unified-Bezeichnungs Client, Version 2.8.85.0

- [Anpassungen von Administratoren für AIP-Popups in Outlook](#administrator-customizations-for-aip-popups-in-outlook) 
- [Administrator Anpassungen für entsprechende Eingabe Aufforderungen](#administrator-customizations-for-justification-prompts) 
- [Überwachungs Protokoll Updates](#audit-log-updates) 
- [Auf Vorlagen basierende DKE-Beschriftungs Updates](#dke-template-based-labeling-updates)

#### <a name="administrator-customizations-for-aip-popups-in-outlook"></a>Anpassungen von Administratoren für AIP-Popups in Outlook

AIP-Administratoren können nun die Popups, die in Outlook angezeigt werden, für Endbenutzer anpassen, z. b. Popups für blockierte e-Mails, Warnmeldungen und einrichtungsoraufforderungen.

Weitere Informationen, einschließlich mehrerer Beispiel Regeln für gängige Anwendungsszenarien, finden Sie unter [Anpassen von Outlook-Popup Nachrichten](clientv2-admin-guide-customizations.md#customize-outlook-popup-messages).

#### <a name="administrator-customizations-for-justification-prompts"></a>Administrator Anpassungen für entsprechende Eingabe Aufforderungen

AIP-Administratoren können nun eine der Optionen in den entsprechenden Eingabe Aufforderungen anpassen, die angezeigt werden, wenn Endbenutzer Klassifizierungs Bezeichnungen für Dokumente und e-Mails ändern. 

Weitere Informationen finden Sie unter [Anpassen von Eingabe Aufforderungs Texten für geänderte Bezeichnungen](clientv2-admin-guide-customizations.md#customize-justification-prompt-texts-for-modified-labels).

#### <a name="audit-log-updates"></a>Überwachungs Protokoll Updates

Überwachungs Protokolle für Zugriffsereignisse vom Unified Label-Client werden nun nur gesendet, wenn Benutzer mit der Bezeichnung oder den geschützten Dateien geöffnet werden, um einen besseren Hinweis auf den Benutzer Zugriff zu erhalten.

Weitere Informationen finden Sie unter [zugreifen](../audit-logs.md#access-audit-logs)auf Überwachungs Protokolle.

#### <a name="dke-template-based-labeling-updates"></a>Auf Vorlagen basierende DKE-Beschriftungs Updates

Azure Information Protection unterstützt jetzt eine DKE-vorlagenbasierte (Double Key Encryption) vorlagenbasierte Bezeichnung in der Überprüfung sowie die Verwendung des Datei-Explorers und von PowerShell.

Weitere Informationen finden Sie unter

- [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-implement-tenant-key.md)
- [Doppelte Schlüssel Verschlüsselung](/microsoft-365/compliance/double-key-encryption) in den Microsoft 365-Dokumentation

### <a name="fixes-and-improvements-version-28850"></a>Korrekturen und Verbesserungen, Version 2.8.85.0

- [Korrekturen und Verbesserungen bei Scanner](#azure-information-protection-scanner-fixed-issues-version-28850)
- [Client Korrekturen und-Verbesserungen](#azure-information-protection-client-fixed-issues-version-28850)

#### <a name="azure-information-protection-scanner-fixed-issues-version-28850"></a>Behobene Probleme mit Azure Information Protection Scanner, Version 2.8.85.0

Die folgenden Korrekturen wurden in Version 2.8.85.0 des Azure Information Protection Unified-Beschriftungs Scanners übermittelt:

- Verbesserungen [beim Scannen von Dateien mit langen Pfaden](../deploy-aip-scanner-prereqs.md#file-path-requirements)
- Der AIP-Scanner scannt nun vollständige [SharePoint](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) -Umgebungen, wenn mehrere Content-Datenbanken vorhanden sind.
- Der AIP-Scanner unterstützt jetzt [SharePoint](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) -Dateien mit einem Punkt im Pfad, aber keine Erweiterung. Beispielsweise wird eine Datei mit dem Pfad `https://sharepoint.contoso.com/shared documents/meeting-notes` ohne Erweiterung nun erfolgreich gescannt.
- Der AIP-Scanner unterstützt jetzt [benutzerdefinierte vertrauliche Informationstypen](../deploy-aip-scanner-configure-install.md#identify-all-custom-conditions-and-known-sensitive-information-types) , die im Microsoft Security and Compliance Center erstellt wurden und keiner Richtlinie angehören.

#### <a name="azure-information-protection-client-fixed-issues-version-28850"></a>Probleme bei der Azure Information Protection Clients behoben, Version 2.8.85.0

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

**Zusetzen**

Das Problem für PPT-, Excel-und Word-Benutzer wurde behoben, das dazu geführt hat, dass Dateien eingefroren, abgestürzt sind oder dass die Speicherung wiederholt werden musste, die mit obligatorischen Bezeichnungen verknüpft war, die mit Schutz, Wasserzeichen und/oder Inhaltsmarkierung

## <a name="version-27990"></a>Version 2.7.99.0

Unified-Beschriftungs Scanner und Client Version 2.7.99.0

**Veröffentlicht** 07/20/2020

**Korrekturen und Verbesserungen:**

Behobene Probleme bei Datei Bezeichnungs Aktionen für **neue Beschriftungs** Überwachungs Protokolle.

Weitere Informationen finden Sie unter [Version 2.7.96.0](#version-27960) und [Azure Information Protection Audit Log Reference (Public Preview)](../audit-logs.md).

## <a name="version-27960"></a>Version 2.7.96.0

Unified-Beschriftungs Scanner und Client Version 2.7.96.0

**Veröffentlicht** 06/29/2020

**Neue Features für den Unified-Beschriftungs Scanner:**

- [Verwenden Sie Scanner, um Bezeichnungen auf der Grundlage der empfohlenen Bedingungen anzuwenden](../deploy-aip-scanner-prereqs.md). AIP-Kunden können nun festlegen, dass nur Dienst seitige Authentifizierung implementiert werden soll. Diese Funktion ermöglicht es AIP-Endbenutzern, immer Empfehlungen anstelle des vorherigen Szenarios zu befolgen, das nur die automatische Bezeichnung auf der Benutzerseite aktiviert hat.

- [Informationen dazu, welche Dateien zuvor von Scanner erkannt wurden, wurden aus dem gescannten Repository gelöscht](../reports-aip.md) Diese gelöschten Dateien wurden zuvor nicht in AIP Analytics gemeldet und sind jetzt im Bericht zur scannerermittlung verfügbar.

- [Berichte aus der Überprüfung bei Fehlern zum Anwenden von Aktions Ereignissen erhalten](../reports-aip.md#friendly-schema-reference-for-event-functions). Verwenden Sie Berichte, um mehr über fehlgeschlagene Aktions Ereignisse und Möglichkeiten zu erfahren, wie Sie zukünftige vorkommen vermeiden. 

- Einführung des AIP Scanner Diagnostics Analyzer Tool zur Erkennung und Analyse allgemeiner Scanner-Fehler. Um mit der Verwendung der AIP-Scanner-Diagnose zu beginnen, [führen Sie das neue Cmdlet **Start-aipscannerdiagnostics**](../deploy-aip-scanner-manage.md#troubleshooting-using-the-scanner-diagnostic-tool)aus. 

- Sie können nun die maximale CPU-Auslastung auf dem Überprüfungs Computer verwalten und begrenzen. Erfahren Sie, wie Sie die CPU-Auslastung von 100% verhindern und die CPU-Auslastung mithilfe der [beiden neuen erweiterten Einstellungen **scannermaxcpu** und **scannermincpu**](./clientv2-admin-guide-customizations.md#limit-cpu-consumption)verwalten. 

- Nun können Sie den Unified-Beschriftungs Scanner so konfigurieren, dass bestimmte Dateien abhängig von ihren Dateiattributen übersprungen werden. Hiermit wird die Liste der Dateiattribute definiert, durch die eine Datei mit der neuen **[scannerfsattributestoskip](clientv2-admin-guide-customizations.md#skip-or-ignore-files-during-scans-depending-on-file-attributes)** Advanced-Einstellung übersprungen wird.

**Neue Features für den Unified-Bezeichnungs Client:**

- [**Ausrichtungpopups**](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent) werden jetzt für Änderungen angezeigt, die an Standard Bezeichnungen im Unified Label-Client vorgenommen werden.
    
- Reibungslosere Integration mit visuellen Inhalts Markierungen, die von Office angewendet werden. Weitere Informationen zum Konfigurieren von Inhalts Markierungen in Office-Dokumenten finden [Sie unter Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information](../configure-policy-markings.md)Protection.

- Die neue **wordshapenametoremove** Advanced-Eigenschaft ermöglicht das Entfernen von Inhalts Markierungen in Word-Dokumenten, die von Anwendungen von Drittanbietern erstellt wurden. Erfahren Sie mehr darüber, wie [Sie vorhandene Shape-Namen identifizieren und mithilfe von **wordshapenametoremove** zum Entfernen definieren](./clientv2-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions).

- Unterstützung für **Double Key Encryption (DKE)** (Public Preview). 

    Nun können Sie den Unified-Bezeichnungs Client verwenden, um hochgradig sensiblen Inhalt zu schützen, während Sie die vollständige Kontrolle über Ihren Schlüssel behalten. DKE erfordert zwei Schlüssel für den Zugriff auf geschützte Inhalte: ein Schlüssel wird in Azure gespeichert, und der andere Schlüssel wird vom Kunden gespeichert. 

    Weitere Informationen zu den standardmäßigen cloudbasierten Mandanten Stamm Schlüsseln finden [Sie unter Planning and Implementierungs your Azure Information Protection Tenant Key](../plan-implement-tenant-key.md). Informationen zum Implementieren der doppelten Schlüssel Verschlüsselung finden Sie unter [doppelte Schlüssel Verschlüsselung](/microsoft-365/compliance/double-key-encryption) in der Microsoft 365-Dokumentation.

**Es wurden neue Überwachungs Protokolle für entfernte Dateien generiert.**

Überwachungs Protokolle werden nun immer generiert, wenn der Scanner erkennt, dass eine zuvor überprüfte Datei entfernt wurde.

Weitere Informationen finden Sie unter
- [Datei entfernte Überwachungs Protokolle](../audit-logs.md#file-removed-audit-logs)
- [Zentrale Berichterstellung für Azure Information Protection](../reports-aip.md)

> [!IMPORTANT]
> In dieser Version generieren Datei Bezeichnungs Aktionen keine neuen Überwachungs Protokolle für die **Bezeichnung** .
> Wenn Sie die Überprüfung im Modus **erzwingen = on** ausführen, wird empfohlen, ein Upgrade auf [Version 2.7.99.0](#version-27990)durchzuführen.
> 

**Erzwingen von TLS 1.2**

Ab dieser Version des Azure Information Protection Clients werden nur die TLS-Versionen 1,2 oder höher unterstützt.
    
Kunden, die über ein TLS-Setup verfügen, das TLS 1,2 nicht unterstützt, müssen zu einem Setup wechseln, das TLS 1,2 unterstützt, um Azure Information Protection Richtlinien, Token, Überwachung und Schutz zu verwenden und Azure Information Protection-basierte Kommunikation zu empfangen. 
    
Weitere Informationen zu den Anforderungen finden Sie unter [Firewalls und Netzwerkinfrastruktur Anforderungen](../requirements.md#firewalls-and-network-infrastructure).

**Korrekturen und Verbesserungen** 

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

- Wenn mehrere Exchange-Konten konfiguriert sind und der Azure Information Protection Outlook-Client aktiviert ist, werden die e-Mails wie erwartet vom sekundären Konto gesendet. Weitere Informationen zum Konfigurieren des Unified-Bezeichnungs Clients mit Outlook finden Sie unter [zusätzliche Voraussetzungen für den Azure Information Protection Unified-Bezeichnung-Client](clientv2-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-unified-labeling-client).

- Wenn ein Dokument mit einer höheren Vertraulichkeits Bezeichnung per Drag and Drop per Drag and Drop in eine e-Mail eingefügt wird, erhält die e-Mail nun automatisch die höhere Vertraulichkeits Bezeichnung wie erwartet. Weitere Informationen zum bezeichnen von Client Funktionen finden Sie in der [Bezeichnung Client Vergleichstabelle](use-client.md#compare-the-labeling-clients-for-windows-computers).

- Benutzerdefinierte Berechtigungen werden jetzt erwartungsgemäß auf e-Mails angewendet, wenn e-Mail-Adressen sowohl einen Apostroph (') als auch einen Zeitraum (.) enthalten. Weitere Informationen zum Konfigurieren des Unified-Bezeichnungs Clients mit Outlook finden Sie unter [zusätzliche Voraussetzungen für den Azure Information Protection Unified-Bezeichnung-Client](clientv2-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-unified-labeling-client).

- Standardmäßig geht der NTFS-Besitzer einer Datei verloren, wenn die Datei durch die vereinheitlichte Bezeichnung Scanner, PowerShell oder die Datei-Explorer-Erweiterung gekennzeichnet wird. Nun können Sie das System so konfigurieren, dass der NTFS-Besitzer der Datei beibehalten wird, indem Sie die neue **[usecopyandshandentfsowner](clientv2-admin-guide-customizations.md#preserve-ntfs-owners-during-labeling-public-preview)** Advanced-Einstellung auf " **true**" festlegen. 

    Die erweiterte Einstellung **usecopyandkonservierungs entbersowner** erfordert eine geringe Latenz, eine zuverlässige Netzwerkverbindung zwischen dem Scanner und dem gescannten Repository.

## <a name="version-261110"></a>Version 2.6.111.0 

**Veröffentlicht** 03/09/2020

Unterstützt durch 12/29/2020

**Neue Features:**

- Allgemein verfügbare Version des [Scanners](../deploy-aip-scanner.md)zum Überprüfen und bezeichnen von Dokumenten in lokalen Daten speichern. 

- [Scanner](../deploy-aip-scanner.md) -bezogen:
    - [Einfachere lokale und untergeordnete SharePoint-](../quickstart-findsensitiveinfo.md#permission-users-to-scan-sharepoint-repositories)Ermittlung. Das Festlegen der einzelnen Standorte ist nicht mehr erforderlich. 
    - Erweiterte Eigenschaft für die SQL-Segment [Größen](../deploy-aip-scanner-prereqs.md#storage-requirements-and-capacity-planning-for-sql-server) Änderung hinzugefügt.
    - Administratoren haben jetzt die Möglichkeit, [vorhandene Scans anzuhalten und eine erneute Überprüfung durchzuführen](../deploy-aip-scanner-manage.md#stopping-a-scan) , wenn die Standard Bezeichnung geändert wurde.
    - Standardmäßig legt Scanner jetzt minimale Telemetrie für schnellere Scans und eine reduzierte Protokoll Größe fest, und Informationstypen werden nun in der Datenbank zwischengespeichert. Erfahren Sie mehr über die [Scanner-Optimierung](../deploy-aip-scanner-configure-install.md#optimizing-scanner-performance). 
    - Scanner unterstützt jetzt separate bereit Stellungen für die Datenbank und den Dienst, während **sysadmin** -Rechte nur für die Daten Bank Bereitstellung erforderlich sind.
    - Verbesserungen an der Leistung des Scanners. 

- Änderung des [PowerShell](./clientv2-admin-guide-powershell.md) -Cmdlets **Set-aipfilelabel** , um das Entfernen des Schutzes von PST-, rar-, 7zip-und MSG-Dateien zu ermöglichen. Diese Funktion ist standardmäßig deaktiviert und muss mithilfe des [Set-labelpolicy](./clientv2-admin-guide-customizations.md) -Cmdlets aktiviert werden, wie [hier](./clientv2-admin-guide-customizations.md#enable-removal-of-protection-from-compressed-files)beschrieben.  

- Die Möglichkeit, Azure Information Protection Administratoren zu steuern, wann die Pfile-Erweiterungen für Dateien verwendet werden. Erfahren Sie mehr über das [ändern geschützter Dateitypen](./clientv2-admin-guide-customizations.md#change-which-file-types-to-protect). 

- Unterstützung für dynamisches visuelles Element für Anwendungen und Variablen hinzugefügt. Weitere Informationen zum Konfigurieren von [Bezeichnungen für visuelle Kennzeichnungen](../configure-policy-markings.md). 

- Verbesserungen an [anpassbaren Richtlinien Tipps für automatische und empfohlene Bezeichnungen](use-client.md).   

- Unterstützung für [Offline Beschriftungs Funktionen](./clientv2-admin-guide-customizations.md#support-for-disconnected-computers) mit Office-Apps im Unified-Bezeichnungs Client hinzugefügt.

**Fehlerbehebungen:**

- In Fällen, in denen Benutzer erfolglos versuchten, geschützte TIFF-Dateien und TIFF-Dateien zu öffnen, die von RightFax erstellt wurden, werden die TIFF-Dateien nun geöffnet und bleiben erwartungsgemäß stabil.  
- Vorherige Beschädigungen geschützter txt-und PDF-Dateien werden aufgelöst.
- In Log Analytics wurde eine inkonsistente Bezeichnung zwischen **automatischen** und **manuellen** Bezeichnungen korrigiert. 
- Unerwartete Vererbungs Probleme, die zwischen neuen e-Mails und der zuletzt geöffneten e-Mail eines Benutzers erkannt wurden, sind nun behoben.  
- Der Schutz von **. msg** -Dateien als **. msg. pfiles** funktioniert jetzt erwartungsgemäß. 
- Die von den benutzerdefinierten Office-Einstellungen hinzugefügten Berechtigungen für Mitbesitzer werden nun wie erwartet angewendet. 
- Wenn Sie die Berechtigungs Herabstufung eingeben, kann Text nicht mehr eingegeben werden, wenn bereits andere Optionen ausgewählt sind. 

## <a name="next-steps"></a>Nächste Schritte

Sie sind nicht sicher, ob Unified Bezeichnung der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen des zu verwendenden Kunden für Windows-Computer](use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

Weitere Informationen zum Installieren und Verwenden des Unified-Beschriftungs Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection Unified-Bezeichnung Client Administrator Handbuch](clientv2-admin-guide.md)