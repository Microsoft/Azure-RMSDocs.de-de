---
title: "Anforderungen an Azure Information Protection: Vollständiger Artikel | Azure Information Protection"
description: "Voraussetzungen für die Bereitstellung von Azure Information Protection für Ihre Organisation."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 10cf9371-a61b-495f-9d42-898448806994
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: a71123cd055052e6e4a372a945727063b7c2d666


---


# <a name="requirements-for-azure-information-protection"></a>Anforderungen an Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*


Damit Sie Azure Information Protection für Ihre Organisation bereitstellen können, müssen die folgenden Voraussetzungen erfüllt sein. 

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Abonnement für Azure Information Protection|Überprüfen Sie anhand der [Abonnementinformationen](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) und der [Featureliste](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website, ob das Abonnement Ihrer Organisation die gewünschten Azure Information Protection-Features umfasst.|
|Azure Active Directory|Ihre Organisation muss über ein Azure Active Directory-Verzeichnis (Azure AD) verfügen, um die Benutzerauthentifizierung für Azure Information Protection zu unterstützen. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.<br /><br />Wenn Ihre Konten verbunden sind (wenn Sie z.B. AD FS verwenden), müssen diese die integrierte Windows-Authentifizierung verwenden. Die formularbasierte Authentifizierung wird für Azure Information Protection nicht unterstützt.<br /><br />Multi-Factor Authentication (MFA) wird mit Azure Information Protection unterstützt, wenn die erforderliche Clientsoftware installiert ist und Sie die für MFA erforderliche unterstützende Infrastruktur richtig konfiguriert haben.<br /><br />Weitere Informationen finden Sie unter [Azure Active Directory-Anforderungen für Azure Information Protection](requirements-azure-ad.md).|
|Clientgeräte|Benutzer müssen Clientgeräte (Computer oder mobile Geräte) verwenden, unter deren Betriebssystem Azure Information Protection unterstützt wird.<br /><br />Die folgenden Geräte unterstützen den Azure Information Protection-Client, mit dem Benutzer ihre Office-Dokumente und E-Mails klassifizieren und bezeichnen können:<br /><br />- Windows 10 (x86, x64)<br /><br />- Windows 8.1 (x86, x64)<br /><br />- Windows 8 (x86, x64)<br /><br />- Windows 7 Service Pack 1 (x86, x64)<br /><br />Wenn auf diesem Client die Daten mit dem Azure Rights Management-Dienst geschützt werden, kann er von den gleichen Geräten (Windows, Mac, iOS, Android) genutzt werden, die auch den Azure Rights Management-Dienst unterstützen. <br /><br />Weitere Informationen zu den vom Azure Rights Management-Dienst unterstützten Geräten finden Sie unter [Clientgeräte mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-client-devices.md).|
|Anwendungen|Der Azure Information Protection-Client unterstützt die Bezeichnung und den Schutz von Dateien und E-Mails, die mithilfe der folgenden Office-Programme erstellt werden: **Word**, **Excel**, **PowerPoint** und **Outlook** aus folgenden Office-Suiten:<br /><br />Office Professional Plus 2016<br /><br />Office Professional Plus 2013 mit Service Pack 1<br /><br />Office Professional Plus 2010<br /><br />Informationen zu den Anwendungen, die der Azure Rights Management-Dienst unterstützt, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-applications.md).|
|Infrastruktur, die Verbindungen mit dem Internet und abhängige Cloud-Dienste unterstützt|Wenn Sie eine Firewall oder ähnliche zwischengeschaltete Netzwerkgeräte nutzen, die konfiguriert werden müssen, um bestimmte Verbindungen zu erlauben, lesen Sie die Informationen zu **Azure Rights Management (RMS)** im Abschnitt [Office 365-Portal und gemeinsame Dienste](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) aus dem folgenden Office-Artikel: [URLs und IP-Adressbereiche von Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Verwenden Sie die Anleitungen in diesem Office-Artikel, um bei Änderungen an diesen Informationen mithilfe eines RSS-Feed-Abonnements auf dem neuesten Stand zu bleiben.<br /><br />Zusätzlich zu den Informationen im Office-Artikel, spezifisch für Azure Information Protection:<br /><br />- Lassen Sie auf TCP 443 HTTPS-Datenverkehr zu **api.informationprotection.azure.com** zu.<br /><br />– Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z.B. zur Durchführung von Überprüfungen auf Paketebene). Wenn Sie dies tun, wird die Anheftung von Zertifikaten unterbrochen, die RMS-Clients mit von Microsoft verwalteten Zertifizierungsstellen verwenden, um ihre Kommunikation mit Azure RMS zu sichern.<br /><br />– Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.|

Wenn Sie den Azure Rights Management-Dienst von Azure Information Protection auf lokalen Servern verwenden möchten, werden folgende Produkte unterstützt:

-   Exchange Server

-   SharePoint Server

-   Windows Server-Dateiserver, die die Dateiklassifizierungsinfrastruktur unterstützen.

Informationen zu den zusätzlichen Anforderungen für dieses Szenario finden Sie unter [Lokale Server mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-servers.md).

> [!IMPORTANT]
> Das folgende Bereitstellungsszenario wird nur unterstützt, wenn Sie den AD RMS-Schutz mit Azure Information Protection verwenden (HYOK-Konfiguration, „Hold Your Own Key“):
> 
> -   Parallele Ausführung von AD RMS und Azure RMS in derselben Organisation (mit Ausnahme der Migration), wie unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md) beschrieben.
> 
> Es gibt einen unterstützten Migrationspfad [von AD RMS zu Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) und [von Azure Information Protection zu AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Wenn Sie Azure Information Protection bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](../deploy-use/decommission-deactivate.md).

## <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Azure Active Directory-Anforderungen für Azure Information Protection

Für die Verwendung von Azure Information Protection benötigen Sie ein Azure AD-Verzeichnis. Für die Anmeldung am klassischen Azure-Portal, in dem Sie z. B. Rights Management-Vorlagen konfigurieren und verwalten können, verwenden Sie Ihr Organisationskonto für dieses Verzeichnis.

Falls Sie noch kein Azure-Abonnement für Ihre Organisation besitzen, können Sie sich für eine kostenlose Testversion anmelden: Folgen Sie den Anweisungen auf der [Seite für die ersten Schritten mit Azure](https://account.windowsazure.com/organization).

Weitere Informationen finden Sie in den folgenden Ressourcen in der Azure Active Directory-Dokumentation:

-   [Was ist ein Azure AD-Verzeichnis?](/active-directory/active-directory-whatis)

-   [Beziehung zwischen Azure-Abonnements und Azure AD-Verzeichnissen](/active-directory/active-directory-how-subscriptions-associated-directory)

Wenn Sie das Azure AD-Verzeichnis in Ihre lokalen AD-Gesamtstrukturen integrieren möchten, helfen Ihnen die Informationen unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](/active-directory/active-directory-aadconnect) weiter.

> [!NOTE]
> Wenn Sie über mobile Geräte oder Mac-Computer verfügen, die lokal mithilfe von AD FS oder einem äquivalenten Authentifizierungsanbieter authentifiziert werden, müssen Sie wie folgt vorgehen:
> 
> -   Sie müssen AD FS mit einer Mindestserverversion von **Windows Server 2012 R2** oder einem alternativen Authentifizierungsanbieter verwenden, der das OAuth 2.0-Protokoll verwendet.

### <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>Multi-Factor Authentication (MFA) und Azure Information Protection
Damit Sie Multi-Factor Authentication (MFA) mit Azure Information Protection verwenden können, ist mindestens eine der folgenden Komponenten erforderlich:

-   Office 2013 (Mindestversion):

    -   Wenn Sie Office 2013 haben, müssen Sie auch das [Update vom 9. Juni 2015 für Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853) installieren. Weitere Informationen zu diesem Update sowie dazu, wie die moderne Authentifizierung ADAL-basierte Anmeldungen (Active Directory Authentication Library) in Office 2013 integriert, finden Sie im Office-Blog unter [Office 2013 modern authentication public preview announced](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) (Ankündigung der öffentlichen Vorschau für moderne Authentifizierung in Office 2013).

-   Rights Management-Freigabeanwendung für Windows:

    -   Sie müssen mindestens die Version 1.0.1908.0 installiert haben. Sie können dies in der Systemsteuerung in „Programme und Features“ prüfen. Weitere Informationen zur Freigabeanwendung finden Sie unter [Rights Management-Freigabeanwendung für Windows](../rms-client/sharing-app-windows.md).

-   Rights Management-Freigabe-App für mobile Geräte und Mac-Computer:

    -   Stellen Sie sicher, dass Sie die neueste Version installiert haben. MFA-Unterstützung wurde in die September 2015-Version der RMS-Freigabe-App integriert.

Konfigurieren Sie dann Ihre MFA-Lösung:

-   Für von Microsoft verwaltete Mandanten (Sie haben Azure Active Directory oder Office 365):

    -   Konfigurieren Sie Azure MFA, um MFA für Benutzer zu erzwingen. Anweisungen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication in der Cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) in der Multi-Factor Authentication-Dokumentation.

        Weitere Informationen zu Azure MFA finden Sie unter [Was ist Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication).

-   Für Verbundmandanten (Sie betreiben Verbundserver lokal):

    -   Konfigurieren Sie Ihre Verbundserver für Azure Active Directory oder Office 365. Wenn Sie beispielsweise AD FS verwenden, finden Sie Informationen unter [Konfigurieren zusätzlicher Authentifizierungsmethoden für AD FS](https://technet.microsoft.com/library/dn758113.aspx) auf TechNet.

        Weitere Informationen zu diesem Szenario finden Sie unter [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Programm „Works with Office 365 – Identity“ wurde jetzt optimiert) im Office-Blog.

## <a name="client-devices-that-support-azure-rights-management-data-protection"></a>Clientgeräte mit Unterstützung für den Azure Rights Management-Schutz von Daten

In den folgenden Abschnitten sind die Geräte aufgeführt, die den Azure Rights Management-Dienst zum Schutz von Daten für Azure Information Protection unterstützen.

### <a name="computers"></a>Computer
Folgende Computerbetriebssysteme unterstützen den Azure Rights Management-Dienst:

-   **Windows 7** (x86, x64)

-   **Windows 8** (x86, x64)

-   **Windows 8.1** (x86, x64)

-   **Windows 10** (x86, x64)

-   **Mac OS X**: Mindestversion Mac OS X 10.8 (Mountain Lion)

### <a name="mobile-devices"></a>Mobile Geräte
Folgende Mobilbetriebssysteme unterstützen den Azure Rights Management-Dienst:

-   **Windows Phone**: Windows Phone 8.1

-   **Android-Telefone und -Tablets**: Mindestversion Android 4.0.3

-   **iPhone und iPad**: Mindestversion iOS 7.0

-   **Windows-Tablets**: Windows 10 Mobile und Windows 8.1 RT

## <a name="applications-that-support-azure-rights-management-data-protection"></a>Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten

In der folgenden Tabelle sind die Anwendungen aufgeführt, die den Azure Rights Management-Dienst (Azure RMS) nativ unterstützen, der den Schutz von Daten für Azure Information Protection bietet. 

Die Rights Management-Unterstützung ist in diesen Anwendungen eng integriert, d.h., Nutzungseinschränkungen werden mithilfe der Rights Management-APIs unterstützt. Diese Anwendungen werden auch als "RMS-aktiviert" bezeichnet:

Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. Außerdem ist für die AD RMS-Unterstützung unter iOS, Android, OS X und Windows Phone 8.1 die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](https://technet.microsoft.com/library/dn673574.aspx) erforderlich.

Informationen über die Tabellenspalten:

-   **Geschützte PDF**: Dateien mit der Dateierweiterung PPDF, die automatisch erstellt werden, wenn Sie zur Freigabe von Office- und PDF-Dateien per E-Mail die RMS-Freigabeanwendung verwenden. Die RMS-Freigabeanwendung und die Azure Information Protection-App für iOS und Android umfassen einen Reader für geschützte PDF-Dateien. Zuvor konnten Sie erstellte PDF-Dateien, die Sie mithilfe von Azure RMS oder AD RMS geschützt haben, weiterhin mithilfe von Foxit Reader und Nitro Pro auf Windows-, iOS- und Android-Geräten lesen.

-   **E-Mail**: Die aufgeführten E-Mail-Clients können die E-Mail-Nachricht selbst schützen, wodurch angehängte Dateien automatisch geschützt sind. In diesem Szenario kann das Vorschaufeature des Clients autorisierten Empfängern die geschützten Inhalte (Nachricht und Anhang) anzeigen. Wenn eine E-Mail-Nachricht selbst jedoch nicht geschützt, der Anhang jedoch geschützt ist, kann das Vorschaufeature des Clients autorisierten Empfängern die geschützten Inhalte nicht anzeigen.

-   **Andere Dateitypen**: Text- und Bilddateien umfassen u. a. Dateien mit der Dateierweiterung TXT, XML, JPG und JPEG. Die Dateierweiterung dieser Dateien ändert sich, nachdem sie durch Rights Management nativ geschützt wurden und schreibgeschützt sind. Dateien mit der Dateierweiterung „.pfile“ können nicht nativ geschützt werden, wenn sie generisch durch Rights Management geschützt sind. Weitere Informationen finden Sie im [Rights Management-Freigabeanwendung – Administratorhandbuch](../rms-client/sharing-app-admin-guide.md).


|**Gerätebetriebssystem**|Word, Excel, PowerPoint|Geschützte PDF|E-Mail|Weitere Dateitypen|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Mobile-Apps (nur Azure RMS)[1](#footnote-1)<br /><br />Office Online[[2]](#footnote-2)|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS-Freigabeanwendung|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA)[3](#footnote-3)<br /><br />Windows Mail[[4]](#footnote-4)|RMS-Freigabeanwendung für Windows: Text, Bilder, PFILE<br /><br />Siemens JT2Go: JT-Dateien (nur Windows 10)|
|**iOS**|Office für iPad und iPhone[[5]](#footnote-5)<br /><br />Office Online[[2]](#footnote-2)<br /><br />TITUS-Dokumentation|Azure Information Protection-App [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />TITUS-Dokumentation|Azure Information Protection-App [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für iPad und iPhone[[4]](#footnote-4)<br /><br />OWA für iOS[[3]](#footnote-3)<br /><br />TITUS Mail|Azure Information Protection-App [[1]](#footnote-1): Text, Bilder<br /><br />TITUS-Dokumentation: PFILE|
|**Android**|GigaTrust App für Android<br /><br />Office Online[[2]](#footnote-2)<br /><br />Office Mobile (nur Azure RMS) [[1]](#footnote-1)|Azure Information Protection-App [[1]](#footnote-1)<br /><br />GigaTrust App für Android<br /><br />Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|9Folders[[4]](#footnote-4)<br /><br />Azure Information Protection-App [[1]](#footnote-1)<br /><br />GigaTrust App für Android[[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für Android [[4]](#footnote-4)<br /><br />OWA für Android [[3]](#footnote-3) und [[7]](#footnote-7)<br /><br />Samsung E-Mail (S3 und neuer)[7](#footnote-7)<br /><br />TITUS-Klassifizierung für mobile Geräte|Azure Information Protection-App [[1]](#footnote-1): Text, Bilder|
|**OS X**|Office 2011 (nur AD RMS)<br /><br />Office 2016 für Mac<br /><br />Office Online[[2]](#footnote-2)|Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|Outlook 2011 (nur AD RMS)<br /><br />Outlook 2016 für Mac<br /><br />Outlook für Mac|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
|**Windows 10 Mobile**|Office Mobile-Apps (nur Azure RMS)[[1]](#footnote-1)|Nicht unterstützt|Citrix WorxMail [[6]](#footnote-6)<br /><br />Outlook Mail|Nicht unterstützt|
|**Windows RT**|Office 2013 RT<br /><br />Office Online[[2]](#footnote-2)|Nicht unterstützt|Outlook 2013 RT<br /><br />E-Mail-App für Windows<br /><br />Windows Mail[[4]](#footnote-4)|Siemens JT2Go: JT-Dateien|
|**Windows Phone 8.1**|Office Mobile (nur AD RMS)|RMS-Freigabeanwendung[[1]](#footnote-1)|Outlook Mobile[[4]](#footnote-4)|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
|**Blackberry 10**|Nicht unterstützt|Nicht unterstützt|Blackberry-E-Mail[[4]](#footnote-4)|Nicht unterstützt|


##### <a name="footnote-1"></a>Fußnote 1
Unterstützt die Anzeige geschützter Inhalte.

##### <a name="footnote-2"></a>Fußnote 2 
Unterstützt die Anzeige von geschützten Dokumenten, wenn ein ungeschütztes Dokument in eine geschützte Bibliothek in SharePoint Online und OneDrive for Business hochgeladen wird 

##### <a name="footnote-3"></a>Fußnote 3
Wenn ein Empfänger eine geschützte E-Mail erhält und als Mailserver nicht Exchange verwendet, oder wenn der Absender zu einer anderen Organisation gehört, kann der Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden. Dieser Inhalt kann nicht in Outlook Web Access geöffnet werden.

##### <a name="footnote-4"></a>Fußnote 4
Verwendet Exchange ActiveSync IRM, das vom Exchange-Administrator aktiviert werden muss. Benutzer können „Anzeigen“, „Antworten“ und „Allen antworten“ für geschützte E-Mail-Nachrichten ausführen, können selbst aber keine neuen E-Mail-Nachrichten schützen.

Wenn ein Empfänger eine geschützte E-Mail erhält und als Mailserver nicht Exchange verwendet, oder wenn der Absender zu einer anderen Organisation gehört, kann der Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden. Dieser Inhalt kann nicht über Outlook Web Access oder mobile E-Mail-Clients, die Exchange Active Sync-IRM verwenden, geöffnet werden.

##### <a name="footnote-5"></a>Fußnote 5
Unterstützt das Anzeigen und Bearbeiten von geschützten Dokumenten. Weitere Informationen finden Sie im Office-Blog im Beitrag zu [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Azure Rights Management-Unterstützung jetzt auch für Office für iPad und iPhone).

##### <a name="footnote-6"></a>Fußnote 6
Weitere Informationen finden Sie unter der Citrix [Produktdokumentation für WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html).

##### <a name="footnote-7"></a>Fußnote 7
Weitere Informationen finden Sie im Office-Blog im Beitrag zu: [OWA for Android now available on select devices](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) (OWA für Android ist nun für ausgewählte Geräte verfügbar).

## <a name="more-information-about-azure-rms-support-for-office"></a>Weitere Informationen zur Azure RMS-Unterstützung für Office

Azure RMS ist eng in die Word-, Excel-, PowerPoint- und Outlook-Apps integriert. Dort wird diese Funktionalität oft als Information Rights Management (IRM) bezeichnet. Die folgenden Editionen von Office-Clients unterstützen den Schutz von Dateien und E-Mails mithilfe von Azure RMS:

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Alle Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

Azure RMS mit Office Professional Plus 2010 oder Office Professional 2010:

- Erfordert die Rights Management-Freigabeanwendung für Windows

- Unter Windows 10 nicht unterstützt

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Weitere Informationen zur Azure Information Protection-App für iOS und Android

Die Azure Information Protection-App für iOS und Android ersetzt die RMS-Freigabeanwendung für diese Geräte. Sie bietet dieselbe Funktionalität und unterstützt darüber hinaus durch Rights Management geschützte E-Mails und durch Rights Management geschützte PDF-Dateien in SharePoint Online.

Wenn Ihre iOS- und Android-Geräte bei Microsoft Intune registriert sind, können Sie diese App mithilfe einer richtlinienverwalteten App bereitstellen und verwalten. Weitere Informationen finden Sie in der Intune-Dokumentation unter [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console). Befolgen Sie in Schritt 2 dieser Intune-Dokumentation die Anweisungen zum Veröffentlichen einer richtlinienverwalteten App.

Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](../rms-client/mobile-app-faq.md).


### <a name="more-information-about-the-rights-management-sharing-application"></a>Weitere Informationen zur Rights Management-Freigabeanwendung

Weitere Informationen zur Rights Management-Freigabeanwendung für Windows finden Sie in den folgenden Ressourcen:

-   [Administratorhandbuch der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md)

Weitere Informationen zur Rights Management-Freigabeanwendung für mobile Plattformen finden Sie in den folgenden Ressourcen:

-   Laden Sie die relevante App über die Links auf der [Microsoft Rights Management-Seite](http://go.microsoft.com/fwlink/?LinkId=303970) herunter.

-   [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile Plattformen](https://technet.microsoft.com/dn451248)

> [!NOTE]
> Die RMS-Freigabeanwendung für iOS und Android wird ab sofort von der Azure Information Protection-App ersetzt.

### <a name="more-information-about-other-applications-that-support-azure-rms"></a>Weitere Informationen zu anderen Anwendungen, die Azure RMS unterstützen

Zusätzlich zu den Anwendungen in der Tabelle kann jede Anwendung, die diese RMS-APIs unterstützt, in Azure RMS integriert werden. Hierzu zählen:

- Branchenanwendungen, die intern mithilfe des RMS SDK geschrieben wurden.

- Anwendungen von Softwareherstellern, die mithilfe des RMS SDK geschrieben wurden.

Weitere Informationen zum SDK finden Sie unter [Microsoft Rights Management SDK](../develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Nicht von Azure RMS unterstützte Anwendungen

Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:

-   Microsoft Office für Mac 2011

-   Microsoft OneDrive for Business für SharePoint Server 2013

-   XPS-Viewer
 
Zusätzlich liegen bei der RMS-Freigabeanwendung folgende Einschränkungen vor:

-   Für Windows-Computer: Erfordert eine Mindestversion von Windows 7 Service Pack 1.

## <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Lokale Server mit Unterstützung für den Azure Rights Management-Schutz von Daten

Bei Verwendung des Azure Rights Management-Connectors werden die folgenden lokalen Serverprodukte mit Azure Information Protection unterstützt. Dieser Connector dient als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und dem Azure Rights Management-Dienst, über den durch Azure Information Protection Office-Dokumente und E-Mails geschützt werden. 

Für die Verwendung des Connectors müssen Sie die Verzeichnissynchronisierung zwischen Ihren Active Directory-Gesamtstrukturen und Azure Active Directory konfigurieren.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Da Dateiserver, auf denen Windows Server 2008 R2 ausgeführt wird, über keine integrierte Taskaktion zum Anwenden des Rights Management-Schutzes verfügen, können Sie den Rights Management-Connector für dieses Szenario nicht verwenden. Sie können jedoch die Dateiklassifizierungsinfrastruktur und Azure RMS auf diesen Betriebssystemen verwenden, wenn Sie einen benutzerdefinierten Dateiverwaltungstask konfigurieren, über den eine Datei oder ein Skript ausgeführt wird, um die Dateien mithilfe von Azure RMS zu schützen. Beispielsweise ein Windows PowerShell-Skript, in dem die [RMS-Schutz-Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx) verwendet werden.
    > 
    > Sie können diese Cmdlets auch mit Servern mit höheren Versionen von Windows Server verwenden. Dies hat den Vorteil, dass diese Cmdlets alle Dateitypen schützen können. Der RMS-Connector schützt nur Office-Dateien. Anweisungen zur Vorgehensweise finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](../rms-client/configure-fci.md).

Der Rights Management-Connector wird unter Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 unterstützt.

Weitere Informationen zum Konfigurieren des Rights Management-Connectors für diese lokalen Server finden Sie unter [Bereitstellen des Azure Rights Management-Connectors](../deploy-use/deploy-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


