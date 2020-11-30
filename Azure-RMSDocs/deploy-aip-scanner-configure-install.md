---
title: Installieren und Konfigurieren der Unified-Bezeichnung für Azure Information Protection (AIP)
description: Anweisungen zum Installieren und Konfigurieren des Azure Information Protection Unified Bezeichnung Scanner zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: de4c71b6cb7b6836d6757c7cd74bc21e30999a38
ms.sourcegitcommit: d31cb53de64bafa2097e682550645cadc612ec3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96316567"
---
# <a name="configuring-and-installing-the--azure-information-protection-unified-labeling-scanner"></a>Konfigurieren und Installieren des Azure Information Protection Unified-Beschriftungs Scanner

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2*

>[!NOTE] 
> Wenn Sie mit dem klassischen AIP-Scanner arbeiten, finden Sie weitere Informationen unter [Installieren und Konfigurieren des Azure Information Protection klassischen Scanner](deploy-aip-scanner-configure-install-classic.md).

Vergewissern Sie sich vor dem Konfigurieren und Installieren des Azure Information Protection Scanners, dass Ihr System die [erforderlichen Voraussetzungen](deploy-aip-scanner-prereqs.md)erfüllt. 

Wenn Sie fertig sind, fahren Sie mit den folgenden Schritten fort:

1. [Konfigurieren des Scanners im Azure-Portal](#configure-the-scanner-in-the-azure-portal)

1. [Installieren der Überprüfung](#install-the-scanner)

1. [Abrufen eines Azure AD-Tokens für die Überprüfung](#get-an-azure-ad-token-for-the-scanner)

1. [Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz](#configure-the-scanner-to-apply-classification-and-protection)
 
Führen Sie die folgenden zusätzlichen Konfigurationsverfahren aus, die für Ihr System erforderlich sind:

|Verfahren  |BESCHREIBUNG  |
|---------|---------|
|[Ändern der zu schützenden Dateitypen](#change-which-file-types-to-protect) |Möglicherweise möchten Sie verschiedene Dateitypen Scannen, klassifizieren oder schützen als die Standardwerte. Weitere Informationen finden Sie unter [AIP-Scanvorgang](deploy-aip-scanner.md#aip-scanning-process). |
|[Aktualisieren Ihres Scanners](#upgrading-your-scanner) | Aktualisieren Sie Ihren Scanner, um die neuesten Features und Verbesserungen zu nutzen.|
|[Bearbeiten von Datenrepository-Einstellungen in einem Massen Vorgang](#editing-data-repository-settings-in-bulk)| Verwenden Sie Import-und Exportoptionen, um für mehrere Daten Depots Massen Änderungen vorzunehmen.|
|[Verwenden des Scanners mit alternativen Konfigurationen](#using-the-scanner-with-alternative-configurations)| Verwenden Sie den Scanner, ohne Bezeichnungen mit Bedingungen zu konfigurieren. |
|[Optimieren der Leistung](#optimizing-scanner-performance)| Leitfaden zur Optimierung der Leistung des Scanners|
| | |

Weitere Informationen finden Sie auch [in der Liste der Cmdlets für den Scanner](#list-of-cmdlets-for-the-scanner).

## <a name="configure-the-scanner-in-the-azure-portal"></a>Konfigurieren des Scanners im Azure-Portal

Bevor Sie die Überprüfung installieren oder von einer älteren Version der allgemeinen Verfügbarkeit aktualisieren, konfigurieren oder überprüfen Sie die Überprüfungs Einstellungen im Bereich Azure Information Protection der Azure-Portal.

So konfigurieren Sie Ihren Scanner: 

1. Melden Sie sich mit einer der folgenden Rollen beim [Azure-Portal](https://portal.azure.com) an:

    - **Complianceadministrator**
    - **Compliancedatenadministrator**
    - **Sicherheitsadministrator**
    - **Globaler Administrator**

    Navigieren Sie dann zum Bereich **Azure Information Protection** .
    
    Beginnen Sie beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumentation mit der Eingabe von **Information**, und wählen Sie **Azure Information Protection** aus.

1. [Erstellen Sie einen scannercluster](#create-a-scanner-cluster). Dieser Cluster definiert ihren Scanner und wird zur Identifizierung der Überprüfungs Instanz verwendet, z. b. während der Installation, Upgrades und anderen Prozessen.

1. Optionale [Scannen Sie Ihr Netzwerk auf riskante Depots](#create-a-network-scan-job-public-preview). Erstellen Sie einen Netzwerk Scanauftrag, um eine bestimmte IP-Adresse oder einen bestimmten Bereich zu scannen, und geben Sie eine Liste der riskanten Depots an, die vertrauliche Inhalte enthalten können, die Sie sichern möchten.  

    Führen Sie Ihren Netzwerk Scanauftrag aus, und analysieren Sie dann [alle gefundenen riskanten Depots](#analyze-risky-repositories-found-public-preview).

1. [Erstellen Sie einen Auftrag](#create-a-content-scan-job) für die Inhalts Überprüfung, um die zu überprüfenden Depots zu definieren.

### <a name="create-a-scanner-cluster"></a>Erstellen eines Scanner-Clusters  

1. Wählen Sie im Menü **Scanner** auf der linken Seite **Cluster** ![Cluster Symbol](media/i-clusters.png "Cluster (Symbol)")aus.

1. Wählen Sie im Bereich **Azure Information Protection-Cluster** die Option Add- ![Symbol](media/i-add.png "Symbol hinzufügen")hinzu **fügen** aus.
    
1. Geben Sie im Bereich **neuen Cluster hinzufügen** einen aussagekräftigen Namen für die Überprüfung ein, und geben Sie optional eine Beschreibung ein. 
    
    Der Cluster Name wird verwendet, um die Konfigurationen und Depots des Scanners zu identifizieren. Sie können z. b. **Europa** eingeben, um die geografischen Standorte der zu überprüfenden Daten Depots zu ermitteln. 

    Sie verwenden diesen Namen später, um zu ermitteln, wo Sie Ihren Scanner installieren oder aktualisieren möchten.

1. Aktivieren **Sie das** ![Symbol](media/qs-tutor/save-icon.png "Symbol "Speichern"") speichern, um die Änderungen zu speichern.

### <a name="create-a-network-scan-job-public-preview"></a>Erstellen eines Netzwerk Scan Auftrags (öffentliche Vorschau)

Ab Version [2.8.85.0](rms-client/unifiedlabelingclient-version-release-history.md#version-28850)können Sie Ihr Netzwerk auf riskante Depots überprüfen. Fügen Sie einem Inhalts Überprüfungs Auftrag mindestens ein Repository hinzu, um Sie auf sensiblen Inhalt zu überprüfen.

- [Voraussetzungen der Netzwerk Ermittlung](#network-discovery-prerequisites)
- [Erstellen eines Netzwerk Scan Auftrags](#creating-a-network-scan-job)

> [!NOTE]
> Die Azure Information Protection Network Discovery-Funktion befindet sich derzeit in der Vorschau Phase. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 
> 

#### <a name="network-discovery-prerequisites"></a>Voraussetzungen der Netzwerk Ermittlung

|Voraussetzung  |BESCHREIBUNG  |
|---------|---------|
|**Installieren des Netzwerkerkennungsdiensts**     |   Wenn Sie vor kurzem ein Upgrade Ihres Scanners durchgeführt haben, müssen Sie möglicherweise weiterhin den Netzwerk Ermittlungsdienst installieren. <br /><br />Führen Sie das Cmdlet [**install-mipnetworkdiscovery**](/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery) aus, um Netzwerk Scanaufträge zu aktivieren.      |
|**Azure Information Protection Analytics**     | Stellen Sie sicher, dass Azure Information Protection Analytics aktiviert ist. <br /><br />Wechseln Sie in der Azure-Portal zu **Azure Information Protection > verwalten > configure Analytics (Vorschau).** <br /><br />Weitere Informationen finden Sie unter [Zentrale Berichterstellung für Azure Information Protection (öffentliche Vorschau)](reports-aip.md).|
| | |

#### <a name="creating-a-network-scan-job"></a>Erstellen eines Netzwerk Scan Auftrags

1. Melden Sie sich beim Azure-Portal an, und wechseln Sie zu **Azure Information Protection.** Wählen Sie im Menü **Scanner** auf der linken Seite die Option Netzwerk Scan **Aufträge (Vorschau)** ![Netzwerk Scanaufträge Symbol](media/i-network-scan-jobs.png "Symbol "Netzwerk Scanaufträge"")aus.
    
1. Wählen Sie im Bereich **Azure Information Protection-Netzwerk Scanaufträge** die Option Add- ![Symbol](media/i-add.png "Symbol hinzufügen")hinzu **fügen** aus.
    
1. Legen Sie auf der Seite **neuen Netzwerk Scanauftrag hinzufügen** die folgenden Einstellungen fest:
        
    |Einstellung  |BESCHREIBUNG  |
    |---------|---------|
    |**Name des Netzwerk Scan Auftrags**     |Geben Sie einen aussagekräftigen Namen für diesen Auftrag ein.  Dieses Feld ist erforderlich.       |
    |**Beschreibung**     |   Geben Sie eine aussagekräftige Beschreibung ein.      |
    |**Wählen Sie den Cluster aus.**     |Wählen Sie in der Dropdown Liste den Cluster aus, den Sie zum Scannen der konfigurierten Netzwerkspeicher Orte verwenden möchten.  <br /><br />**Tipp:** Stellen Sie bei der Auswahl eines Clusters sicher, dass die Knoten im Cluster, den Sie zuweisen, über SMB auf die konfigurierten IP-Adressbereiche zugreifen können.      |
    |**Zu ermittelnde IP-Adressbereiche konfigurieren**     |   Klicken Sie, um eine IP-Adresse oder einen Bereich zu definieren. <br /><br />Geben Sie im Bereich **IP-Bereiche auswählen** einen optionalen Namen und dann eine Start-IP-Adresse und eine End-IP-Adresse für Ihren Bereich ein. <br /><br />**Tipp:** Um nur eine bestimmte IP-Adresse zu scannen, geben Sie die gleiche IP-Adresse in den Feldern **Start-IP** und **End-IP** ein.      |
    |**Zeitplan festlegen**     | Legen Sie fest, wie oft dieser Netzwerk Scanauftrag ausgeführt werden soll.  <br /><br />Wenn Sie **wöchentlich** auswählen, wird die Einstellung **Netzwerk Scanauftrag ausführen auf** angezeigt. Wählen Sie die Wochentage aus, an denen der Netzwerk Scanauftrag ausgeführt werden soll.       |
    |**Startzeit (UTC) festlegen**     |Definieren Sie das Datum und die Uhrzeit, zu der die Ausführung dieses Netzwerk Scan Auftrags gestartet werden soll. Wenn Sie ausgewählt haben, dass der Auftrag täglich, wöchentlich oder monatlich ausgeführt wird, wird der Auftrag mit der von Ihnen ausgewählten Wiederholung zum festgelegten Zeitpunkt ausgeführt. <br /><br />**Hinweis**: seien Sie vorsichtig, wenn Sie das Datum auf einen beliebigen Tag am Monatsende festlegen. Wenn Sie **31 auswählen,** wird der Netzwerk Scanauftrag nicht in einem Monat ausgeführt, der höchstens 30 Tage beträgt.    |
    | | |

1. Aktivieren **Sie das** ![Symbol](media/qs-tutor/save-icon.png "Symbol "Speichern"") speichern, um die Änderungen zu speichern.

> [!TIP]
> Wenn Sie dieselbe Netzwerk Überprüfung mit einem anderen Scanner ausführen möchten, ändern Sie den im Netzwerk Scanauftrag definierten Cluster.
> 
> Wechseln Sie zurück zum Bereich **Netzwerk Scanaufträge** , und wählen Sie **zu Cluster zuweisen** aus, um einen anderen Cluster zu wählen, oder heben Sie die **Zuweisung der Cluster** auf, um später weitere Änderungen vorzunehmen. 
>     

### <a name="analyze-risky-repositories-found-public-preview"></a>Analysieren von riskanten Depots gefunden (öffentliche Vorschau)

Durch einen Netzwerk Scanauftrag, einen Inhalts Überprüfungs Auftrag oder durch den in Protokolldateien erkannten Benutzer Zugriff gefundene Depots werden aggregiert und im [Symbol](media/i-repositories.png "Repository (Symbol)") Bereich **Scanner > Repository** -Repository aufgeführt.

Wenn Sie [einen Netzwerk Scanauftrag definiert](#create-a-network-scan-job-public-preview) haben und ihn so festgelegt haben, dass er zu einem bestimmten Zeitpunkt ausgeführt wird, warten Sie, bis die Ausführung abgeschlossen ist, um die Ergebnisse zu überprüfen. Sie können hier auch nach dem Ausführen eines [Inhalts Scan Auftrags](#create-a-content-scan-job) zurückkehren, um aktualisierte Daten anzuzeigen.

> [!NOTE]
> Die Azure Information Protection- **Repository** -Funktion befindet sich derzeit in der Vorschau Phase. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 
> 

1. Wählen Sie im Menü **Scanner** auf der linken Seite die Option **Repository** - ![Repository-Symbol](media/i-repositories.png "Repository (Symbol)")aus.
    
    Die gefundenen Depots werden wie folgt angezeigt:
    - Das Diagramm " **Repository nach Status** " zeigt an, wie viele Depots bereits für einen inhaltscanauftrag konfiguriert sind und wie viele nicht.
    - In den **ersten 10 nicht verwalteten Repository nach Zugriffs** Diagramm sind die obersten 10 Repository aufgelistet, die derzeit keinem Inhalts Überprüfungs Auftrag zugewiesen sind, sowie Details zu ihren Zugriffsebenen. Zugriffsebenen können angeben, wie riskant ihre Depots sind.
    - In der Tabelle unterhalb der Diagramme werden alle gefundenen Repository und deren Details aufgelistet.

1. Führen Sie einen der folgenden Schritte aus:
    
    |Option  |BESCHREIBUNG  |
    |---------|---------|
    |![Symbol "Spalten"](media/i-columns.png "Symbol "Spalten"")    | Wählen Sie **Spalten** aus, um die angezeigten Tabellen Spalten zu ändern.        |
    |![Symbol "Aktualisieren"](media/i-refresh.png "Symbol "Aktualisieren"")   | Wenn Ihr Scanner vor kurzem Netzwerk Scanergebnisse ausgeführt hat, wählen Sie **Aktualisieren** aus, um die Seite zu aktualisieren.      |
    |![Symbol hinzufügen](media/i-add.png "Symbol hinzufügen")   | Wählen Sie ein oder mehrere in der Tabelle aufgeführte Depots aus, und wählen Sie dann **ausgewählte Elemente zuweisen** aus, um Sie einem Inhalts Überprüfungs Auftrag zuzuweisen.          |
    |**Filter**     |   In der Filter Zeile werden alle derzeit angewendeten Filterkriterien angezeigt. Wählen Sie eines der angezeigten Kriterien aus, um die Einstellungen zu ändern, oder wählen Sie **Filter hinzufügen** aus, um neue Filterkriterien hinzuzufügen. <br /><br />Wählen Sie **Filter** aus, um die Änderungen zu übernehmen und die Tabelle mit dem aktualisierten Filter zu aktualisieren.       |
    |![Log Analytics Symbol](media/i-log-analytics.png "Log Analytics Symbol") |Klicken Sie in der oberen rechten Ecke des Diagramms für nicht verwaltete Depots auf das **Log Analytics** -Symbol, um zu Log Analytics Daten für diese Depots zu springen. |
    | | |

#### <a name="repositories-with-public-access"></a>Depots mit öffentlichem Zugriff

In den Depots, in denen der **öffentliche Zugriff** über **Lese** **-oder Lese-/Schreibfunktionen** verfügt, können vertrauliche Inhalte vorhanden sein, die geschützt werden müssen. Wenn der **öffentliche Zugriff** auf false gilt, ist das Repository überhaupt nicht zugänglich.

Der öffentliche Zugriff auf ein Repository wird nur gemeldet, wenn Sie ein schwaches Konto im **standarddomainsuseraccount** -Parameter des Cmdlets [**install-mipnetworkdiscovery**](/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery) festgelegt haben.

- Die in diesen Parametern definierten Konten werden verwendet, um den Zugriff eines schwachen Benutzers auf das Repository zu simulieren. Wenn der schwache Benutzer, der dort definiert ist, auf das Repository zugreifen kann, bedeutet dies, dass auf das Repository öffentlich zugegriffen werden kann. 

- Stellen Sie sicher, dass der in diesen Parametern angegebene Benutzer nur Mitglied der Gruppe " **Domänen Benutzer** " ist, um sicherzustellen, dass der öffentliche Zugriff ordnungsgemäß gemeldet wird.
       
### <a name="create-a-content-scan-job"></a>Erstellen eines Inhalts Scan Auftrags

Ausführliche Informationen zu ihren Inhalten, um bestimmte Depots auf sensiblen Inhalt zu überprüfen. 

Dies ist möglicherweise erst nach dem Ausführen eines Netzwerk Scan Auftrags zum Analysieren der Depots in Ihrem Netzwerk möglich. Sie können jedoch auch ihre Depots selbst definieren.
 
1. Wählen Sie im Menü **Scanner** auf der linken Seite die Option **Inhalts Scanaufträge** aus. 
   
1. Wählen Sie im Bereich **Azure Information Protection-Inhalts Scanaufträge** die Option Add- ![Symbol](media/i-add.png "Symbol "Speichern"")hinzu **fügen** aus.
 
1. Konfigurieren Sie für diese Erstkonfiguration die folgenden Einstellungen, und wählen Sie dann **Speichern** aus, aber schließen Sie den Bereich nicht.
    
    |Einstellung  |BESCHREIBUNG  |
    |---------|---------|
    |**Einstellungen für den Content Scan-Auftrag**     |    - **Zeitplan**: behalten Sie den Standardwert **manuell** bei. <br />- **Zu ermittelnde Informationstypen**: **nur in Richtlinie** ändern <br />- **Repository konfigurieren**: Konfigurieren Sie zu diesem Zeitpunkt nicht, da der Inhalts Überprüfungs Auftrag zuerst gespeichert werden muss.         |
    |**Richtlinienerzwingung**     | - **Erzwingen**: SELECT **Off** <br />- Bezeichnungs **Dateien basierend auf dem Inhalt**: behalten Sie die Standardeinstellung **bei** . <br />- **Standard Bezeichnung**: Standardwert der Standard **Richtlinie für Richtlinie** beibehalten <br />- **Dateien** neu bezeichnen: Standardwert " **aus** " beibehalten        |
    |**Konfigurieren von Datei Einstellungen**     | - **"Datum geändert", "zuletzt geändert" und "geändert von**" beibehalten: behalten Sie die Standardeinstellung **bei** . <br />- **Zu überprüfende Dateitypen**: Standard Dateitypen für **Ausschluss** beibehalten <br />- **Standard Besitzer**: behalten Sie die Standardeinstellung **Scanner-Konto** bei.        |
    | | |

1. Nachdem der Auftrag für die Inhalts Überprüfung erstellt und gespeichert wurde, können Sie zur Option " **Depots konfigurieren** " zurückkehren, um die Datenspeicher anzugeben, die gescannt werden sollen. 

    Geben Sie UNC-Pfade und SharePoint-Server-URLs für lokale SharePoint-Dokument Bibliotheken und-Ordner an. 
    
    > [!NOTE]
    > SharePoint Server 2019, SharePoint Server 2016 und SharePoint Server 2013 werden für SharePoint unterstützt. Ferner wird SharePoint Server 2010 unterstützt, wenn Sie über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.
    >     
    Wenn Sie den ersten Datenspeicher hinzufügen möchten, wählen Sie im Bereich **neuen Inhalts Überprüfungs Auftrag hinzufügen** die Option **Repository konfigurieren** aus, um den Bereich **Depots** zu öffnen:
    
    :::image type="content" source="media/scanner-repositories-bar.png" alt-text="Konfigurieren von Datenrepositorys für den Azure Information Protection-Scanner":::

    1. Klicken Sie im Bereich **Repositorys** auf die Option **Hinzufügen**:
    
        :::image type="content" source="media/scanner-repository-add.png" alt-text="Hinzufügen eines Datenrepositorys für den Azure Information Protection-Scanner":::

    1. Geben Sie im Bereich **Repository** den Pfad für das Datenrepository an, und klicken Sie dann auf **Speichern**.
    
        
        - Verwenden Sie für eine Netzwerkfreigabe `\\Server\Folder` . 
        - Verwenden Sie für eine SharePoint-Bibliothek `http://sharepoint.contoso.com/Shared%20Documents/Folder` .
        - Für einen lokalen Pfad: `C:\Folder`
        - Für einen UNC-Pfad: `\\Server\Folder`

    > [!NOTE]
    > Platzhalter und WebDav-Speicherorte werden nicht unterstützt.
    >  
  
    Wenn Sie einen SharePoint-Pfad für frei **gegebene Dokumente** hinzufügen:
    - Geben Sie **Freigegebene Dokumente** im Pfad an, wenn alle Dokumente und Ordner in „Freigegebene Dokumente“ überprüft werden sollen. 
    Beispiel: `http://sp2013/SharedDocuments`
    - Geben Sie **Dokumente** im Pfad an, wenn alle Dokumente und Ordner in einem Unterordner von „Freigegebene Dokumente“ überprüft werden sollen. 
    Beispiel: `http://sp2013/Documents/SalesReports`
    - Oder geben Sie nur den voll qualifizierten Domänen Namen ( **FQDN** ) Ihres SharePoint `http://sp2013` an, um z. b. [alle SharePoint-Sites und-untergeordneten Sites unter einer bestimmten URL](deploy-aip-scanner-prereqs.md#discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url) und untergeordneten untergeordneten URLs zu ermitteln Erteilen Sie den Überprüfungs Berechtigungen für Scanner- **Website Sammler** , um dies zu ermöglichen 
    >


    Für die restlichen Einstellungen in diesem Bereich sollten Sie diese nicht für diese anfängliche Konfiguration ändern, sondern als Standardwert für den **inhaltscanauftrag** beibehalten. Die Standardeinstellung bedeutet, dass das Datenrepository die Einstellungen vom Inhalts Überprüfungs Auftrag erbt.

    Verwenden Sie die folgende Syntax, wenn Sie SharePoint-Pfade hinzufügen:
    
    |Pfad  |Syntax  |
    |---------|---------|
    |**Stammpfad**     | `http://<SharePoint server name>` <br /><br />Scannt alle Websites, einschließlich sämtlicher Site Sammlungen, die für den scannerbenutzer zulässig sind. <br />Erfordert [zusätzliche Berechtigungen](quickstart-findsensitiveinfo.md#permission-users-to-scan-sharepoint-repositories) zum automatischen ermitteln von Stamm Inhalten        |
    |**Bestimmte SharePoint-unter Website oder-Sammlung**     | Eine der folgenden Möglichkeiten: <br />- `http://<SharePoint server name>/<subsite name>` <br />- `http://SharePoint server name>/<site collection name>/<site name>` <br /><br />Erfordert [zusätzliche Berechtigungen](quickstart-findsensitiveinfo.md#permission-users-to-scan-sharepoint-repositories) zum automatischen ermitteln von Website Sammlungs Inhalten         |
    |**Bestimmte SharePoint-Bibliothek**     | Eine der folgenden Möglichkeiten: <br />- `http://<SharePoint server name>/<library name>` <br />- `http://SharePoint server name>/.../<library name>`       |
    |**Bestimmter SharePoint-Ordner**     | `http://<SharePoint server name>/.../<folder name>`        |
    | | |
    

1. Wiederholen Sie die vorherigen Schritte, um beliebig viele Depots hinzuzufügen.

    Wenn Sie fertig sind, schließen Sie sowohl die Bereiche " **Repository** " als auch " **Inhalts Scan** ". 

Im Bereich **Azure Information Protection Inhalts** Überprüfung wird der Name Ihres Inhalts Scans angezeigt, und die Spalte " **Zeitplan** " zeigt " **manuell** " an, und die Spalte " **erzwingen** " ist leer.

Nun können Sie den Scanner mit dem von Ihnen erstellten Inhalts Überprüfungs Auftrag installieren. Fahren Sie mit [der Installation des Scanners](#install-the-scanner)fort.

## <a name="install-the-scanner"></a>Installieren der Überprüfung

Nachdem Sie [den Azure Information Protection Scanner im Azure-Portal konfiguriert](#configure-the-scanner-in-the-azure-portal)haben, führen Sie die folgenden Schritte aus, um die Überprüfung zu installieren:

1. Melden Sie sich bei dem Windows Server-Computer an, auf dem die Überprüfung ausgeführt werden soll. Verwenden Sie ein Konto mit lokalen Administratorrechten und den Berechtigungen zum Schreiben in die SQL Server-Masterdatenbank.

    > [!IMPORTANT]
    > Weitere Informationen finden Sie unter [Voraussetzungen für die Installation und Bereitstellung der Azure Information Protection Scanner](deploy-aip-scanner-prereqs.md).
    >
 
1. Starten Sie eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

1. Führen Sie das Cmdlet [install-aipscanner](/powershell/module/azureinformationprotection/Install-AIPScanner) aus, und geben Sie dabei die SQL Server Instanz an, auf der eine Datenbank für den Azure Information Protection Scanner erstellt werden soll, und den Namen des scannerclusters, den Sie im vorherigen Abschnitt angegeben haben: 
    
    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Profile <cluster name>
    ```
    
    Beispiele, in denen der Profilname **Europa** verwendet wird:
    
    - Für eine Standardinstanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1 -Profile Europe`
    
    - Für eine benannte Instanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Profile Europe`
    
    - Für SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Profile Europe`
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Anmelde Informationen für das Überprüfungs Dienst Konto ( \<domain\user name> ) und das Kennwort an.

1. Vergewissern Sie sich, dass der Dienst jetzt mithilfe der Dienste **Verwaltung** installiert ist  >  **Services**. 
    
    Der installierte Dienst heißt **Azure Information Protection-Überprüfung** und ist für die Ausführung mithilfe des von Ihnen erstellten Überprüfungsdienstkontos konfiguriert.

Nachdem Sie den Scanner installiert haben, müssen Sie [ein Azure AD Token für das](#get-an-azure-ad-token-for-the-scanner) Überprüfungs Dienst Konto für die Authentifizierung erhalten, damit die Überprüfung unbeaufsichtigt ausgeführt werden kann. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Abrufen eines Azure AD-Tokens für die Überprüfung

Ein Azure AD Token ermöglicht es dem Scanner, sich beim Azure Information Protection-Dienst zu authentifizieren, sodass der Scanner nicht interaktiv ausgeführt werden kann.

Weitere Informationen finden Sie unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](./rms-client/clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection).

So erhalten Sie ein Azure AD Token:

1. Kehren Sie zum Azure-Portal zurück, um eine Azure AD-Anwendung zu erstellen und ein Zugriffs Token für die Authentifizierung anzugeben.

1. Wenn Ihrem Überprüfungs Dienst Konto auf dem Windows Server-Computer die Berechtigung zum **lokalen anmelden** für die Installation erteilt wurde, melden Sie sich mit diesem Konto an, und starten Sie eine PowerShell-Sitzung. 

    Führen Sie [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) aus, und geben Sie die Werte an, die Sie aus dem vorherigen Schritt kopiert haben:
    
    ```PowerShell
    Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
    ```
        
    Beispiel:

    ```PowerShell
    $pscreds = Get-Credential CONTOSO\scanner
    Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
    Acquired application access token on behalf of CONTOSO\scanner.
    ```

> [!TIP]
> Wenn Ihrem Überprüfungs Dienst Konto die Berechtigung " **Lokal anmelden** " für die Installation nicht gewährt werden kann, verwenden Sie den *onbehalfof* -Parameter mit " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication)", wie unter Gewusst [wie: nicht interaktives bezeichnen von Dateien für Azure Information Protection](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection)beschrieben.

Der Scanner verfügt jetzt über ein Token zum Authentifizieren bei Azure AD. Dieses Token ist für ein Jahr, zwei Jahre oder nie gültig, gemäß ihrer Konfiguration der **Web-App/API** geheimer Client Schlüssel in Azure AD. 

Wenn das Token abläuft, müssen Sie dieses Verfahren wiederholen.

Nun können Sie den ersten Scanvorgang im Ermittlungsmodus ausführen. Weitere Informationen finden Sie unter [Ausführen eines Ermittlungs Zyklen und Anzeigen von Berichten für die](deploy-aip-scanner-manage.md#run-a-discovery-cycle-and-view-reports-for-the-scanner)Überprüfung.

Nachdem Sie die erste Ermittlungs Überprüfung ausgeführt haben, fahren Sie mit [Konfigurieren des Scanners fort, um Klassifizierung und Schutz anzuwenden](#configure-the-scanner-to-apply-classification-and-protection).

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz

Mit den Standardeinstellungen wird die Überprüfung so konfiguriert, dass Sie einmalig ausgeführt wird, und im Bericht Erstellungs Modus.

Um diese Einstellungen zu ändern, bearbeiten Sie den Auftrag für die Inhalts Überprüfung:

1. Wählen Sie im Azure-Portal im Bereich **Azure Information Protection-Inhalts Scanaufträge** den Auftrag Cluster und Inhalts Überprüfung aus, um ihn zu bearbeiten.

2. Ändern Sie im Bereich Inhalts Überprüfungs Auftrag die folgenden Einstellungen, und wählen Sie dann **Speichern** aus:
    
   - Im Abschnitt **Content Scan Job** : Ändern des **Zeitplans** in **Always**
   - Aus dem Abschnitt zur **Richtlinien** Erzwingung: Ändern von **erzwingen** **in ein**
    
    > [!TIP]
    > Möglicherweise möchten Sie andere Einstellungen in diesem Bereich ändern, z. b. ob Dateiattribute geändert werden und ob der Scanner Dateien neu bezeichnen kann. Weitere Informationen zu den einzelnen Konfigurationseinstellungen finden Sie in der Popuphilfe mit Informationen.

3. Notieren Sie sich die aktuelle Uhrzeit, und starten Sie die Überprüfung erneut über den Bereich **Azure Information Protection-Inhalts Scanaufträge** :

    :::image type="content" source="media/scanner-scan-now.png" alt-text="Initiieren der Überprüfung für den Azure Information Protection-Scanner":::
    
    Alternativ können Sie den folgenden Befehl in der PowerShell-Sitzung ausführen:
    
    ```PowerShell
    Start-AIPScan
    ```

Der Scanner ist jetzt für die kontinuierliche Ausführung geplant. Wenn die Überprüfung alle konfigurierten Dateien durchläuft, wird automatisch ein neuer Zeitraum gestartet, sodass neue und geänderte Dateien ermittelt werden.

## <a name="change-which-file-types-to-protect"></a>Ändern der zu schützenden Dateitypen

Der AIP-Scanner schützt standardmäßig nur Office-Dateitypen und PDF-Dateien.

Verwenden Sie PowerShell-Befehle, um dieses Verhalten nach Bedarf zu ändern, z. b. zum Konfigurieren der Überprüfung, um alle Dateitypen zu schützen, ebenso wie der Client, oder um zusätzliche, bestimmte Dateitypen zu schützen. 

Geben Sie für eine Bezeichnungs Richtlinie, die für das Benutzerkonto gilt, das Bezeichnungen für den Scanner herunterlädt, eine PowerShell-erweiterte Einstellung mit dem Namen **pfilesupportedextensions** an. 

Bei einem Scanner, der Zugriff auf das Internet hat, ist dieses Benutzerkonto das Konto, das Sie für den Parameter " *delegateduser* " mit dem Befehl "Set-AIPAuthentication" angeben.

**Beispiel 1:**  PowerShell-Befehl für die Überprüfung, um alle Dateitypen zu schützen, deren Bezeichnung "Scanner" lautet:

```PowerShell
Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions="*"}
```

**Beispiel 2:** PowerShell-Befehl für die Überprüfung, um XML-Dateien und TIFF-Dateien zusätzlich zu Office-Dateien und PDF-Dateien zu schützen, wobei die Bezeichnung "Scanner" lautet:

```PowerShell
Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions=ConvertTo-Json(".xml", ".tiff")}
```

Weitere Informationen finden Sie unter [Ändern der zu schützenden Dateitypen](./rms-client/clientv2-admin-guide-customizations.md#change-which-file-types-to-protect).

## <a name="upgrading-your-scanner"></a>Aktualisieren Ihres Scanners
 
Wenn Sie den Scanner bereits installiert haben und ein Upgrade durchführen möchten, befolgen Sie die Anweisungen unter [Aktualisieren der Azure Information Protection Scanner](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

[Konfigurieren](deploy-aip-scanner-configure-install.md) und verwenden Sie dann wie gewohnt [Ihren Scanner](deploy-aip-scanner-manage.md) , und überspringen Sie die Schritte zur Installation des Scanners.

## <a name="editing-data-repository-settings-in-bulk"></a>Bearbeiten von Datenrepository-Einstellungen in einem Massen Vorgang

Verwenden Sie die Schaltflächen **exportieren** und **importieren** , um Änderungen für Ihren Scanner in mehreren Depots durchführen zu können. 

Auf diese Weise müssen Sie die gleichen Änderungen nicht mehrmals manuell im Azure-Portal vornehmen.

Wenn Sie z. b. einen neuen Dateityp in mehreren SharePoint-Daten Depots haben, können Sie die Einstellungen für diese Depots in einem Massen Vorgang aktualisieren.

So führen Sie Massen Änderungen in mehreren Depots durch:

1. Wählen Sie im Bereich für die Azure-Portal im Bereich " **Depots** " die Option **exportieren** aus. Beispiel:

    :::image type="content" source="media/export-scanner-repositories.png" alt-text="Exportieren von Datenrepository-Einstellungen für den Azure Information Protection Scanner":::

1. Bearbeiten Sie die exportierte Datei manuell, um die Änderung vorzunehmen. 

1. Verwenden Sie die **Import** -Option auf der gleichen Seite, um die Aktualisierungen in ihren Depots wieder zu importieren.

## <a name="using-the-scanner-with-alternative-configurations"></a>Verwenden der Überprüfung mit alternativen Konfigurationen

Der Azure Information Protection Scanner sucht in der Regel nach Bedingungen, die für ihre Bezeichnungen angegeben sind, um Ihre Inhalte nach Bedarf zu klassifizieren und zu schützen.

In den folgenden Szenarien kann der Azure Information Protection Scanner auch Ihre Inhalte Scannen und Bezeichnungen verwalten, ohne dass Bedingungen konfiguriert sind:

- [Anwenden einer Standard Bezeichnung auf alle Dateien in einem Datenrepository](#apply-a-default-label-to-all-files-in-a-data-repository)
- [Vorhandene Bezeichnungen aus allen Dateien in einem Datenrepository entfernen](#remove-existing-labels-from-all-files-in-a-data-repository)
- [Alle benutzerdefinierten Bedingungen und bekannten sensiblen Informationstypen identifizieren](#identify-all-custom-conditions-and-known-sensitive-information-types)
### <a name="apply-a-default-label-to-all-files-in-a-data-repository"></a>Anwenden einer Standard Bezeichnung auf alle Dateien in einem Datenrepository

In dieser Konfiguration werden alle nicht gekennzeichneten Dateien im Repository mit der Standard Bezeichnung gekennzeichnet, die für das Repository oder den Inhaltsüberprüfungs Auftrag angegeben ist. Dateien werden ohne Untersuchung bezeichnet. 

Konfigurieren Sie die folgenden Einstellungen: 

|Einstellung  |BESCHREIBUNG  |
|---------|---------|
|**Bezeichnungs Dateien basierend auf dem Inhalt**    |Auf **Off** festgelegt         |
|**Standard Bezeichnung**     | Legen Sie auf **Custom** fest, und wählen Sie die zu verwendende Bezeichnung aus.       |
|**Standard Bezeichnung erzwingen**     | Wählen Sie diese Option aus, damit die Standard Bezeichnung auf alle Dateien angewendet wird, auch wenn Sie bereits eine Bezeichnung aufweisen.        |
| | |

### <a name="remove-existing-labels-from-all-files-in-a-data-repository"></a>Vorhandene Bezeichnungen aus allen Dateien in einem Datenrepository entfernen

In dieser Konfiguration werden alle vorhandenen Bezeichnungen entfernt, einschließlich des Schutzes, wenn der Schutz mit der Bezeichnung angewendet wurde. Der Schutz, der unabhängig von einer Bezeichnung angewendet wird, wird beibehalten.

Konfigurieren Sie die folgenden Einstellungen: 

|Einstellung  |BESCHREIBUNG  |
|---------|---------|
|**Bezeichnungs Dateien basierend auf dem Inhalt**    |Auf **Off** festgelegt         |
|**Standard Bezeichnung**     | Auf " **None** " festlegen  |
|**Neu bezeichnen von Dateien** | Auf **on** festgelegt, wobei das Kontrollkästchen **Standard Bezeichnung erzwingen** ausgewählt ist.|
| | |

### <a name="identify-all-custom-conditions-and-known-sensitive-information-types"></a>Alle benutzerdefinierten Bedingungen und bekannten sensiblen Informationstypen identifizieren

Mit dieser Konfiguration können Sie vertrauliche Informationen, die Sie möglicherweise nicht bemerkt haben, auf Kosten der Scan Raten für den Scanner finden. 

Legen Sie die zu **ermittelnden Informationstypen** auf **alle** fest. 

Zum Identifizieren von Bedingungen und Informationstypen für die Bezeichnung verwendet der Scanner alle angegebenen benutzerdefinierten sensiblen Informationstypen und die Liste der integrierten Typen sensibler Informationen, die zur Auswahl verfügbar sind, wie in Ihrem Bezeichnungs Verwaltungs Center definiert.

## <a name="optimizing-scanner-performance"></a>Optimieren der Scanner-Leistung

> [!NOTE]
> Wenn Sie die Reaktionsfähigkeit des Scanner-Computers anstelle der Überprüfungs Leistung verbessern möchten, verwenden Sie eine erweiterte Client Einstellung, um [die Anzahl der von der Überprüfung verwendeten Threads einzuschränken](./rms-client/clientv2-admin-guide-customizations.md#limit-the-number-of-threads-used-by-the-scanner).
> 

Verwenden Sie die folgenden Optionen und Anleitungen, um die Leistung der Scanner zu optimieren:

|Option  |BESCHREIBUNG  |
|---------|---------|
|**Verwenden Sie eine schnelle und zuverlässige Netzwerkverbindung zwischen dem Überprüfungscomputer und dem überprüften Datenspeicher**     |  Platzieren Sie z. b. den Überprüfungs Computer im selben LAN oder vorzugsweise im selben Netzwerksegment wie der gescannte Datenspeicher. <br /><br />Die Qualität der Netzwerkverbindung wirkt sich auf die Überprüfungs Leistung aus, da der Scanner zum Überprüfen der Dateien den Inhalt der Dateien auf den Computer überträgt, auf dem der Überprüfungs Dienst ausgeführt wird. <br /><br />Durch das reduzieren oder eliminieren der Netzwerk Hops, die für die zu übertragenden Daten erforderlich sind, wird auch die Auslastung Ihres Netzwerks reduziert.      |
|**Achten Sie darauf, dass der überprüfende Computer verfügbare Prozessorressourcen aufweist**     | Die Untersuchung der Dateiinhalte und das Verschlüsseln und Entschlüsseln von Dateien sind prozessorintensive Aktionen. <br /><br />Überwachen Sie die üblichen Überprüfungszyklen für die angegebenen Datenspeicher, um zu ermitteln, ob sich die Leistung der Überprüfung durch fehlende Prozessorressourcen beeinträchtigt.        |
|**Installieren mehrerer Instanzen des Scanners** | Der Azure Information Protection Scanner unterstützt mehrere Konfigurations Datenbanken auf derselben SQL Server-Instanz, wenn Sie einen benutzerdefinierten Cluster Namen (Profil) für die Überprüfung angeben. <br /><br />Mehrere Scanner können auch denselben Cluster (Profil) verwenden, was zu schnelleren Scanzeiten führt.|
|**Überprüfen Sie Ihre alternative Konfigurations Verwendung** |Die Überprüfung wird schneller ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der eine Standardbezeichnung auf alle Dateien angewendet wird, ohne dass die Dateiinhalte überprüft werden. <br/><br />Die Überprüfung wird langsamer ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der alle benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen identifiziert werden.|
| | |


### <a name="additional-factors-that-affect-performance"></a>Weitere Faktoren, die die Leistung beeinträchtigen

Weitere Faktoren, die sich auf die Scanner-Leistung auswirken, sind:

|Faktor  |BESCHREIBUNG  |
|---------|---------|
|**Lade-/Antwort-Zeiten**     |Die aktuellen Lade-und Antwortzeiten der Datenspeicher, die die zu überprüfenden Dateien enthalten, wirken sich auch auf die Leistung des Scanners aus.         |
|**Scanmodus** (Ermittlung/erzwingen)    | Der Ermittlungs Modus hat normalerweise eine höhere Scanrate als der Erzwingungs Modus. <br /><br />Die Ermittlung erfordert eine einzelne Datei Leseaktion, während der Erzwingungs Modus Lese-und Schreib Aktionen erfordert.        |
|**Richtlinienänderungen**     |Die Leistung der Überprüfung kann beeinträchtigt werden, wenn Sie Änderungen an der Auto Layout-Richtlinie vorgenommen haben. <br /><br />Der erste Scan Zyklus, bei dem der Scanner jede Datei überprüfen muss, dauert länger als nachfolgende Überprüfungszyklen, die standardmäßig nur neue und geänderte Dateien untersuchen. <br /><br />Wenn Sie die Bedingungen oder die Authentifizierungs Einstellungen ändern, werden alle Dateien erneut gescannt. Weitere Informationen finden Sie unter [erneutanup von Dateien](deploy-aip-scanner-manage.md#rescanning-files).|
|**Regex-Konstruktionen**    | Die Leistung des Scanners ist von der Erstellung der Regex-Ausdrücke für benutzerdefinierte Bedingungen betroffen. <br /><br /> Überprüfen Sie Ihre regulären Ausdrücke für einen effizienten Musterabgleich, um eine hohe Arbeitsspeichernutzung und das Risiko von Timeouts (15 Minuten pro Datei) zu vermeiden. <br /><br />Beispiel: <br />-Vermeiden [gieriger quantifiziererer](/dotnet/standard/base-types/quantifiers-in-regular-expressions) <br />-Verwenden Sie nicht Erfassungs Gruppen wie z. b. `(?:expression)` anstelle von. `(expression)`    |
|**Protokollebene**     |  Optionen auf Protokollebene umfassen **Debug**, **Info**, **Error** und **Off** für die scannerberichte.<br /><br />- **Off** führt zu einer optimalen Leistung. <br />- Das **Debuggen** verlangsamt den Scanner erheblich und sollte nur zur Problembehandlung verwendet werden. <br /><br />Weitere Informationen finden Sie beim Parameter *ReportLevel* für das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).       |
|**Dateien, die gescannt werden**     |-Mit Ausnahme von Excel-Dateien werden Office-Dateien schneller gescannt als PDF-Dateien. <br /><br />-Ungeschützte Dateien sind schneller zu scannen als geschützte Dateien. <br /><br />-Die Überprüfung großer Dateien dauert offensichtlich länger als bei kleinen Dateien.         |
| | |

## <a name="list-of-cmdlets-for-the-scanner"></a>Auflisten der Cmdlets für die Überprüfung

In diesem Abschnitt werden die für den Azure Information Protection Scanner unterstützten PowerShell-Cmdlets aufgeführt.

Zu den unterstützten Cmdlets für den Scanner gehören:

- [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository)

- [Export-aiplogs](/powershell/module/azureinformationprotection/Export-AIPLogs)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-aipscannercontentscanjob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Get-mipnetworkdiscoveryconfiguration](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryConfiguration)

- [Get-mipnetworkdiscoveryjobs](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryJobs)

- [Get-mipnetworkdiscoverystatus](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryStatus)

- [Import-aipscannerconfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration)

- [Set-mipnetworkdiscovery](/powershell/module/azureinformationprotection/set-mipnetworkdiscovery)

- [Import-mipnetworkdiscoveryconfiguration](/powershell/module/azureinformationprotection/Import-MIPNetworkDiscoveryConfiguration)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Install-mipnetworkdiscovery](/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Set-aipscannercontentscanjob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob)

- [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository)

- [Set-mipnetworkdiscoveryconfiguration](/powershell/module/azureinformationprotection/Set-MIPNetworkDiscoveryConfiguration)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- [Start-aipscandiagnostics](/powershell/module/azureinformationprotection/Start-AIPScannerDiagnostics)

- [Start-mipnetworkdiscovery](/powershell/module/azureinformationprotection/Start-MIPNetworkDiscovery)

- ["Beendet-aipscan"](/powershell/module/azureinformationprotection/Stop-AIPScan)

- [Remove-aipscannercontentscanjob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob)

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Deinstallation von mipnetworkdiscovery](/powershell/module/azureinformationprotection/Uninstall-MIPNetworkDiscovery)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihren Scanner installiert und konfiguriert haben, können Sie mit [dem Scannen der Dateien](deploy-aip-scanner-manage.md)beginnen.

Siehe auch: bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).

**Weitere Informationen:**

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Vielleicht Fragen Sie sich: [worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

- Verwenden Sie PowerShell, um Dateien interaktiv zu klassifizieren und von Ihrem Desktop Computer zu schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden [Sie unter Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide-powershell.md).