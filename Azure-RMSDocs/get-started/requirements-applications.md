---
title: "Unterstützung von Anwendungen für den RMS-Datenschutz"
description: "Stellen Sie fest, welche Anwendungen über RMS-APIs den Azure Rights Management-Dienst von Azure Information Protection nativ unterstützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9b2395ad67bfee226bf10f36613cb6465eb0b019
ms.sourcegitcommit: 0fd2e63822280ec96ab957e22868c63de9ef3d47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2017
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten

>*Gilt für: Azure Information Protection, Office 365*


In der folgenden Tabelle sind die Anwendungen und Lösungen aufgeführt, die den Azure Rights Management-Dienst (Azure RMS) nativ unterstützen, der Datenschutz für Azure Information Protection bietet. 

Die Rights Management-Unterstützung ist in diesen Anwendungen und Lösungen eng integriert, d.h., Nutzungseinschränkungen werden mithilfe der Rights Management-APIs unterstützt. Diese Anwendungen und Lösungen werden auch als „RMS-aktiviert“ bezeichnet.

Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. Außerdem ist für die AD RMS-Unterstützung unter iOS, Android, macOS und Windows Phone 8.1 die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](https://technet.microsoft.com/library/dn673574.aspx) erforderlich.

## <a name="rms-enlightened-applications"></a>RMS-aktivierte Anwendungen

Die folgende Tabelle zeigt RMS-aktivierte Clientanwendungen von Microsoft und anderen Softwareherstellern.

Informationen über die Tabellenspalten:

-   **Geschützte PDF**: Diese Dateien können die Erweiterung PDF oder PPDF aufweisen.

-   **E-Mail**: Die aufgeführten E-Mail-Clients können die E-Mail-Nachricht selbst schützen, wodurch noch ungeschützte, angehängte Office-Dateien automatisch geschützt werden. In diesem Szenario kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte (Nachricht und Anhang) anzeigen. Wenn eine E-Mail-Nachricht selbst jedoch nicht geschützt der Anhang jedoch geschützt ist, kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte nicht anzeigen.

-   **Andere Dateitypen**: Text- und Bilddateien umfassen u. a. Dateien mit der Dateierweiterung TXT, XML, JPG und JPEG. Die Dateierweiterung dieser Dateien ändert sich, nachdem sie durch Rights Management nativ geschützt wurden und schreibgeschützt sind. Dateien mit der Dateierweiterung „.pfile“ können nicht nativ geschützt werden, wenn sie generisch durch Rights Management geschützt sind. Weitere Informationen finden Sie im Administratorhandbuch zum Azure Information Protection-Client unter [Unterstützte Dateitypen](../rms-client/client-admin-guide-file-types.md).


|**Gerätebetriebssystem**|Word, Excel, PowerPoint|Geschützte PDF|E-Mail|Weitere Dateitypen|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Mobile-Apps (nur Azure RMS)[1](#footnote-1)<br /><br />Office Online[[2]](#footnote-2)|Azure Information Protection-Client für Windows <br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS-Freigabeanwendung|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA)[3](#footnote-3)<br /><br />Windows Mail[[4]](#footnote-4)|Azure Information Protection-Client für Windows: Text, Bilder, PFILE<br /><br />RMS-Freigabeanwendung für Windows: Text, Bilder, PFILE<br /><br />SealPath RMS-Plug-In für AutoCAD [[8]](#footnote-8): DWG<br />|
|**iOS**|Office für iPad und iPhone[[5]](#footnote-5)<br /><br />Office Online[[2]](#footnote-2)<br /><br />TITUS-Dokumentation|Azure Information Protection-App [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />GigaTrust<br /><br />TITUS-Dokumentation|Azure Information Protection-App [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für iPad und iPhone[[4]](#footnote-4)<br /><br />OWA für iOS[[3]](#footnote-3)<br /><br />TITUS Mail|Azure Information Protection-App [[1]](#footnote-1): Text, Bilder<br /><br />TITUS-Dokumentation: PFILE|
|**Android**|GigaTrust App für Android<br /><br />Office Online[[2]](#footnote-2)<br /><br />Office Mobile [[1]](#footnote-1)|Azure Information Protection-App [[1]](#footnote-1)<br /><br />GigaTrust App für Android<br /><br />Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|9Folders[[4]](#footnote-4)<br /><br />Azure Information Protection-App [[1]](#footnote-1)<br /><br />GigaTrust App für Android[[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für Android [[4]](#footnote-4)<br /><br />OWA für Android [[3]](#footnote-3) und [[7]](#footnote-7)<br /><br />Samsung E-Mail (S3 und neuer)[7](#footnote-7)<br /><br />TITUS-Klassifizierung für mobile Geräte|Azure Information Protection-App [[1]](#footnote-1): Text, Bilder|
|**macOS**|Office 2011 (nur AD RMS)<br /><br />Office 2016 für Mac<br /><br />Office Online[[2]](#footnote-2)|Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|Outlook 2011 (nur AD RMS)<br /><br />Outlook 2016 für Mac<br /><br />Outlook für Mac|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
|**Windows 10 Mobile**|Office Mobile-Apps (nur Azure RMS)[1](#footnote-1)|Nicht unterstützt|Citrix WorxMail [[6]](#footnote-6)<br /><br />Outlook Mail|Nicht unterstützt|
|**Windows RT**|Office 2013 RT<br /><br />Office Online[[2]](#footnote-2)|Nicht unterstützt|Outlook 2013 RT<br /><br />E-Mail-App für Windows<br /><br />Windows Mail[[4]](#footnote-4)|Siemens JT2Go: JT-Dateien|
|**Windows Phone 8.1**|Office Mobile (nur AD RMS)|RMS-Freigabeanwendung[[1]](#footnote-1)|Outlook Mobile[[4]](#footnote-4)|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
|**Blackberry 10**|Nicht unterstützt|Nicht unterstützt|Blackberry-E-Mail[[4]](#footnote-4)|Nicht unterstützt|


###### <a name="footnote-1"></a>Fußnote 1
Unterstützt die Anzeige geschützter Inhalte.

###### <a name="footnote-2"></a>Fußnote 2 
Unterstützt die Anzeige von geschützten Dokumenten, wenn ein ungeschütztes Dokument in eine geschützte Bibliothek in SharePoint Online und OneDrive for Business hochgeladen wird 

###### <a name="footnote-3"></a>Fußnote 3
Wenn ein Empfänger eine geschützte E-Mail erhält und als Mailserver nicht Exchange verwendet, oder wenn der Absender zu einer anderen Organisation gehört, kann der Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden. Dieser Inhalt kann nicht in Outlook Web Access geöffnet werden.

###### <a name="footnote-4"></a>Fußnote 4
Verwendet Exchange ActiveSync IRM, das vom Exchange-Administrator aktiviert werden muss. Benutzer können „Anzeigen“, „Antworten“ und „Allen antworten“ für geschützte E-Mail-Nachrichten ausführen, können selbst aber keine neuen E-Mail-Nachrichten schützen.

Wenn ein Empfänger eine geschützte E-Mail erhält und als Mailserver nicht Exchange verwendet, oder wenn der Absender zu einer anderen Organisation gehört, kann der Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden. Dieser Inhalt kann nicht über Outlook Web Access oder mobile E-Mail-Clients, die Exchange Active Sync-IRM verwenden, geöffnet werden.

###### <a name="footnote-5"></a>Fußnote 5
Unterstützt das Anzeigen und Bearbeiten von geschützten Dokumenten bei iOS. Weitere Informationen finden Sie im Office-Blog im Beitrag zu [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Azure Rights Management-Unterstützung jetzt auch für Office für iPad und iPhone).

###### <a name="footnote-6"></a>Fußnote 6
Weitere Informationen finden Sie unter der Citrix [Produktdokumentation für WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html).

###### <a name="footnote-7"></a>Fußnote 7
Weitere Informationen finden Sie im Office-Blog im Beitrag zu: [OWA for Android now available on select devices](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) (OWA für Android ist nun für ausgewählte Geräte verfügbar).

###### <a name="footnote-8"></a>Fußnote 8
Weitere Informationen finden Sie im folgenden Beitrag auf dem „Enterprise und Mobility“-Blog [SealPath brings RMS protection to AutoCAD (SealPath setzt den RMS-Schutz auf AutoCAD)](https://blogs.technet.microsoft.com/enterprisemobility/2015/09/08/sealpath-brings-rms-protection-to-autocad/).


### <a name="more-information-about-azure-rms-support-for-office"></a>Weitere Informationen zur Azure RMS-Unterstützung für Office

Azure RMS ist eng in die Word-, Excel-, PowerPoint- und Outlook-Apps integriert. Dort wird diese Funktionalität oft als Information Rights Management (IRM) bezeichnet. 

Die folgenden Editionen von Office-Clients unterstützen den Schutz von Dateien und E-Mails auf Windows-Computern mithilfe von Azure RMS:

- Office 365 ProPlus: Office 2016 und Office 2013

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010 mit Service Pack 2

Alle Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

Azure RMS mit Office Professional Plus 2010 mit Service Pack 2 oder Office Professional 2010 mit Service Pack 2:

- Erfordert den Azure Information Protection-Client für Windows oder die Rights Management-Freigabeanwendung für Windows

- Unter Windows 10 nicht unterstützt

- Die formularbasierte Authentifizierung für Verbundbenutzerkonten wird nicht unterstützt. Diese Konten müssen die integrierte Windows-Authentifizierung verwenden.

Die folgenden Editionen von Office-Clients unterstützen den Schutz von Dateien und E-Mails auf macOS-Computern mithilfe von Azure RMS:

- Office 365 ProPlus: Office 2016

- Office 2016 für Mac

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Weitere Informationen zur Azure Information Protection-App für iOS und Android

Die Azure Information Protection-App für iOS und Android ersetzt die RMS-Freigabeanwendung für diese Geräte. Sie bietet dieselbe Funktionalität und unterstützt darüber hinaus durch Rights Management geschützte E-Mails und durch Rights Management geschützte PDF-Dateien in SharePoint Online.

Wenn Ihre iOS- und Android-Geräte bei Microsoft Intune registriert sind, können Sie diese App mithilfe einer richtlinienverwalteten App bereitstellen und verwalten. Weitere Informationen finden Sie in der Intune-Dokumentation unter [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console). Befolgen Sie in Schritt 2 dieser Intune-Dokumentation die Anweisungen zum Veröffentlichen einer richtlinienverwalteten App.

Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](../rms-client/mobile-app-faq.md).


### <a name="more-information-about-the-azure-information-protection-client-for-windows"></a>Weitere Informationen zum Azure Information Protection-Client für Windows

Dieser Client ersetzt jetzt Rights Management-Freigabeanwendung für Windows. 

Weitere Informationen finden Sie in den folgenden Ressourcen:

- [Azure Information Protection-Client – Administratorhandbuch](../rms-client/client-admin-guide.md)

- [Azure Information Protection-Client – Benutzerhandbuch](../rms-client/client-user-guide.md)

- [Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android](../rms-client/mobile-app-faq.md)

Laden Sie die relevante App über die Links auf der [Microsoft Azure Information Protection-Seite](http://go.microsoft.com/fwlink/?LinkId=303970) herunter.

### <a name="more-information-about-the-rights-management-sharing-application"></a>Weitere Informationen zur Rights Management-Freigabeanwendung

Diese Anwendung wird durch den Azure Information Protection-Client ersetzt. Sie ist weiterhin für Macintosh-Computer und mobile Geräte mit Windows Phone erforderlich. 

Weitere Informationen finden Sie in den folgenden Ressourcen:

-   [Administratorhandbuch der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md)

-   [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile Plattformen](https://technet.microsoft.com/dn451248)

Laden Sie die App für Macintosh-Computer und Windows Phone über die Links auf der [Microsoft Azure Information Protection-Seite](http://go.microsoft.com/fwlink/?LinkId=303970) herunter.


### <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Weitere Informationen zu anderen Anwendungen, die Azure Information Protection unterstützen

Zusätzlich zu den Anwendungen in der Tabelle kann jede Anwendung, die APIs für den Azure Rights Management Service unterstützt, in Azure Informationen Protection integriert werden. Dazu zählen die Folgenden:

- Branchenanwendungen, die intern mithilfe der RMS-SDKs geschrieben wurden.

- Anwendungen von Softwareherstellern, die mithilfe der RMS-SDKs geschrieben wurden.

Weitere Informationen finden Sie im [Azure Information Protection-Entwicklerhandbuch](../develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Nicht von Azure RMS unterstützte Anwendungen

Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:

-   Microsoft Office für Mac 2011

-   Microsoft OneDrive for Business für SharePoint Server 2013

-   XPS-Viewer
 
Darüber hinaus weisen die RMS-Freigabeanwendung und der Azure Information Protection-Client die folgenden Einschränkungen auf:

-   Für Windows-Computer: Erfordert eine Mindestversion von Windows 7 Service Pack 1.

## <a name="rms-enlightened-solutions"></a>RMS-aktivierte Lösungen

Die folgende Tabelle zeigt RMS-aktivierte Lösungen von Softwareherstellern.

Wenn Sie Softwarehersteller sind und über eine Lösung verfügen, die nicht in dieser Tabelle aufgeführt ist, registrieren Sie Ihre Anwendung bei Azure AD. Weitere Informationen finden Sie unter [Vorgehensweise: Registrieren Ihrer App für Azure AD und Aktivieren der App für RMS](../develop/authentication-integration.md).


|Produkt|Hersteller|Beschreibung|
|-------------------------------|---------------------------|-----------------|
|Absolut|Absolut|Verhinderung von Datenverlust (Data Loss Prevention, DLP) zum Schutz von Inhalten.|
|Content Locker|VMware|Speichert, nutzt und erstellt geschützte Inhalte.|
|Controle|TakeControle|eDiscovery mithilfe von Bezeichnung und Schutz.|
|Halocore|Secude|Schützt aus SAP-Umgebungen exportierte Dateien.|
|MaaS 360|IBM|Integration zum Nutzen und Schützen von Dokumenten.|
|Mobiliya|Mobiliya|Sichert Dokumente aus Documentum-Repositorys von EMC.
|Ramessys|Ramessys|Integration für Chemcart und Documentum.
|Sealpath|Sealpath Technologies|Integration in CAD-Entwurfstools wie AutoCAD und Siemens Jt2GO.
|SecRMM|Sqaudra Technologies |Dokumentschutz für Wechselmedien.
|Security Sheriff|CryptZone |Zugriffsverwaltung auf SharePoint und Schutz für Dokumente basierend auf deren Klassifizierung und Zugriffsberechtigungen.
|Symantec DLP|Symantec |Erkennung und Überwachung für geschützte Dateien.

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements-azure-rms.md).

Weitere Informationen dazu, wie die gängigsten Anwendungen Azure RMS unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](../understand-explore/applications-support.md).

Informationen dazu, wie die gängigsten Anwendungen für Azure RMS konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]