---
title: Anwendungsunterstützung für den RMS-Datenschutz für Azure Information Protection
description: Identifizieren Sie die Anwendungen und Lösungen mit nativer Unterstützung für den Azure Rights Management-Dienst (Azure RMS). Azure RMS bietet Datenschutz für Azure Information Protection (AIP).
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/04/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 37cb3b1f3c3eb60459cabe813f0cb00fb69b7d5b
ms.sourcegitcommit: dec5df81b569283a72f0a983d3f53b82cbbc562c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87802163"
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Die auf dieser Seite aufgeführten Anwendungen und Lösungen verfügen über systemeigene Unterstützung für den Azure Rights Management (Azure RMS)-Dienst, der Datenschutz für Azure Information Protection bereitstellt.

Diese Anwendungen und Lösungen werden als "RMS-angezündet" bezeichnet und verfügen über Rights Management-und [Nutzungseinschränkungen](configure-usage-rights.md) , die eng mit Rights Management-APIs integriert sind.

> [!NOTE]
> Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. 
>
> AD RMS Unterstützung unter IOS, Android, macOS und Windows Phone 8,1 erfordert auch die [Active Directory Rights Management Services Mobile-Geräte Erweiterung](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\)).
> 

## <a name="windows-rms-enlightened-applications"></a>Windows RMS-aktivierte Anwendungen

|Typ  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    | - [Office 365-apps](#office-365-app-support) <br />- Office 2010 <br />-Office 2013<br />- Office 2016 <br />-Office 2019 <br />- [Office für das Web (Anzeigen geschützter Dokumente)](#viewing-protected-documents-in-office-for-the-web)<br />- [Webbrowser](#web-browser-support)        |
|[**Email**](#viewing-protected-content-in-email-clients)      |   -Outlook 2010<br />-Outlook 2013<br />-Outlook 2016 <br />-Outlook 2019 <br />-Outlook von Office 365 ProPlus<br />- [Webbrowser](#web-browser-support)<br />- [Windows Mail](#email-clients-using-exchange-activesync-irm)|
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    |  -Visio von Office 365-apps, Office 2019 und Office 2016: **vsdm,** **vsdx,** **VSSM**, **VSTM**, **vssx**, **vstx** <br />-Azure Information Protection Client für Windows: Text, Bilder, **Pfile** <br />-Sealpath RMS-Plug-in für AutoCAD: **. DWG**       |
| | |

## <a name="macos-rms-enlightened-applications"></a>mit macOS RMS aktivierte Anwendungen

|Typ  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    |  -Office 365-apps<br />-Office 2019 für Mac<br />-Office 2016 für Mac<br />- [Office für das Web](#viewing-protected-documents-in-office-for-the-web)<br />- [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)   |   -Outlook 2019 für Mac<br />-Outlook 2016 für Mac<br />- [Webbrowser](#web-browser-support)     |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    | RMS-Freigabe-App (Anzeige von geschützten Texten, Abbildungen und generisch geschützten Dateien)   |
| | |

## <a name="android-rms-enlightened-applications"></a>Android RMS-aktivierte Anwendungen

|Typ  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    |-GigaTrust App für Android<br />- [Office für das Web](#viewing-protected-documents-in-office-for-the-web)<br />-Office Mobile (es sei denn, Sie verwenden Vertraulichkeits Bezeichnungen, sind auf das Anzeigen und bearbeiten geschützter Dokumente beschränkt) <br />- [Webbrowser](#web-browser-support)      |
|[**Email**](#viewing-protected-content-in-email-clients)     | - [9Folders](#email-clients-using-exchange-activesync-irm)<br />-Azure Information Protection app (Anzeigen geschützter e-Mails)<br />-BlackBerry-Arbeit <br />- [GigaTrust App für Android](#email-clients-using-exchange-activesync-irm) <br />-Citrix worxmail <br />- [NitroDesk](#email-clients-using-exchange-activesync-irm)<br />- [Outlook für Android](#email-clients-using-exchange-activesync-irm)<br />- [Samsung-e-Mail (S3 und höher)](#email-clients-using-exchange-activesync-irm)<br />-Titus-Klassifizierung für mobile Geräte <br /><br />- [Webbrowser](#web-browser-support)       |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    |  Azure Information Protection-App (Anzeige von geschützten Texten und Abbildungen)  |
| | |


## <a name="ios-rms-enlightened-applications"></a>mit IOS RMS aktivierte Anwendungen

|Typ  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    |  -GigaTrust<br />-Office Mobile <br />- [Office für das Web](#viewing-protected-documents-in-office-for-the-web)<br />-Titus docs<br />- [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)     |   -Azure Information Protection app (Anzeigen geschützter e-Mails)<br />-BlackBerry-Arbeit<br />-Citrix worxmail <br />- [NitroDesk](#email-clients-using-exchange-activesync-irm)<br />- [Outlook für iPad und iPhone](#email-clients-using-exchange-activesync-irm)<br />-Titus Mail <br />- [Webbrowser](#web-browser-support)     |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)     | -Azure Information Protection app (Anzeigen von Schutz von Text und Bildern)<br />-Titus docs: **Pfile**  |
| | |

## <a name="windows-10-mobile-rms-enlightened-applications"></a>Windows 10 Mobile RMS-aktivierte Anwendungen

|Typ  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    | -Mobile Office-Apps (Anzeigen geschützter Dokumente mithilfe Azure RMS) <br />- [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)    |  -Citrix worxmail <br />-Outlook Mail (Anzeigen geschützter e-Mails) <br />- [Webbrowser](#web-browser-support)     |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    | Nicht unterstützt   |
| | |

## <a name="blackberry-10-rms-enlightened-applications"></a>BlackBerry 10 RMS-aktivierte Anwendungen

|Typ  |Unterstützte Anwendungen   |
|---------|---------|
|**Word, Excel, PowerPoint**    | - [Webbrowser](#web-browser-support)    |
|[**Email**](#viewing-protected-content-in-email-clients)   | - [BlackBerry-e-Mail](#email-clients-using-exchange-activesync-irm) <br />- [Webbrowser](#web-browser-support)      |
|[**Weitere Dateitypen**](#supported-text-and-image-file-types)    | Nicht unterstützt   |
| | |


## <a name="additional-details-about-rms-enlightened-applications"></a>Weitere Informationen zu RMS-fähigen Anwendungen

Weitere Informationen zu den oben aufgeführten Tabellen mit RMS-fähigen Anwendungen finden Sie unter:

- [Anzeigen geschützter Inhalte in e-Mail-Clients](#viewing-protected-content-in-email-clients)
- [Unterstützte Text-und Bild Dateitypen](#supported-text-and-image-file-types)
- [Office 365-app-Unterstützung](#office-365-app-support)
- [Anzeigen geschützter Dokumente in Office für das Web](#viewing-protected-documents-in-office-for-the-web)
- [Webbrowser Unterstützung](#web-browser-support)
- [E-Mail-Clients mithilfe von Exchange ActiveSync-Informationen Rights Management (unm)](#email-clients-using-exchange-activesync-irm)

### <a name="viewing-protected-content-in-email-clients"></a>Anzeigen geschützter Inhalte in e-Mail-Clients

Wenn ein e-Mail-Client eine Nachricht schützt, werden alle Office-Dateien, die an die Nachricht angefügt sind und derzeit nicht geschützt sind, mit der e-Mail-Nachricht geschützt. In solchen Fällen können die e-Mail-Nachricht und die Anlagen nur von autorisierten Empfängern im e-Mail-Client angezeigt werden.

Wenn jedoch nur die Anlage geschützt ist, aber nicht die e-Mail-Nachricht selbst, kann die Anlage nicht durch den e-Mail-Client angezeigt werden, auch nicht durch autorisierte Empfänger.

> [!TIP]
> Bei der Nutzung von E-Mail-Clients, die den Schutz von E-Mails nicht unterstützen, sollten Sie [Nachrichtenflussregeln von Exchange Online zum Anwenden dieses Schutzes](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8) verwenden.

### <a name="supported-text-and-image-file-types"></a>Unterstützte Text-und Bild Dateitypen

Andere Dateitypen als Office-Dateien und e-Mail-Nachrichten enthalten Text-und Bild Dateitypen mit Erweiterungen wie **txt,** **XML,** **JPG** und **JPEG.** 

Diese Dateien ändern die Dateinamenerweiterung, nachdem Sie durch Rights Management System intern geschützt wurden, und werden dann schreibgeschützt. 

Dateien, die nicht System intern geschützt werden können, haben die Dateinamenerweiterung **. Pfile** , nachdem Sie durch Rights Management generisch geschützt wurden.

Weitere Informationen finden Sie unter [Unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md).

### <a name="office-365-app-support"></a>Office 365-app-Unterstützung

Enthält: 
- Office-Apps, Mindestversion 1805, Build 9330,2078 aus Office 365 Business oder Microsoft 365 Business. Wird nur unterstützt, wenn dem Benutzer eine Lizenz für Azure Rights Management (auch bekannt als Azure Information Protection für Office 365) zugewiesen wird.
- Office 365 ProPlus-apps

### <a name="viewing-protected-documents-in-office-for-the-web"></a>Anzeigen geschützter Dokumente in Office für das Web

Wird nur mit Microsoft SharePoint und onedrive unterstützt, und die Dokumente sind ungeschützt, bevor Sie in eine geschützte Bibliothek hochgeladen werden.

### <a name="web-browser-support"></a>Webbrowserunterstützung

- Webbrowser werden für **Word-, Excel-und PowerPoint-** Dateien unterstützt, wenn die [Office-Anlagen](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) mithilfe [der Nachrichten Verschlüsselung von Office 365 mit den neuen Funktionen](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)geschützt werden.

- Für **e-Mails** werden Webbrowser nur in den folgenden Szenarien unterstützt:

    - Wenn der Absender und der Empfänger Teil derselben Organisation sind
    - Wenn der Absender oder Empfänger Exchange Online verwendet
    - Wenn der Absender Exchange lokal in einer Hybrid Konfiguration verwendet 

### <a name="email-clients-using-exchange-activesync-irm"></a>E-Mail-Clients mithilfe von Exchange ActiveSync-IRiM

Die folgenden e-Mail-Clients verwenden Exchange ActiveSync unm, das vom Exchange-Administrator aktiviert werden muss:

- Windows Mail
- 9Folders
- GigaTrust App für Android
- NitroDesk
- Outlook für Android
- Samsung Email (S3 und neuer)
- Outlook für iPad und iPhone
- BlackBerry-e-Mail

Benutzer können geschützte e-Mails anzeigen, Antworten und Antworten, aber keine neuen e-Mail-Nachrichten schützen.
 
Sollte die E-Mail-Anwendung die Nachricht nicht rendern können, weil IRM in Exchange ActiveSync deaktiviert ist, kann der Empfänger die E-Mail nur in einem Webbrowser sehen, wenn der Sender entweder Exchange Online oder Exchange lokal in einer Hybridkonfiguration verwendet. 

## <a name="azure-rms-support-for-office"></a>Unterstützung für Office Azure RMS

Azure RMS ist eng in die Word-, Excel-, PowerPoint- und Outlook-Apps integriert. Dort wird diese Funktionalität oft als Information Rights Management (IRM) bezeichnet. 

- [Windows-Computer für Information Rights Management (IRM)](#windows-computers-for-information-rights-management-irm)
- [Mac-Computer für Information Rights Management (IRM)](#mac-computers-for-information-rights-management-irm)

Siehe auch: [Dienstbeschreibung für Office-Anwendungen](https://technet.microsoft.com/library/office-applications-service-description.aspx)

### <a name="windows-computers-for-information-rights-management-irm"></a>Windows-Computer für Information Rights Management (IRM)

Die folgenden Office-Clientsuites unterstützen den Schutz von Dateien und E-Mails auf Windows-Computern mithilfe von Azure Rights Management:

- **Office-Apps, Mindestversion 1805, Build 9330,2078 aus Office 365 Business oder Microsoft 365 Business,** wenn dem Benutzer eine Lizenz für Azure Rights Management (auch bekannt als Azure Information Protection für Office 365) zugewiesen ist.

- **Office 365 ProPlus**

    Diese Editionen von Office sind in den meisten Office 365-Abonnements enthalten, bei denen durch Azure Information Protection Datenschutz gewährleistet wird. Überprüfen Sie Ihre Abonnementinformationen, um zu sehen, ob Office 365 ProPlus enthalten ist. Sie finden diese Informationen auch im [Datenblatt zu Azure Information Protection](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- **Office Professional Plus 2019**

- **Office Professional Plus 2016**

- **Office Professional Plus 2013**

- **Office Professional Plus 2010 mit Service Pack 2**

Alle Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

#### <a name="azure-rights-management-service-with-office-professional-plus-2010-and-service-pack-2-or-office-professional-2010-with-service-pack-2"></a>Azure Rights Management Service mit Office Professional Plus 2010 und Service Pack 2 oder Office Professional 2010 mit Service Pack 2

Wenn Sie den Azure Rights Management-Dienst mit Office Professional Plus 2010 und Service Pack 2 oder Office Professional 2010 mit Service Pack 2 verwenden, müssen Sie auch über den AIP-Client für Windows verfügen.

Außerdem gilt diese Konfiguration:

- Wird unter Windows 10 nicht unterstützt.
- Die formularbasierte Authentifizierung für Verbundbenutzerkonten wird nicht unterstützt. Für diese Konten muss die integrierte Windows-Authentifizierung verwendet werden.
- Unterstützt nicht die Möglichkeit, den Vorlagen Schutz mithilfe benutzerdefinierter Berechtigungen zu überschreiben, die mit dem AIP-Client ausgewählt wurden. In diesem Fall muss der ursprüngliche Schutz zunächst entfernt werden, bevor benutzerdefinierte Berechtigungen angewendet werden können.

### <a name="mac-computers-for-information-rights-management-irm"></a>Mac-Computer für Information Rights Management (IRM)

Die folgenden Office-Clientsuites unterstützen den Schutz von Dateien und E-Mails auf macOS-Computern mithilfe von Azure RMS:

- Office 365 ProPlus
- Office Standard 2019 für Mac
- Office Standard 2016 für Mac

Alle Editionen von Office für Mac 2019 und Office für Mac 2016 können geschützte Inhalte nutzen.

> [!TIP]
> Für den Einstieg in den Schutz von Dokumenten mithilfe von Office für Mac finden Sie möglicherweise die folgenden häufig gestellten Fragen: [Gewusst wie Konfigurieren eines Macintosh-Computers zum schützen und Nachverfolgen von Dokumenten?](faqs-rms.md#how-do-i-configure-a-mac-computer-to-protect-and-track-documents)
> 
## <a name="azure-information-protection-apps-for-ios-and-android"></a>Azure Information Protection-Apps für iOS und Android

Die Azure Information Protection-App für IOS und Android bietet einen Viewer für durch Rechte geschützte e-Mail-Nachrichten **(rpmsg** -Dateien), wenn diese mobilen Geräte keine e-Mail-APP haben, die geschützte e-Mails öffnen kann. Mit dieser App können Sie außerdem rechtegeschützte PDF-Dateien, Bilder und Textdateien anzeigen.

Wenn Ihre iOS- und Android-Geräte durch Microsoft Intune registriert wurden, können Benutzer die App über das Unternehmensportal installieren, und Sie können die App mithilfe der [App-Schutzrichtlinien](/intune/app-protection-policies) von Intune verwalten.

Weitere Informationen zur Verwendung der App finden Sie unter [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](./rms-client/mobile-app-faq.md).

## <a name="the-azure-information-protection-client-for-windows"></a>Der Azure Information Protection-Client für Windows

Der-Azure Information Protection (AIP)-Client umfasst zwei Versionen mit Administrator-und Benutzerhandbüchern für jede Version:

- **Einheitlicher**Bezeichnungs Client:
    - [Administratorhandbuch](./rms-client/clientv2-admin-guide.md)
    - [Benutzerhandbuch](./rms-client/clientv2-user-guide.md)

- **Klassischer Client**:
    - [Administratorhandbuch](./rms-client/client-admin-guide.md)
    - [Benutzerhandbuch](./rms-client/client-user-guide.md)

Laden Sie die relevante APP von der [Seite Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970)herunter.

> [!NOTE]
> Sie sind nicht sicher, welche Unterschiede zwischen diesen beiden Versionen bestehen? Lesen Sie die relevanten [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients).
> 
## <a name="rights-management-sharing-app"></a>Rights Management-Freigabeanwendung

Für Macintosh-Computer bietet die Rights Management Freigabe-APP einen Viewer für geschützte PDF-Dateien **(. ppdf),** geschützte Text Bilder und generisch geschützte Dateien. Sie kann auch Bilddateien, jedoch keine anderen Dateien schützen. Verwenden Sie zum Schützen von Office-Dateien auf diesen Computern Office für Mac oder Office 365 ProPlus. 

Weitere Informationen finden Sie in den häufig gestellten Fragen [zur Microsoft Rights Management-Freigabe Anwendung für mobile Plattformen](https://technet.microsoft.com/dn451248) .

Laden Sie die Rights Management Freigabe-App für Macintosh-Computer von der [Seite Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970)herunter.

## <a name="other-applications-that-support-azure-information-protection"></a>Andere Anwendungen, die Azure Information Protection unterstützen

Zusätzlich zu den oben aufgeführten Anwendungen kann jede Anwendung, die die APIs für den Azure Rights Management-Dienst unterstützt, in Azure Information Protection integriert werden. 

Beispiele sind u. a. Geschäftsanwendungen, die intern geschrieben wurden, oder Anwendungen von Softwareherstellern, die mithilfe der RSM-sdken geschrieben wurden.

Weitere Informationen finden Sie im [Azure Information Protection-Entwicklerhandbuch](./develop/developers-guide.md).

## <a name="applications-that-are-not-supported-by-azure-rms"></a>Nicht von Azure RMS unterstützte Anwendungen

Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:

- Microsoft onedrive für SharePoint Server 2013
- XPS-Viewer
- Anwendungen, die unter Windows-Versionen vor Windows 7, Service Pack 1 ausgeführt werden


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen:

- [Anforderungen für Azure Information Protection](requirements.md).
- [Wie Anwendungen den Azure Rights Management-Dienst unterstützen](./applications-support.md).
- [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md).

Die neuesten Informationen zu Lösungen, die den Azure Rights Management-Dienst und Azure Information Protection unterstützen, finden Sie im Blogbeitrag [Microsoft Ignite 2019 – Microsoft Information Protection Solutions Partner Ecosystem Showcase](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Ignite-2019-Microsoft-Information-Protection-solutions/ba-p/967024).
