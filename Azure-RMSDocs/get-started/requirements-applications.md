---
title: "Unterstützung von Anwendungen für den Schutz von Daten | Azure Information Protection"
description: "Stellen Sie fest, welche Anwendungen über RMS-APIs den Azure Rights Management-Dienst von Azure Information Protection nativ unterstützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/14/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4ffe5949c080073f8acaadd7780b2c68b4b155f8
ms.openlocfilehash: 1381a93b3a4f262c1747fa136467132137421ecb


---


# <a name="applications-that-support-azure-rights-management-data-protection"></a>Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten

>*Gilt für: Azure Information Protection, Office 365*


In der folgenden Tabelle sind die Anwendungen aufgeführt, die den Azure Rights Management-Dienst (Azure RMS) nativ unterstützen, der den Schutz von Daten für Azure Information Protection bietet. 

Die Rights Management-Unterstützung ist in diesen Anwendungen eng integriert, d.h., Nutzungseinschränkungen werden mithilfe der Rights Management-APIs unterstützt. Diese Anwendungen werden auch als "RMS-aktiviert" bezeichnet:

Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. Außerdem ist für die AD RMS-Unterstützung unter iOS, Android, OS X und Windows Phone 8.1 die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](https://technet.microsoft.com/library/dn673574.aspx) erforderlich.

Informationen über die Tabellenspalten:

-   **Geschützte PDF**: Dateien mit der Dateierweiterung PPDF, die automatisch erstellt werden, wenn Sie zur Freigabe von Office- und PDF-Dateien per E-Mail die RMS-Freigabeanwendung verwenden. Die RMS-Freigabeanwendung, die Azure Information Protection-App für iOS und Android sowie der Azure Information Protection-Client für Windows (Vorschau) umfassen einen Reader für geschützte PDF-Dateien. Zuvor konnten Sie erstellte PDF-Dateien, die Sie mithilfe von Azure RMS oder AD RMS geschützt haben, weiterhin mithilfe von Foxit Reader und Nitro Pro auf Windows-, iOS- und Android-Geräten lesen.

-   **E-Mail**: Die aufgeführten E-Mail-Clients können die E-Mail-Nachricht selbst schützen, wodurch angehängte Dateien automatisch geschützt sind. In diesem Szenario kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte (Nachricht und Anhang) anzeigen. Wenn eine E-Mail-Nachricht selbst jedoch nicht geschützt der Anhang jedoch geschützt ist, kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte nicht anzeigen.

-   **Andere Dateitypen**: Text- und Bilddateien umfassen u. a. Dateien mit der Dateierweiterung TXT, XML, JPG und JPEG. Die Dateierweiterung dieser Dateien ändert sich, nachdem sie durch Rights Management nativ geschützt wurden und schreibgeschützt sind. Dateien mit der Dateierweiterung „.pfile“ können nicht nativ geschützt werden, wenn sie generisch durch Rights Management geschützt sind. Weitere Informationen finden Sie im [Rights Management-Freigabeanwendung – Administratorhandbuch](../rms-client/sharing-app-admin-guide.md).


|**Gerätebetriebssystem**|Word, Excel, PowerPoint|Geschützte PDF|E-Mail|Weitere Dateitypen|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Mobile-Apps (nur Azure RMS)[1](#footnote-1)<br /><br />Office Online[[2]](#footnote-2)|Azure Information Protection-Client für Windows (Vorschau)<br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS-Freigabeanwendung|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA)[3](#footnote-3)<br /><br />Windows Mail[[4]](#footnote-4)|Azure Information Protection-Client für Windows (Vorschau): Text, Bilder PFILE<br /><br />RMS-Freigabeanwendung für Windows: Text, Bilder, PFILE<br /><br />SealPath RMS-Plug-In für AutoCAD [[8]](#footnote-8): DWG<br />|
|**iOS**|Office für iPad und iPhone[[5]](#footnote-5)<br /><br />Office Online[[2]](#footnote-2)<br /><br />TITUS-Dokumentation|Azure Information Protection-App [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />TITUS-Dokumentation|Azure Information Protection-App [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für iPad und iPhone[[4]](#footnote-4)<br /><br />OWA für iOS[[3]](#footnote-3)<br /><br />TITUS Mail|Azure Information Protection-App [[1]](#footnote-1): Text, Bilder<br /><br />TITUS-Dokumentation: PFILE|
|**Android**|GigaTrust App für Android<br /><br />Office Online[[2]](#footnote-2)<br /><br />Office Mobile (nur Azure RMS) [[1]](#footnote-1)|Azure Information Protection-App [[1]](#footnote-1)<br /><br />GigaTrust App für Android<br /><br />Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|9Folders[[4]](#footnote-4)<br /><br />Azure Information Protection-App [[1]](#footnote-1)<br /><br />GigaTrust App für Android[[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für Android [[4]](#footnote-4)<br /><br />OWA für Android [[3]](#footnote-3) und [[7]](#footnote-7)<br /><br />Samsung E-Mail (S3 und neuer)[7](#footnote-7)<br /><br />TITUS-Klassifizierung für mobile Geräte|Azure Information Protection-App [[1]](#footnote-1): Text, Bilder|
|**OS X**|Office 2011 (nur AD RMS)<br /><br />Office 2016 für Mac<br /><br />Office Online[[2]](#footnote-2)|Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|Outlook 2011 (nur AD RMS)<br /><br />Outlook 2016 für Mac<br /><br />Outlook für Mac|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
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
Unterstützt das Anzeigen und Bearbeiten von geschützten Dokumenten für iOS; unterstützt die Anzeige von geschützten Dokumenten für Android. Weitere Informationen finden Sie im Office-Blog im Beitrag zu [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Azure Rights Management-Unterstützung jetzt auch für Office für iPad und iPhone).

###### <a name="footnote-6"></a>Fußnote 6
Weitere Informationen finden Sie unter der Citrix [Produktdokumentation für WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html).

###### <a name="footnote-7"></a>Fußnote 7
Weitere Informationen finden Sie im Office-Blog im Beitrag zu: [OWA for Android now available on select devices](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) (OWA für Android ist nun für ausgewählte Geräte verfügbar).

###### <a name="footnote-8"></a>Fußnote 8
Weitere Informationen finden Sie im folgenden Beitrag zum „Enterprise und Mobility“-Blog: [SealPath brings RMS protection to AutoCAD:(https://blogs.technet.microsoft.com/enterprisemobility/2015/09/08/sealpath-brings-rms-protection-to-autocad/)


## <a name="more-information-about-azure-rms-support-for-office"></a>Weitere Informationen zur Azure RMS-Unterstützung für Office

Azure RMS ist eng in die Word-, Excel-, PowerPoint- und Outlook-Apps integriert. Dort wird diese Funktionalität oft als Information Rights Management (IRM) bezeichnet. Die folgenden Editionen von Office-Clients unterstützen den Schutz von Dateien und E-Mails mithilfe von Azure RMS:

- Office 365 ProPlus: Office 2016 und Office 2013

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Alle Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

Azure RMS mit Office Professional Plus 2010 oder Office Professional 2010:

- Erfordert die Rights Management-Freigabeanwendung für Windows

- Unter Windows 10 nicht unterstützt

- Die formularbasierte Authentifizierung für Verbundbenutzerkonten wird nicht unterstützt. Diese Konten müssen die integrierte Windows-Authentifizierung verwenden.

## <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Weitere Informationen zur Azure Information Protection-App für iOS und Android

Die Azure Information Protection-App für iOS und Android ersetzt die RMS-Freigabeanwendung für diese Geräte. Sie bietet dieselbe Funktionalität und unterstützt darüber hinaus durch Rights Management geschützte E-Mails und durch Rights Management geschützte PDF-Dateien in SharePoint Online.

Wenn Ihre iOS- und Android-Geräte bei Microsoft Intune registriert sind, können Sie diese App mithilfe einer richtlinienverwalteten App bereitstellen und verwalten. Weitere Informationen finden Sie in der Intune-Dokumentation unter [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console). Befolgen Sie in Schritt 2 dieser Intune-Dokumentation die Anweisungen zum Veröffentlichen einer richtlinienverwalteten App.

Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](../rms-client/mobile-app-faq.md).


## <a name="more-information-about-the-azure-information-protection-client-for-windows-preview"></a>Weitere Informationen zum Azure Information Protection-Client für Windows (Vorschau)

Diese Vorschauversion des Azure Information Protection-Clients ist für die Bewertung und für Feedbacks vorgesehen. Sie ersetzt die vorhandene Rights Management-Freigabeanwendung für Windows. 

Weitere Informationen zu dieser Vorschauversion des Clients finden Sie in der [Blogbeitragsankündigung](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/) und dem [Benutzerhandbuch zur Vorschau](../rms-client/client-user-guide.md).

## <a name="more-information-about-the-rights-management-sharing-application"></a>Weitere Informationen zur Rights Management-Freigabeanwendung

Weitere Informationen zur Rights Management-Freigabeanwendung für Windows finden Sie in den folgenden Ressourcen:

-   [Administratorhandbuch der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md)

Weitere Informationen zur Rights Management-Freigabeanwendung für mobile Plattformen finden Sie in den folgenden Ressourcen:

-   Laden Sie die relevante App über die Links auf der [Microsoft Rights Management-Seite](http://go.microsoft.com/fwlink/?LinkId=303970) herunter.

-   [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile Plattformen](https://technet.microsoft.com/dn451248)

> [!NOTE]
> Die RMS-Freigabeanwendung für iOS und Android wird ab sofort von der Azure Information Protection-App ersetzt.

## <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Weitere Informationen zu anderen Anwendungen, die Azure Information Protection unterstützen

Zusätzlich zu den Anwendungen in der Tabelle kann jede Anwendung, die APIs für den Azure Rights Management Service unterstützt, in Azure Informationen Protection integriert werden. Dazu zählen die Folgenden:

- Branchenanwendungen, die intern mithilfe der RMS-SDKs geschrieben wurden.

- Anwendungen von Softwareherstellern, die mithilfe der RMS-SDKs geschrieben wurden.

Weitere Informationen finden Sie im [Azure Information Protection-Entwicklerhandbuch](../develop/developers-guide.md).

## <a name="applications-that-are-not-supported-by-azure-rms"></a>Nicht von Azure RMS unterstützte Anwendungen

Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:

-   Microsoft Office für Mac 2011

-   Microsoft OneDrive for Business für SharePoint Server 2013

-   XPS-Viewer
 
Zusätzlich liegen bei der RMS-Freigabeanwendung folgende Einschränkungen vor:

-   Für Windows-Computer: Erfordert eine Mindestversion von Windows 7 Service Pack 1.



## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements-azure-rms.md).

Weitere Informationen dazu, wie die gängigsten Anwendungen Azure RMS unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](../understand-explore/applications-support.md).

Informationen dazu, wie die gängigsten Anwendungen für Azure RMS konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).


<!--HONumber=Dec16_HO3-->


