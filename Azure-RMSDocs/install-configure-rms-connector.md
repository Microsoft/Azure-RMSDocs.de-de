---
title: Installieren und Konfigurieren des Rights Management-Connectors – AIP
description: Hier erhalten Sie Informationen zum Installieren und Konfigurieren des Connectors von Azure Rights Management (RMS). Diese Verfahren beziehen sich auf die unter „Bereitstellen des Azure Rights Management-Connectors“ beschriebenen Schritte 1 bis 4.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 07/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.subservice: connector
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: dd8a63f3bc761cd7bcaa7b8b40a3309488385acb
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568351"
---
# <a name="installing-and-configuring-the-azure-rights-management-connector"></a>Installieren und Konfigurieren des Azure Rights Management-Connectors

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, 2016, 2012 R2 und Windows Server 2012*

Anhand der folgenden Informationen können Sie den Connector von Azure Rights Management (RMS) installieren und konfigurieren. Diese Verfahren beziehen sich auf die unter [Bereitstellen des Azure Rights Management-Connectors](deploy-rms-connector.md) beschriebenen Schritte 1 bis 4.

Stellen Sie vorab sicher, dass Sie die [Voraussetzungen](deploy-rms-connector.md#prerequisites-for-the-rms-connector) für diese Bereitstellung überprüft haben.

Stellen Sie sicher, dass Sie die richtige Azure Sovereign Cloud-Instanz kennen, damit ihr Connector Setup und Konfiguration durchführen kann: 
- **Azurecloud**: kommerzielles Angebot von Azure
- **Azurechinacloud**: Azure wird von 21ViaNet betrieben
- **Azureus Government**: Azure Government (gcc High/DoD)
- **AzureUSGovernment2**: Azure Government 2
- **AzureUSGovernment3**: Azure Government 3


## <a name="installing-the-rms-connector"></a>Installieren des RMS-Connectors

1.  Identifizieren Sie die Computer (mindestens zwei), um den RMS-Connector auszuführen. Diese Computer müssen die in den Voraussetzungen aufgeführte Mindestspezifikation erfüllen.

    > [!NOTE]
    > Installieren Sie einen einzelnen RMS-Connector (bestehend aus mehreren Servern für Hochverfügbarkeit) pro Mandant (Microsoft 365 Mandanten oder Azure AD Mandanten). Im Gegensatz zu Active Directory RMS müssen Sie nicht in jeder Gesamtstruktur einen RMS-Connector installieren.

2.  Laden Sie die Quelldateien für den RMS-Connector aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=314106) herunter.

    Laden Sie zum Installieren des RMS-Connectors die Datei „RMSConnectorSetup.exe“ herunter.

    Zusätzlich:

    -   Wenn Sie das Serverkonfigurationstool für den RMS-Connector verwenden möchten, um die Konfiguration der Registrierungseinstellungen auf Ihren lokalen Servern zu automatisieren, müssen Sie auch die Komponente „GenConnectorConfig.ps1“ herunterladen.

3.  Führen Sie auf dem Computer, auf dem Sie den RMS-Connector installieren möchten, **RMSConnectorSetup.exe** mit Administratorrechten aus.

4.  Wählen Sie auf der Willkommensseite von Microsoft Rights Management Connector-Setup **die Option Microsoft Rights Management Connector auf dem Computer installieren** aus, und klicken Sie dann auf **weiter**.

5.  Lesen und akzeptieren Sie die Lizenzbedingungen des RMS-Verbindungsdiensts, und klicken Sie auf **Weiter**.


## <a name="entering-credentials"></a>Eingeben von Anmeldeinformationen

Bevor Sie den RMS-Verbindungs Dienst konfigurieren können, müssen Sie zuerst die Cloud-Umgebung auswählen, die ihrer Lösung entspricht.   
- **Azurecloud**: kommerzielles Angebot von Azure
- **Azurechinacloud**: Azure wird von 21ViaNet betrieben
- **Azureus Government**: Azure Government (gcc High/DoD)
- **AzureUSGovernment2**: Azure Government 2
- **AzureUSGovernment3**: Azure Government 3

:::image type="content" source="media/authenticate_tenant_rms_connector.png" alt-text="Wählen Sie die richtige Azure-Umgebung aus, um Ihren neuen Aad RM-Connector zu authentifizieren":::

Nachdem Sie Ihre cloudumgebung ausgewählt haben, geben Sie Ihren **Benutzernamen** und Ihr **Kennwort ein** Stellen Sie sicher, dass Sie die Anmelde Informationen für ein Konto eingeben, das über ausreichende Berechtigungen zum Konfigurieren des RMS-Verbindungs Verbindungs Beispielsweise können Sie eingeben <strong>admin@contoso.com</strong> und dann das Kennwort für dieses Konto angeben.


Wenn Sie [Onboarding-Steuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) implementiert haben, müssen Sie darüber hinaus sicherstellen, dass das von Ihnen angegebene Konto Inhalte schützen kann. Wenn Sie beispielsweise die Möglichkeit zum Schützen von Inhalten auf die Gruppe „IT-Abteilung“ beschränkt haben, muss das Konto, das Sie hier angeben, ein Mitglied dieser Gruppe sein. Andernfalls wird die folgende Fehlermeldung angezeigt: Fehler **beim Versuch, den Speicherort des Verwaltungs Dienstanbieter und der Organisation zu ermitteln. Stellen Sie sicher, dass Microsoft Rights Management Service für Ihre Organisation aktiviert ist.**

Sie können ein Konto verwenden, das über eine der folgenden Berechtigungen verfügt:

-   **Globaler Administrator für Ihren** Mandanten: ein Konto, das ein globaler Administrator für Ihren Microsoft 365 Mandanten oder Azure AD Mandanten ist.

-   **Globaler Azure Rights Management-Administrator**: Ein Konto in Azure Active Directory, dem die Rolle „Globaler Azure RMS-Administrator“ zugewiesen wurde.

-   **Azure Rights Management-Connectoradministrator**: Ein Konto in Azure Active Directory, dem Rechte zum Installieren und Verwalten des RMS-Connectors für Ihre Organisation erteilt wurden.

    > [!NOTE]
    > Die Rolle "globaler Azure Rights Management-Administrator" und "Azure Rights Management Connector-Administrator" werden Konten mithilfe des Cmdlets " [Add-aipservicerolebasedadministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator) " zugewiesen.
    > 
    > Wenn der RMS-Connector mit den Mindestberechtigungen ausgeführt werden soll, erstellen Sie ein dediziertes Konto für diesen Zweck, dem Sie dann die Rolle „Azure RMS-Connectoradministrator“ zuweisen, indem Sie die folgenden Schritte ausführen:
    >
    > 1. Wenn Sie dies noch nicht getan haben, laden Sie das PowerShell-Modul aipservice herunter, und installieren Sie es. Weitere Informationen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).
    >
    >     Starten Sie Windows PowerShell mit dem Befehl **als Administrator ausführen** , und stellen Sie mithilfe des Befehls [Connect-aipservice](/powershell/module/aipservice/connect-aipservice) eine Verbindung mit dem Schutzdienst her:
    >
    >     ```
    >     Connect-AipService                   //provide Microsoft 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  Führen Sie dann den Befehl [Add-aipservicerolebasedadministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator) aus, und verwenden Sie dabei nur einen der folgenden Parameter:
    >
    >     ```
    >     Add-AipServiceRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AipServiceRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AipServiceRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     Geben Sie beispielsweise Folgendes ein: **Add-aipservicerolebasedadministrator-EmailAddress melisa@contoso.com -Role "Connector Administrator"** .
    >
    >     Obwohl diese Befehle die Rolle "Connector-Administrator" zuweisen, können Sie hier auch die Rolle "globaladministrator" verwenden.

Während der Installation des RMS-Connectors werden alle erforderlichen Softwareanwendungen überprüft und installiert, Internetinformationsdienste (Internet Information Services, IIS) wird installiert, sofern nicht bereits vorhanden, und die Connectorsoftware wird installiert und konfiguriert. Darüber hinaus wird Azure RMS für die Konfiguration vorbereitet, indem Folgendes erstellt wird:

-   Eine leere Tabelle für Server, die autorisiert sind, den Connector für die Kommunikation mit Azure RMS zu verwenden. Fügen Sie dieser Tabelle später Server hinzu.

-   Ein Satz von Sicherheitstoken für den Connector, die Vorgänge mit Azure RMS autorisieren. Diese Token werden aus Azure RMS heruntergeladen und auf dem lokalen Computer in der Registrierung installiert. Sie werden mithilfe der Datenschutz-Anwendungsprogrammierschnittstelle (Data Protection Application Programming Interface, DPAPI) und Anmeldeinformationen für das lokale Systemkonto geschützt.

Führen Sie auf der letzten Seite des Assistenten Folgendes durch, und klicken Sie dann auf **Fertig stellen**:

-   Wenn dies der erste Verbindungsdienst ist, den Sie installiert haben, aktivieren Sie dabei noch nicht **Verbindungsdienst-Administratorkonsole zum Autorisieren von Servern starten**. Sie wählen diese Option aus, nachdem Sie Ihren zweiten (oder letzten) RMS-Connector installiert haben. Führen Sie stattdessen den Assistenten auf mindestens einem anderen Computer erneut aus. Sie müssen mindestens zwei Connectors installieren.

-   Wenn Sie Ihren zweiten (oder letzten) Verbindungsdienst installiert haben, aktivieren Sie **Verbindungsdienst-Administratorkonsole zum Autorisieren von Servern starten**.

> [!TIP]
> Zu diesem Zeitpunkt gibt es einen Überprüfungstest, den Sie ausführen können, um zu testen, ob die Webdienste für den RMS-Connector funktionieren:
>
> -   Stellen Sie über einen Webbrowser eine Verbindung mit **http://&lt;Connectoradresse&gt;/_wmcs/certification/servercertification.asmx** her, wobei Sie *&lt;Connectoradresse&gt;* durch die Adresse oder den Namen des Servers ersetzen, auf dem der RMS-Connector installiert ist. Bei einer erfolgreichen Verbindung wird eine Seite **ServerCertificationWebService** angezeigt.

Wenn Sie den RMS-Connector deinstallieren müssen, führen Sie den Assistenten erneut aus, und wählen Sie die Option „Deinstallieren“ aus.

Wenn während der Installation Probleme auftreten, überprüfen Sie das Installationsprotokoll: **%LocalAppData%\Temp\Microsoft Rights Management connector_ \<date and time> . log** 

Ihr Installationsprotokoll könnte beispielsweise wie folgt aussehen: „C:\Benutzer\Administrator\AppData\Local\Temp\Microsoft Rights Management-Connector_20170803110352.log“.

## <a name="authorizing-servers-to-use-the-rms-connector"></a>Autorisieren von Servern für die Verwendung des RMS-Connectors
Wenn Sie den RMS-Connector auf mindestens zwei Computern installiert haben, können Sie die Server und Dienste autorisieren, die den RMS-Connector verwenden sollen. Beispielsweise Server, auf denen Exchange Server 2013 oder SharePoint Server 2013 ausgeführt wird.

Um diese Server zu definieren, führen Sie das Verwaltungstool für den RMS-Connector aus, und fügen Sie der Liste zugelassener Server Einträge hinzu. Sie können dieses Tool ausführen, wenn Sie am Ende des Installations-Assistenten des Microsoft Rights Management-Verbindungsdiensts **Verbindungsdienst-Administratorkonsole zum Autorisieren von Servern starten** auswählen, oder Sie führen ihn gesondert aus dem Assistenten heraus aus.

Berücksichtigen Sie beim Autorisieren dieser Server die folgenden Aspekte:

- Servern, die Sie hinzufügen, werden besondere Berechtigungen erteilt. Allen Konten, die Sie für die Exchange Server-Rolle in der Konfiguration des Connectors angeben, wird in Azure RMS die [Administratorrolle](configure-super-users.md) zugewiesen, die den Konten Zugriff auf alle Inhalte für diesen RMS-Mandanten gewährt. Die Administratorfunktion wird zu diesem Zeitpunkt bei Bedarf automatisch aktiviert. Um Sicherheitsrisiken durch Rechteerweiterungen zu vermeiden, achten Sie sorgfältig darauf, nur Konten anzugeben, die von den Exchange-Servern Ihrer Organisation verwendet werden. Alle als SharePoint-Server oder Dateiserver konfigurierten Server, die FCI verwenden, erhalten normale Benutzerrechte.

- Sie können mehrere Server als einzelnen Eintrag hinzufügen, indem Sie eine Active Directory-Sicherheits- oder -Verteilergruppe oder ein von mehreren Servern verwendetes Dienstkonto angeben. Bei Verwendung dieser Konfiguration verwendet die Gruppe von Servern gemeinsam dieselben RMS-Zertifikate, und alle werden als Besitzer von Inhalten angesehen, die einer von ihnen geschützt hat. Zur Minimierung des Verwaltungsaufwands empfehlen wir die Verwendung dieser Konfiguration einer Einzelgruppe statt einzelner Server, um die Exchange-Server Ihrer Organisation oder eine SharePoint-Serverfarm zu autorisieren.

Klicken Sie auf der Seite **Zur Verwendung des Verbindungsdiensts berechtigte Server** auf **Hinzufügen**.

> [!NOTE]
> Das Autorisieren von Servern ist die äquivalente Konfiguration in Azure RMS zur AD RMS-Konfiguration, bei der die NTFS-Rechte auf „ServerCertification.asmx“ für die Dienst- oder Servercomputerkonten manuell angewendet werden und die Administratorrechte den Exchange-Konten manuell zugewiesen werden. Das Anwenden von NTFS-Rechten auf „ServerCertification.asmx“ ist für den Connector nicht erforderlich.


### <a name="add-a-server-to-the-list-of-allowed-servers"></a>Hinzufügen eines Servers zur Liste zugelassenen Server
Geben Sie auf der Seite **Einem Server die Nutzung des Verbindungsdiensts gestatten** den Namen des Objekts ein, oder durchsuchen Sie, um das zu autorisierende Objekt zu identifizieren.

Es ist wichtig, dass Sie das richtige Objekt autorisieren. Damit ein Server den Connector verwenden kann, muss das Konto, das den lokalen Dienst (z. B. Exchange oder SharePoint) ausführt, zur Autorisierung ausgewählt werden. Wenn z. B. der Dienst als konfiguriertes Dienstkonto ausgeführt wird, fügen Sie der Liste den Namen dieses Dienstkontos hinzu. Wenn der Dienst als lokales System ausgeführt wird, fügen Sie den Namen des Computerobjekts (z. B. SERVERNAME$) hinzu. Als bewährte Methode erstellen Sie eine Gruppe, die diese Konten enthält, und geben Sie anstelle einzelner Servernamen die Gruppe an.

Weitere Informationen zu den verschiedenen Serverrollen:

-   Für Server, auf denen Exchange ausgeführt wird, gilt Folgendes: Sie müssen eine Sicherheitsgruppe angeben, und Sie können die Standardgruppe (**Exchange-Server**) verwenden, die Exchange automatisch erstellt und für alle Exchange-Server in der Gesamtstruktur verwaltet.

-   Für Server, auf denen SharePoint ausgeführt wird, gilt Folgendes:

    -   Wenn ein SharePoint 2010-Server für die Ausführung als lokales System konfiguriert ist (es wird kein Dienstkonto verwendet), erstellen Sie manuell eine Sicherheitsgruppe in Active Directory Domain Services, und fügen Sie dieser Gruppe das Computernamensobjekt für den Server in dieser Konfiguration hinzu.

    -   Wenn ein SharePoint-Server für die Verwendung eines Dienstkontos konfiguriert ist (Empfehlung für SharePoint 2010 und die einzige Option für SharePoint 2016 und SharePoint 2013), gehen Sie wie folgt vor:

        1.  Fügen Sie das Dienstkonto hinzu, das den SharePoint-Zentraladministrationsdienst ausführt, damit SharePoint über die Administratorkonsole konfiguriert werden kann.

        2.  Fügen Sie das Konto hinzu, das für den SharePoint-App-Pool konfiguriert ist.

        > [!TIP]
        > Wenn sich diese beiden Konten unterscheiden, sollten Sie in Erwägung ziehen, eine einzige Gruppe zu erstellen, die beide Konten enthält, um den Verwaltungsaufwand zu minimieren.

-   Für Dateiserver, die die Dateiklassifizierungsinfrastruktur verwenden, werden die zugeordneten Dienste unter dem lokalen Systemkonto ausgeführt, sodass Sie das Computerkonto für die Dateiserver (z. B. SERVERNAME$) oder eine Gruppe, die diese Computerkonten enthält, autorisieren müssen.

Wenn Sie mit dem Hinzufügen von Servern zu der Liste fertig sind, klicken Sie auf **Schließen**.

Wenn Sie dies nicht bereits getan haben, müssen Sie jetzt den Lastenausgleich für die Server konfigurieren, auf denen der RMS-Connector installiert ist, und überlegen, ob HTTPS für die Verbindungen zwischen diesen Servern und den Servern verwendet werden soll, die Sie gerade autorisiert haben.

## <a name="configuring-load-balancing-and-high-availability"></a>Konfigurieren von Lastausgleich und hoher Verfügbarkeit
Nachdem Sie die zweite oder letzte Instanz des RMS-Verbindungs dienstanschlusses installiert haben, definieren Sie einen Connector-URL-Servernamen, und konfigurieren Sie ein Lasten Ausgleichssystem.

Der Connector-URL-Servername kann ein beliebiger Name unter einem Namespace sein, der von Ihnen gesteuert wird. Beispielsweise können Sie einen Eintrag in Ihrem DNS-System für **rmsconnector.contoso.com** erstellen und diesen Eintrag so konfigurieren, dass eine IP-Adresse in Ihrem Lasten Ausgleichssystem verwendet wird. Für diesen Namen gibt es keine besonderen Anforderungen, und er muss nicht auf den Connector-Servern konfiguriert werden. Wenn Ihre Exchange-und SharePoint-Server nicht über das Internet mit dem Connector kommunizieren, muss dieser Name im Internet nicht aufgelöst werden.

> [!IMPORTANT]
> Wir empfehlen Ihnen, diesen Namen nach der Konfiguration von Exchange- oder SharePoint-Servern für die Verwendung des Connectors nicht mehr zu ändern, weil Sie ansonsten alle IRM-Konfigurationen auf diesen Servern löschen und diese dann neu konfigurieren müssen.

Nachdem der Name in DNS erstellt und für eine IP-Adresse konfiguriert wurde, konfigurieren Sie den Lastenausgleich für diese Adresse, die den Datenverkehr an die Connector-Server leitet. Sie können zu diesem Zweck jedes IP-basierte Lastenausgleichsmodul verwenden, das den Netzwerklastenausgleich (Network Load Balancing, NLB) von Windows Server enthält. Weitere Informationen finden Sie unter [Lastenausgleich – Bereitstellungsleitfaden](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754833(v=ws.10)).

Verwenden Sie die folgenden Einstellungen, um den NLB-Cluster zu konfigurieren:

-   Ports: 80 (für HTTP) oder 443 (für HTTPS)

    Weitere Informationen dazu, ob Sie HTTP oder HTTPS verwenden sollten, finden Sie im nächsten Abschnitt.

-   Affinität: Keine

-   Verteilungsmethode: Gleich

Dieser Name, den Sie für das System mit Lastenausgleich (für die Server, auf denen der RMS-Connectordienst ausgeführt wird) definieren, ist der Name des RMS-Connectors Ihrer Organisation, den Sie später beim Konfigurieren der lokalen Server für die Verwendung von Azure RMS verwenden.

## <a name="configuring-the-rms-connector-to-use-https"></a>Konfigurieren des RMS-Connectors für die Verwendung von HTTPS
> [!NOTE]
> Dieser Konfigurationsschritt ist optional, wird jedoch als zusätzliche Sicherheitsmaßnahme empfohlen.

Obwohl die Verwendung von TLS oder SSL für den RMS-Connector optional ist, empfehlen wir sie für jeden HTTP-basierten sicherheitsrelevanten Dienst. Diese Konfiguration authentifiziert die Server, auf denen der Connector ausgeführt wird, gegenüber Ihren Exchange- und SharePoint-Servern, die den Connector verwenden. Darüber hinaus werden alle von diesen Servern an den Connector gesendeten Daten verschlüsselt.

Um den RMS-Connector für die Verwendung von TLS zu aktivieren, installieren Sie auf jedem Server, auf dem der RMS-Connector ausgeführt wird, ein Serverauthentifizierungszertifikat, das den Namen enthält, den Sie für den Connector verwenden. Wenn Ihr RMS-Connectorname, den Sie in DNS definiert haben, beispielsweise **rmsconnector.contoso.com** lautet, stellen Sie ein Serverauthentifizierungszertifikat bereit, das **rmsconnector.contoso.com** als allgemeinen Namen im Zertifikatantragsteller enthält. Oder geben Sie **rmsconnector.contoso.com** im alternativen Namen des Zertifikats als DNS-Wert an. Das Zertifikat muss nicht den Namen des Servers enthalten. Binden Sie dann in IIS dieses Zertifikat an die Standardwebsite.

Stellen Sie bei Verwendung der HTTPS-Option sicher, dass alle Server, auf denen der Connector ausgeführt wird, über ein gültiges Serverauthentifizierungszertifikat verfügen, das mit einer Stammzertifizierungsstelle verkettet ist, der Ihre Exchange- und SharePoint Server vertrauen. Und wenn die Zertifizierungsstelle, die die Zertifikate für die Connector-Server ausgestellt hat, eine Zertifikatsperrliste veröffentlicht, müssen die Exchange- und SharePoint-Server darüber hinaus in der Lage sein, diese Zertifikatsperrliste herunterzuladen.

> [!TIP]
> Mithilfe der folgenden Informationen und Ressourcen können Sie ein Serverauthentifizierungszertifikat anfordern und installieren und dieses Zertifikat an die Standardwebsite in ISS binden:
>
> - Wenn Sie Active Directory-Zertifikatdienste (AD CS) und eine Unternehmenszertifizierungsstelle verwenden, um diese Serverauthentifizierungszertifikate bereitzustellen, können Sie die Webserver-Zertifikatvorlage duplizieren und dann verwenden. Diese Zertifikatvorlage verwendet **Informationen wurden in der Anforderung angegeben** als Zertifikatantragstellernamen, was bedeutet, dass Sie den FQDN des RMS-Verbindungsdienstnamens als Zertifikatnamen für den Zertifikatantragstellernamen oder für den alternativen Antragstellernamen angeben können, wenn Sie das Zertifikat anfordern.
> -   Wenn Sie eine eigenständige Zertifizierungsstelle verwenden oder dieses Zertifikat von einem anderen Unternehmen kaufen, lesen Sie [Konfigurieren von Internetserverzertifikaten (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731977(v=ws.10)) in der Dokumentationsbibliothek von [Webserver (IIS)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10)) auf der TechNet-Website.
> - Informationen zum Konfigurieren von ISS für die Verwendung des Zertifikats finden Sie unter [Hinzufügen einer Bindung zu einer Website (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731692(v=ws.10)) in der Dokumentationsbibliothek von [Webserver (IIS)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10)) auf der TechNet-Website.

## <a name="configuring-the-rms-connector-for-a-web-proxy-server"></a>Konfigurieren des RMS-Connectors für einen Webproxyserver
Wenn die Connector-Server in einem Netzwerk installiert sind, das keine direkte Internetverbindung besitzt und eine manuelle Konfiguration eines Webproxyservers für ausgehenden Internet Zugriff erfordert, müssen Sie die Registrierung auf diesen Servern für den RMS-Verbindungs Dienst konfigurieren.

#### <a name="to-configure-the-rms-connector-to-use-a-web-proxy-server"></a>So konfigurieren Sie den RMS-Connector für die Verwendung eines Webproxyservers

1.  Öffnen Sie auf jedem Server, auf dem der RMS-Connector ausgeführt wird, einen Registrierungs-Editor, z. B. Regedit.

2.  Navigieren Sie zu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  Fügen Sie den Zeichenfolgenwert **ProxyAddress** hinzu, und legen Sie dann die Daten für diesen Wert auf **http://&lt;MeineProxyDomäneOderIPAdresse&gt;:&lt;MeinProxyPort&gt;** fest.

    Beispiel: **http://proxyserver.contoso.com:8080**

4.  Schließen Sie den Registrierungs-Editor, und starten Sie dann den Server neu, oder führen Sie einen IISReset-Befehl aus, um IIS neu zu starten.

## <a name="installing-the-rms-connector-administration-tool-on-administrative-computers"></a>Installieren des Verwaltungstools für den RMS-Connector auf administrativen Computern
Sie können das Verwaltungstool für den RMS-Connector auf einem Computer ausführen, auf dem der RMS-Connector nicht installiert ist, wenn dieser Computer die folgenden Anforderungen erfüllt:

-   Ein physischer oder virtueller Computer, auf dem Windows Server 2019, 2016, 2012 oder Windows Server 2012 R2 (alle Editionen), Windows 10, Windows 8.1 oder Windows 8 ausgeführt wird.

-   Mindestens 1 GB RAM.

-   Mindestens 64 GB Speicherplatz auf dem Datenträger.

-   Mindestens eine Netzwerkschnittstelle.

-   Zugriff auf das Internet über eine Firewall (oder einen Webproxy).

Führen Sie zum Installieren des Verwaltungstools für den RMS-Connector die folgenden Dateien aus:

-   Auf einem 64-Bit-Computer: „RMSConnectorSetup.exe“

Wenn Sie diese Dateien noch nicht heruntergeladen haben, können Sie diese aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=314106) herunterladen.


## <a name="next-steps"></a>Nächste Schritte
Nachdem der RMS-Connector nun installiert und konfiguriert ist, können Sie Ihre lokalen Server für dessen Verwendung konfigurieren. Navigieren Sie zu [Konfigurieren von Servern für den Azure Rights Management-Verbindungsdienst](configure-servers-rms-connector.md).