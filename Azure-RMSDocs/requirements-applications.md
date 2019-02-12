---
title: Unterstützung von Anwendungen für den RMS-Datenschutz
description: Stellen Sie fest, welche Anwendungen über RMS-APIs den Azure Rights Management-Dienst von Azure Information Protection nativ unterstützen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/01/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e6ee0410ede61e32ad371aad7559e58742c5c93a
ms.sourcegitcommit: 8558af7116f62414054feffa346aba197a1250d9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560021"
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


In der folgenden Tabelle sind die Anwendungen und Lösungen aufgeführt, die den Azure Rights Management-Dienst (Azure RMS) nativ unterstützen, der Datenschutz für Azure Information Protection bietet.

Die Rights Management-Unterstützung ist in diesen Anwendungen und Lösungen eng integriert, d.h., Nutzungseinschränkungen werden mithilfe der Rights Management-APIs unterstützt. Diese Anwendungen und Lösungen werden auch als „RMS-aktiviert“ bezeichnet.

Wenn nicht anders angegeben, gelten die unterstützten Funktionen für Azure RMS und AD RMS. Außerdem ist für die AD RMS-Unterstützung unter iOS, Android, macOS und Windows Phone 8.1 die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](https://technet.microsoft.com/library/dn673574.aspx) erforderlich.

## <a name="rms-enlightened-applications"></a>RMS-aktivierte Anwendungen

Die folgende Tabelle zeigt RMS-aktivierte Clientanwendungen von Microsoft und anderen Softwareherstellern. 

Weitere Informationen zum Anzeigen geschützter PDF-Dokumente finden Sie unter [Protected PDF readers for Microsoft Information Protection (Reader für geschützte PDF-Dokumente für Microsoft Azure Information Protection)](./rms-client/protected-pdf-readers.md).

Informationen über die Tabellenspalten:

-   **E-Mail:** Die aufgeführten E-Mail-Clients können die E-Mail-Nachricht selbst schützen, wodurch noch ungeschützte, angefügte Office-Dateien automatisch geschützt werden. In diesem Szenario kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte (Nachricht und Anhang) anzeigen. Wenn eine E-Mail-Nachricht selbst jedoch nicht geschützt der Anhang jedoch geschützt ist, kann das Client-Vorschaufeature autorisierten Empfängern die geschützten Inhalte nicht anzeigen. 
    
    Tipp: Bei der Nutzung von E-Mail-Clients, die den Schutz von E-Mails nicht unterstützen, sollten Sie [Nachrichtenflussregeln von Exchange Online zum Anwenden dieses Schutzes](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8) verwenden.

-   **Weitere Dateitypen**: Text- und Bilddateien umfassen u. a. Dateien mit der Dateierweiterung TXT, XML, JPG und JPEG. Die Dateierweiterung dieser Dateien ändert sich, nachdem sie durch Rights Management nativ geschützt wurden und schreibgeschützt sind. Dateien mit der Dateierweiterung „.pfile“ können nicht nativ geschützt werden, wenn sie generisch durch Rights Management geschützt sind. Weitere Informationen finden Sie im Administratorhandbuch zum Azure Information Protection-Client unter [Unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md).


|**Gerätebetriebssystem**|Word, Excel, PowerPoint|E-Mail|Weitere Dateitypen|
|---------------------------|-----------------------|-----------------|---------|
|**Windows**|Office 365-Apps [[1]](#footnote-1)<br /><br />Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office 2019 <br /><br />Office Online (Anzeige von geschützten Dokumenten) [[2]](#footnote-2)<br /><br />Webbrowser [[3]](#footnote-3)|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Office 2019 <br /><br />Office 365 ProPlus<br /><br />Webbrowser [[4]](#footnote-4)<br /><br />Windows Mail [[5]](#footnote-5) |Azure Information Protection-Client für Windows: Text, Bilder, PFILE<br /><br />SealPath RMS-Plug-In für AutoCAD: .dwg|
|**iOS**|GigaTrust<br /><br /> Office Mobile (Anzeige und Bearbeitung von geschützten Dokumenten)<br /><br />Office Online[[2]](#footnote-2)<br /><br />TITUS-Dokumentation<br /><br />Webbrowser [[3]](#footnote-3)|Azure Information Protection-App (Anzeige von geschützten E-Mails)<br /><br />BlackBerry Work<br /><br />Citrix-WorxMail <br /><br />NitroDesk [[5]](#footnote-5)<br /><br />Outlook für iPad und iPhone [[5]](#footnote-5)<br /><br />TITUS Mail <br /><br />Webbrowser [[4]](#footnote-4)|Azure Information Protection-App (Anzeige von geschützten Texten und Abbildungen)<br /><br />TITUS-Dokumentation: Pfile|
|**Android**|GigaTrust App für Android<br /><br />Office Online[[2]](#footnote-2)<br /><br />Office Mobile <br /><br />Webbrowser [[3]](#footnote-3)|9Folders [[5]](#footnote-5)<br /><br />Azure Information Protection-App (Anzeige von geschützten E-Mails)<br /><br />BlackBerry Work <br /><br />GigaTrust App für Android [[5]](#footnote-5)<br /><br />Citrix-WorxMail <br /><br />NitroDesk [[5]](#footnote-5)<br /><br />Outlook für Android [[5]](#footnote-5)<br /><br />Samsung E-Mail (S3 und neuer) [[5]](#footnote-5)<br /><br />TITUS-Klassifizierung für mobile Geräte <br /><br />Webbrowser [[4]](#footnote-4)|Azure Information Protection-App (Anzeige von geschützten Texten und Abbildungen)|
|**macOS**|Office 365-Apps<br /><br />Office 2019 für Mac<br /><br />Office 2016 für Mac<br /><br />Office Online[[2]](#footnote-2)<br /><br />Webbrowser [[3]](#footnote-3)|Outlook 2019 für Mac<br /><br /> Outlook 2016 für Mac<br /><br />Webbrowser [[4]](#footnote-4)|RMS-Freigabe-App (Anzeige von geschützten Texten, Abbildungen und generisch geschützten Dateien)|
|**Windows 10 Mobile**|Office Mobile-Apps (Anzeige von geschützter Dokumentation mit Azure RMS) <br /><br />Webbrowser [[3]](#footnote-3)|Citrix-WorxMail <br /><br />Outlook Mail (Ansicht von geschützten E-Mails) <br /><br />Webbrowser [[4]](#footnote-4)|Nicht unterstützt|
|**Blackberry 10**|Webbrowser [[3]](#footnote-3)|Blackberry-E-Mail [[5]](#footnote-5) <br /><br />Webbrowser [[4]](#footnote-4)|Nicht unterstützt|

###### <a name="footnote-1"></a>Fußnote 1
Dies umfasst Folgendes: 
- Mindestversion 1805 von Office-Apps, Build 9330.2078 von Office 365 Business oder Microsoft 365 Business, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.
- Office 365 ProPlus-Apps

###### <a name="footnote-2"></a>Fußnote 2
Wird nur mit SharePoint Online und OneDrive for Business unterstützt, und die Dokumente sind vor dem Upload in eine geschützte Bibliothek ungeschützt.

###### <a name="footnote-3"></a>Fußnote 3
Für [Anlagen in Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM), die durch die [Office 365-Nachrichtenverschlüsselung mit den neuen Funktionen](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) geschützt sind

###### <a name="footnote-4"></a>Fußnote 4
Wenn Sender und Empfänger derselben Organisation angehören oder eine der folgenden Bedingungen zutrifft:
- Sender oder Empfänger verwenden Exchange Online.
- Der Sender verwendet Exchange lokal in einer Hybridkonfiguration. 

###### <a name="footnote-5"></a>Fußnote 5
Verwendet Exchange ActiveSync IRM, das vom Exchange-Administrator aktiviert werden muss. Benutzer können zwar die Funktionen zum Anzeigen, Antworten und allen Antworten für geschützte E-Mail-Nachrichten ausführen, können selbst aber keine neuen E-Mail-Nachrichten schützen.
 
Sollte die E-Mail-Anwendung die Nachricht nicht rendern können, weil IRM in Exchange ActiveSync deaktiviert ist, kann der Empfänger die E-Mail nur in einem Webbrowser sehen, wenn der Sender entweder Exchange Online oder Exchange lokal in einer Hybridkonfiguration verwendet. 

### <a name="more-information-about-azure-rms-support-for-office"></a>Weitere Informationen zur Azure RMS-Unterstützung für Office

Azure RMS ist eng in die Word-, Excel-, PowerPoint- und Outlook-Apps integriert. Dort wird diese Funktionalität oft als Information Rights Management (IRM) bezeichnet. 

Siehe auch: [Dienstbeschreibung für Office-Anwendungen](https://technet.microsoft.com/library/office-applications-service-description.aspx)

#### <a name="windows-computers-for-information-rights-management-irm"></a>Windows-Computer für Information Rights Management (IRM)

Die folgenden Office-Clientsuites unterstützen den Schutz von Dateien und E-Mails auf Windows-Computern mithilfe von Azure Rights Management:

- Mindestversion 1805 von Office-Apps, Build 9330.2078 von Office 365 Business oder Microsoft 365 Business, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.

- Office 365 ProPlus
    
    Diese Editionen von Office sind in den meisten Office 365-Abonnements enthalten, bei denen durch Azure Information Protection Datenschutz gewährleistet wird. Überprüfen Sie Ihre Abonnementinformationen, um zu sehen, ob Office 365 ProPlus enthalten ist. Sie finden diese Informationen auch im [Datenblatt zu Azure Information Protection](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- Office Professional Plus 2019

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010 mit Service Pack 2

Alle Editionen von Office (mit Ausnahme von Office 2007) können geschützte Inhalte nutzen.

Für die Verwendung von Azure Rights Management mit Office Professional Plus 2010 und Service Pack 2 bzw. Office Professional 2010 und Service Pack 2 gilt Folgendes:

- Erfordert den Azure Information Protection-Client für Windows

- Unter Windows 10 nicht unterstützt.

- Die formularbasierte Authentifizierung für Verbundbenutzerkonten wird nicht unterstützt. Diese Konten müssen die integrierte Windows-Authentifizierung verwenden.

- Das Überschreiben des Schutzes von Vorlagen mit benutzerdefinierten Berechtigungen, die vom Benutzer mit dem Azure Information Protection-Client ausgewählt, wird nicht unterstützt. In diesem Fall muss der ursprüngliche Schutz zunächst entfernt werden, bevor benutzerdefinierte Berechtigungen angewendet werden können.

#### <a name="mac-computers-for-information-rights-management-irm"></a>Mac-Computer für Information Rights Management (IRM)

Die folgenden Office-Clientsuites unterstützen den Schutz von Dateien und E-Mails auf macOS-Computern mithilfe von Azure RMS:

- Office 365 ProPlus

- Office Standard 2019 für Mac

- Office Standard 2016 für Mac

Alle Editionen von Office für Mac 2019 und Office für Mac 2016 können geschützte Inhalte nutzen.

Tipp: Hilfreiche Hinweise zu den ersten Schritten zum Schützen von Dokumenten mithilfe von Office für Mac finden Sie im folgenden FAQ-Abschnitt: [Wie konfiguriere ich einen Macintosh-Computer für den Schutz und die Nachverfolgung von Dokumenten?](faqs-rms.md#how-do-i-configure-a-mac-computer-to-protect-and-track-documents)

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Weitere Informationen zur Azure Information Protection-App für iOS und Android

Die Azure Information Protection-App für iOS und Android stellt einen Viewer für rechtegeschützte E-Mail-Nachrichten (RPMSG-Dateien) für den Fall bereit, dass auf diesen mobilen Geräten keine E-Mail-App installiert ist, mit der geschützte E-Mails geöffnet werden können. Mit dieser App können Sie außerdem rechtegeschützte PDF-Dateien, Bilder und Textdateien anzeigen.

Wenn Ihre iOS- und Android-Geräte durch Microsoft Intune registriert wurden, können Benutzer die App über das Unternehmensportal installieren, und Sie können die App mithilfe der [App-Schutzrichtlinien](/intune/app-protection-policies) von Intune verwalten.

Weitere Informationen zur Verwendung der App finden Sie unter [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](./rms-client/mobile-app-faq.md).


### <a name="more-information-about-the-azure-information-protection-client-for-windows"></a>Weitere Informationen zum Azure Information Protection-Client für Windows

Weitere Informationen finden Sie in den folgenden Ressourcen:

- [Azure Information Protection-Client – Administratorhandbuch](./rms-client/client-admin-guide.md)

- [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/client-user-guide.md)

- [Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android](./rms-client/mobile-app-faq.md)

Laden Sie die relevante App über die Links auf der [Microsoft Azure Information Protection-Seite](https://go.microsoft.com/fwlink/?LinkId=303970) herunter.

### <a name="more-information-about-the-rights-management-sharing-app"></a>Weitere Informationen zur Rights Management-Freigabe-App

Für Mac-Computer stellt die Rights Management-Freigabe-App einen Viewer für geschützte PDF-Dateien (.ppdf), geschützte Textbilder und allgemein geschützte Dateien bereit. Sie kann auch Bilddateien, jedoch keine anderen Dateien schützen. Verwenden Sie zum Schützen von Office-Dateien auf diesen Computern Office für Mac oder Office 365 ProPlus. 

Weitere Informationen finden Sie in den folgenden Ressourcen:

-   [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile Plattformen](https://technet.microsoft.com/dn451248)

Laden Sie die Rights Management-Freigabe-App für Mac-Computer über die Links auf der [Microsoft Azure Information Protection-Seite](https://go.microsoft.com/fwlink/?LinkId=303970) herunter.


### <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Weitere Informationen zu anderen Anwendungen, die Azure Information Protection unterstützen

Zusätzlich zu den Anwendungen in der Tabelle kann jede Anwendung, die APIs für den Azure Rights Management Service unterstützt, in Azure Informationen Protection integriert werden. Dazu zählen die Folgenden:

- Branchenanwendungen, die intern mithilfe der RMS-SDKs geschrieben wurden.

- Anwendungen von Softwareherstellern, die mithilfe der RMS-SDKs geschrieben wurden.

Weitere Informationen finden Sie im [Azure Information Protection-Entwicklerhandbuch](./develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Nicht von Azure RMS unterstützte Anwendungen

Folgende Anwendungen werden zurzeit nicht von Azure RMS unterstützt:

- Microsoft OneDrive for Business für SharePoint Server 2013

- XPS-Viewer

Zudem unterliegt der Azure Information Protection-Client folgenden Einschränkungen:

- Für Windows-Computer: Erfordert eine Mindestversion von Windows 7 Service Pack 1.

## <a name="rms-enlightened-solutions"></a>RMS-aktivierte Lösungen

Die folgende Tabelle zeigt RMS-aktivierte Lösungen von Softwareherstellern.

Wenn Sie Softwarehersteller sind und über eine Lösung verfügen, die nicht in dieser Tabelle aufgeführt ist, registrieren Sie Ihre Anwendung bei Azure AD. Weitere Informationen finden Sie unter [Vorgehensweise: Registrieren Ihrer App für Azure AD und Aktivieren der App für RMS](./develop/authentication-integration.md).


|Produkt|Hersteller|Beschreibung|
|-------------------------------|---------------------------|-----------------|
|Absolut|Absolut|Verhinderung von Datenverlust (Data Loss Prevention, DLP) zum Schutz von Inhalten.|
|Content Locker|VMware|Speichert, nutzt und erstellt geschützte Inhalte.|
|Controle|TakeControle|eDiscovery mithilfe von Bezeichnung und Schutz.|
|Forcepoint|Forcepoint DLP|Endpunktlösung zur Verhinderung von Datenverlust, die die Sicherheitsrichtlinien für die Daten einer Organisation verstärken sollen.|
|Halocore|Secude|Schützt aus SAP-Umgebungen exportierte Dateien.|
|MaaS 360|IBM|Integration zum Nutzen und Schützen von Dokumenten.|
|Mobiliya|Mobiliya|Sichert Dokumente aus Documentum-Repositorys von EMC.
|Ramessys|Ramessys|Integration für Chemcart und Documentum.
|Sealpath|Sealpath Technologies|Integration in CAD-Entwurfstools wie AutoCAD und Siemens Jt2GO.
|SecRMM|Sqaudra Technologies |Dokumentschutz für Wechselmedien.
|Security Sheriff|CryptZone |Zugriffsverwaltung auf SharePoint und Schutz für Dokumente basierend auf deren Klassifizierung und Zugriffsberechtigungen.
|Symantec DLP|Symantec |Erkennung und Überwachung für geschützte Dateien.

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

Weitere Informationen dazu, wie die gängigsten Anwendungen Azure RMS unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](./applications-support.md).

Informationen dazu, wie die gängigsten Anwendungen für Azure RMS konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md).

