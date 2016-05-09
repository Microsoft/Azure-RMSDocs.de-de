---
title: TEST: Voraussetzungen für Azure Rights Management
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: TEST
author: Cabailey
---
# ZUVOR: Voraussetzungen für Azure Rights Management
Für die Bereitstellung von Azure Rights Management (RMS) in Ihrer Organisation müssen die folgenden Voraussetzungen erfüllt sein. Anschließend können Sie Rights Management mithilfe der [Roadmap für die Bereitstellung von Rights Management](deployment-roadmap.md) für Ihre Organisation bereitstellen.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Cloud-Abonnement für RMS|Ihre Organisation muss ein Cloud-Abonnement besitzen, das RMS unterstützt.<br /><br />Weitere Informationen zur Lizenzierung finden Sie im Abschnitt [Cloudabonnements, die Azure RMS unterstützen](requirements-azure-rms.md#BKMK_SupportedSubscriptions) in diesem Thema.|
|Azure AD-Verzeichnis|Ihre Organisation muss ein Azure AD-Verzeichnis besitzen, um die Benutzerauthentifizierung für RMS zu unterstützen. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.<br /><br />Multi-Factor Authentication (MFA) wird mit Azure RMS unterstützt, wenn Sie die erforderliche Clientsoftware haben und die für MFA erforderliche unterstützende Infrastruktur ordnungsgemäß konfiguriert haben.<br /><br />Weitere Informationen finden Sie in diesem Thema im Abschnitt [Azure AD-Verzeichnis](requirements-azure-rms.md#BKMK_AzureADTenant).|
|Clientgeräte|Benutzer müssen Clientgeräte (Computer oder mobile Geräte) besitzen, die ein Betriebssystem ausführen, das RMS unterstützt.<br /><br />Weitere Informationen finden Sie im Abschnitt [Clientgeräte, die Azure RMS unterstützen](requirements-azure-rms.md#BKMK_SupportedDevices) in diesem Thema.|
|Applications|Benutzer müssen Anwendungen ausführen, die RMS unterstützen.<br /><br />Weitere Informationen finden Sie im Abschnitt [Anwendungen, die Azure RMS unterstützen](requirements-azure-rms.md#BKMK_SupportedApplications) in diesem Thema.|
|Infrastruktur, die Verbindungen mit dem Internet und abhängige Cloud-Dienste unterstützt|Wenn Sie eine Firewall oder ähnliche Interventionsnetzwerkgeräte verwenden, die so konfiguriert werden müssen, dass bestimmte Verbindungen erlaubt sind, lesen Sie [Office 365-URLs und IP-Adressbereiche](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Die Liste der URLs und IP-Adressen im Abschnitt **Office 365-Portal und -Identität** gilt für das Office 365-Portal, für Azure Active Directory-Ressourcen und für Azure Rights Management. Verwenden Sie die Anleitungen in diesem Artikel, um bei Änderungen an diesen Informationen auf dem neuesten Stand zu bleiben, indem Sie einen RSS-Feed abonnieren.<br /><br />Zusätzlich zu den Informationen im Office-Artikel, spezifisch für Azure RMS:<br /><br />Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z. B. zur Durchführung von Überprüfungen auf Paketebene). Wenn Sie dies tun, wird die Anheftung von Zertifikaten unterbrochen, die RMS-Clients mit von Microsoft verwalteten Zertifizierungsstellen verwenden, um ihre Kommunikation mit Azure RMS zu sichern.<br /><br />Verwenden Sie keine Webproxykonfiguration, die im Auftrag eines Benutzers authentifiziert.|

Wenn Sie Azure RMS mit lokalen Servern verwenden möchten, werden folgende Produkte unterstützt:

-   Exchange Server

-   SharePoint Server

-   Windows Server-Dateiserver, die die Dateiklassifizierungsinfrastruktur unterstützen.

Informationen zu den zusätzlichen Voraussetzungen für Azure RMS für dieses Szenario finden Sie in diesem Thema im Abschnitt [Lokale Server, die Azure RMS unterstützen](requirements-azure-rms.md#BKMK_SupportedServers).

> [!IMPORTANT]
> Das folgende Bereitstellungsszenario wird nicht unterstützt:
> 
> -   Parallele Ausführung von AD RMS und Azure RMS in derselben Organisation (mit Ausnahme der Migration), wie unter [Migration von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) beschrieben.
> 
> Es gibt einen unterstützten Migrationspfad von [AD RMS zu Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx) und von [Azure RMS zu AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Wenn Sie Azure RMS bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](decommission-deactivate.md).

Verwenden Sie die folgenden Abschnitte, um mehr über die Voraussetzungen für Azure RMS zu erfahren.

## <a name="BKMK_SupportedSubscriptions"></a>Cloud-Abonnements, die Azure RMS unterstützen
Um Azure RMS zu verwenden, muss die Organisation mindestens eines der folgenden Abonnements mit einer ausreichenden Anzahl von Lizenzen für Benutzer und Dienste besitzen, die E-Mail-Nachrichten und Dateien schützen. Wenn Sie einen Dienst verwenden, der Schutz auf Benutzer anwendet (Besitzer der Dateien oder E-Mail-Nachrichten), benötigt jeder dieser Benutzer eine dieser Lizenzen. Benutzer, die diese geschützten Daten lediglich nutzen (z. B. lesen und bearbeiten), benötigen keine Lizenz.

-   Office 365

-   Azure Rights Management Premium (früher Azure RMS Standalone)

-   Enterprise Mobility Suite

-   RMS for Individuals

Weitere Informationen und Registrierungsoptionen finden Sie in den folgenden Abschnitten.

Einen Lizenzierungsvergleich der Azure RMS-Funktionen für kostenpflichtige Abonnements finden Sie unter [Vergleich der Angebote zu den Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

Haben Sie weitere Fragen zur Lizenzierung von Azure RMS? Laden Sie die **häufig gestellten Fragen zur Lizenzierung von Azure Rights Management** von der Seite [Informationen zum Erwerb von Azure Rights Management](https://www.microsoft.com/en-us/server-cloud/products/azure-rights-management/Purchasing.aspx) herunter. 

### Office 365-Abonnement
[Kostenlose 30-Tage-Testversion: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Dieses Abonnement ist auf Organisationen ausgelegt, die die Office Onlinedienste und deren IRM-Feature, das Azure RMS verwendet, benutzen möchten. Aber nicht alle Office 365-Abonnements enthalten Azure RMS.

|Lizenzierungsoption|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|--------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Verwaltung von Informationsrechten (IRM)|Nein|Nein|Nein|Ja|Ja|Ja|Nein|Nein|Nein|

### Azure Rights Management-Premiumabonnement
[Kostenlose 30-Tage-Testversion](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Dieses Abonnement wurde früher als Azure RMS Standalone bezeichnet und ist auf Organisationen ausgelegt, die Azure RMS verwenden möchten, aber kein Abonnement haben, das Azure RMS umfasst. Wenn Sie z. B. ein Abonnement für Office 365 Business Essentials oder Office 365 Enterprise E1 haben, enthalten diese Abonnements kein Azure RMS (siehe die Tabelle im vorherigen Abschnitt). Um Azure RMS zu verwenden, können Sie ein Abonnement für Azure Rights Management Premium kaufen (oder ein anderes Abonnement, z. B. Office 365 Enterprise E4, das Azure RMS enthält).

Weitere Informationen finden Sie unter [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Dieses Abonnement bietet außerdem einen Testzeitraum, in dem Sie Azure RMS für 25 Benutzer kostenlos testen können. Wenn das Abonnement abläuft, bevor Sie ein Ersatzabonnement gekauft haben, finden Sie Informationen hierzu unter „Was passiert, wenn das Testabonnement abläuft?“.

|Lizenzierungsoption|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|--------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Verwaltung von Informationsrechten (IRM)|Ja|Ja [Fußnote 1]|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
Fußnote 1: Für Business Premium gibt es einige Clienteinschränkungen: Sie können Inhalte schützen und geschützte Inhalte mit RMS mithilfe der Outlook Web App und der RMS-Freigabe-App nutzen. Sie können geschützte Inhalte mit allen anderen Office-Anwendungen einschließlich Office Online und den Client-Anwendungen für Office 365 Business Premium nutzen.

#### <a name="BKMK_TrialExpiryBehavior"></a>Was passiert, wenn das Testabonnement abläuft?
Wenn Ihr Testabonnement abläuft, verlieren Sie den Zugriff auf Inhalt, der im Rahmen Ihres Testabonnements für Azure RMS geschützt wurde. Wenn Sie dann jedoch ein Abonnement kaufen, das Azure RMS unterstützt, wird der Zugriff automatisch wiederhergestellt.

Eine Ausnahme vom Zugriffsverlust bei Ablauf besteht, wenn Ihre Organisation Azure RMS mit dem "RMS for Individuals"-Abonnement verwendet hat, bevor Sie das Testabonnement erworben haben. Dann bleibt der Zugriff auf zuvor geschützte Inhalte bestehen, auch nach Ablauf des Testabonnements.

### Enterprise Mobility Suite-Abonnement
[Kostenlose 30-Tage-Testversion](http://go.microsoft.com/fwlink/?LinkId=615385)

Dieses Abonnement ist auf Organisationen ausgelegt, die eine Kombination aus Azure Active Directory Premium, Windows Intune und Azure Rights Management verwenden möchten. Weitere Informationen finden Sie unter [Übersicht über Microsoft Enterprise Mobility](http://go.microsoft.com/fwlink/?LinkId=615386).

|Lizenzierungsoption|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|--------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Verwaltung von Informationsrechten (IRM)|Ja|Ja [Fußnote 1]|Ja|Ja|Ja|Ja|Ja|Ja|Ja|
Fußnote 1: Für Business Premium gibt es einige Clienteinschränkungen: Sie können Inhalte schützen und geschützte Inhalte mit RMS mithilfe der Outlook Web App und der RMS-Freigabe-App nutzen. Sie können geschützte Inhalte mit allen anderen Office-Anwendungen einschließlich Office Online und den Client-Anwendungen für Office 365 Business Premium nutzen.

### RMS for Individuals-Abonnement
Dieses Abonnement ist auf Einzelpersonen in einer Organisation ausgelegt, in der weder Azure RMS noch AD RMS bereitgestellt ist. Es ermöglicht diesen Personen, Inhalte zu lesen, die von einer Organisation geschützt wurden, die Azure RMS verwendet, sowie ihre eigenen Inhalte zu schützen.

Weitere Informationen finden Sie unter [RMS for Individuals und Azure Rights Management](rms-for-individuals.md).

## <a name="BKMK_AzureADTenant"></a>Azure AD-Verzeichnis
Für die Verwendung von Azure RMS benötigen Sie ein Azure AD-Verzeichnis. Für die Anmeldung am klassischen Azure-Portal, in dem Sie z. B. Rights Management-Vorlagen konfigurieren und verwalten können, verwenden Sie Ihr Organisationskonto für dieses Verzeichnis.

Falls Sie noch kein Azure-Abonnement für Ihre Organisation besitzen, können Sie sich für eine kostenlose Testversion anmelden: Folgen Sie den Anweisungen auf der [Seite für die ersten Schritten mit Azure](https://account.windowsazure.com/organization).

Weitere Informationen finden Sie in den folgenden Ressourcen in der Azure Active Directory-Dokumentation:

-   [Was ist ein Azure AD-Verzeichnis?](http://msdn.microsoft.com/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Die Beziehung zwischen Azure-Abonnements und Azure AD](http://msdn.microsoft.com/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Wenn Sie Ihr Azure AD-Verzeichnis in Ihre lokalen AD-Gesamtstrukturen integrieren möchten, finden Sie Informationen hierzu unter [Verzeichnisintegration](http://msdn.microsoft.com/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Wenn Sie über mobile Geräte oder Mac-Computer verfügen, die lokal mithilfe von AD FS oder einem äquivalenten Authentifizierungsanbieter authentifiziert werden, müssen Sie wie folgt vorgehen:
> 
> -   Sie müssen AD FS mit einer Mindestserverversion **Windows Server 2012 R2** oder einem alternativen Authentifizierungsanbieter verwenden, der das OAuth 2.0-Protokoll verwendet.

### <a name="BKMK_MFA"></a>Multi-Factor-Authentication (MFA) und Azure RMS
Damit Sie Multi-Factor-Authentication (MFA) und Azure RMS verwenden können, ist mindestens eine der folgenden Komponenten erforderlich:

-   Office 2013 (Mindestversion):

    -   Wenn Sie Office 2013 haben, müssen Sie auch das [Update vom 9. Juni 2015 für Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853) installieren. Weitere Informationen zu diesem Update sowie dazu, wie moderne Authentifizierung ADAL-basierte (Active Directory Authentication Library) Anmeldung in Office 2013 einbringt, finden Sie unter [Office 2013 modern authentication public preview announced](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) im Office-Blog.

-   Rights Management-Freigabeanwendung für Windows:

    -   Sie müssen mindestens die Version 1.0.1908.0 installiert haben. Sie können dies in der Systemsteuerung in „Programme und Features“ prüfen. Weitere Informationen zur Freigabeanwendung finden Sie unter [Rights Management-Freigabeanwendung für Windows](sharing-app-windows.md).

-   Rights Management-Freigabe-App für mobile Geräte und Mac-Computer:

    -   Stellen Sie sicher, dass Sie die neueste Version installiert haben. MFA-Unterstützung wurde in die September 2015-Version der RMS-Freigabe-App integriert.

Konfigurieren Sie dann Ihre MFA-Lösung:

-   Für von Microsoft verwaltete Mandanten (Sie haben Azure Active Directory oder Office 365):

    -   Konfigurieren Sie Azure MFA, um MFA für Benutzer zu erzwingen. Anweisungen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication in der Cloud](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) in der Azure-Dokumentation.

        Weitere Informationen zu Azure MFA finden Sie unter [Was ist Azure Multi-Factor Authentication?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/).

-   Für Verbundmandanten (Sie betreiben Verbundserver lokal):

    -   Konfigurieren Sie Ihre Verbundserver für Azure Active Directory oder Office 365. Wenn Sie beispielsweise AD FS verwenden, finden Sie Informationen unter [Configure Additional Authentication Methods for AD FS](https://technet.microsoft.com/library/dn758113.aspx) auf TechNet.

        Weitere Informationen zu diesem Szenario finden Sie unter [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) im Office-Blog.

## <a name="BKMK_SupportedDevices"></a>Clientgeräte, die Azure RMS unterstützen
Verwenden Sie die folgenden Abschnitte, um zu identifizieren, welche Geräte Azure Rights Management (RMS) unterstützen und welche einzelnen RMS-Funktionen sie unterstützen.

-   [Computer](requirements-azure-rms.md#BKMK_RMSSupportedComputers)

-   [Mobile Geräte](requirements-azure-rms.md#BKMK_RMSSupportedMobileDevices)

-   [Clientgerätefunktionen](requirements-azure-rms.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Computer
Folgende Computerbetriebssysteme unterstützen Azure Rights Management:

-   **Windows 7** (x86, x64)

-   **Windows 8** (x86, x64)

-   **Windows 8.1** (x86, x64)

-   **Windows 10** (x86, x64)

-   **Mac OS X**: Mindestversion Mac OS X 10.8 (Mountain Lion)

### <a name="BKMK_RMSSupportedMobileDevices"></a>Mobile Geräte
Folgende Betriebssysteme für mobile Geräte unterstützen Azure Rights Management:

-   **Windows Phone**: Windows Phone 8.1

-   **Android-Telefone und -Tablets**: Mindestversion Android 4.0.3

-   **iPhone und iPad**: Mindestversion iOS 7.0

-   **Windows RT-Tablets**: Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>Clientgerätefunktionen
Nicht alle unterstützten Clientgeräte unterstützen zurzeit alle RMS-Funktionen. Verwenden Sie die folgende Tabelle, um zu identifizieren, welche Anwendungen die RMS-Funktionen unterstützen, sowie die Ausnahmen.

Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. Außerdem ist für die AD RMS-Unterstützung unter iOS, Android, OS X und Windows Phone 8.1 die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341) erforderlich.

Informationen über die Tabellenspalten:

-   **Geschützte PDF**: Dateien mit der Dateierweiterung PPDF, die automatisch erstellt werden, wenn Sie zur Freigabe von Office- und PDF-Dateien per E-Mail die RMS-Freigabeanwendung verwenden. Die RMS-Freigabeanwendung umfasst einen Reader für geschützte PDF-Dateien. Zuvor konnten Sie erstellte PDF-Dateien, die Sie mithilfe von Azure RMS oder AD RMS geschützt haben, weiterhin mithilfe von Foxit Reader und Nitro Pro auf Windows-, iOS- und Android-Geräten lesen.

-   **E-Mail**: Die aufgeführten E-Mail-Clients können die E-Mail-Nachricht selbst schützen, wodurch angehängte Dateien automatisch geschützt sind. In diesem Szenario kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte (Nachricht und Anhang) anzeigen. Wenn eine E-Mail-Nachricht selbst jedoch nicht geschützt der Anhang jedoch geschützt ist, kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte nicht anzeigen.

-   **Andere Dateitypen**: Text- und Bilddateien umfassen u. a. Dateien mit der Dateierweiterung TXT, XML, JPG und JPEG. Die Dateierweiterung dieser Dateien ändert sich, sobald sie systemintern durch RMS geschützt werden und schreibgeschützt sind. Dateien mit der Dateierweiterung ".pfile" können nicht systemintern geschützt werden, wenn sie generisch durch RMS geschützt sind. Weitere Informationen finden Sie unter [Schutzstufe – systemeigen und generisch](https://technet.microsoft.com/library/dn339003.aspx) und in den Abschnitten [Unterstützte Dateitypen und Dateierweiterungen](https://technet.microsoft.com/library/dn339003.aspx) im [Rights Management-Freigabeanwendung – Administratorhandbuch](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**Gerätebetriebssystem**|Word, Excel, PowerPoint|Geschützte PDF|E-Mail|Weitere Dateitypen|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office Mobile-Apps (nur Azure RMS) [Fußnote 1]<br /><br />Office Online [Fußnote 2]|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS-Freigabeanwendung|Outlook 2010<br /><br />Outlook 2013<br /><br />Outlook Web App (OWA) [Fußnote 3]<br /><br />Windows Mail [Fußnote 4]|RMS-Freigabeanwendung für Windows: Text, Bilder, PFILE<br /><br />Siemens JT2Go: JT-Dateien (nur Windows 10)|
|**iOS**|Office für iPad und iPhone [Fußnote 5]<br /><br />Office Online [Fußnote 2]<br /><br />TITUS-Dokumentation|Foxit Reader<br /><br />RMS-Freigabe-App [Fußnote 1]<br /><br />TITUS-Dokumentation|NitroDesk [Fußnote 4]<br /><br />Outlook für iPad und iPhone [Fußnote 4]<br /><br />OWA für iOS [Fußnote 3]<br /><br />TITUS Mail|RMS-Freigabeanwendung [Fußnote 1]: Text, Bilder, PFILE<br /><br />TITUS-Dokumentation: PFILE|
|**Android**|GigaTrust App für Android<br /><br />Office Online [Fußnote 2]|GigaTrust App für Android<br /><br />Foxit Reader<br /><br />RMS-Freigabe-App [Fußnote 1]|9Folders [Fußnote 4]<br /><br />GigaTrust App für Android [Fußnote 4]<br /><br />NitroDesk [Fußnote 4]<br /><br />OWA für Android [Fußnoten 3 und 6]<br /><br />Samsung Email (S3 und neuer) [Fußnote 6]<br /><br />TITUS-Klassifizierung für mobile Geräte|RMS-Freigabeanwendung [Fußnote 1]: Text, Bilder, PFILE|
|**OS X**|Office 2011 (nur AD RMS)<br /><br />Office 2016 für Mac<br /><br />Office Online [Fußnote 2]|Foxit Reader<br /><br />RMS-Freigabe-App [Fußnote 1]|Outlook 2011 (nur AD RMS)<br /><br />Outlook 2016 für Mac<br /><br />Outlook für Mac|RMS-Freigabeanwendung [Fußnote 1]: Text, Bilder, PFILE|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [Fußnote 2]|Nicht unterstützt|Outlook 2013 RT<br /><br />E-Mail-App für Windows<br /><br />Windows Mail [Fußnote 4]|Siemens JT2Go: JT-Dateien|
|**Windows Phone 8.1**|Office Mobile (nur AD RMS)|RMS-Freigabe-App [Fußnote 1]|Outlook Mobile [Fußnote 4]|RMS-Freigabeanwendung [Fußnote 1]: Text, Bilder, PFILE|
|**Blackberry 10**|Nicht unterstützt|Nicht unterstützt|Blackberry-E-Mail [Fußnote 4]|Nicht unterstützt|
Fußnote 1: Unterstützt die Anzeige geschützter Inhalte.

Fußnote 2: Unterstützt die Anzeige von geschützten Inhalten in SharePoint Online, OneDrive for Business und Outlook Web Access.

Fußnote 3: Wenn ein Empfänger über ein Postfach in einer lokalen Exchange-Installation verfügt und er eine geschützte E-Mail empfängt, kann dieser Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden.  Dieser Inhalt kann nicht in Outlook Web Access geöffnet werden.

Fußnote 4: Verwendet Exchange ActiveSync IRM, das vom Exchange-Administrator aktiviert werden muss. Benutzer können „Anzeigen“, „Antworten“ und „Allen antworten“ für geschützte E-Mail-Nachrichten ausführen, können selbst aber keine neuen E-Mail-Nachrichten schützen.

Wenn ein Empfänger über ein Postfach in einer lokalen Exchange-Installation verfügt und er eine geschützte E-Mail von einer anderen Organisation empfängt, die ebenfalls Exchange verwendet, kann der Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden.  Dieser Inhalt kann nicht auf einem Gerät geöffnet werden, das Exchange Active Sync IRM verwendet.

Fußnote 5: Unterstützt das Anzeigen und Bearbeiten von geschützten Dokumenten. Weitere Informationen finden Sie im Office-Blog im Beitrag zu [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Azure Rights Management-Unterstützung jetzt auch für Office für iPad und iPhone).


Fußnote 6: Weitere Informationen finden Sie im folgenden Beitrag des Office-Blogs: [OWA für Android ist nun für ausgewählte Geräte verfügbar](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> Weitere Informationen über die RMS-Unterstützung, die demnächst in Office für verschiedene Plattformen erhältlich sein wird, finden Sie im folgenden Beitrag des Office-Blogs: [Office everywhere, encryption everywhere](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Anwendungen, die Azure RMS unterstützen
Die folgenden Anwendungen bieten systemeigene Unterstützung für Azure RMS, was bedeutet, dass RMS in diese Anwendungen eng integriert ist durch Verwendung von RMS-APIs zur Unterstützung von Nutzungseinschränkungen. Diese Anwendungen werden auch als „RMS-aktiviert“ bezeichnet:

-   **Microsoft Office-Anwendungen** (Word, Excel, PowerPoint und Outlook) aus folgenden Suiten können Inhalte mithilfe von Azure RMS schützen:

    -   Office 365 ProPlus

    -   Office 365 Enterprise E3

    -   Office 365 Enterprise E4

    -   Office 365 Enterprise E5

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Andere Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

    > [!NOTE]
    > Azure RMS mit Office Professional Plus 2010 oder Office Professional 2010:
    > 
    > -   Erfordert die Rights Management-Freigabeanwendung für Windows
    > -   Unter Windows 10 nicht unterstützt

-   **Die Rights Management-Freigabeanwendung für Windows**

    Weitere Informationen zur Rights Management-Freigabeanwendung für Windows finden Sie in den folgenden Ressourcen:

    -   [Rights Management-Freigabeanwendung – Administratorhandbuch](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Rights Management-Freigabeanwendung – Benutzerhandbuch](http://technet.microsoft.com/library/dn339006.aspx)

-   **Die Rights Management-Freigabeanwendung für mobile Plattformen**

    Weitere Informationen zur Rights Management-Freigabeanwendung für mobile Plattformen finden Sie in den folgenden Ressourcen:

    -   Laden Sie die relevante App über die Links auf der [Microsoft Rights Management-Seite](http://go.microsoft.com/fwlink/?LinkId=303970) herunter.
 
    -   [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile Plattformen](http://technet.microsoft.com/dn451248)

-   **Sonstige Anwendungen, die die RMS-APIs unterstützen**:

    -   Branchenanwendungen, die intern mithilfe des RMS SDK geschrieben wurden.

    -   Anwendungen von Softwareherstellern, die mithilfe des RMS SDK geschrieben wurden.

    Weitere Informationen zum SDK finden Sie unter [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:
> 
> -   Microsoft Office für Mac 2011
> -   Microsoft OneDrive for Business für SharePoint Server 2013
> -   XPS-Viewer
> 
> Zusätzlich liegen bei der RMS-Freigabeanwendung folgende Einschränkungen vor:
> 
> -   Für Windows-Computer: Erfordert eine Mindestversion von Windows 7 Service Pack 1.

Weitere Informationen dazu, wie diese Anwendungen Azure RMS unterstützen, finden Sie unter [Unterstützung von Azure Rights Management durch Anwendungen](applications-support.md).

Informationen dazu, wie diese Anwendungen konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md).

## <a name="BKMK_SupportedServers"></a>Lokale Server, die Azure RMS unterstützen
Die folgenden lokalen Serverprodukte werden mit Azure RMS unterstützt, wenn Sie den Azure RMS-Verbindungsdienst verwenden, der als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und Azure RMS fungiert. Zusätzlich erfordert diese Konfiguration, dass Sie die Verzeichnissynchronisierung zwischen Ihren Active Directory-Gesamtstrukturen und Azure Active Directory konfigurieren.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Da Dateiserver, auf denen Windows Server 2008 R2 ausgeführt wird, über keine integrierte Taskaktion zum Anwenden des RMS-Schutzes verfügen, können Sie den RMS Connector für dieses Szenario verwenden. Sie können jedoch die Dateiklassifizierungsinfrastruktur und Azure RMS auf diesen Betriebssystemen verwenden, wenn Sie einen benutzerdefinierten Dateiverwaltungstask konfigurieren, über den eine Datei oder ein Skript ausgeführt wird, um die Dateien mithilfe von Azure RMS zu schützen. Beispielsweise ein Windows PowerShell-Skript, in dem die [RMS-Schutz-Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx) verwendet werden.
    > 
    > Sie können diese Cmdlets auch mit Servern mit höheren Versionen von Windows Server verwenden. Dies hat den Vorteil, dass diese Cmdlets alle Dateitypen schützen können. Der RMS-Connector schützt nur Office-Dateien. Anweisungen zur Vorgehensweise finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](configure-fci.md).

Der RMS-Verbindungsdienst wird unter Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 unterstützt.

Weitere Informationen dazu, wie Sie den RMS-Connector für diese lokalen Server konfigurieren, finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

## Siehe auch
[Erste Schritte mit Azure Rights Management](getting-started-with-azure-rights-management.md)



<!--HONumber=Apr16_HO3-->


