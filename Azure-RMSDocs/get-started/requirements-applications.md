---
title: 'Azure RMS-Anforderungen: Anwendungen | Azure RMS'
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/15/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b02be530af8ee1bc1e5d5f16275d2fb28e2134b7
ms.openlocfilehash: a885ab6deaf874a8c66623c34eddc2b2778e0005


---


# Azure RMS-Anforderungen: Anwendungen

*Gilt für: Azure Rights Management, Office 365*


Ermitteln Sie in der folgenden Tabelle die Anwendungen, die systemeigene Unterstützung für Azure RMS bieten, was bedeutet, dass RMS in diese Anwendungen eng integriert ist. Dabei kommen RMS-APIs zur Unterstützung von Nutzungseinschränkungen zum Einsatz. Diese Anwendungen werden auch als "RMS-aktiviert" bezeichnet:

Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. Außerdem ist für die AD RMS-Unterstützung unter iOS, Android, OS X und Windows Phone 8.1 die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](https://technet.microsoft.com/library/dn673574.aspx) erforderlich.

Informationen über die Tabellenspalten:

-   **Geschützte PDF**: Dateien mit der Dateierweiterung PPDF, die automatisch erstellt werden, wenn Sie zur Freigabe von Office- und PDF-Dateien per E-Mail die RMS-Freigabeanwendung verwenden. Die RMS-Freigabeanwendung umfasst einen Reader für geschützte PDF-Dateien. Zuvor konnten Sie erstellte PDF-Dateien, die Sie mithilfe von Azure RMS oder AD RMS geschützt haben, weiterhin mithilfe von Foxit Reader und Nitro Pro auf Windows-, iOS- und Android-Geräten lesen.

-   **E-Mail**: Die aufgeführten E-Mail-Clients können die E-Mail-Nachricht selbst schützen, wodurch angehängte Dateien automatisch geschützt sind. In diesem Szenario kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte (Nachricht und Anhang) anzeigen. Wenn eine E-Mail-Nachricht selbst jedoch nicht geschützt der Anhang jedoch geschützt ist, kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte nicht anzeigen.

-   **Andere Dateitypen**: Text- und Bilddateien umfassen u. a. Dateien mit der Dateierweiterung TXT, XML, JPG und JPEG. Die Dateierweiterung dieser Dateien ändert sich, sobald sie systemintern durch RMS geschützt werden und schreibgeschützt sind. Dateien mit der Dateierweiterung ".pfile" können nicht systemintern geschützt werden, wenn sie generisch durch RMS geschützt sind. Weitere Informationen finden Sie im [Rights Management-Freigabeanwendung – Administratorhandbuch](../rms-client/sharing-app-admin-guide.md).


|**Gerätebetriebssystem**|Word, Excel, PowerPoint|Geschützte PDF|E-Mail|Weitere Dateitypen|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Mobile-Apps (nur Azure RMS)[1](#footnote-1)<br /><br />Office Online[[2]](#footnote-2)|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS-Freigabeanwendung|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA)[3](#footnote-3)<br /><br />Windows Mail[[4]](#footnote-4)|RMS-Freigabeanwendung für Windows: Text, Bilder, PFILE<br /><br />Siemens JT2Go: JT-Dateien (nur Windows 10)|
|**iOS**|Office für iPad und iPhone[[5]](#footnote-5)<br /><br />Office Online[[2]](#footnote-2)<br /><br />TITUS-Dokumentation|Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)<br /><br />TITUS-Dokumentation|Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für iPad und iPhone[[4]](#footnote-4)<br /><br />OWA für iOS[[3]](#footnote-3)<br /><br />TITUS Mail|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE<br /><br />TITUS-Dokumentation: PFILE|
|**Android**|GigaTrust App für Android<br /><br />Office Online (nur Azure RMS) [[2]](#footnote-2)<br /><br />Office Mobile [[1]](#footnote-1)|GigaTrust App für Android<br /><br />Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|9Folders[[4]](#footnote-4)<br /><br />GigaTrust App für Android[[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk[[4]](#footnote-4)<br /><br />Outlook für Android [[4]](#footnote-4)<br /><br />OWA für Android [[3]](#footnote-3) und [[7]](#footnote-7)<br /><br />Samsung E-Mail (S3 und neuer)[7](#footnote-7)<br /><br />TITUS-Klassifizierung für mobile Geräte|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
|**OS X**|Office 2011 (nur AD RMS)<br /><br />Office 2016 für Mac<br /><br />Office Online[[2]](#footnote-2)|Foxit Reader<br /><br />RMS-Freigabeanwendung[[1]](#footnote-1)|Outlook 2011 (nur AD RMS)<br /><br />Outlook 2016 für Mac<br /><br />Outlook für Mac|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
|**Windows 10 Mobile**|Office Mobile-Apps (nur Azure RMS)[[1]](#footnote-1)|Nicht unterstützt|Citrix WorxMail [[6]](#footnote-6)<br /><br />Outlook Mail|Nicht unterstützt|
|**Windows RT**|Office 2013 RT<br /><br />Office Online[[2]](#footnote-2)|Nicht unterstützt|Outlook 2013 RT<br /><br />E-Mail-App für Windows<br /><br />Windows Mail[[4]](#footnote-4)|Siemens JT2Go: JT-Dateien|
|**Windows Phone 8.1**|Office Mobile (nur AD RMS)|RMS-Freigabeanwendung[[1]](#footnote-1)|Outlook Mobile[[4]](#footnote-4)|RMS-Freigabeanwendung[[1]](#footnote-1): Text, Bilder, PFILE|
|**Blackberry 10**|Nicht unterstützt|Nicht unterstützt|Blackberry-E-Mail[[4]](#footnote-4)|Nicht unterstützt|


###### Fußnote 1
Unterstützt die Anzeige geschützter Inhalte.

###### Fußnote 2 
Unterstützt die Anzeige von geschützten Inhalten in SharePoint Online, OneDrive for Business und Outlook Web Access.

###### Fußnote 3
Wenn ein Empfänger über ein Postfach in einer lokalen Exchange-Installation verfügt und eine geschützte E-Mail empfängt, kann dieser Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden.  Dieser Inhalt kann nicht in Outlook Web Access geöffnet werden.

###### Fußnote 4
Verwendet Exchange ActiveSync IRM, das vom Exchange-Administrator aktiviert werden muss. Benutzer können „Anzeigen“, „Antworten“ und „Allen antworten“ für geschützte E-Mail-Nachrichten ausführen, können selbst aber keine neuen E-Mail-Nachrichten schützen.

Wenn ein Empfänger über ein Postfach in einer lokalen Exchange-Installation verfügt und er eine geschützte E-Mail von einer anderen Organisation empfängt, die ebenfalls Exchange verwendet, kann der Inhalt nur in einem funktionsreichen E-Mail-Client wie Outlook geöffnet werden.  Dieser Inhalt kann nicht auf einem Gerät geöffnet werden, das Exchange Active Sync IRM verwendet.

###### Fußnote 5
Unterstützt das Anzeigen und Bearbeiten von geschützten Dokumenten. Weitere Informationen finden Sie im Office-Blog im Beitrag zu [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Azure Rights Management-Unterstützung jetzt auch für Office für iPad und iPhone).

###### Fußnote 6
Weitere Informationen finden Sie unter der Citrix [Produktdokumentation für WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html).

###### Fußnote 7
Weitere Informationen finden Sie im Office-Blog im Beitrag zu: [OWA for Android now available on select devices](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) (OWA für Android ist nun für ausgewählte Geräte verfügbar).

## Weitere Informationen zur Azure RMS-Unterstützung für Office

Azure RMS ist eng in die Word-, Excel-, PowerPoint- und Outlook-Apps integriert. Dort wird diese Funktionalität oft als Information Rights Management (IRM) bezeichnet. Die folgenden Editionen von Office-Clients unterstützen den Schutz von Dateien und E-Mails mithilfe von Azure RMS:

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Alle Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

Azure RMS mit Office Professional Plus 2010 oder Office Professional 2010:

- Erfordert die Rights Management-Freigabeanwendung für Windows

- Unter Windows 10 nicht unterstützt


## Weitere Informationen zur Rights Management-Freigabeanwendung

Weitere Informationen zur Rights Management-Freigabeanwendung für Windows finden Sie in den folgenden Ressourcen:

-   [Administratorhandbuch der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md)

Weitere Informationen zur Rights Management-Freigabeanwendung für mobile Plattformen finden Sie in den folgenden Ressourcen:

-   Laden Sie die relevante App über die Links auf der [Microsoft Rights Management-Seite](http://go.microsoft.com/fwlink/?LinkId=303970) herunter.

-   Wenn Sie über Microsoft Intune verfügen, können Sie die App mithilfe einer richtlinienverwalteten App bereitstellen und verwalten: 

    -   Weitere Informationen zu iOS- und Android-Geräten, die von Intune registriert wurden, finden Sie unter: [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console).

    -   Weitere Informationen zu Android-Geräten, die nicht von Intune registriert wurden, finden Sie unter: [Erstellen und Bereitstellen von Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).

-   [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile Plattformen](https://technet.microsoft.com/dn451248)



## Weitere Informationen zu anderen Anwendungen, die Azure RMS unterstützen

Zusätzlich zu den Anwendungen in der Tabelle kann jede Anwendung, die diese RMS-APIs unterstützt, in Azure RMS integriert werden. Hierzu zählen:

- Branchenanwendungen, die intern mithilfe des RMS SDK geschrieben wurden.

- Anwendungen von Softwareherstellern, die mithilfe des RMS SDK geschrieben wurden.

Weitere Informationen zum SDK finden Sie unter [Microsoft Rights Management SDK](../develop/developers-guide.md).

## Nicht von Azure RMS unterstützte Anwendungen

Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:

-   Microsoft Office für Mac 2011

-   Microsoft OneDrive for Business für SharePoint Server 2013

-   XPS-Viewer
 
Zusätzlich liegen bei der RMS-Freigabeanwendung folgende Einschränkungen vor:

-   Für Windows-Computer: Erfordert eine Mindestversion von Windows 7 Service Pack 1.



## Nächste Schritte
Weitere Anforderungen finden Sie unter [Voraussetzungen für Azure Rights Management](requirements-azure-rms.md).

Weitere Informationen dazu, wie die gängigsten Anwendungen Azure RMS unterstützen, finden Sie unter [Unterstützung von Azure Rights Management durch Anwendungen](../understand-explore/applications-support.md).

Informationen dazu, wie die gängigsten Anwendungen für Azure RMS konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).


<!--HONumber=Aug16_HO3-->


