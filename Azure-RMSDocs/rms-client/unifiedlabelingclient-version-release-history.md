---
title: Azure Information Protection vereinheitlichte Bezeichnung für den Client Versionsverlauf & Unterstützungs Richtlinie
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: a8abcbf66f13498e3ff1fb45b979c6a53cf4f016
ms.sourcegitcommit: 129370798e7d1b5baa110b2d7b2f24abd3cad5c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89316694"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection Unified Bezeichnungs Verlauf des Client Versions Verlaufs und der Support Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> **Kunden mit erweitertem Microsoft-Support für Windows 7 und Office 2010 können auch Azure Information Protection Unterstützung für diese Versionen erhalten. Wenden Sie sich an Ihren Support, um ausführliche Informationen zu erhalten.*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Sie können den Azure Information Protection Unified Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunterladen.

Nach einer kurzen Verzögerung von in der Regel einige Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog enthalten. Azure Information Protection Versionen haben den Produktnamen **Microsoft Azure Information Protection**  >  **Microsoft Azure Information Protection Unified**-Bezeichnungs Client und eine Klassifizierung von **Updates**. 

Das Einschließen von Azure Information Protection in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Software Bereitstellungs Mechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [aktualisieren und Verwalten des Azure Information Protection Unified Bezeichnung-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede allgemein verfügbare Version des Azure Information Protection Unified Bezeichnung-Clients wird bis zu sechs Monate nach der Veröffentlichung der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

##### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden:

|Clientversion|Datum der Veröffentlichung|
|--------------|-------------|
|2.2.21.0|09/03/2019|
|2.2.19.0|08/06/2019|
|2.2.14.0|07/15/2019|
|2.0.779.0|05/01/2019|
|2.0.778.0|04/16/2019|

Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.


### <a name="release-information"></a>Informationen zum Release

Verwenden Sie die folgenden Informationen, um zu erfahren, was für eine unterstützte Version des Azure Information Protection Unified Bezeichnung-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn Sie also ein Problem mit dem Unified-Bezeichnungs Client haben, sollten Sie überprüfen, ob es mit der neuesten GA-Version behoben wurde. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

Dieser Client ersetzt den Azure Information Protection Client (klassisch). Informationen zum Vergleichen von Features und Funktionen mit dem klassischen Client finden Sie unter [vergleichen der Bezeichnung für Clients für Windows-Computer](use-client.md#compare-the-labeling-clients-for-windows-computers).

## <a name="version-2885-public-preview"></a>Version 2.8.85 (öffentliche Vorschau)

Unified-Beschriftungs Scanner und Client Version 2.8.85

**Veröffentlicht** 09/02/2020

Diese Version enthält die folgenden neuen Features, Korrekturen und Verbesserungen für den Unified-Beschriftungs Scanner und-Client:

- [Neue Features für den Unified-Beschriftungs Scanner](#new-features-for-the-unified-labeling-scanner)
- [Neue Features für den Unified-Bezeichnungs Client](#new-features-for-the-unified-labeling-client)
- [Korrekturen und Verbesserungen](#fixes-and-improvements)

### <a name="new-features-for-the-unified-labeling-scanner"></a>Neue Features für den Unified-Beschriftungs Scanner

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

1. Führen Sie ein Upgrade Ihrer Überprüfungs Version durch, und stellen Sie sicher, dass Ihr Scanner-Cluster richtig konfiguriert ist. Weitere Informationen finden Sie unter:
    - [Aktualisieren Ihres Scanners](../deploy-aip-scanner-configure-install.md#upgrading-your-scanner)
    - [Erstellen eines Scanner-Clusters](../deploy-aip-scanner-configure-install.md#create-a-scanner-cluster) 
    
1. Stellen Sie sicher, dass Azure Information Protection Analytics aktiviert ist. 

    Wechseln Sie in der Azure-Portal zu **Azure Information Protection > verwalten > configure Analytics (Vorschau).** 

    Weitere Informationen finden Sie unter [Zentrale Berichterstellung für Azure Information Protection (öffentliche Vorschau)](../reports-aip.md).

1. Aktivieren Sie die Netzwerk Ermittlung durch Ausführen des PowerShell-Cmdlets [**install-mipnetworkdiscovery**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery) . 

    > [!IMPORTANT]
    > Wenn Sie dieses Cmdlet ausführen, stellen Sie sicher, dass Sie einen schwachen Benutzer als Wert für den **standarddomainsuseraccount** -Parameter verwenden, um sicherzustellen, dass alle öffentlichen Zugriffe auf die Repository gemeldet werden. 
    >
    > Dieser Benutzer muss nur Mitglied der Gruppe " **Domänen Benutzer** " sein und wird verwendet, um den öffentlichen Zugriff auf die Depots zu simulieren.

1. Wechseln Sie in der Azure-Portal zu Azure Information Protection > **Network Scan-Aufträge** , und [Erstellen Sie Aufträge, um bestimmte Bereiche Ihres Netzwerks zu](../deploy-aip-scanner-configure-install.md#create-a-network-scan-job-public-preview)überprüfen. 

1. Verwenden Sie die generierten Berichte im Bereich "neue [**Depots**](../deploy-aip-scanner-configure-install.md#analyze-risky-repositories-found-public-preview) ", um nach zusätzlichen Netzwerkdatei Freigaben zu suchen, die möglicherweise gefährdet sind. Fügen Sie Ihren [Inhalts Überprüfungs Aufträgen](../deploy-aip-scanner-configure-install.md#create-a-content-scan-job) riskante Dateifreigaben hinzu, um die hinzugefügten Depots auf vertrauliche Inhalte zu scannen.

##### <a name="network-discovery-cmdlets"></a>Cmdlets für die Netzwerk Ermittlung

Folgende PowerShell-Cmdlets sind für die Netzwerk Ermittlung hinzugefügt:

|Cmdlet  |Beschreibung  |
|---------|---------|
|[**Get-mipnetworkdiscoveryconfiguration**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryConfiguration)     |   Ruft die aktuelle Einstellung ab, ob der Netzwerk Ermittlungsdienst Netzwerk Scan Daten aus der Standard-, Online-oder Offline Datei abruft, die aus der Azure-Portal exportiert wurde.      |
|[**Get-mipnetworkdiscoveryjobs**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryJobs)     |    Ruft eine Liste der derzeit konfigurierten Netzwerk Scanaufträge ab.     |
|[**Get-mipnetworkdiscoverystatus**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryStatus)     |     Ruft den aktuellen Status aller Netzwerk Scanaufträge ab, die in Ihrem Mandanten konfiguriert sind.    |
| [**Import-mipnetworkdiscoveryconfiguration**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Import-MIPNetworkDiscoveryConfiguration)     |    Importiert die Konfiguration für einen Netzwerk Scanauftrag aus einer Datei.     |
| [**Install-mipnetworkdiscovery**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery)| Installiert den Netzwerk Ermittlungsdienst. |
|[**Set-mipnetworkdiscoveryconfiguration**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Set-MIPNetworkDiscoveryConfiguration)     |   Legt die Konfiguration fest, ob der Netzwerk Ermittlungsdienst Netzwerk Scan Daten aus der Standard-, Online-oder Offline Datei abruft, die aus der Azure-Portal exportiert wurden.      |
|[**Start-mipnetworkdiscovery**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Start-MIPNetworkDiscovery)     |  Führt sofort einen bestimmten Netzwerk Scanauftrag aus.       |
|[**Deinstallation von mipnetworkdiscovery**](https://docs.microsoft.com/powershell/module/azureinformationprotection/Uninstall-MIPNetworkDiscovery)     |  Deinstalliert den Netzwerk Ermittlungsdienst.       |
| | |

### <a name="new-features-for-the-unified-labeling-client"></a>Neue Features für den Unified-Bezeichnungs Client

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

Weitere Informationen finden Sie unter:

- [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-implement-tenant-key.md)
- [Doppelte Schlüssel Verschlüsselung](https://docs.microsoft.com/microsoft-365/compliance/double-key-encryption) in den Microsoft 365-Dokumentation

### <a name="fixes-and-improvements"></a>Korrekturen und Verbesserungen

- [Korrekturen und Verbesserungen bei Scanner](#azure-information-protection-scanner-fixed-issues)
- [Client Korrekturen und-Verbesserungen](#azure-information-protection-client-fixed-issues)

#### <a name="azure-information-protection-scanner-fixed-issues"></a>Behobene Probleme mit Azure Information Protection Scanner

Die folgenden Korrekturen wurden in Version 2.8.85 des Azure Information Protection Unified-Beschriftungs Scanners übermittelt:

- Verbesserungen [beim Scannen von Dateien mit langen Pfaden](../deploy-aip-scanner-prereqs.md#file-path-requirements)
- Der AIP-Scanner scannt nun vollständige [SharePoint](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) -Umgebungen, wenn mehrere Content-Datenbanken vorhanden sind.
- Der AIP-Scanner unterstützt jetzt [SharePoint](../deploy-aip-scanner-prereqs.md#sharepoint-requirements) -Dateien mit einem Punkt im Pfad, aber keine Erweiterung. Beispielsweise wird eine Datei mit dem Pfad `https://sharepoint.contoso.com/shared documents/meeting-notes` ohne Erweiterung nun erfolgreich gescannt.
- Der AIP-Scanner unterstützt jetzt [benutzerdefinierte vertrauliche Informationstypen](../deploy-aip-scanner-configure-install.md#identify-all-custom-conditions-and-known-sensitive-information-types) , die im Microsoft Security and Compliance Center erstellt wurden und keiner Richtlinie angehören.

#### <a name="azure-information-protection-client-fixed-issues"></a>Behobene Probleme mit Azure Information Protection Clients

Die folgenden Korrekturen wurden in Version 2.8.85 des Azure Information Protection Unified-Bezeichnung Client übermittelt:

- Ein neuer, erzählter Hinweis für alle Elemente, die momentan aus dem Symbolmenü " **Vertraulichkeits** ![Spalten](../media/selected-sensitivity-options.png "Symbol "Spalten"") " in Office-Apps ausgewählt werden. Weitere Informationen finden Sie auf der Seite über [Vertraulichkeits Bezeichnungen in den Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#what-sensitivity-labels-can-do)-Dokumentation.
- Korrekturen zum Anzeigen von JPEG-Dateien im [AIP-Viewer](clientv2-view-use-files.md)
- **Das herab** Stufen einer Bezeichnung schließt jetzt automatisch den Schutz Besitzer in Überwachungs [Ereignissen](../audit-logs.md#downgrade-label-audit-logs) ein.
- Änderungs Ereignisse enthalten jetzt das **LastModifiedDate** in den Überwachungs [Protokollen](../audit-logs.md#change-protection-audit-logs) .
- Unterstützung für **Proxy. PAC** -Dateien hinzugefügt, wenn [ein Proxy](../requirements.md#firewalls-and-network-infrastructure) zum Abrufen eines Tokens verwendet wird. Legen Sie zum Aktivieren dieses Fixes den neuen Registrierungsschlüssel **usedefaultkredentialsinproxy = 1**fest.
- Korrekturen für die Authentifizierung beim Aktualisieren von [Richtlinien](../configure-policy.md#making-changes-to-the-policy)
- Korrekturen für [Automatische Inhalte kennzeichnen](../configure-policy-markings.md) von Aktualisierungen für PowerPoint im schreibgeschützten Modus
- Verbesserungen bei Popups und Fehler Texten
- QuickInfo-Updates, um die höchste [Klassifizierung für e-Mail-Anhänge](../faqs-infoprotect.md#when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling)anzuzeigen, wobei sowohl die Klassifizierung der e-Mail als auch die Anlage berücksichtigt werden. 
- Fehlerbehebungen für den **Bericht einen Problem** Text beim Ändern von Vertraulichkeits Beschriftungs Richtlinien mithilfe des Cmdlets " [**Set-labelpolicy**](https://docs.microsoft.com/powershell/module/exchange/set-labelpolicy) "
- Korrekturen in Fehlern, die angezeigt werden, wenn das Cmdlet " [**Set-aipfilelabel**](https://docs.microsoft.com/powershell/module/azureinformationprotection/set-aipfilelabel?view=azureipps) " mit einer ungültigen Bezeichnungs-ID verwendet wird. 
- Leistungsfehler Behebungen für das [Entschlüsseln von SMIME](clientv2-view-use-files.md) -e-Mails im Lesebereich von Outlook.
- Fehlerbehebungen für das [Entschlüsseln von PST-Dateien](clientv2-admin-guide-file-types.md) , die Kenn Wort verschlüsselte Dateien enthalten. Das Entschlüsseln von PST-Dateien schlägt nicht mehr fehl, wenn die PST-Datei eine Kenn Wort geschützte Datei enthält.
- Durch das Entfernen einer Schutz Bezeichnung, die nicht in der Bereichs bezogenen [Richtlinie](../configure-policy-scope.md) enthalten ist, wird der Schutz des Inhalts nicht mehr aufgehoben.


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

- [Verwenden Sie Scanner, um Bezeichnungen auf der Grundlage der empfohlenen Bedingungen anzuwenden](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#prerequisites-for-the-azure-information-protection-scanner). AIP-Kunden können nun festlegen, dass nur Dienst seitige Authentifizierung implementiert werden soll. Diese Funktion ermöglicht es AIP-Endbenutzern, immer Empfehlungen anstelle des vorherigen Szenarios zu befolgen, das nur die automatische Bezeichnung auf der Benutzerseite aktiviert hat.

- [Informationen dazu, welche Dateien zuvor von Scanner erkannt wurden, wurden aus dem gescannten Repository gelöscht](https://docs.microsoft.com/azure/information-protection/reports-aip) Diese gelöschten Dateien wurden zuvor nicht in AIP Analytics gemeldet und sind jetzt im Bericht zur scannerermittlung verfügbar.

- [Berichte aus der Überprüfung bei Fehlern zum Anwenden von Aktions Ereignissen erhalten](https://docs.microsoft.com/azure/information-protection/reports-aip#friendly-schema-reference-for-event-functions). Verwenden Sie Berichte, um mehr über fehlgeschlagene Aktions Ereignisse und Möglichkeiten zu erfahren, wie Sie zukünftige vorkommen vermeiden. 

- Einführung des AIP Scanner Diagnostics Analyzer Tool zur Erkennung und Analyse allgemeiner Scanner-Fehler. Um mit der Verwendung der AIP-Scanner-Diagnose zu beginnen, [führen Sie das neue Cmdlet **Start-aipscannerdiagnostics** ](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#troubleshooting-using-scanner-diagnostic-tool)aus. 

- Sie können nun die maximale CPU-Auslastung auf dem Überprüfungs Computer verwalten und begrenzen. Erfahren Sie, wie Sie die CPU-Auslastung von 100% verhindern und die CPU-Auslastung mithilfe der [beiden neuen erweiterten Einstellungen **scannermaxcpu**und **scannermincpu**](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#limit-cpu-consumption)verwalten. 

- Nun können Sie den Unified-Beschriftungs Scanner so konfigurieren, dass bestimmte Dateien abhängig von ihren Dateiattributen übersprungen werden. Hiermit wird die Liste der Dateiattribute definiert, durch die eine Datei mit der neuen **[scannerfsattributestoskip](clientv2-admin-guide-customizations.md#skip-or-ignore-files-during-scans-depending-on-file-attributes)** Advanced-Einstellung übersprungen wird.

**Neue Features für den Unified-Bezeichnungs Client:**

- [**Ausrichtungpopups**](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent) werden jetzt für Änderungen angezeigt, die an Standard Bezeichnungen im Unified Label-Client vorgenommen werden.
    
- Reibungslosere Integration mit visuellen Inhalts Markierungen, die von Office angewendet werden. Weitere Informationen zum Konfigurieren von Inhalts Markierungen in Office-Dokumenten finden [Sie unter Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information](../configure-policy-markings.md)Protection.

- Die neue **wordshapenametoremove** Advanced-Eigenschaft ermöglicht das Entfernen von Inhalts Markierungen in Word-Dokumenten, die von Anwendungen von Drittanbietern erstellt wurden. Erfahren Sie mehr darüber, wie [Sie vorhandene Shape-Namen identifizieren und mithilfe von **wordshapenametoremove**zum Entfernen definieren](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solutions).

- Unterstützung für **Double Key Encryption (DKE)** (Public Preview). 

    Nun können Sie den Unified-Bezeichnungs Client verwenden, um hochgradig sensiblen Inhalt zu schützen, während Sie die vollständige Kontrolle über Ihren Schlüssel behalten. DKE erfordert zwei Schlüssel für den Zugriff auf geschützte Inhalte: ein Schlüssel wird in Azure gespeichert, und der andere Schlüssel wird vom Kunden gespeichert. 

    Weitere Informationen zu den standardmäßigen cloudbasierten Mandanten Stamm Schlüsseln finden [Sie unter Planning and Implementierungs your Azure Information Protection Tenant Key](../plan-implement-tenant-key.md). Informationen zum Implementieren der doppelten Schlüssel Verschlüsselung finden Sie unter [doppelte Schlüssel Verschlüsselung](https://docs.microsoft.com/microsoft-365/compliance/double-key-encryption) in der Microsoft 365-Dokumentation.

**Es wurden neue Überwachungs Protokolle für entfernte Dateien generiert.**

Überwachungs Protokolle werden nun immer generiert, wenn der Scanner erkennt, dass eine zuvor überprüfte Datei entfernt wurde.

Weitere Informationen finden Sie unter:
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
        
- Verbesserte Benutzer Benachrichtigungen für fehlende Richtlinien. Weitere Informationen zu Bezeichnungs Richtlinien für den Unified Label-Client finden [Sie unter welche Bezeichnungs Richtlinien können](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do) in der Microsoft 365-Dokumentation funktionieren.

- [Automatische Bezeichnungen](../configure-policy-classification.md) werden jetzt in Excel für Szenarien angewendet, in denen ein Benutzer mit dem Schließen einer Datei beginnt, ohne zu speichern, genauso wie wenn ein Benutzer eine Datei aktiv speichert.

- Kopf-und Fußzeilen werden erwartungsgemäß entfernt und nicht für jedes Dokument gespeichert, wenn die [externalcontentmarkingtoremove](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions) -Einstellung konfiguriert ist.

- [Dynamische Benutzervariablen](../configure-policy-markings.md#using-variables-in-the-text-string) werden nun wie erwartet in den visuellen Kennzeichnungen eines Dokuments angezeigt.

- Das Problem, dass nur die erste Seite des Inhalts einer PDF-Datei zum Anwenden von Regeln für die automatische Klassifizierung verwendet wurde, ist jetzt aufgelöst, und die automatische Klassifizierung basierend auf dem gesamten Inhalt in der PDF-Datei wird jetzt erwartungsgemäß fortgesetzt. Weitere Informationen zur Klassifizierung und Bezeichnung finden Sie in den häufig gestellten Fragen zur [Klassifizierung und Bezeichnung](https://docs.microsoft.com/azure/information-protection/faqs-infoprotect). 

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
    - [Einfachere lokale und untergeordnete SharePoint-](https://docs.microsoft.com/azure/information-protection/quickstart-findsensitiveinfo#permission-users-to-scan-sharepoint-repositories)Ermittlung. Das Festlegen der einzelnen Standorte ist nicht mehr erforderlich. 
    - Erweiterte Eigenschaft für die SQL-Segment [Größen](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#storage-requirements-and-capacity-planning-for-sql-server) Änderung hinzugefügt.
    - Administratoren haben jetzt die Möglichkeit, [vorhandene Scans anzuhalten und eine erneute Überprüfung durchzuführen](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#stop-a-scan) , wenn die Standard Bezeichnung geändert wurde.
    - Standardmäßig legt Scanner jetzt minimale Telemetrie für schnellere Scans und eine reduzierte Protokoll Größe fest, und Informationstypen werden nun in der Datenbank zwischengespeichert. Erfahren Sie mehr über die [Scanner-Optimierung](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#optimizing-the-performance-of-the-scanner). 
    - Scanner unterstützt jetzt separate bereit Stellungen für die Datenbank und den Dienst, während **sysadmin** -Rechte nur für die Daten Bank Bereitstellung erforderlich sind.
    - Verbesserungen an der Leistung des Scanners. 

- Änderung des [PowerShell](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-powershell) -Cmdlets **Set-aipfilelabel** , um das Entfernen des Schutzes von PST-, rar-, 7zip-und MSG-Dateien zu ermöglichen. Diese Funktion ist standardmäßig deaktiviert und muss mithilfe des [Set-labelpolicy](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations) -Cmdlets aktiviert werden, wie [hier](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-removal-of-protection-from-compressed-files)beschrieben.  

- Die Möglichkeit, Azure Information Protection Administratoren zu steuern, wann die Pfile-Erweiterungen für Dateien verwendet werden. Erfahren Sie mehr über das [ändern geschützter Dateitypen](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#change-which-file-types-to-protect). 

- Unterstützung für dynamisches visuelles Element für Anwendungen und Variablen hinzugefügt. Weitere Informationen zum Konfigurieren von [Bezeichnungen für visuelle Kennzeichnungen](https://docs.microsoft.com/azure/information-protection/configure-policy-markings). 

- Verbesserungen an [anpassbaren Richtlinien Tipps für automatische und empfohlene Bezeichnungen](use-client.md).   

- Unterstützung für [Offline Beschriftungs Funktionen](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#support-for-disconnected-computers) mit Office-Apps im Unified-Bezeichnungs Client hinzugefügt.

**Fehlerbehebungen:**

- In Fällen, in denen Benutzer erfolglos versuchten, geschützte TIFF-Dateien und TIFF-Dateien zu öffnen, die von RightFax erstellt wurden, werden die TIFF-Dateien nun geöffnet und bleiben erwartungsgemäß stabil.  
- Vorherige Beschädigungen geschützter txt-und PDF-Dateien werden aufgelöst.
- In Log Analytics wurde eine inkonsistente Bezeichnung zwischen **automatischen** und **manuellen** Bezeichnungen korrigiert. 
- Unerwartete Vererbungs Probleme, die zwischen neuen e-Mails und der zuletzt geöffneten e-Mail eines Benutzers erkannt wurden, sind nun behoben.  
- Der Schutz von **. msg** -Dateien als **. msg. pfiles** funktioniert jetzt erwartungsgemäß. 
- Die von den benutzerdefinierten Office-Einstellungen hinzugefügten Berechtigungen für Mitbesitzer werden nun wie erwartet angewendet. 
- Wenn Sie die Berechtigungs Herabstufung eingeben, kann Text nicht mehr eingegeben werden, wenn bereits andere Optionen ausgewählt sind. 


## <a name="version-25330"></a>Version 2.5.33.0

**Veröffentlicht**: 10/23/2019

Unterstützt durch 09/09/2020

**Neue Features:**

- Vorschauversion des [Scanners](../deploy-aip-scanner.md), um lokale Datenspeicher zu überprüfen und zu bezeichnen. Mit dieser Version des Scanners:
    
    - Wenn Sie die Scanner für die Verwendung desselben Scanner-Profils konfigurieren, können mehrere Scanner dieselbe SQL Server Datenbank gemeinsam nutzen. Diese Konfiguration erleichtert die Verwaltung mehrerer Scanner und führt zu schnelleren Scanzeiten. Wenn Sie diese Konfiguration verwenden, warten Sie immer, bis die Installation eines Scanners abgeschlossen ist, bevor Sie einen weiteren Scanner mit dem gleichen Profil installieren.
    
    - Sie müssen ein Profil angeben, wenn Sie den Scanner installieren, und die Scannerdatenbank hat den Namen **AIPScannerUL_ \<profile_name> **. Der Parameter " *profile* " ist auch für "Set-aipscanner" obligatorisch.
    
    - Sie können in allen Dokumenten eine Standard Bezeichnung festlegen, auch wenn Dokumente bereits mit der Bezeichnung versehen sind. Legen Sie in den Überprüfungs Profil-oder Repository-Einstellungen die Option **Dateien** neu bezeichnen auf ein fest **, und aktivieren** Sie das Kontrollkästchen neue **Bezeichnung Standard Bezeichnung erzwingen** .
    
    - Sie können vorhandene Bezeichnungen aus allen Dokumenten entfernen, und dieser Vorgang umfasst das Entfernen des Schutzes, wenn dieser zuvor durch eine Bezeichnung angewendet wurde. Der Schutz, der unabhängig von einer Bezeichnung angewendet wird, wird beibehalten. Diese Scannerkonfiguration wird in den Einstellungen für das Scanner-Profil oder im Repository mit den folgenden Einstellungen erreicht:
        - Bezeichnungs **Dateien basierend auf dem Inhalt**: **Off**
        - **Standard Bezeichnung**: **keine**
        - **Dateien**neu bezeichnen: **aktivieren** Sie das Kontrollkästchen **Standard Bezeichnung erzwingen** ausgewählt haben.
    
    - Wie bei der Überprüfung des klassischen Clients schützt der Scanner standardmäßig Office-Dateien und PDF-Dateien. Sie können andere Dateitypen schützen, wenn Sie eine [Erweiterte PowerShell-Einstellung](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect)verwenden.
    
    - Ereignis-IDs für die Start-und Beendigungs Zyklen der Scanner werden nicht in das Windows-Ereignisprotokoll geschrieben. Verwenden Sie stattdessen die Azure-Portal für diese Informationen.
    
    - Bekanntes Problem: neue und umbenannte Bezeichnungen können nicht als Standard Bezeichnung für das Scanner-Profil oder die Repository-Einstellungen ausgewählt werden. Problemumgehungen:
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

- Neues Cmdlet " [Export-aiplogs](https://docs.microsoft.com/powershell/module/azureinformationprotection/export-aiplogs)", um alle Protokolldateien aus "%LocalAppData%\microsoft\msip\logs" zu erfassen und Sie in einer einzelnen komprimierten Datei mit dem ZIP-Format zu speichern. Sie können diese ZIP-Datei an Microsoft-Support senden, wenn Sie aufgefordert werden, Protokolldateien zu senden, um ein gemeldetes Problem zu untersuchen.

**Fehlerbehebungen:**

- Sie können mit dem Datei-Explorer erfolgreich Änderungen an einer geschützten Datei vornehmen und mit der rechten Maustaste klicken, nachdem ein Kennwort für die Datei entfernt wurde.

- Sie können nativ geschützte Dateien im Viewer öffnen, ohne dass das [Nutzungsrecht](../configure-usage-rights.md#usage-rights-and-descriptions)"Speichern unter", "exportieren (exportieren)" erforderlich ist.

- Bezeichnungen und Richtlinien Einstellungen werden erwartungsgemäß aktualisiert, ohne dass " [Clear-aipauthentication](/powershell/module/azureinformationprotection/clear-aipauthentication?)" ausgeführt werden muss, oder Sie müssen den Ordner "%LocalAppData%\microsoft\msip\mip" manuell löschen.

**Weitere Änderungen**

- Durch [Zurücksetzen](clientv2-admin-guide.md#more-information-about-the-reset-settings-option) werden nun die Ordner%LocalAppData%\microsoft\msip\mip \\ *\<ProcessName.exe\>* anstelle des Ordners%LocalAppData%\microsoft\msip\mip \\ *\<ProcessName\>* \mip gelöscht.

- " [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) " enthält jetzt die Inhalts-ID für ein geschütztes Dokument.


## <a name="next-steps"></a>Nächste Schritte

Sie sind nicht sicher, ob Unified Bezeichnung der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen des zu verwendenden Kunden für Windows-Computer](use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

Weitere Informationen zum Installieren und Verwenden des Unified-Beschriftungs Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection Unified-Bezeichnung Client Administrator Handbuch](clientv2-admin-guide.md)

