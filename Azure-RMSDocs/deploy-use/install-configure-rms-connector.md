---
title: "Installieren und Konfigurieren des Rights Management-Connectors – AIP"
description: "Hier erhalten Sie Informationen zum Installieren und Konfigurieren des Connectors von Azure Rights Management (RMS). Diese Verfahren beziehen sich auf die unter „Bereitstellen des Azure Rights Management-Connectors“ beschriebenen Schritte 1 bis 4."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/03/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3e4aabc3c571ca132327748935ab3aeafa002db0
ms.sourcegitcommit: e21fb3385de6f0e251167e5dc973e90f0e7f2bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="installing-and-configuring-the-azure-rights-management-connector"></a>Installieren und Konfigurieren des Azure Rights Management-Connectors

>*Gilt für: Azure Information Protection, Office 365*

Anhand der folgenden Informationen können Sie den Connector von Azure Rights Management (RMS) installieren und konfigurieren. Diese Verfahren beziehen sich auf die unter [Bereitstellen des Azure Rights Management-Connectors](deploy-rms-connector.md) beschriebenen Schritte 1 bis 4.

Stellen Sie vorab sicher, dass Sie die [Voraussetzungen](deploy-rms-connector.md#prerequisites-for-the-rms-connector) für diese Bereitstellung überprüft haben.


## <a name="installing-the-rms-connector"></a>Installieren des RMS-Connectors

1.  Identifizieren Sie die Computer (mindestens zwei), auf denen der RMS-Connector ausgeführt wird. Sie müssen die in den Voraussetzungen aufgeführte Mindestspezifikation erfüllen.

    > [!NOTE]
    > Sie installieren einen einzigen RMS-Connector (bestehend aus mehreren Servern zur Gewährleistung hoher Verfügbarkeit) pro Mandant (Office 365-Mandant oder Azure AD-Mandant). Im Gegensatz zu Active Directory RMS müssen Sie nicht in jeder Gesamtstruktur einen RMS-Connector installieren.

2.  Laden Sie die Quelldateien für den RMS-Connector aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106) herunter.

    Laden Sie zum Installieren des RMS-Connectors die Datei „RMSConnectorSetup.exe“ herunter.

    Berücksichtigen Sie zudem Folgendes:

    -   Wenn Sie den Connector später auf einem 32-Bit-Computer konfigurieren möchten, müssen Sie auch die Datei „RMSConnectorAdminToolSetup_x86.exe“ herunterladen.

    -   Wenn Sie das Serverkonfigurationstool für den RMS-Connector verwenden möchten, um die Konfiguration der Registrierungseinstellungen auf Ihren lokalen Servern zu automatisieren, müssen Sie auch die Komponente „GenConnectorConfig.ps1“ herunterladen.

3.  Führen Sie auf dem Computer, auf dem Sie den RMS-Connector installieren möchten, die Datei **RMSConnectorSetup.exe** mit Administratorrechten aus.

4.  Wählen Sie auf der Willkommensseite für die Installation des Microsoft Rights Management-Connectors die Option **Microsoft Rights Management-Connector auf dem Computer installieren** aus, und klicken Sie dann auf **Weiter**.

5.  Lesen und akzeptieren Sie die Lizenzbedingungen für den RMS-Connector, und klicken Sie dann auf **Weiter**.

Geben Sie zum Fortsetzen des Vorgangs ein Konto und ein Kennwort ein, um den RMS-Connector zu konfigurieren.

## <a name="entering-credentials"></a>Eingeben von Anmeldeinformationen
Bevor Sie den RMS-Connector konfigurieren können, müssen Sie Anmeldeinformationen für ein Konto eingeben, das über ausreichende Berechtigungen zum Konfigurieren des RMS-Connectors verfügt. Sie könnten z. B. **admin@contoso.com** eingeben und dann das Kennwort für dieses Konto angeben.

Für dieses Konto ist keine mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) erforderlich, weil das Microsoft Rights Management-Verwaltungstool keine MFA für dieses Konto unterstützt. 

Für den Connector gelten auch einige Zeicheneinschränkungen für dieses Kennwort. Kennwörter mit einem der folgenden Zeichen dürfen nicht verwendet werden: Kaufmännisches Und-Zeichen (**&**), spitze Klammer links (**[**), spitze Klammer rechts (**]**), gerade Anführungszeichen (**"**) und Apostroph (**'**). Wenn Ihr Kennwort eines dieser Zeichen enthält, schlägt die Authentifizierung für den RMS-Connector fehl, und die Fehlermeldung **Die Kombination aus Benutzername und Kennwort ist nicht korrekt** wird angezeigt, obwohl Sie sich in anderen Szenarien mit diesem Konto und Kennwort erfolgreich anmelden können. Wenn dieses Szenario auf Ihr Kennwort zutrifft, verwenden Sie entweder ein anderes Konto mit einem Kennwort, das keines dieser Sonderzeichen enthält, oder setzen Sie Ihr Kennwort so zurück, dass es keines dieser Sonderzeichen enthält.

Wenn Sie [Onboarding-Steuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) implementiert haben, müssen Sie darüber hinaus sicherstellen, dass das von Ihnen angegebene Konto Inhalte schützen kann. Wenn Sie beispielsweise die Möglichkeit zum Schützen von Inhalten auf die Gruppe „IT-Abteilung“ beschränkt haben, muss das Konto, das Sie hier angeben, ein Mitglied dieser Gruppe sein. Andernfalls wird die folgende Fehlermeldung angezeigt: **Fehler beim Versuch, den Speicherort des Verwaltungsdiensts und der Organisation zu ermitteln. Stellen Sie sicher, dass der Microsoft Rights Management-Dienst für Ihre Organisation aktiviert ist.**

Sie können ein Konto verwenden, das über eine der folgenden Berechtigungen verfügt:

-   **Globaler Administrator für Ihren Mandanten**: Ein Konto, das ein globaler Administrator für Ihren Office 365- oder Azure AD-Mandanten ist.

-   **Globaler Azure Rights Management-Administrator**: Ein Konto in Azure Active Directory, dem die Rolle „Globaler Azure RMS-Administrator“ zugewiesen wurde.

-   **Azure Rights Management-Connectoradministrator**: Ein Konto in Azure Active Directory, dem Rechte zum Installieren und Verwalten des RMS-Connectors für Ihre Organisation erteilt wurden.

    > [!NOTE]
    > Die Rollen „Globaler Azure Rights Management-Administrator“ und „Azure Rights Management-Connectoradministrator“ werden Konten mithilfe des Azure RMS-Cmdlets [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) zugewiesen.
    > 
    > Wenn der RMS-Connector mit den Mindestberechtigungen ausgeführt werden soll, erstellen Sie ein dediziertes Konto für diesen Zweck, dem Sie dann die Rolle „Azure RMS-Connectoradministrator“ zuweisen, indem Sie die folgenden Schritte ausführen:
    >
    > 1.  Wenn Sie dies noch nicht getan haben, laden Sie Windows PowerShell für Rights Management herunter, und installieren Sie die Komponente. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell für Azure Rights Management](install-powershell.md).
    >
    >     Starten Sie Windows PowerShell mit dem Befehl **Als Administrator ausführen**, und stellen Sie mithilfe des Befehls [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice) eine Verbindung mit dem Azure RMS-Dienst her:
    >
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  Führen Sie dann den Befehl [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) mit nur einem der folgenden Parameter aus:
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     Geben Sie z. B. **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"** ein.
    >
    >     Mit diesen Befehlen wird zwar die Rolle „Connectoradministrator“ zugewiesen, Sie könnten hier aber auch die Rolle „Globaler Administrator“ verwenden.

Während der Installation des RMS-Connectors werden alle erforderlichen Softwareanwendungen überprüft und installiert, Internetinformationsdienste (Internet Information Services, IIS) wird installiert, sofern nicht bereits vorhanden, und die Connectorsoftware wird installiert und konfiguriert. Darüber hinaus wird Azure RMS für die Konfiguration vorbereitet, indem Folgendes erstellt wird:

-   Eine leere Tabelle für Server, die autorisiert sind, den Connector für die Kommunikation mit Azure RMS zu verwenden. Sie fügen dieser Tabelle später Server hinzu.

-   Ein Satz von Sicherheitstoken für den Connector, die Vorgänge mit Azure RMS autorisieren. Diese Token werden aus Azure RMS heruntergeladen und auf dem lokalen Computer in der Registrierung installiert. Sie werden mithilfe der Datenschutz-Anwendungsprogrammierschnittstelle (Data Protection Application Programming Interface, DPAPI) und Anmeldeinformationen für das lokale Systemkonto geschützt.

Führen Sie auf der letzten Seite des Assistenten die folgenden Schritte aus, und klicken Sie dann auf **Fertig stellen**:

-   Wenn dies der erste Connector ist, den Sie installiert haben, wählen Sie zu diesem Zeitpunkt noch nicht die Option **Verwaltungskonsole des Connectors zum Autorisieren von Servern starten** aus. Sie wählen diese Option aus, nachdem Sie Ihren zweiten (oder letzten) RMS-Connector installiert haben. Führen Sie stattdessen den Assistenten auf mindestens einem anderen Computer erneut aus. Sie müssen mindestens zwei Connectors installieren.

-   Wenn Sie Ihren zweiten (oder letzten) Connector installiert haben, wählen Sie **Verwaltungskonsole des Connectors zum Autorisieren von Servern starten** aus.

> [!TIP]
> Zu diesem Zeitpunkt gibt es einen Überprüfungstest, den Sie ausführen können, um zu testen, ob die Webdienste für den RMS-Connector funktionieren:
>
> -   Stellen Sie über einen Webbrowser eine Verbindung mit **http://&lt;Connectoradresse&gt;/_wmcs/certification/servercertification.asmx** her, wobei Sie *&lt;Connectoradresse&gt;* durch die Adresse oder den Namen des Servers ersetzen, auf dem der RMS-Connector installiert ist. Bei einer erfolgreichen Verbindung wird eine Seite **ServerCertificationWebService** angezeigt.

Wenn Sie den RMS-Connector deinstallieren müssen, führen Sie den Assistenten erneut aus, und wählen Sie die Option „Deinstallieren“ aus.

Wenn während der Installation Probleme auftreten, überprüfen Sie das Installationsprotokoll: **%LocalAppData%\Temp\Microsoft Rights Management-Connector_\<Datum und Uhrzeit>.log**. 

Ihr Installationsprotokoll könnte beispielsweise wie folgt aussehen: „C:\Benutzer\Administrator\AppData\Local\Temp\Microsoft Rights Management-Connector_20170803110352.log“.

## <a name="authorizing-servers-to-use-the-rms-connector"></a>Autorisieren von Servern für die Verwendung des RMS-Connectors
Wenn Sie den RMS-Connector auf mindestens zwei Computern installiert haben, können Sie die Server und Dienste autorisieren, die den RMS-Connector verwenden sollen. Beispielsweise Server, auf denen Exchange Server 2013 oder SharePoint Server 2013 ausgeführt wird.

Um diese Server zu definieren, führen Sie das Verwaltungstool für den RMS-Connector aus, und fügen Sie der Liste zugelassener Server Einträge hinzu. Sie können dieses Tool ausführen, wenn Sie am Ende des Installations-Assistenten des Microsoft Rights Management-Connectors die Option **Verwaltungskonsole des Connectors zum Autorisieren von Servern starten** auswählen, oder Sie können es separat vom Assistenten ausführen.

Berücksichtigen Sie beim Autorisieren dieser Server die folgenden Aspekte:

- Servern, die Sie hinzufügen, werden besondere Berechtigungen erteilt. Allen Konten, die Sie für die Exchange Server-Rolle in der Konfiguration des Connectors angeben, wird in Azure RMS die [Administratorrolle](configure-super-users.md) zugewiesen, die den Konten Zugriff auf alle Inhalte für diesen RMS-Mandanten gewährt. Die Administratorfunktion wird zu diesem Zeitpunkt bei Bedarf automatisch aktiviert. Um Sicherheitsrisiken durch Rechteerweiterungen zu vermeiden, achten Sie sorgfältig darauf, nur Konten anzugeben, die von den Exchange-Servern Ihrer Organisation verwendet werden. Alle als SharePoint-Server oder Dateiserver konfigurierten Server, die FCI verwenden, erhalten normale Benutzerrechte.

- Sie können mehrere Server als einzelnen Eintrag hinzufügen, indem Sie eine Active Directory-Sicherheits- oder -Verteilergruppe oder ein von mehreren Servern verwendetes Dienstkonto angeben. Bei Verwendung dieser Konfiguration verwendet die Gruppe von Servern gemeinsam dieselben RMS-Zertifikate, und alle werden als Besitzer von Inhalten angesehen, die einer von ihnen geschützt hat. Zur Minimierung des Verwaltungsaufwands empfehlen wir die Verwendung dieser Konfiguration einer Einzelgruppe statt einzelner Server, um die Exchange-Server Ihrer Organisation oder eine SharePoint-Serverfarm zu autorisieren.

Klicken Sie auf der Seite **Server, von denen der Connector verwendet werden darf** auf **Hinzufügen**.

> [!NOTE]
> Das Autorisieren von Servern ist die äquivalente Konfiguration in Azure RMS zur AD RMS-Konfiguration, bei der die NTFS-Rechte auf „ServerCertification.asmx“ für die Dienst- oder Servercomputerkonten manuell angewendet werden und die Administratorrechte den Exchange-Konten manuell zugewiesen werden. Das Anwenden von NTFS-Rechten auf „ServerCertification.asmx“ ist für den Connector nicht erforderlich.


### <a name="add-a-server-to-the-list-of-allowed-servers"></a>Hinzufügen eines Servers zur Liste zugelassenen Server
Geben Sie auf der Seite **Zulassen, dass der Connector von einem Server verwendet werden darf** den Namen des Objekts ein, oder suchen Sie nach dem zu autorisierenden Objekt.

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

Wenn Sie der Liste alle gewünschten Server hinzugefügt haben, klicken Sie auf **Schließen**.

Wenn Sie dies nicht bereits getan haben, müssen Sie jetzt den Lastenausgleich für die Server konfigurieren, auf denen der RMS-Connector installiert ist, und überlegen, ob HTTPS für die Verbindungen zwischen diesen Servern und den Servern verwendet werden soll, die Sie gerade autorisiert haben.

## <a name="configuring-load-balancing-and-high-availability"></a>Konfigurieren von Lastausgleich und hoher Verfügbarkeit
Definieren Sie nach der Installation der zweiten oder letzten Instanz des RMS-Connectors einen Connector-URL-Servernamen, und konfigurieren Sie ein Lastenausgleichssystem.

Der Connector-URL-Servername kann ein beliebiger Name unter einem Namespace sein, der von Ihnen gesteuert wird. Sie können z. B. in Ihrem DNS-System einen Eintrag für **rmsconnector.contoso.com** erstellen und diesen Eintrag für die Verwendung einer IP-Adresse in Ihrem Lastenausgleichssystem konfigurieren. Für diesen Namen gibt es keine besonderen Anforderungen, und er muss nicht auf den Connector-Servern konfiguriert werden. Wenn Ihre Exchange- und SharePoint-Server nicht über das Internet mit dem Connector kommunizieren, muss dieser Name im Internet nicht aufgelöst werden können.

> [!IMPORTANT]
> Wir empfehlen Ihnen, diesen Namen nach der Konfiguration von Exchange- oder SharePoint-Servern für die Verwendung des Connectors nicht mehr zu ändern, weil Sie ansonsten alle IRM-Konfigurationen auf diesen Servern löschen und diese dann neu konfigurieren müssen.

Nachdem der Name in DNS erstellt und für eine IP-Adresse konfiguriert wurde, konfigurieren Sie den Lastenausgleich für diese Adresse, die den Datenverkehr an die Connector-Server leitet. Sie können zu diesem Zweck jedes IP-basierte Lastenausgleichsmodul verwenden, das den Netzwerklastenausgleich (Network Load Balancing, NLB) von Windows Server enthält. Weitere Informationen finden Sie unter [Lastenausgleich – Bereitstellungsleitfaden](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx).

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
> -   Wenn Sie Active Directory-Zertifikatdienste (AD CS) und eine Unternehmenszertifizierungsstelle verwenden, um diese Serverauthentifizierungszertifikate bereitzustellen, können Sie die Webserver-Zertifikatvorlage duplizieren und dann verwenden. Diese Zertifikatvorlage verwendet **Informationen wurden in der Anforderung angegeben** als Zertifikatantragstellernamen, was bedeutet, dass Sie den FQDN des RMS-Connectornamens für den Zertifikatantragstellernamen oder für den alternativen Antragstellernamen angeben können, wenn Sie das Zertifikat anfordern.
> -   Wenn Sie eine eigenständige Zertifizierungsstelle verwenden oder dieses Zertifikat von einem anderen Unternehmen kaufen, lesen Sie [Konfigurieren von Internetserverzertifikaten (IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) in der Dokumentationsbibliothek von [Webserver (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) auf der TechNet-Website.
> -   Informationen zum Konfigurieren von ISS für die Verwendung des Zertifikats finden Sie unter [Hinzufügen einer Bindung zu einer Website (IIS 7)](http://technet.microsoft.com/library/cc731692.aspx) in der Dokumentationsbibliothek von [Webserver (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) auf der TechNet-Website.

## <a name="configuring-the-rms-connector-for-a-web-proxy-server"></a>Konfigurieren des RMS-Connectors für einen Webproxyserver
Wenn Ihre Connector-Server in einem Netzwerk installiert sind, das keine direkte Internetverbindung besitzt und eine manuelle Konfiguration eines Webproxyservers für ausgehenden Internetzugriff erfordert, müssen Sie die Registrierung auf diesen Servern für den RMS-Connector konfigurieren.

#### <a name="to-configure-the-rms-connector-to-use-a-web-proxy-server"></a>So konfigurieren Sie den RMS-Connector für die Verwendung eines Webproxyservers

1.  Öffnen Sie auf jedem Server, auf dem der RMS-Connector ausgeführt wird, einen Registrierungs-Editor, z. B. Regedit.

2.  Navigieren Sie zu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**.

3.  Fügen Sie den Zeichenfolgenwert **ProxyAddress** hinzu, und legen Sie dann die Daten für diesen Wert auf **http://&lt;MeineProxyDomäneOderIPAdresse&gt;:&lt;MeinProxyPort&gt;** fest.

    Beispiel: **http://proxyserver.contoso.com:8080**

4.  Schließen Sie den Registrierungs-Editor, und starten Sie dann den Server neu, oder führen Sie einen IISReset-Befehl aus, um IIS neu zu starten.

## <a name="installing-the-rms-connector-administration-tool-on-administrative-computers"></a>Installieren des Verwaltungstools für den RMS-Connector auf administrativen Computern
Sie können das Verwaltungstool für den RMS-Connector auf einem Computer ausführen, auf dem der RMS-Connector nicht installiert ist, wenn dieser Computer die folgenden Anforderungen erfüllt:

-   Ein physischer oder virtueller Computer unter Windows Server 2012 oder Windows Server 2012 R2 (alle Editionen), Windows Server 2008 R2 oder Windows Server 2008 R2 Service Pack 1 (alle Editionen), Windows 8.1, Windows 8 oder Windows 7.

-   Mindestens 1 GB RAM.

-   Mindestens 64 GB Speicherplatz auf dem Datenträger.

-   Mindestens eine Netzwerkschnittstelle.

-   Zugriff auf das Internet über eine Firewall (oder einen Webproxy).

Führen Sie zum Installieren des Verwaltungstools für den RMS-Connector die folgenden Dateien aus:

-   Auf einem 32-Bit-Computer: „RMSConnectorAdminToolSetup_x86.exe“

-   Auf einem 64-Bit-Computer: „RMSConnectorSetup.exe“

Wenn Sie diese Dateien noch nicht heruntergeladen haben, können Sie diese aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106) herunterladen.


## <a name="next-steps"></a>Nächste Schritte
Nachdem der RMS-Connector nun installiert und konfiguriert ist, können Sie Ihre lokalen Server für dessen Verwendung konfigurieren. Navigieren Sie zu [Konfigurieren von Servern für den Azure Rights Management-Verbindungsdienst](configure-servers-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
