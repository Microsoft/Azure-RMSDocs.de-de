---
title: Unterstützung von Anwendungen für den RMS-Datenschutz für Azure Information Protection
description: Identifizieren Sie die Anwendungen und Lösungen mit integrierter Unterstützung für den Azure Rights Management-Dienst (Azure RMS). Azure RMS bietet Datenschutz für Azure Information Protection (AIP).
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 13454e0642cfaf60ed3bd742050cd3eb0d3a38dc
ms.sourcegitcommit: ee20112ada09165b185d9c0c9e7f1179fc39e7cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98659135"
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen AIP-Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


Die auf dieser Seite aufgeführten Anwendungen und Lösungen verfügen über integrierte Unterstützung für den Azure Rights Management-Dienst (Azure RMS), der den Schutz von Daten für Azure Information Protection gewährleistet.

Diese Anwendungen und Lösungen werden „RMS-aktiviert“ genannt. Sie bieten über Rights Management-Funktionen und [Nutzungseinschränkungen](configure-usage-rights.md), die über Rights Management-APIs eng integriert sind.

> [!NOTE]
> Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. 
>
> Für die AD RMS-Unterstützung unter iOS, Android, macOS und Windows Phone 8.1 ist zudem die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\)) erforderlich.
> 

## <a name="windows-rms-enlightened-applications"></a>RMS-aktivierte Anwendungen für Windows

|type  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    | - [Microsoft 365 Apps](#microsoft-365-app-support) <br />- Office 2010 <br />– Office 2013<br />- Office 2016 <br />– Office 2019 <br />- [Office für das Web (Anzeige von geschützten Dokumenten)](#viewing-protected-documents-in-office-for-the-web)<br />- [Webbrowser](#web-browser-support)        |
|[**Email**](#viewing-protected-content-in-email-clients)      |   – Outlook 2010<br />– Outlook 2013<br />– Outlook 2016 <br />– Outlook 2019 <br />– Outlook von Microsoft 365 Apps for Enterprise<br />- [Webbrowser](#web-browser-support)<br />- [Windows Mail](#email-clients-using-exchange-activesync-irm)|
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    |  – Visio von Microsoft 365-Apps, Office 2019 und Office 2016: **.vsdm,** **.vsdx,** **.vssm**, **.vstm**, **.vssx**, **.vstx** <br />– Azure Information Protection-Client für Windows: Text, Bilder, **PFILE** <br />– SealPath RMS-Plug-In für AutoCAD: **.dwg**       |
| | |

## <a name="macos-rms-enlightened-applications"></a>RMS-aktivierte Anwendungen für macOS

|type  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    |  – Microsoft 365-Apps, Version 16.40 oder höher <br />– Office 2019 für Mac, Version 16.40 oder höher<br />– Office 2016 für Mac, Version 16.16.27 oder höher<br />- [Office für das Web](#viewing-protected-documents-in-office-for-the-web)<br />- [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)   |   – Outlook 2019 für Mac, Version 16.40 oder höher<br />– Outlook 2016 für Mac, Version 16.16.27 oder höher<br />- [Webbrowser](#web-browser-support)     |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    | RMS-Freigabe-App (Anzeige von geschützten Texten, Abbildungen und generisch geschützten Dateien)   |
| | |

## <a name="android-rms-enlightened-applications"></a>RMS-aktivierte Anwendungen für Android

|type  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    |– GigaTrust App für Android<br />- [Office für das Web](#viewing-protected-documents-in-office-for-the-web)<br />– Office Mobile (sofern keine Vertraulichkeitsbezeichnungen verwendet werden, beschränkt auf die Anzeige und Bearbeitung geschützter Dokumente) <br />- [Webbrowser](#web-browser-support)      |
|[**Email**](#viewing-protected-content-in-email-clients)     | - [9Folders](#email-clients-using-exchange-activesync-irm)<br />– Azure Information Protection-App (Anzeige von geschützten E-Mails)<br />– BlackBerry Work <br />- [GigaTrust App für Android](#email-clients-using-exchange-activesync-irm) <br />– Citrix WorxMail <br />- [NitroDesk](#email-clients-using-exchange-activesync-irm)<br />- [Outlook für Android](#email-clients-using-exchange-activesync-irm)<br />- [Samsung E-Mail (S3 und neuer)](#email-clients-using-exchange-activesync-irm)<br />– TITUS-Klassifizierung für mobile Geräte <br /><br />- [Webbrowser](#web-browser-support)       |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    |  Azure Information Protection-App (Anzeige von geschützten Texten und Abbildungen)  |
| | |


## <a name="ios-rms-enlightened-applications"></a>RMS-aktivierte Anwendungen für iOS

|type  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    |  – GigaTrust<br />– Office Mobile <br />- [Office für das Web](#viewing-protected-documents-in-office-for-the-web)<br />– TITUS Docs<br />- [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)     |   – Azure Information Protection-App (Anzeige von geschützten E-Mails)<br />– BlackBerry Work<br />– Citrix WorxMail <br />- [NitroDesk](#email-clients-using-exchange-activesync-irm)<br />- [Outlook für iPad und iPhone](#email-clients-using-exchange-activesync-irm)<br />– TITUS Mail <br />- [Webbrowser](#web-browser-support)     |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)     | – Azure Information Protection-App (Anzeige von geschützten Texten und Bildern)<br />– TITUS Docs: **PFILE**  |
| | |

## <a name="windows-10-mobile-rms-enlightened-applications"></a>RMS-aktivierte Anwendungen für Windows 10 Mobile

|type  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    | – Office Mobile-Apps (Anzeige von geschützter Dokumentation mit Azure RMS) <br />- [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)    |  – Citrix WorxMail <br />– Outlook Mail (Ansicht von geschützten E-Mails) <br />- [Webbrowser](#web-browser-support)     |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    | Nicht unterstützt   |
| | |

## <a name="blackberry-10-rms-enlightened-applications"></a>RMS-aktivierte Anwendungen für BlackBerry 10

|type  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    | - [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)   | - [BlackBerry-E-Mail](#email-clients-using-exchange-activesync-irm) <br />- [Webbrowser](#web-browser-support)      |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    | Nicht unterstützt   |
| | |


## <a name="additional-details-about-rms-enlightened-applications"></a>Weitere Informationen zu RMS-aktivierten Anwendungen

Weitere Informationen zu den oben aufgeführten Tabellen mit RMS-aktivierten Anwendungen finden Sie unter:

- [Anzeigen geschützter Inhalte in E-Mail-Clients](#viewing-protected-content-in-email-clients)
- [Unterstützte Text-und Bilddateitypen](#supported-text-and-image-file-types)
- [Microsoft 365 App-Unterstützung](#microsoft-365-app-support)
- [Anzeigen von in Office für das Web geschützten Dokumenten](#viewing-protected-documents-in-office-for-the-web)
- [Webbrowserunterstützung](#web-browser-support)
- [E-Mail-Clients mit Informationen Rights Management (IRM) von Exchange ActiveSync](#email-clients-using-exchange-activesync-irm)

### <a name="viewing-protected-content-in-email-clients"></a>Anzeigen geschützter Inhalte in E-Mail-Clients

Wenn ein E-Mail-Client eine Nachricht schützt, werden alle Office-Dateien, die an die Nachricht angehängt und aktuell nicht geschützt sind, zusammen mit der E-Mail-Nachricht geschützt. In solchen Fällen können sowohl die E-Mail-Nachricht als auch die Anlagen im E-Mail-Client nur von autorisierten Empfängern angezeigt werden.

Wenn jedoch nur die Anlage, nicht aber die E-Mail-Nachricht selbst geschützt ist, kann die Anlage vom E-Mail-Client selbst von autorisierten Empfängern nicht in der Vorschau angezeigt werden.

> [!TIP]
> Bei der Nutzung von E-Mail-Clients, die den Schutz von E-Mails nicht unterstützen, sollten Sie [Nachrichtenflussregeln von Exchange Online zum Anwenden dieses Schutzes](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8) verwenden.

### <a name="supported-text-and-image-file-types"></a>Unterstützte Text-und Bilddateitypen

Andere Dateitypen als Office-Dateien und E-Mail-Nachrichten umfassen Text- und Bilddateitypen mit Erweiterungen wie **.txt,** **.xml,** **.jpg,** und **.jpeg**. 

Die Dateierweiterung dieser Dateien ändert sich, nachdem sie durch Rights Management nativ geschützt wurden und dann schreibgeschützt sind. 

Dateien mit der Dateierweiterung **.pfile** können nicht nativ geschützt werden, wenn sie generisch durch Rights Management geschützt sind.

Weitere Informationen finden Sie unter [Unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md).

### <a name="microsoft-365-app-support"></a>Microsoft 365 App-Unterstützung

Enthält: 
- Office-Apps für die in der [Tabelle der unterstützten Versionen für Microsoft 365-Apps nach Updatekanal](/officeupdates/update-history-microsoft365-apps-by-date) aufgeführten Versionen von Microsoft 365 Apps for Business oder Microsoft 365 Business Premium, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Microsoft 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.
- Microsoft 365 Apps for Enterprise

### <a name="viewing-protected-documents-in-office-for-the-web"></a>Anzeigen von in Office für das Web geschützten Dokumenten

Wird nur mit Microsoft SharePoint und OneDrive unterstützt, und die Dokumente sind vor dem Upload in eine geschützte Bibliothek ungeschützt.

### <a name="web-browser-support"></a>Webbrowserunterstützung

- Webbrowser werden für **Word-, Excel- und PowerPoint-Dateien** unterstützt, wenn die [Office-Anlagen](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) mit den [neuen Funktionen von Microsoft 365 Message Encryption](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) geschützt sind.

- Für **E-Mails** werden Webbrowser nur in den folgenden Szenarios unterstützt:

    - Wenn sowohl Sender als auch Empfänger derselben Organisation angehören
    - Wenn der Sender oder Empfänger Exchange Online verwenden
    - Wenn der Sender Exchange lokal in einer Hybridkonfiguration verwendet 

### <a name="email-clients-using-exchange-activesync-irm"></a>E-Mail-Clients mit Exchange ActiveSync IRM

Die folgenden E-Mail-Clients nutzen Exchange ActiveSync IRM, das vom Exchange-Administrator aktiviert werden muss:

- Windows Mail
- 9Folders
- GigaTrust App für Android
- NitroDesk
- Outlook für Android
- Samsung Email (S3 und neuer)
- Outlook für iPad und iPhone
- Blackberry-E-Mail

Benutzer können zwar die Funktionen zum Anzeigen, Antworten und allen Antworten für geschützte E-Mail-Nachrichten ausführen, können selbst aber keine neuen E-Mail-Nachrichten schützen.
 
Sollte die E-Mail-Anwendung die Nachricht nicht rendern können, weil IRM in Exchange ActiveSync deaktiviert ist, kann der Empfänger die E-Mail nur in einem Webbrowser sehen, wenn der Sender entweder Exchange Online oder Exchange lokal in einer Hybridkonfiguration verwendet. 

## <a name="azure-rms-support-for-office"></a>Azure RMS-Unterstützung für Office

Azure RMS ist eng in die Word-, Excel-, PowerPoint- und Outlook-Apps integriert. Dort wird diese Funktionalität oft als Information Rights Management (IRM) bezeichnet. 

- [Windows-Computer für Information Rights Management (IRM)](#windows-computers-for-information-rights-management-irm)
- [Mac-Computer für Information Rights Management (IRM)](#mac-computers-for-information-rights-management-irm)

Siehe auch: [Dienstbeschreibung für Office-Anwendungen](/office365/servicedescriptions/office-applications-service-description/office-applications-service-description)

### <a name="windows-computers-for-information-rights-management-irm"></a>Windows-Computer für Information Rights Management (IRM)

Die folgenden Office-Clientsuites unterstützen den Schutz von Dateien und E-Mails auf Windows-Computern mithilfe von Azure Rights Management:

- **Office-Apps** für die in der [Tabelle der unterstützten Versionen für Microsoft 365-Apps nach Updatekanal](/officeupdates/update-history-microsoft365-apps-by-date) aufgeführten Versionen von Microsoft 365 Apps for Business oder Microsoft 365 Business Premium, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Microsoft 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.

- **Microsoft 365 Apps for Enterprise**

    Diese Editionen von Office sind in den meisten Abonnements enthalten, bei denen durch Azure Information Protection Datenschutz gewährleistet wird. Überprüfen Sie Ihre Abonnementinformationen, um zu sehen, ob Microsoft 365 Apps for Enterprise ProPlus enthalten ist. Sie finden diese Informationen auch im [Datenblatt zu Azure Information Protection](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- **Office Professional Plus 2019**

- **Office Professional Plus 2016**

- **Office Professional Plus 2013**

- **Office Professional Plus 2010 mit Service Pack 2**

Alle Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

#### <a name="azure-rights-management-service-with-office-professional-plus-2010-and-service-pack-2-or-office-professional-2010-with-service-pack-2"></a>Azure Rights Management-Dienst mit Office Professional Plus 2010 und Service Pack 2 bzw. Office Professional 2010 mit Service Pack 2

Für die Verwendung von Azure Rights Management mit Office Professional Plus 2010 und Service Pack 2 bzw. Office Professional 2010 und Service Pack 2 benötigen Sie auch den AIP-Client für Windows.

Außerdem wird diese Konfiguration:

- unter Windows 10 nicht unterstützt.
- Die formularbasierte Authentifizierung für Verbundbenutzerkonten wird nicht unterstützt. Diese Konten müssen die integrierte Windows-Authentifizierung verwenden.
- Unterstützt nicht die Möglichkeit, den Vorlagenschutz durch benutzerdefinierte Berechtigungen, die mit dem AIP-Client ausgewählt wurden, außer Kraft zu setzen. In diesem Fall muss der ursprüngliche Schutz zunächst entfernt werden, bevor benutzerdefinierte Berechtigungen angewendet werden können.

### <a name="mac-computers-for-information-rights-management-irm"></a>Mac-Computer für Information Rights Management (IRM)

Die folgenden Office-Clientsuites unterstützen den Schutz von Dateien und E-Mails auf macOS-Computern mithilfe von Azure RMS:

- Microsoft 365 Apps for Enterprise
- Office Standard 2019 für Mac
- Office Standard 2016 für Mac

Alle Editionen von Office für Mac 2019 und Office für Mac 2016 können geschützte Inhalte nutzen.

> [!TIP]
> Wenn Sie den klassischen Client auf einem Mac-Computer verwenden, können sich die folgenden häufig gestellten Fragen als nützlich erweisen: [Wie konfiguriere ich einen Macintosh-Computer für den Schutz und die Nachverfolgung von Dokumenten?](faqs-classic.md#how-do-i-configure-a-mac-computer-to-protect-and-track-documents)
> 
## <a name="azure-information-protection-apps-for-ios-and-android"></a>Azure Information Protection-Apps für iOS und Android

Die Azure Information Protection-App für iOS und Android stellt einen Viewer für rechtegeschützte E-Mail-Nachrichten (**RPMSG**-Dateien) für den Fall bereit, dass auf diesen mobilen Geräten keine E-Mail-App installiert ist, mit der geschützte E-Mails geöffnet werden können. Mit dieser App können Sie außerdem rechtegeschützte PDF-Dateien, Bilder und Textdateien anzeigen.

Wenn Ihre iOS- und Android-Geräte durch Microsoft Intune registriert wurden, können Benutzer die App über das Unternehmensportal installieren, und Sie können die App mithilfe der [App-Schutzrichtlinien](/intune/apps/app-protection-policies) von Intune verwalten.

Weitere Informationen zur Verwendung der App finden Sie unter [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](./rms-client/mobile-app-faq.md).

## <a name="the-azure-information-protection-client-for-windows"></a>Azure Information Protection-Client für Windows

Sie müssen den AIP-Client in Ihrem System bereitstellen, um Azure Information Protection zu verwenden. 

Laden Sie den Client für einheitliche Bezeichnungen von der [Microsoft Azure Information Protection-Seite](https://go.microsoft.com/fwlink/?LinkId=303970) herunter. 

   Weitere Informationen finden Sie unter

- [Die Clientseite von Azure Information Protection](rms-client/use-client.md)
- [Administratorleitfaden für den Client für einheitliche Bezeichnungen](./rms-client/clientv2-admin-guide.md)
- [Benutzerleitfaden für den Client für einheitliche Bezeichnungen](./rms-client/clientv2-user-guide.md)

### <a name="aips-classic-client"></a>Der klassische AIP-Client

Wenn Sie noch kein Upgrade durchgeführt haben, ist möglicherweise weiterhin der [klassische Azure Information Protection-Legacyclient](./rms-client/aip-client.md) bereitgestellt.

Weitere Informationen über die Bereitstellung und Verwendung des klassischen Clients finden Sie unter:

- [Klassischer AIP-Client](./rms-client/aip-client.md)
- [Administratorleitfaden für den klassischen Client](./rms-client/client-admin-guide.md)
- [Benutzerleitfaden für den klassischen Client](./rms-client/client-user-guide.md)

> [!NOTE]
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. 
>
> In diesem Zeitraum haben alle aktuellen Azure Information Protection-Kunden die Möglichkeit, zur Microsoft Information Protection-Lösung für einheitliche Bezeichnungen zu wechseln. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>
> 
>

## <a name="rights-management-sharing-app"></a>Rights Management-Freigabeanwendung

Für Mac-Computer stellt die Rights Management-Freigabeanwendung einen Viewer für geschützte PDF-Dateien (**PPDF**), geschützte Textbilder und allgemein geschützte Dateien bereit. Sie kann auch Bilddateien, jedoch keine anderen Dateien schützen. Verwenden Sie zum Schützen von Office-Dateien auf diesen Computern Office für Mac oder Microsoft 365 Apps for Enterprise. 

Weitere Informationen finden Sie unter [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile Plattformen](/previous-versions/msdn10/dn451248(v=msdn.10)).

Laden Sie die Rights Management-Freigabeanwendung für Mac-Computer von der [Microsoft Azure Information Protection-Seite](https://go.microsoft.com/fwlink/?LinkId=303970) herunter.

## <a name="other-applications-that-support-azure-information-protection"></a>Unterstützung von Azure Information Protection durch Anwendungen

Zusätzlich zu den oben aufgeführten Anwendungen kann jede Anwendung, die APIs für den Azure Rights Management-Dienst unterstützt, mit Azure Informationen Protection integriert werden. 

Beispiele hierfür können Branchenanwendungen sein, die intern geschrieben wurden, oder Anwendungen von Softwareanbietern, die mit den RSM SDKs geschrieben wurden.

## <a name="applications-that-are-not-supported-by-azure-rms"></a>Nicht von Azure RMS unterstützte Anwendungen

Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:

- Microsoft OneDrive for SharePoint Server 2013
- XPS-Viewer
- Anwendungen, die unter Windows-Versionen vor Windows 7, Service Pack 1, ausgeführt werden


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen:

- [Anforderungen für Azure Information Protection](requirements.md).
- [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](./applications-support.md)
- [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md)

Die neuesten Informationen über Lösungen, die den Azure Rights Management-Dienst und Azure Information Protection unterstützen, finden Sie im Blogbeitrag, [Microsoft Ignite 2019 - Microsoft Information Protection solutions Partner ecosystem showcase](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Ignite-2019-Microsoft-Information-Protection-solutions/ba-p/967024) (Microsoft Ignite 2019 – Vorstellung des Partnerökosystems für Microsoft Information Protection-Lösungen).