---
title: Konfigurieren von Servern für den Rights Management-Connector – AIP
description: Informationen, die Sie beim Konfigurieren Ihrer lokalen Server unterstützen, die den RMS-Connector (Azure Rights Management) verwenden sollen. Diese Verfahren beziehen sich auf Schritt 5 aus „Bereitstellen des Azure Rights Management-Verbindungsdiensts“.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 09/10/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 75846ee1-2370-4360-81ad-e2b6afe3ebc9
ms.subservice: connector
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 3a616092ac1b74c2ae530898c69a61f071e93ea1
ms.sourcegitcommit: af7ac2eeb8f103402c0036dd461c77911fbc9877
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "98559794"
---
# <a name="configuring-servers-for-the-azure-rights-management-connector"></a>Konfigurieren von Servern für den Azure Rights Management-Verbindungsdienst

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Verwenden Sie die folgenden Informationen, um Ihre lokale Server für die Verwendung des Azure Rights Management (RMS)-Verbindungsdiensts zu konfigurieren. Diese Verfahren beziehen sich auf Schritt 5 der Bereitstellung [des Azure Rights Management-Verbindungs-Connector](deploy-rms-connector.md).

**Voraussetzungen**: bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
    - Der RMS-Connector wurde installiert und konfiguriert.
    - Alle [Voraussetzungen](deploy-rms-connector.md#prerequisites-for-the-rms-connector) für die Server, von denen der Connector verwendet wird, wurden geprüft.

## <a name="configuring-servers-to-use-the-rms-connector"></a>Konfigurieren von Servern für die Verwendung des RMS-Verbindungsdiensts
Nachdem Sie den RMS-Verbindungs Dienst installiert und konfiguriert haben, können Sie die lokalen Server konfigurieren, die eine Verbindung mit dem Azure Rights Management-Dienst herstellen, und diese Schutz Technologie mithilfe des-Verbindungs Dienstanbieter verwenden. 

Dies bedeutet, dass die folgenden Server zu konfigurieren sind:

|Umgebung  |Zu konfigurier gende Server  |
|---------|---------|
|**Exchange 2016 und Exchange 2013**     |  Clientzugriffsserver und Postfachserver       |
|**Exchange 2019**     |   Clientzugriffsserver und Hub-Transport-Server      |
|**SharePoint**     |    Front-End-SharePoint-Webserver, einschließlich der Server, die den zentralen Verwaltungsserver hosten     |
|**Dateiklassifizierungsinfrastruktur**     |   Windows Server-Computer, auf denen der Ressourcen-Manager für Dateien installiert ist      |
| | |

Diese Konfiguration erfordert Registrierungs Einstellungen mit den folgenden Optionen:

- [Registrierungs Einstellungen automatisch bearbeiten](#edit-registry-settings-automatically---advantages-and-disadvantages)
- [Manuelles Bearbeiten von Registrierungs Einstellungen](#edit-registry-settings-manually---advantages-and-disadvantages)

> [!IMPORTANT]
> In beiden Fällen müssen Sie manuell alle vorausgesetzten Komponenten installieren und Exchange, SharePoint und die Dateiklassifizierungsinfrastruktur zur Verwendung von Rights Management konfigurieren.

> [!NOTE]
> Für die meisten Organisationen stellt die automatische Konfiguration unter Verwendung des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst die bessere Möglichkeit dar, weil sie effizienter und zuverlässiger als eine manuelle Konfiguration ist.
> 

Nachdem Sie die Konfigurationsänderungen auf diesen Servern vorgenommen haben, müssen Sie Sie neu starten, wenn Exchange oder SharePoint ausgeführt wird und Sie zuvor für die Verwendung von AD RMS konfiguriert wurden. Sie brauchen diese Server nicht neu zu starten, wenn Sie sie zum ersten Mal für Rights Management konfigurieren. 

Der Dateiserver, der zur Verwendung der Dateiklassifizierungsinfrastruktur konfiguriert ist, muss nach diesen Konfigurationsänderungen immer neu gestartet werden.
### <a name="edit-registry-settings-automatically---advantages-and-disadvantages"></a>Registrierungs Einstellungen automatisch bearbeiten: vor-und Nachteile

Bearbeiten Sie die Registrierungs Einstellungen automatisch mithilfe des Server Konfigurationstools für Microsoft RMS Connector.

Zu den **Vorteilen gehören**:

- Keine direkte Bearbeitung der Registrierung. Diese wird für Sie mithilfe eines Skripts automatisiert.

- Keine Notwendigkeit zur Ausführung eines Windows PowerShell-Cmdlets, um Ihre Microsoft RMS-URL abzurufen.

- Die Voraussetzungen werden automatisch für Sie überprüft (aber nicht automatisch behoben), wenn die Ausführung lokal erfolgt.

**Nachteile umfassen Folgendes**: Wenn Sie das Tool ausführen, müssen Sie eine Verbindung mit einem Server herstellen, auf dem bereits der RMS-Connector ausgeführt wird.

Weitere Informationen finden Sie unter [Verwenden des Server Konfigurationstools für Microsoft RMS Connector](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector).
### <a name="edit-registry-settings-manually---advantages-and-disadvantages"></a>Manuelles Bearbeiten von Registrierungs Einstellungen: vor-und Nachteile

Zu den **Vorteilen gehören**: Es ist keine Verbindung mit einem Server erforderlich, auf dem der RMS-Connector ausgeführt wird

Zu den **Nachteile gehören**:

- Höherer Verwaltungsaufwand, der fehleranfällig ist.

- Sie müssen Ihre Microsoft RMS-URL abrufen, wofür Sie einen Windows PowerShell-Befehl ausführen müssen.

- Sie müssen immer alle Überprüfungen der Voraussetzungen selbst durchführen.

### <a name="how-to-use-the-server-configuration-tool-for-microsoft-rms-connector"></a>Verwenden des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst

1.  Wenn Sie das Skript für das Server Konfigurationstool für Microsoft RMS Connector **(GenConnectorConfig.ps1)** nicht bereits heruntergeladen haben, laden Sie es aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=314106)herunter.

2.  Speichern Sie die **GenConnectorConfig.ps1** Datei auf dem Computer, auf dem Sie das Tool ausführen möchten. 

    Wenn Sie das Tool lokal ausführen, muss dies der Server sein, den Sie für die Kommunikation mit dem RMS-Verbindungsdienst konfigurieren möchten. Andernfalls können Sie sie auf einem beliebigen Computer speichern.

3.  Entscheiden Sie, wie das Tool ausgeführt werden soll:
    
    |Methode  |BESCHREIBUNG  |
    |---------|---------|
    |**Zutaten**     |  Führen Sie das Tool interaktiv von dem Server aus, der für die Kommunikation mit dem RMS-Connector konfiguriert werden soll. <br><br>**Tipp**: Dies ist nützlich für eine einmalige Konfiguration, z. b. eine Testumgebung.       |
    |**Softwarebereitstellung**     |  Führen Sie das Tool aus, um Registrierungsdateien zu entwickeln, die Sie dann auf einem oder mehreren relevanten Servern bereitstellen. <br><br>Stellen Sie die Registrierungsdateien mithilfe einer Systems Management-Anwendung bereit, die Software Bereitstellung unterstützt, z. b. System Center Configuration Manager       |
    |**Gruppenrichtlinie**     | Führen Sie das Tool aus, um ein Skript zu erstellen, das Sie einem Administrator zur Verfügung stellen, der Gruppenrichtlinie Objekte für die zu konfigurierenden Server erstellen kann. <br><br>Dieses Skript erstellt ein Gruppenrichtlinienobjekt für jeden Servertyp, der konfiguriert werden soll, dem der Administrator dann die relevanten Server zuweisen kann.        |
    | | |

    > [!NOTE]
    > Dieses Tool konfiguriert die Server, die mit dem RMS-Verbindungsdienst kommunizieren werden und am Anfang dieses Abschnitts aufgelistet sind. Führen Sie dieses Tool nicht auf den Servern aus, auf denen der RMS-Verbindungsdienst ausgeführt wird.

4.  Starten Sie Windows PowerShell mit der Option **als Administrator ausführen** , und verwenden Sie den Befehl **Get-Help** , um Anweisungen zur Verwendung des Tools für die gewählte Konfigurations Methode zu erhalten:

    ```PowerShell
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

Zum Ausführen des Skripts müssen Sie die URL des RMS-Connectors für Ihre Organisation eingeben. 

Geben Sie das Protokollpräfix (HTTP:// oder HTTPS://) und den Namen des Connectors, den Sie in DNS definiert haben, als Lastenausgleichsadresse Ihres Connectors ein. Beispielsweise `https:\//connector.contoso.com`. 

Das Tool verwendet dann diese URL, um sich mit den Servern zu verbinden, auf denen der RMS-Verbindungsdienst ausgeführt wird, und um weitere Parameter abzurufen, die zum Erstellen der erforderlichen Konfigurationen verwendet werden.

> [!IMPORTANT]
> Wenn Sie dieses Tool ausführen, stellen Sie sicher, dass Sie den Namen des RMS-Verbindungsdiensts mit Lastenausgleich für Ihre Organisation angeben, und nicht den Namen eines einzelnen Servers, auf dem der RMS-Verbindungsdienst ausgeführt wird.

In den folgenden Abschnitten finden Sie spezifische Informationen für jeden Diensttyp:

-   [Konfigurieren eines Exchange-Servers für die Verwendung des Verbindungs-Connector](#configuring-an-exchange-server-to-use-the-connector)

-   [Konfigurieren eines SharePoint-Servers für die Verwendung des Verbindungsdiensts](#configuring-a-sharepoint-server-to-use-the-connector)

-   [Konfigurieren eines Dateiservers, der die Dateiklassifizierungsinfrastruktur verwendet, für die Verwendung des Verbindungsdiensts](#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)

**Wann müssen Client Anwendungen auf separaten Computern installiert werden, die nicht für die Verwendung des Verbindungs-Connector konfiguriert sind**

Nachdem diese Server zur Verwendung des Verbindungsdiensts konfiguriert sind, funktionieren Anwendungen, die lokal auf diesen Servern installiert sind, möglicherweise nicht mit RMS. Wenn dies eintritt, liegt das daran, dass die Anwendungen versuchen, den Verbindungsdienst zu verwenden, statt RMS direkt zu verwenden – dies wird aber nicht unterstützt.

Wenn Office 2010 lokal auf einem Exchange-Server installiert ist, können die unm-Features der Client-App außerdem von diesem Computer aus funktionieren, nachdem der Server für die Verwendung des Verbindungs Diensts konfiguriert wurde. Dies wird jedoch nicht unterstützt. 

In beiden Szenarios müssen Sie die Clientanwendungen auf getrennten Computern installieren, die nicht für die Verwendung des Verbindungsdiensts konfiguriert sind. Sie verwenden dann korrekt RMS direkt.

> [!IMPORTANT]
> Der erweiterte Support von Office 2010 endete am 13. Oktober 2020. Weitere Informationen finden Sie unter [AIP und ältere Windows-und Office-Versionen](known-issues.md#aip-and-legacy-windows-and-office-versions).
> 
## <a name="configuring-an-exchange-server-to-use-the-connector"></a>Konfigurieren eines Exchange-Servers für die Verwendung des Verbindungsdiensts
Die folgenden Exchange-Rollen kommunizieren mit dem RMS-Verbindungsdienst:

-   Für Exchange 2016 und Exchange 2013: Clientzugriffsserver und Postfachserver

-   Für Exchange 2019: Client Zugriffs Server und Hub-Transport-Server

Damit diese Server, auf denen Exchange ausgeführt wird, den RMS-Verbindungsdienst verwenden, müssen sie eine der folgenden Softwareversionen ausführen:

-   Exchange Server 2016

-   Exchange Server 2013 mit kumulativem Update 3 für Exchange 2013

-   Exchange Server 2019

Auf diesen Servern muss außerdem eine Version 1 des RMS-Clients (auch als MSDRM bezeichnet) installiert sein, die Unterstützung für den RMS-Kryptografiemodus 2 enthält. Alle Windows-Betriebssysteme enthalten den MSRDM-Client, in frühen Versionen des Clients wurde jedoch der Kryptografiemodus 2 nicht unterstützt. Wenn auf Ihren Exchange-Servern mindestens Windows Server 2012 ausgeführt wird, ist keine weitere Aktion erforderlich, weil der mit diesen Betriebssystemen installierte RMS-Client systemeigene Unterstützung für den Kryptografiemodus 2 bietet. 


> [!IMPORTANT]
> Wenn diese Versionen oder höhere Versionen von Exchange und der MSDRM-Client nicht installiert sind, können Sie Exchange nicht für die Verwendung des Connectors konfigurieren. Überprüfen Sie, ob diese Versionen installiert sind, bevor Sie fortfahren.

### <a name="to-configure-exchange-servers-to-use-the-connector"></a>So konfigurieren Sie Exchange-Server für die Verwendung des Verbindungsdiensts

1. Stellen Sie sicher, dass die Exchange-Server für die Verwendung des RMS-Verbindungsdiensts autorisiert sind, indem Sie das Administrationstool des RMS-Verbindungsdiensts und die Informationen aus dem Abschnitt [Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) verwenden. 

    Diese Konfiguration ist erforderlich, damit Exchange den RMS-Verbindungsdienst verwenden kann.

2. Führen Sie für die Exchange-Serverrollen, die mit dem RMS-Verbindungsdienst kommunizieren, einen der folgenden Schritte aus:

   -   **Führen Sie das Server Konfigurationstool für Microsoft RMS Connector aus**. 

       Weitere Informationen finden Sie unter [Verwenden des Server Konfigurationstools für Microsoft RMS Connector](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector).

        Um das Tool beispielsweise lokal auszuführen, um einen Server mit Exchange 2016 oder Exchange 2013 zu konfigurieren:

       ```PowerShell
       .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
       ```

    
   -   **Manuelle Registrierungs Änderungen vornehmen** Weitere Informationen finden Sie unter [Registrierungs Einstellungen für den RMS-Connector](rms-connector-registry-settings.md). 

3. Aktivieren Sie die unm-Funktionalität für Exchange mithilfe des Exchange PowerShell-Cmdlets [Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration). Legen Sie `InternalLicensingEnabled $true` und `ClientAccessServerEnabled $true` fest.


## <a name="configuring-a-sharepoint-server-to-use-the-connector"></a>Konfigurieren eines SharePoint-Servers für die Verwendung des Verbindungsdiensts

Front-End-SharePoint-Webserver, einschließlich der Server, die den zentralen Verwaltungs Server hosten, kommunizieren mit dem RMS-Connector.

Damit diese Server, auf denen SharePoint ausgeführt wird, den RMS-Verbindungsdienst verwenden, müssen sie eine der folgenden Softwareversionen ausführen:

-   SharePoint Server 2019

-   SharePoint Server 2016

-   SharePoint Server 2013

-   SharePoint Server 2010

Auf einem Server, auf dem SharePoint 2019, 2016 oder SharePoint 2013 ausgeführt wird, muss außerdem eine Version des msipc-Clients 2,1 ausgeführt werden, die mit dem RMS-Connector unterstützt wird. 

Um sicherzustellen, dass Sie eine unterstützte Version haben, laden Sie den aktuellen Client aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=38396)herunter.

> [!WARNING]
> Es gibt mehrere Versionen des MSIPC 2.1-Clients, achten Sie also darauf, dass Sie Version 1.0.2004.0 oder höher haben.
>
> Sie können die Clientversion überprüfen, indem Sie die Versionsnummer der Datei „MSIPC.dll“ prüfen, die sich in **\Programme\Active Directory Rights Management Services Client 2.1** befindet. Das Dialogfeld „Eigenschaften“ zeigt die Versionsnummer des MSIPC 2.1-Clients.

Auf Servern mit SharePoint 2010 muss eine Version des MSDRM-Clients installiert sein, die die Unterstützung für den RMS-Kryptografiemodus 2 enthält. Windows Server 2012 und Windows Server 2012 R2 verfügen über systemeigene Unterstützung für Kryptografiemodus 2.

### <a name="to-configure-sharepoint-servers-to-use-the-connector"></a>So konfigurieren Sie SharePoint-Server für die Verwendung des Verbindungsdiensts

1. Stellen Sie sicher, dass die SharePoint-Server für die Verwendung des RMS-Verbindungsdiensts autorisiert sind, indem Sie das Administrationstool des RMS-Verbindungsdiensts und die Informationen aus dem Abschnitt [Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) verwenden. 

    Diese Konfiguration ist erforderlich, damit Ihre SharePoint-Server den RMS-Verbindungsdienst verwenden können.

2.  Führen Sie auf den SharePoint-Servern, die mit dem RMS-Verbindungsdienst kommunizieren, einen der folgenden Schritte aus:

    -   **Ausführen des Server Konfigurationstools für Microsoft RMS Connector** 

        Weitere Informationen finden Sie unter [Verwenden des Server Konfigurationstools für Microsoft RMS Connector](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector).

        Um das Tool beispielsweise lokal auszuführen, um einen Server zu konfigurieren, auf dem SharePoint 2019, 2016 oder SharePoint 2013 ausgeführt wird:

        ```PowerShell
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   **Wenn Sie SharePoint 2019, 2016 oder SharePoint 2013 verwenden, nehmen Sie manuelle Registrierungs Änderungen vor,** indem Sie die Informationen unter [Registrierungs Einstellungen für den RMS-Connector](rms-connector-registry-settings.md) verwenden, um Registrierungs Einstellungen auf den Servern manuell hinzuzufügen. 

3.  Aktivieren Sie IRM in SharePoint. Weitere Informationen finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](/previous-versions/office/sharepoint-server-2010/hh545607(v=office.14)) in der SharePoint-Bibliothek.

    Wenn Sie diese Anleitungen befolgen, müssen Sie SharePoint für die Verwendung des Verbindungsdiensts konfigurieren, indem Sie **Diesen RMS-Server verwenden** angeben und dann die URL des Verbindungsdiensts mit Lastenausgleich eingeben, die Sie konfiguriert haben. 

    Geben Sie das Protokollpräfix (HTTP:// oder HTTPS://) und den Namen des Connectors, den Sie in DNS definiert haben, als Lastenausgleichsadresse Ihres Connectors ein. 

    Wenn Ihr Connector beispielsweise den Namen `https:\//connector.contoso.com` hat, sieht Ihre Konfiguration wie im folgenden Bild aus:

    ![Konfigurieren von SharePoint Server für den RMS-Connector](./media/AzRMS_SharePointConnector.png)

    Nachdem in einer SharePoint-Farm IRM aktiviert ist, können Sie IRM für einzelne Bibliotheken aktivieren, indem Sie die Option **Verwaltung von Informationsrechten** auf der Seite **Bibliothekseinstellungen** für jede der Bibliotheken verwenden.

## <a name="configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector"></a>Konfigurieren eines Dateiservers, der die Dateiklassifizierungsinfrastruktur verwendet, für die Verwendung des Verbindungsdiensts

Damit ein Dateiserver den RMS-Connector und die Dateiklassifizierungsinfrastruktur verwendet, um Office-Dokumente zu schützen, muss er eins der folgenden Betriebssysteme ausführen:

- Windows Server 2016

- Windows Server 2012 R2

- Windows Server 2012

### <a name="to-configure-file-servers-to-use-the-connector"></a>So konfigurieren Sie Dateiserver für die Verwendung des Verbindungsdiensts

1. Stellen Sie sicher, dass die Dateiserver für die Verwendung des RMS-Verbindungsdiensts autorisiert sind, indem Sie das Administrationstool des RMS-Verbindungsdiensts und die Informationen aus dem Abschnitt [Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) verwenden. 

    Diese Konfiguration ist erforderlich, damit Ihre Dateiserver den RMS-Verbindungsdienst verwenden können.

2. Führen Sie auf den Dateiservern, die für die Dateiklassifizierungsinfrastruktur konfiguriert sind und mit dem RMS-Verbindungsdienst kommunizieren, einen der folgenden Schritte aus:

    -   **Ausführen des Server Konfigurationstools für Microsoft RMS Connector** 
    
        Weitere Informationen finden Sie unter [Verwenden des Server Konfigurationstools für Microsoft RMS Connector](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector).

        Um beispielsweise das Tool lokal zum Konfigurieren eines Servers mit ausgeführter FCI auszuführen:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    - Bearbeiten Sie manuell die **Registrierung** , indem Sie die Informationen unter [Registrierungs Einstellungen für den RMS-Connector](rms-connector-registry-settings.md) verwenden, um auf den Servern manuell Registrierungs Einstellungen hinzuzufügen. 

3. Erstellen Sie Klassifizierungsregeln und Dateiverwaltungsaufgaben zum Schützen von Dokumenten mit RMS-Verschlüsselung, und geben Sie dann eine RMS-Vorlage an, um die RMS-Richtlinien automatisch anzuwenden. 

    Weitere Informationen finden Sie unter [Ressourcen-Manager für Dateiserver (Übersicht)](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831701(v=ws.11)) in der Windows Server-Dokumentationsbibliothek.

## <a name="next-steps"></a>Nächste Schritte
Nachdem der RMS-Connector installiert und konfiguriert ist und Ihre Server für dessen Verwendung konfiguriert sind, können IT-Administratoren und Benutzer E-Mail-Nachrichten und Dokumente mithilfe des Azure Rights Management Service schützen und verwenden. 

Um dies für Benutzer zu vereinfachen, können Sie den Azure Information Protection-Client bereitstellen, der ein Add-On für Office installiert und dem Datei-Explorer neue Kontextmenüoptionen hinzufügt. 

Weitere Informationen finden Sie unter [Azure Information Protection-Client – Administratorhandbuch](./rms-client/client-admin-guide.md).

Beachten Sie Folgendes: Wenn Sie Abteilungsvorlagen konfigurieren, die Sie mit Exchange-Transportregeln oder Windows Server FCI verwenden möchten, muss in der Bereichskonfiguration für die Anwendungskompatibilitätsoption das Kontrollkästchen **Zeigen Sie diese Vorlage allen Benutzern, wenn die Anwendungen die Benutzeridentität nicht unterstützen.** aktiviert sein.

Sie können die [Roadmap für die Bereitstellung von Azure Information Protection](deployment-roadmap-classify-label-protect.md) verwenden, um herauszufinden, ob Sie vor dem Rollout von Azure Rights Management für Benutzer und Administratoren ggf. weitere Konfigurationsschritte ausführen sollten.

Informationen zum Überwachen des RMS-Connectors finden Sie unter [Überwachen des Azure Rights Management-Connectors](monitor-rms-connector.md).