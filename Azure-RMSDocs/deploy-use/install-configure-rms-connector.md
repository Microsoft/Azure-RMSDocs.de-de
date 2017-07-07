---
title: "Installieren und Konfigurieren des Rights Management-Connectors – AIP"
description: "Informationen zur Unterstützung bei der Installation und Konfiguration des RMS-Connectors (Azure Rights Management). Diese Verfahren beziehen sich auf die Schritte 1 bis 4 unter „Bereitstellen des Azure Rights Management-Connectors“."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d03cb1ff146839e4de805b66f5b2e6a3df851430
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="installing-and-configuring-the-azure-rights-management-connector"></a>Installieren und Konfigurieren des Azure Rights Management-Verbindungsdiensts

>*Gilt für: Azure Information Protection, Office 365*

Verwenden Sie folgende Informationen als Hilfestellung bei des Installation und Konfiguration der Azure Rights Management (RMS)-Verbindungsdiensts. Diese Verfahren beziehen sich auf die Schritte 1 bis 4 unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

Lesen und erfüllen Sie vor Beginn unbedingt die [Voraussetzungen](deploy-rms-connector.md#prerequisites-for-the-rms-connector) für diese Bereitstellung.


## <a name="installing-the-rms-connector"></a>Installieren des RMS-Verbindungsdiensts

1.  Identifizieren Sie die Computer (mindestens zwei), auf denen der RMS-Verbindungsdienst ausgeführt werden soll. Sie müssen die in den Voraussetzungen aufgeführte Mindestspezifikation erfüllen.

    > [!NOTE]
    > Sie installieren einen einzelnen RMS-Verbindungsdienst (bestehend aus mehreren Servern zwecks hoher Verfügbarkeit) pro Mandant (Office 365-Mandant oder Azure AD-Mandant). Im Gegensatz zu Active Directory RMS müssen Sie nicht in jeder Gesamtstruktur einen RMS-Verbindungsdienst installieren.

2.  Laden Sie die Quelldateien für den RMS-Connector aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106)herunter.

    Laden Sie zum Installieren des RMS-Verbindungsdiensts die Datei „RMSConnectorSetup.exe“ herunter.

    Zusätzlich:

    -   Wenn Sie den Verbindungsdienst später von einem 32-Bit-Computer aus konfigurieren möchten, laden Sie auch „RMSConnectorAdminToolSetup_x86.exe“ herunter.

    -   Wenn Sie das Serverkonfigurationstool für den RMS-Verbindungsdienst verwenden möchten, um die Konfiguration von Registrierungseinstellungen auf Ihren lokalen Servern zu automatisieren, laden Sie außerdem „GenConnectorConfig.ps1“ herunter.

3.  Führen Sie auf dem Computer, auf dem Sie den RMS-Verbindungsdienst installieren möchten, **RMSConnectorSetup.exe** mit Administratorrechten aus.

4.  Wählen Sie auf der Begrüßungsseite des Installations-Assistenten des Microsoft Rights Management-Verbindungsdiensts **Microsoft Rights Management-Verbindungsdienst auf dem Computer installieren**, und klicken Sie dann auf **Weiter**.

5.  Lesen und akzeptieren Sie die Lizenzbedingungen des RMS-Verbindungsdiensts, und klicken Sie dann auf **Weiter**.

Geben Sie zum Fortfahren ein Konto und ein Kennwort zum Konfigurieren des RMS-Verbindungsdiensts ein.

## <a name="entering-credentials"></a>Eingeben von Anmeldeinformationen
Bevor Sie den RMS-Verbindungsdienst konfigurieren können, müssen Sie Anmeldeinformationen für ein Konto eingeben, das über ausreichende Rechte zum Konfigurieren des RMS-Verbindungsdiensts verfügt. Beispielsweise könnten Sie **admin@contoso.com** eingeben und dann das Kennwort für dieses Konto angeben.

Es gibt einige Zeicheneinschränkungen für dieses Kennwort. Kennwörter dürfen keines der folgenden Zeichen enthalten: kaufmännisches Und-Zeichen ( **&** ), öffnende eckige Klammer ( **[** ), schließende eckige Klammer ( **]** ), gerade Anführungszeichen ( **"** ) und Apostroph ( **'** ). Enthält Ihr Passwort eines dieser Zeichen, schlägt die Authentifizierung für den RMS-Connector fehl, und es wird die Fehlermeldung **Die Kombination aus Benutzername und Kennwort ist nicht korrekt** angezeigt, auch wenn Sie sich in anderen Zusammenhängen erfolgreich mit diesem Konto und Kennwort anmelden können. Trifft dies auf Ihr Kennwort zu, verwenden Sie entweder ein anderes Konto mit einem Kennwort, das keines dieser Sonderzeichen enthält, oder setzen Sie Ihr Kennwort zurück, sodass es keines dieser Sonderzeichen enthält.

Außerdem müssen Sie, wenn Sie [Onboarding-Steuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) implementiert haben, sicherstellen, dass das von Ihnen angegebene Konto Inhalte schützen kann. Wenn Sie beispielsweise die Fähigkeit, Inhalte zu schützen, auf der Gruppe „IT-Abteilung“ beschränkt haben, muss das hier angegebene Konto ein Mitglied dieser Gruppe sein Andernfalls wird folgende Fehlermeldung angezeigt: **Fehler beim Versuch, den Speicherort des Verwaltungsdiensts und der Organisation zu ermitteln. Stellen Sie sicher, dass der Microsoft Rights Management Service für Ihre Organisation aktiviert ist.**

Sie können ein Konto verwenden, das eins der folgenden Rechte besitzt:

-   **Globaler Administrator für Ihren Mandanten**: ein Konto, das ein globaler Administrator für Ihren Office 365- oder Azure AD-Mandanten ist.

-   **Globaler Azure Rights Management-Administrator**: ein Konto in Azure Active Directory, dem die Azure RMS-Rolle „GlobalAdministrator“zugewiesen wurde.

-   **Azure Rights Management-Connectoradministrator**: ein Konto in Azure Active Directory, dem Rechte zum Installieren und Verwalten des RMS-Connectors für Ihre Organisation gewährt wurden.

    > [!NOTE]
    > Die Azure Rights Management-Rollen „GlobalAdministrator“ und „ConnectorAdministrator“ werden mithilfe des Azure RMS-Cmdlets [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) Konten zugewiesen.
    > 
    > Erstellen Sie zum Ausführen des RMS-Connectors mit geringstmöglichen Berechtigungen ein dediziertes Konto für diesen Zweck, dem Sie anschließend wie folgt die Azure RMS-Rolle „ConnectorAdministrator“ zuweisen:
    >
    > 1.  Falls noch nicht geschehen, müssen Sie Windows PowerShell für Azure Rights Management herunterladen und installieren. Weitere Informationen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).
    >
    >     Starten Sie Windows PowerShell mit dem Befehl **Als Administrator ausführen**, und stellen Sie mithilfe des Befehls [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice) eine Verbindung mit dem Azure RMS-Dienst her:
    >
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  Führen Sie dann mit nur einem der folgenden Parameter den Befehl [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) aus:
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
    >     Geben Sie beispielsweise Folgendes ein: **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"**
    >
    >     Obwohl diese Befehle die Rolle „ConnectorAdministrator“ verwenden, könnten Sie hier ebenfalls die Rolle „GlobalAdministrator“ verwenden.

Während der Installation des RMS-Connectors werden alle Softwarevoraussetzungen überprüft und installiert, Internetinformationsdienste (IIS) wird installiert, falls noch nicht vorhanden, und die Conector-Software wird installiert und konfiguriert. Darüber hinaus wird Azure RMS für die Konfiguration vorbereitet, indem Folgendes erstellt wird:

-   Eine leere Tabelle für Server, die autorisiert sind, den Connector dazu zu verwenden, mit RMS zu kommunizieren. Dieser Tabelle fügen Sie später Server hinzu.

-   Eine Reihe von Sicherheitstoken für den Connector, die Vorgänge mit Azure RMS autorisieren. Diese Token werden aus Azure RMS heruntergeladen und auf dem lokalen Computer in der Registrierung installiert. Sie werden geschützt, indem die Datenschutz-API (DPAPI) und die Anmeldeinformationen des Kontos „Lokales System“ verwendet werden.

Führen Sie auf der letzten Seite des Assistenten Folgendes durch, und klicken Sie dann auf **Fertig stellen**:

-   Wenn dies der erste Verbindungsdienst ist, den Sie installiert haben, aktivieren Sie dabei noch nicht **Verbindungsdienst-Administratorkonsole zum Autorisieren von Servern starten** . Diese Option wird aktiviert, nachdem Sie Ihren zweiten (oder letzten) RMS-Verbindungsdienst installiert haben. Führen Sie stattdessen den Assistenten erneut auf mindestens einem weiteren Computer aus. Sie müssen mindestens zwei Verbindungsdienste installieren.

-   Wenn Sie Ihren zweiten (oder letzten) Verbindungsdienst installiert haben, aktivieren Sie **Verbindungsdienst-Administratorkonsole zum Autorisieren von Servern starten**.

> [!TIP]
> Zu diesem Zeitpunkt gibt es einen Überprüfungstest, den Sie ausführen können, um zu testen, ob die Webdienste für den RMS-Verbindungsdienst funktionieren:
>
> -   Stellen Sie aus einem Webbrowser heraus eine Verbindung zu **http://&lt;Connectoradresse&gt;/_wmcs/certification/servercertification.asmx** her, wobei Sie *&lt;Connectoradresse&gt;* durch die Adresse oder den Namen des Servers ersetzen, auf dem der RMS-Connector installiert ist. Bei einer erfolgreichen Verbindung wird eine Seite **ServerCertificationWebService** angezeigt.

Wenn Sie den RMS-Verbindungsdienst deinstallieren müssen, führen Sie den Assistenten erneut aus, und wählen Sie die Option „Deinstallieren“ aus.

## <a name="authorizing-servers-to-use-the-rms-connector"></a>Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts
Wenn Sie den RMS-Verbindungsdienst auf mindestens zwei Computern installiert haben, können Sie die Server und Dienste autorisieren, die den RMS-Verbindungsdienst verwenden sollen. Beispielsweise Server, die Exchange Server 2013 oder SharePoint Server 2013 ausführen.

Um diese Server zu definieren, führen Sie das Administrationstool des RMS-Verbindungsdiensts aus, und fügen Sie der Liste zugelassener Server Einträge hinzu. Sie können dieses Tool ausführen, wenn Sie am Ende des Installations-Assistenten des Microsoft Rights Management-Verbindungsdiensts **Verbindungsdienst-Administratorkonsole zum Autorisieren von Servern starten** auswählen, oder Sie führen ihn gesondert aus dem Assistenten heraus aus.

Bedenken Sie Folgendes, wenn Sie diese Server autorisieren:

-   Server, die Sie hinzufügen, erhalten spezielle Rechte. Allen Konten, die Sie für die Exchange Server-Rolle in der Verbindungsdienstkonfiguration angeben, wird die [Administratorrolle](configure-super-users.md) in Azure RMS gewährt. Sie erhalten dadurch Zugriff auf alle Inhalte für diesen RMS-Mandanten. Die Administratorfunktion wird zu diesem Zeitpunkt bei Bedarf automatisch aktiviert. Um Sicherheitsrisiken durch Rechteerweiterungen zu vermeiden, müssen Sie darauf achten, nur Konten anzugeben, die von den Exchange-Servern Ihrer Organisation verwendet werden. Alle als SharePoint-Server oder Dateiserver, die FCI verwenden, konfigurierten Server erhalten normale Benutzerrechte.

-   Sie können mehrere Server als einzelnen Eintrag hinzufügen, indem Sie eine Active Directory-Sicherheits- oder -Verteilergruppe angeben oder ein Dienstkonto, das von mehr als einem Server verwendet wird. Wenn Sie diese Konfiguration verwenden, verwendet diese Gruppe von Servern gemeinsam dieselben RMS-Zertifikate, und alle werden als Besitzer von Inhalten angesehen, die einer von ihnen geschützt hat. Um den Verwaltungsaufwand zu minimieren, empfehlen wir, dass Sie diese Konfiguration einer Einzelgruppe statt einzelner Server verwenden, um die Exchange-Server Ihrer Organisation oder eine SharePoint-Serverfarm zu autorisieren.

Klicken Sie auf der Seite **Zur Verwendung des Verbindungsdiensts berechtigte Server** auf **Hinzufügen**.

> [!NOTE]
> Zum Autorisieren von Servern wird in Azure RMS und AD RMS die gleiche Konfiguration verwendet, bei der NTFS-Rechte manuell auf ServerCertification.asmx für die Dienst- oder Servercomputerkonten angewendet und den Exchange-Konten manuell Administratorrechte erteilt werden. Für den Verbindungsdienst müssen keine NTFS-Rechte auf ServerCertification.asmx angewendet werden.


### <a name="add-a-server-to-the-list-of-allowed-servers"></a>Hinzufügen eines Servers zur Liste der zugelassenen Server
Geben Sie auf der Seite **Einem Server die Nutzung des Verbindungsdiensts gestatten** den Namen des Objekts ein, oder durchsuchen Sie, um das zu autorisierende Objekt zu identifizieren.

Es ist wichtig, dass Sie das richtige Objekt autorisieren. Für einen Server muss, damit er den Verbindungsdienst verwenden kann, das Konto zur Autorisierung ausgewählt werden, von dem der lokale Dienst (z. B. Exchange oder SharePoint) ausgeführt wird. Wenn der Dienst beispielsweise als konfiguriertes Dienstkonto ausgeführt wird, fügen Sie der Liste den Namen dieses Dienstkontos hinzu. Wenn der Dienst als „Lokales System“ ausgeführt wird, fügen Sie den Namen des Computerobjekts (z. B. SERVERNAME$) hinzu. Asl bewährte Methode erstellen Sie eine Gruppe, die diese Konten enthält, und geben Sie anstelle einzelner Servernamen die Gruppe an.

Weitere Informationen zu den verschiedenen Serverrollen:

-   Für Server, die Exchange ausführen: Sie müssen eine Sicherheitsgruppe angeben, und Sie können die Standardgruppe verwenden (**Exchange-Server**), die von Exchange automatisch erstellt und für alle Exchange-Server in der Gesamtstruktur gepflegt wird.

-   Für Server, die SharePoint ausführen:

    -   Wenn ein SharePoint 2010-Server für die Ausführung als lokales System (es wird kein Dienstkonto verwendet) konfiguriert ist, erstellen Sie manuell eine Sicherheitsgruppe in Active Directory Domain Services, und fügen Sie das Computernamensobjekt für den Server in dieser Konfiguration zu dieser Gruppe hinzu.

    -   Wenn ein SharePoint-Server für die Verwendung eines Dienstkontos konfiguriert ist (empfohlen für SharePoint 2010 und die einzige Option für SharePoint 2016 und SharePoint 2013), gehen Sie folgendermaßen vor:

        1.  Fügen Sie das Dienstkonto, das den SharePoint-Zentraladministrationsdienst ausführt, hinzu, damit SharePoint über sein Administratorkonsole konfiguriert werden kann.

        2.  Fügen Sie das Konto hinzu, das für den SharePoint-App-Pool konfiguriert ist.

        > [!TIP]
        > Wenn diese zwei Konten unterschiedlich sind, sollten Sie in Betracht ziehen, eine einzelne Gruppe zu erstellen, die beide Konten enthält, um den Verwaltungsaufwand zu minimieren.

-   Für Dateiserver, die die Dateiklassifizierungsinfrastruktur verwenden, werden die zugeordneten Dienste unter dem Konto „Lokales System“ ausgeführt, sodass Sie das Computerkonto für die Dateiserver (z. B. SERVERNAME$) oder eine Gruppe, die diese Computerkonten enthält, autorisieren müssen.

Wenn Sie mit dem Hinzufügen von Servern zu der Liste fertig sind, klicken Sie auf **Schließen**.

Wenn nicht schon geschehen, müssen Sie jetzt den Lastenausgleich für die Server konfigurieren, auf denen der RMS-Verbindungsdienst installiert ist, und erwägen, ob HTTPS für die Verbindungen zwischen diesen Servern und den Servern, die Sie gerade autorisiert haben, verwendet werden soll.

## <a name="configuring-load-balancing-and-high-availability"></a>Konfigurieren von Lastenausgleich und Hochverfügbarkeit
Nachdem Sie die zweite oder letzte Instanz des RMS-Verbindungsdiensts installiert haben, definieren Sie einen Verbindungsdienst-URL-Servernamen, und konfigurieren Sie ein Lastenausgleichssystem.

Der Verbindungsdienst-URL-Servername kann ein beliebiger Name unter einem Namespace sein, den Sie kontrollieren. Beispielsweise können Sie in Ihrem DNS-System einen Eintrag für **rmsconnector.contoso.com** erstellen und diesen Eintrag für die Verwendung einer IP-Adresse in Ihrem Lastenausgleichssystem konfigurieren. Es gibt keine speziellen Anforderungen an diesen Namen, und er muss nicht auf den Verbindungsdienstservern selber konfiguriert werden. Wenn Ihre Exchange- und SharePoint-Server mit dem Verbindungsdienst nicht über das Internet kommunizieren, muss dieser Name im Internet nicht aufgelöst werden können.

> [!IMPORTANT]
> Wir empfehlen Ihnen, diesen Namen nach der Konfiguration von Exchange- oder SharePoint-Servern für die Verwendung des Verbindungsdiensts nicht mehr zu ändern, weil Sie sonst von diesen Servern alle IRM-Konfigurationen entfernen und diese dann neu konfigurieren müssen.

Nachdem der Name in DNS erstellt und für eine IP-Adresse konfiguriert ist, konfigurieren Sie den Lastenausgleich für diese Adresse, die Datenverkehr an die Verbindungsdienstserver leitet. Sie können jedes IP-basierte Lastenausgleichsmodul verwenden, das das NLB-Feature (Network Load Balancing) von Windows Server enthält. Weitere Informationen finden Sie im [Bereitstellungshandbuch für den Lastenausgleich](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx).

Verwenden Sie folgende Einstellungen, um den NLB-Cluster zu konfigurieren:

-   Ports: 80 (für HTTP) oder 443 (für HTTPS)

    Weitere Informationen dazu, ob Sie HTTP oder HTTPS verwenden sollten, finden Sie im nächsten Abschnitt.

-   Affinität: Keine

-   Verteilungsmethode: Gleich

Dieser Name, den Sie für das System mit Lastenausgleich (für die Server mit dem RMS-Verbindungsdienst) definieren, ist der RMS-Verbindungsdienstname Ihrer Organisation, den Sie später beim Konfigurieren der lokalen Server zur Verwendung von Azure RMS verwenden.

## <a name="configuring-the-rms-connector-to-use-https"></a>Konfigurieren des RMS-Verbindungsdiensts für die Verwendung von HTTPS
> [!NOTE]
> Dieser Konfigurationsschritt ist optional, wird aber für zusätzliche Sicherheit empfohlen.

Obgleich die Verwendung von TLS oder SSL für den RMS-Verbindungsdienst optional ist, empfehlen wir es für jeden HTTP-basierten, sicherheitsrelevanten Dienst. Diese Konfiguration authentifiziert die Server, auf denen der Verbindungsdienst ausgeführt wird, gegenüber Ihren Exchange- und SharePoint-Servern, die den Verbindungsdienst verwenden. Zusätzlich werden alle Daten, die von diesen Servern an den Verbindungsdienst gesendet werden, verschlüsselt.

Um den RMS-Verbindungsdienst für die Verwendung von TLS zu aktivieren, installieren Sie auf jedem Server, auf dem der RMS-Verbindungsdienst ausgeführt wird, ein Serverauthentifizierungszertifikat, das den Namen enthält, den Sie für den Verbindungsdienst verwenden werden. Wenn der von Ihnen in DNS definierte RMS-Verbindungsdienstname beispielsweise **rmsconnector.contoso.com** lautet, stellen Sie ein Serverauthentifizierungszertifikat bereit, das **rmsconnector.contoso.com** als allgemeinen Namen für den Zertifikatantragsteller enthält. Oder geben Sie**rmsconnector.contoso.com** als DNS-Wert für den alternativen Zertifikatnamen an. Das Zertifikat muss den Namen des Servers nicht enthalten. Binden Sie dann in IIS dieses Zertifikat an die Standardwebsite.

Wenn Sie die HTTPS-Option verwenden, stellen Sie sicher, dass alle Server, auf denen der Verbindungsdienst ausgeführt wird, ein gültiges Authentifizierungszertifikat besitzen, das bis zu einer Stammzertifizierungsstelle verkettet ist, zu der Ihre Exchange- und SharePoint-Server eine Vertrauensstellung haben. Darüber hinaus müssen die Exchange- und SharePoint-Server, wenn die Zertifizierungstelle, die die Zertifikate für die Verbindungsdienstserver ausgestellt hat, eine Zertifikatsperrliste veröffentlicht, in der Lage sein, diese Zertifikatsperrliste herunterzuladen.

> [!TIP]
> Sie können mithilfe folgender Informationen und Ressourcen ein Serverauthentifizierungszertifikat anfordern und installieren und dieses Zertifikat an die Standardwebsite in ISS binden:
>
> -   Wenn Sie die Active Directory-Zertifikatdienste (AD CS) und eine Unternehmenszertifizierungsstelle verwenden, um diese Serverauthentifizierungszertifikate bereitzustellen, können Sie die Webserver-Zertifikatvorlage duplizieren und dann verwenden. Diese Zertifikatvorlage verwendet **Informationen wurden in der Anforderung angegeben** als Zertifikatantragstellernamen, was bedeutet, dass Sie den FQDN des RMS-Verbindungsdienstnamens als Zertifikatnamen für den Zertifikatantragstellernamen oder für den alternativen Antragstellernamen angeben können, wenn Sie das Zertifikat anfordern.
> -   Wenn Sie eine eigenständige Zertifizierungsstelle verwenden oder dieses Zertifikat von einer anderen Firma kaufen, finden Sie hierzu Informationen unter [Konfigurieren von Internetserverzertifikaten (IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) in der [Webserver (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx)-Dokumentationsbibliothek in TechNet.
> -   Informationen zum Konfigurieren von IIS für die Verwendung des Zertifikats finden Sie unter [Eine Bindung zu einer Website (IIS 7) hinzufügen](http://technet.microsoft.com/library/cc731692.aspx) in der [Webserver (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) -Dokumentationsbibliothek in TechNet.

## <a name="configuring-the-rms-connector-for-a-web-proxy-server"></a>Konfigurieren des RMS-Verbindungsdiensts für einen Webproxyserver
Wenn Ihre Verbindungsdienstserver in einem Netzwerk installiert sind, das keine direkte Internetverbindung besitzt und eine manuelle Konfiguration eines Webproxyservers für ausgehenden Internetzugriff erfordert, müssen Sie die Registrierung auf diesen Servern für den RMS-Verbindungsdienst konfigurieren.

#### <a name="to-configure-the-rms-connector-to-use-a-web-proxy-server"></a>So konfigurieren Sie den RMS-Verbindungsdienst für die Verwendung eines Webproxyservers

1.  Öffnen Sie auf jedem Server, auf dem der RMS-Verbindungsdienst ausgeführt wird, einen Registrierungs-Editor, z. B. Regedit.

2.  Navigieren Sie zu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**.

3.  Fügen Sie den Zeichenfolgenwert **ProxyAddress** hinzu, und legen Sie anschließend die Daten für diesen Wert auf **http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;** fest.

    Beispiel: **http://proxyserver.contoso.com:8080**

4.  Schließen Sie den Registrierungs-Editor, und starten Sie den Server neu, oder führen Sie einen IISReset-Befehl aus, um IIS neu zu starten.

## <a name="installing-the-rms-connector-administration-tool-on-administrative-computers"></a>Installieren des Administrationstool des RMS-Verbindungsdiensts auf administrativen Computern
Sie können das Verwaltungstool des RMS-Verbindungsdiensts auf einem Computer ausführen, auf dem der RMS-Verbindungsdienst nicht installiert ist, wenn dieser Computer folgende Anforderungen erfüllt:

-   Ein physischer oder virtueller Computer, auf dem Windows Server 2012 oder Windows Server 2012 R2 (alle Editionen), Windows Server 2008 R2 oder Windows Server 2008 R2 Service Pack 1 (alle Editionen), Windows 8.1, Windows 8 oder Windows 7 ausgeführt wird.

-   Mindestens 1 GB RAM.

-   Mindestens 64 GB Datenträgerspeicherplatz.

-   Mindestens eine Netzwerkschnittstelle.

-   Zugriff auf das Internet durch eine Firewall (oder einen Webproxy).

Führen Sie zum Installieren des Administrationstool des RMS-Verbindungsdiensts folgende Dateien aus:

-   Für einen 32-Bit-Computer: RMSConnectorAdminToolSetup_x86.exe

-   Für einen 64-Bit-Computer: RMSConnectorSetup.exe

Wenn Sie diese Dateien noch nicht heruntergeladen haben, können Sie dies im [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106)tun.


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den RMS-Verbindungsdienst installiert und konfiguriert haben, können Sie die lokalen Server für dessen Verwendung konfigurieren. Gehen Sie zu [Konfigurieren von Servern für den Azure Rights Management-Verbindungsdienst](configure-servers-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]