---
# required metadata

title: Konfigurieren von Servern für den Azure Rights Management-Verbindungsdienst | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 75846ee1-2370-4360-81ad-e2b6afe3ebc9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurieren von Servern für den Azure Rights Management-Verbindungsdienst

*Gilt für: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*


Verwenden Sie die folgenden Informationen, um Ihre lokale Server für die Verwendung des Azure Rights Management (RMS)-Verbindungsdiensts zu konfigurieren. Diese Verfahren beziehen sich auf Schritt 5 aus [Bereitstellen des Azure Rights Management-Connectors](deploy-rms-connector.md).

Stellen Sie zunächst sicher, dass Sie den RMS-Verbindungsdienst installiert und konfiguriert haben und dass Sie alle [Voraussetzungen](deploy-rms-connector.md#prerequisites-for-the-rms-connector) für die Server, die den Verbindungsdienst verwenden können, überprüft haben.


## Konfigurieren von Servern für die Verwendung des RMS-Verbindungsdiensts
Nachdem Sie den RMS-Verbindungsdienst installiert und konfiguriert haben, können Sie Ihre lokalen Server konfigurieren, die Rights Management verwenden und mithilfe des Verbindungsdiensts eine Verbindung mit Azure RMS herstellen werden. Dies bedeutet, dass die folgenden Server zu konfigurieren sind:

-   **Für Exchange 2016 und Exchange 2013**: Clientzugriffsserver und Postfachserver

-   **Für Exchange 2010**: Clientzugriffsserver und Hub-Transport-Server

-   **Für SharePoint**: Front-End-SharePoint-Webserver, einschließlich der Server, die den zentralen Verwaltungsserver hosten

-   **Für die Dateiklassifizierungsinfrastruktur**: Windows Server-Computer, auf denen der Ressourcen-Manager für Dateien installiert ist

Diese Konfiguration erfordert das Festlegen von Registrierungseinstellungen. Zu diesem Zweck haben Sie zwei Optionen: automatisch mithilfe des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst oder manuell durch Bearbeiten der Registrierung.

---

**Automatisch mithilfe des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst:**

- Vorteile:

    - Keine direkte Bearbeitung der Registrierung. Diese wird für Sie mithilfe eines Skripts automatisiert.

    - Keine Notwendigkeit zur Ausführung eines Windows PowerShell-Cmdlets, um Ihre Microsoft RMS-URL abzurufen.

    - Die Voraussetzungen werden automatisch für Sie überprüft (aber nicht automatisch behoben), wenn die Ausführung lokal erfolgt.

Nachteile:

- Wenn Sie das Tool ausführen, müssen Sie eine Verbindung mit einem Server herstellen, auf dem bereits der RMS-Verbindungsdienst ausgeführt wird.

---

**Manuell durch Bearbeitung der Registrierung:**

- Vorteile:

    - Es ist keine Verbindung mit einem Server erforderlich, der den RMS-Verbindungsdienst ausführt.

- Nachteile:

    - Höherer Verwaltungsaufwand, der fehleranfällig ist.

    - Sie müssen Ihre Microsoft RMS-URL abrufen, wofür Sie einen Windows PowerShell-Befehl ausführen müssen.

    - Sie müssen immer alle Überprüfungen der Voraussetzungen selbst durchführen.


---

> [!IMPORTANT]
> In beiden Fällen müssen Sie manuell alle vorausgesetzten Komponenten installieren und Exchange, SharePoint und die Dateiklassifizierungsinfrastruktur zur Verwendung von Rights Management konfigurieren.

Für die meisten Organisationen stellt die automatische Konfiguration unter Verwendung des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst die bessere Möglichkeit dar, weil sie effizienter und zuverlässiger als eine manuelle Konfiguration ist.

Nachdem Sie die Konfigurationsänderungen auf diesen Servern vorgenommen haben, müssen Sie sie neu starten, wenn auf diesen Exchange oder SharePoint ausgeführt wird und die Server zuvor zur Verwendung von AD RMS konfiguriert waren. Sie brauchen diese Server nicht neu zu starten, wenn Sie sie zum ersten Mal für Rights Management konfigurieren. Der Dateiserver, der zur Verwendung der Dateiklassifizierungsinfrastruktur konfiguriert ist, muss nach diesen Konfigurationsänderungen immer neu gestartet werden.

### Verwenden des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst

1.  Wenn Sie das Skript für das Serverkonfigurationstool für den Microsoft RMS-Connector (GenConnectorConfig.ps1) noch nicht heruntergeladen haben, tun Sie dies vom [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106) aus.

2.  Speichern Sie die Datei „GenConnectorConfig.ps1“ auf dem Computer, auf dem Sie das Tool ausführen möchten. Wenn Sie das Tool lokal ausführen, muss dies der Server sein, den Sie für die Kommunikation mit dem RMS-Verbindungsdienst konfigurieren möchten. Andernfalls können Sie sie auf einem beliebigen Computer speichern.

3.  Entscheiden Sie, wie das Tool ausgeführt werden soll:

    -   **Lokal**: Sie können das Tool interaktiv auf dem Server ausführen, der für die Kommunikation mit dem RMS-Verbindungsdienst konfiguriert werden soll. Dies ist nützlich für eine einmalige Konfiguration, beispielsweise in einer Testumgebung.

    -   **Softwarebereitstellung**: Sie können das Tool ausführen, um Registrierungsdateien zu erzeugen, die Sie dann auf einem oder mehreren relevanten Servern bereitstellen, indem Sie eine Systemverwaltungsanwendung verwenden, die Softwarebereitstellung unterstützt, z. B. System Center Configuration Manager.

    -   **Gruppenrichtlinien**: Sie können das Tool ausführen, um ein Skript zu erzeugen, das Sie an einen Administrator weitergeben können, der Gruppenrichtlinienobjekte für die zu konfigurierenden Server erstellen kann. Dieses Skript erstellt ein Gruppenrichtlinienobjekt für jeden Servertyp, der konfiguriert werden soll, dem der Administrator dann die relevanten Server zuweisen kann.

    > [!NOTE]
    > Dieses Tool konfiguriert die Server, die mit dem RMS-Verbindungsdienst kommunizieren werden und am Anfang dieses Abschnitts aufgelistet sind. Führen Sie dieses Tool nicht auf den Servern aus, auf denen der RMS-Verbindungsdienst ausgeführt wird.

4.  Starten Sie die Windows PowerShell mit der Option **Als Administrator ausführen**, und verwenden Sie den Befehl „Get-help“, um Anleitungen zur Verwendung des Tools für Ihre gewählte Konfigurationsmethode anzuzeigen:

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

Zum Ausführen des Skripts müssen Sie die URL des RMS-Connectors für Ihre Organisation eingeben. Geben Sie das Protokollpräfix (HTTP:// oder HTTPS://) und den Namen des Connectors, den Sie in DNS definiert haben, als Lastenausgleichsadresse Ihres Connectors ein. Zum Beispiel: https://connector.contoso.com. Das Tool verwendet dann diese URL, um sich mit den Servern zu verbinden, auf denen der RMS-Verbindungsdienst ausgeführt wird, und um weitere Parameter abzurufen, die zum Erstellen der erforderlichen Konfigurationen verwendet werden.

> [!IMPORTANT]
> Wenn Sie dieses Tool ausführen, stellen Sie sicher, dass Sie den Namen des RMS-Verbindungsdiensts mit Lastenausgleich für Ihre Organisation angeben, und nicht den Namen eines einzelnen Servers, auf dem der RMS-Verbindungsdienst ausgeführt wird.

In den folgenden Abschnitten finden Sie spezifische Informationen für jeden Diensttyp:

-   [Konfigurieren eines Exchange-Servers für die Verwendung des Verbindungsdiensts](#configuring-an-exchange-server-to-use-the-connector)

-   [Konfigurieren eines SharePoint-Servers für die Verwendung des Verbindungsdiensts](#configuring-a-sharepoint-server-to-use-the-connector)

-   [Konfigurieren eines Dateiservers, der die Dateiklassifizierungsinfrastruktur verwendet, für die Verwendung des Verbindungsdiensts](#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)

> [!NOTE]
> Nachdem diese Server zur Verwendung des Verbindungsdiensts konfiguriert sind, funktionieren Anwendungen, die lokal auf diesen Servern installiert sind, möglicherweise nicht mit RMS. Wenn dies eintritt, liegt das daran, dass die Anwendungen versuchen, den Verbindungsdienst zu verwenden, statt RMS direkt zu verwenden – dies wird aber nicht unterstützt.
>
> Darüber hinaus, wenn Office 2010 lokal auf einem Exchange-Server installiert ist, funktionieren die IRM-Features der Client-App möglicherweise von diesem Computer aus, nachdem der Server für die Verwendung des Verbindungsdiensts konfiguriert ist – dies wird aber nicht unterstützt.
>
> In beiden Szenarios müssen Sie die Clientanwendungen auf getrennten Computern installieren, die nicht für die Verwendung des Verbindungsdiensts konfiguriert sind. Sie verwenden dann korrekt RMS direkt.

## Konfigurieren eines Exchange-Servers für die Verwendung des Verbindungsdiensts
Die folgenden Exchange-Rollen kommunizieren mit dem RMS-Verbindungsdienst:

-   Für Exchange 2016 und Exchange 2013: Clientzugriffsserver und Postfachserver

-   Für Exchange 2010: Clientzugriffsserver und Hub-Transport-Server

Damit diese Server, auf denen Exchange ausgeführt wird, den RMS-Verbindungsdienst verwenden, müssen sie eine der folgenden Softwareversionen ausführen:

-   Exchange Server 2016

-   Exchange Server 2013 mit kumulativem Update 3 für Exchange 2013

-   Exchange Server 2010 mit Exchange 2010 Service Pack 3 Updaterollup 6

Sie müssen auf diesen Servern außerdem eine Version des RMS-Clients installieren, die Unterstützung für den RMS-Kryptografiemodus 2 enthält. Die Mindestversion, die in Windows Server 2008 unterstützt wird, ist in dem Hotfix enthalten, das Sie herunterladen können aus [RSA-Schlüssellänge wurde für AD RMS in Windows Server 2008 R2 und Windows Server 2008 auf 2048 Bits erhöht](http://support.microsoft.com/kb/2627272). Die Mindestversion für Windows Server 2008 R2 kann heruntergeladen werden von [RSA-Schlüssellänge für AD RMS in Windows 7 oder Windows Server 2008 R2 wurde auf 2048 Bits erhöht](http://support.microsoft.com/kb/2627273). Windows Server 2012 und Windows Server 2012 R2 verfügen über systemeigene Unterstützung für Kryptografiemodus 2.

> [!IMPORTANT]
> Wenn diese Versionen oder höhere Versionen von Exchange und der RMS-Client nicht installiert sind, können Sie Exchange nicht für die Verwendung des Verbindungsdiensts konfigurieren. Bevor Sie die nächsten Schritte ausführen, vergewissern Sie sich, dass diese Versionen installiert sind.

### So konfigurieren Sie Exchange-Server für die Verwendung des Verbindungsdiensts

1. Stellen Sie sicher, dass die Exchange-Server für die Verwendung des RMS-Verbindungsdiensts autorisiert sind, indem Sie das Administrationstool des RMS-Verbindungsdiensts und die Informationen aus dem Abschnitt [Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) verwenden. Diese Konfiguration ist erforderlich, damit Exchange den RMS-Verbindungsdienst verwenden kann.

2.  Führen Sie für die Exchange-Serverrollen, die mit dem RMS-Verbindungsdienst kommunizieren, einen der folgenden Schritte aus:

    -   Führen Sie das Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst aus. Weitere Informationen finden Sie unter [Verwenden des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) in diesem Artikel.

        Um das Tool beispielsweise lokal auszuführen, um einen Server mit Exchange 2016 oder Exchange 2013 zu konfigurieren:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
        ```

    -   Nehmen Sie manuelle Registrierungsänderungen mithilfe der Informationen unter [Registrierungseinstellungen für den RMS-Verbindungsdienst](rms-connector-registry-settings.md) vor, um Registrierungseinstellungen manuell den Servern hinzuzufügen. 

3.  Aktivieren Sie die IRM-Funktion in Exchange. Weitere Informationen finden Sie unter [Information Rights Management-Prozeduren](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx) in der Exchange-Bibliothek.

    > [!NOTE]
    > Standardmäßig wird nach dem Ausführen von **Set-IRMConfiguration -InternalLicensingEnabled $true** IRM für Outlook Web App und mobile Geräte automatisch aktiviert, zusätzlich zur Aktivierung von IRM für Postfächer. Administratoren können IRM jedoch auf unterschiedlichen Ebenen deaktivieren. Beispielsweise für einen Clientzugriffsserver, das virtuelle Verzeichnis oder die Postfachrichtlinie von Outlook Web App und eine Postfachrichtlinie für mobile Geräte. Wenn Benutzern keine der Azure RMS-Vorlagen in Outlook Web App (nach einem Tag Wartezeit) oder auf mobilen Geräten (wenn sie die Vorlagen im Outlook-Client sehen) angezeigt wird, überprüfen Sie die relevanten Einstellungen, um sicherzustellen, dass IRM nicht deaktiviert ist. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren von Information Rights Management auf Clientzugriffsservern](https://technet.microsoft.com/library/dd876938(v=exchg.150).aspx) in der Exchange-Dokumentation. 


## Konfigurieren eines SharePoint-Servers für die Verwendung des Verbindungsdiensts
Die folgenden SharePoint-Rollen kommunizieren mit dem RMS-Connector:

-   Front-End-SharePoint-Webserver, einschließlich der Server, die den zentralen Verwaltungsserver hosten

Damit diese Server, auf denen SharePoint ausgeführt wird, den RMS-Verbindungsdienst verwenden, müssen sie eine der folgenden Softwareversionen ausführen:

-   SharePoint Server 2016

-   SharePoint Server 2013

-   SharePoint Server 2010

Auf einem Server, auf dem SharePoint 2016 oder SharePoint 2013 ausgeführt wird, muss außerdem eine Version des MSIPC-Clients 2.1 ausgeführt werden, die mit dem RMS-Connector unterstützt wird. Damit sichergestellt ist, dass Sie eine unterstützte Version haben, laden Sie den aktuellen Client aus dem [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=38396) herunter.

> [!WARNING]
> Es gibt mehrere Versionen des MSIPC 2.1-Clients, achten Sie also darauf, dass Sie Version 1.0.2004.0 oder höher haben.
>
> Sie können die Clientversion überprüfen, indem Sie die Versionsnummer der Datei „MSIPC.dll“ prüfen, die sich in **\Programme\Active Directory Rights Management Services Client 2.1** befindet. Das Dialogfeld „Eigenschaften“ zeigt die Versionsnummer des MSIPC 2.1-Clients.

Auf Servern mit SharePoint 2010 muss eine Version des MSDRM-Clients installiert sein, die die Unterstützung für den RMS-Kryptografiemodus 2 enthält. Die Mindestversion, die in Windows Server 2008 unterstützt wird, ist in dem Hotfix enthalten, das Sie herunterladen können von [RSA-Schlüssellänge wurde für AD RMS in Windows Server 2008 R2 und Windows Server 2008 auf 2048 Bits erhöht](http://support.microsoft.com/kb/2627272), und die Mindestversion für Windows Server 2008 R2 kann heruntergeladen werden von [RSA-Schlüssellänge für AD RMS in Windows 7 oder Windows Server 2008 R2 wurde auf 2048 Bits erhöht](http://support.microsoft.com/kb/2627273). Windows Server 2012 und Windows Server 2012 R2 verfügen über systemeigene Unterstützung für Kryptografiemodus 2.

### So konfigurieren Sie SharePoint-Server für die Verwendung des Verbindungsdiensts

1. Stellen Sie sicher, dass die SharePoint-Server für die Verwendung des RMS-Verbindungsdiensts autorisiert sind, indem Sie das Administrationstool des RMS-Verbindungsdiensts und die Informationen aus dem Abschnitt [Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) verwenden. Diese Konfiguration ist erforderlich, damit Exchange den RMS-Verbindungsdienst verwenden kann.

2.  Führen Sie auf den SharePoint-Servern, die mit dem RMS-Verbindungsdienst kommunizieren, einen der folgenden Schritte aus:

    -   Führen Sie das Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst aus. Weitere Informationen finden Sie unter [Verwenden des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) in diesem Artikel.

        Um beispielsweise das Tool lokal zum Konfigurieren eines Servers auszuführen, auf dem SharePoint 2016 oder SharePoint 2013 ausgeführt wird:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   Wenn Sie SharePoint 2016 oder SharePoint 2013 verwenden, nehmen Sie manuelle Registrierungsänderungen mithilfe der Informationen unter [Registrierungseinstellungen für den RMS-Connector](rms-connector-registry-settings.md) vor, um Registrierungseinstellungen den Servern manuell hinzuzufügen. 

3.  Aktivieren Sie IRM in SharePoint. Weitere Informationen finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx) in der SharePoint-Bibliothek.

    Wenn Sie diese Anleitungen befolgen, müssen Sie SharePoint für die Verwendung des Verbindungsdiensts konfigurieren, indem Sie **Diesen RMS-Server verwenden** angeben und dann die URL des Verbindungsdiensts mit Lastenausgleich eingeben, die Sie konfiguriert haben. Geben Sie das Protokollpräfix (HTTP:// oder HTTPS://) und den Namen des Connectors, den Sie in DNS definiert haben, als Lastenausgleichsadresse Ihres Connectors ein. Wenn Ihr Connector beispielsweise den Namen „https://connector.contoso.com“ hat, sieht Ihre Konfiguration wie im folgenden Bild aus:

    ![Konfigurieren von SharePoint Server für den RMS-Connector](../media/AzRMS_SharePointConnector.png)

    Nachdem in einer SharePoint-Farm IRM aktiviert ist, können Sie IRM für einzelne Bibliotheken aktivieren, indem Sie die Option **Verwaltung von Informationsrechten** auf der Seite **Bibliothekseinstellungen** für jede der Bibliotheken verwenden.


## Konfigurieren eines Dateiservers, der die Dateiklassifizierungsinfrastruktur verwendet, für die Verwendung des Verbindungsdiensts
Damit ein Dateiserver den RMS-Connector und die Dateiklassifizierungsinfrastruktur verwendet, um Office-Dokumente zu schützen, muss er eins der folgenden Betriebssysteme ausführen:

-   Windows Server 2012 R2

-   Windows Server 2012

### So konfigurieren Sie Dateiserver für die Verwendung des Verbindungsdiensts

1.  Stellen Sie sicher, dass die Dateiserver für die Verwendung des RMS-Verbindungsdiensts autorisiert sind, indem Sie das Administrationstool des RMS-Verbindungsdiensts und die Informationen aus dem Abschnitt [Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) verwenden. Diese Konfiguration ist erforderlich, damit Exchange den RMS-Verbindungsdienst verwenden kann.

2.  Führen Sie auf den Dateiservern, die für die Dateiklassifizierungsinfrastruktur konfiguriert sind und mit dem RMS-Verbindungsdienst kommunizieren, einen der folgenden Schritte aus:

    -   Führen Sie das Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst aus. Weitere Informationen finden Sie unter [Verwenden des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) in diesem Artikel.

        Um beispielsweise das Tool lokal zum Konfigurieren eines Servers mit ausgeführter FCI auszuführen:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    - Nehmen Sie manuelle Registrierungsänderungen mithilfe der Informationen unter [Registrierungseinstellungen für den RMS-Verbindungsdienst](rms-connector-registry-settings.md) vor, um Registrierungseinstellungen manuell den Servern hinzuzufügen. 

3.  Erstellen Sie Klassifizierungsregeln und Dateiverwaltungsaufgaben zum Schützen von Dokumenten mit RMS-Verschlüsselung, und geben Sie dann eine RMS-Vorlage an, um die RMS-Richtlinien automatisch anzuwenden. Weitere Informationen finden Sie unter [Ressourcen-Manager für Dateiserver (Übersicht)](http://technet.microsoft.com/library/hh831701.aspx) in der Windows Server-Dokumentationsbibliothek.

## Nächste Schritte
Jetzt, wo der RMS-Verbindungsdienst installiert und konfiguriert ist und Ihre Server für dessen Verwendung konfiguriert sind, können IT-Administratoren und Benutzer E-Mail-Nachrichten und Dokumente mithilfe von Azure RMS schützen und verwenden. Um dies für Benutzer zu vereinfachen, können Sie die RMS-Freigabeanwendung bereitstellen, die ein Add-On für Office installiert und dem Datei-Explorer neue Kontextmenüoptionen hinzufügt. Weitere Informationen finden Sie im [Rights Management-Freigabeanwendung – Administratorhandbuch](../rms-client/sharing-app-admin-guide.md).

Zusätzlich können Sie ggf. noch Folgendes verwenden, um den RMS-Verbindungsdienst und die Nutzung von Azure RMS in Ihrer Organisation zu überwachen:

-   Die integrierten Leistungsindikatoren des **Microsoft Rights Management-Verbindungsdiensts**.

-   Das [RMS Analyzer-Tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437) unter Verwendung der RMS-Verbindungsdienstoption zum Überwachen der Integrität des Verbindungsdiensts und Bestimmen etwaiger Konfigurationsprobleme.

-   [Protokollieren und Analysieren der Nutzung von Azure Rights Management](log-analyze-usage.md)

Sie können die [Roadmap für die Bereitstellung von Azure Rights Management](../plan-design/deployment-roadmap.md) verwenden, um herauszufinden, ob Sie vor dem Rollout von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] für Benutzer und Administratoren ggf. weitere Konfigurationsschritte ausführen sollten. 


<!--HONumber=Apr16_HO4-->

