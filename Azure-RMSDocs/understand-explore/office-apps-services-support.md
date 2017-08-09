---
title: "So unterstützen Office-Apps und -Dienste Azure RMS über AIP"
description: "Verwendung des Azure Rights Management-Diensts über AIP zum Schutz der Daten Ihrer Organisation durch Endbenutzer-Office-Anwendungen wie Word und Outlook und Office-Dienste wie Exchange und SharePoint."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5e4d753c6c58394c257466269c5a4f50df6c6fc4
ms.sourcegitcommit: 869e42f35a851c412164a71b1f657621af07b2f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2017
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>So unterstützen Office-Anwendungen und -Dienste Azure Rights Management 

>*Gilt für: Azure Information Protection, Office 365*

Endbenutzer-Office-Anwendungen und Office-Dienste können den Azure Rights Management-Dienst aus Azure Information Protection zum Schutz der Daten Ihrer Organisation verwenden. Diese Office-Anwendungen sind Word, Excel, PowerPoint und Outlook. Die Officedienste sind Exchange und SharePoint. Die Office-Konfigurationen, die den Azure Rights Management-Dienst unterstützen, verwenden oft den Begriff **Information Rights Management (IRM)**.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Office-Anwendungen: Word, Excel, PowerPoint, Outlook
Diese Anwendungen bieten native Unterstützung für Azure Rights Management und ermöglichen Benutzern das Anwenden von Schutz auf ein gespeichertes Dokument oder auf eine zu sendende E-Mail. Benutzer können Vorlagen zum Anwenden des Schutzes anwenden. Alternativ können Benutzer für Word, Excel und PowerPoint individuell anpassbare benutzerdefinierte Einstellungen für Zugriff, Rechte und Nutzungseinschränkungen festlegen. 

Benutzer können z.B. ein Word-Dokument so konfigurieren, dass es nur von Personen in Ihrer Organisation geöffnet werden kann. Sie können alternativ steuern, ob ein Excel-Arbeitsblatt bearbeitet werden kann oder schreibgeschützt ist oder nicht gedruckt werden kann. Für Dateien mit zeitlicher Relevanz kann eine Ablaufzeit konfiguriert werden, nach deren Erreichen kein Zugriff auf die Datei mehr möglich ist. Diese Konfiguration kann direkt von Benutzern oder durch Anwenden einer Vorlage vorgenommen werden. Für Outlook können Benutzer außerdem die Option **Nicht weiterleiten** auswählen, um Datenlecks zu verhindern.

Zusätzlich zur nativen Unterstützung von Azure Rights Management unterstützen diese Anwendungen auch die Azure Information Protection-Leiste, die mit dem [Azure Information Protection-Client](../rms-client/aip-client.md) installiert wird. Auf dieser Leiste werden Bezeichnungen angezeigt, die Benutzern das automatische Anwenden von Schutz auf Dokumente und E-Mails erleichtert, die vertrauliche Daten enthalten.

Wenn Sie bereit sind, Office-Apps und den Azure Information Protection-Client zu konfigurieren:

- Weitere Informationen zum Konfigurieren von Office-Apps finden Sie unter [Office-Apps: Konfiguration für Clients](../deploy-use/configure-office-apps.md).

- Weitere Informationen zum Installieren und Konfigurieren des Azure Information Protection-Clients finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](../deploy-use/configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Exchange Online und Exchange Server
Wenn Sie Exchange Online oder Exchange Server verwenden, können Sie Information Rights Management-Optionen (IRM) zur Unterstützung von Azure Rights Management konfigurieren. Mit dieser Konfiguration kann Exchange die folgenden Lösungen zum Schutz bereitstellen:

-   **Exchange ActiveSync IRM** , sodass mobile Geräte E-Mails schützen und geschützte E-Mails nutzen können.

-   Unterstützung des E-Mail-Schutzes für **Outlook im Web**, was auch gleichzeitig für den Outlook-Client angewendet wird. Mit dieser Konfiguration können Benutzer E-Mail-Nachrichten mithilfe von Vorlagen oder durch Angabe individueller Optionen schützen. Benutzer können geschützte E-Mail-Nachrichten, die an sie gesendet werden, lesen und verwenden.

-   **Schutzregeln** für Outlook-Clients, die ein Administrator so konfiguriert, dass sie automatisch Schutzvorlagen auf E-Mails für angegebene Empfänger anwenden. Wenn beispielsweise interne E-Mails an Ihre Rechtsabteilung gesendet werden, können sie nur von Mitgliedern der Rechtsabteilung gelesen und nicht weitergeleitet werden. Benutzer sehen den auf die E-Mail angewendeten Schutz vor dem Senden und können diesen standardmäßig entfernen, falls sie ihn für unnötig halten. E-Mails werden vor dem Senden verschlüsselt. Weitere Informationen finden Sie unter [Outlook-Schutzregeln](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) und [Erstellen einer Outlook-Schutzregel](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) in der Exchange-Bibliothek.

-   **Transportregeln**, die von einem Administrator konfiguriert werden, um automatisch Schutzvorlagen für E-Mail-Nachrichten anzuwenden. Diese Regeln basieren auf Eigenschaften wie Sender, Empfänger, Betreff der Nachricht und Inhalt. Diese Regeln ähneln in ihrem Konzept den Schutzregeln; Benutzer können den Schutz jedoch nicht entfernen. Die Regeln können auf Outlook im Internet und auf E-Mails angewendet werden, die von mobilen Geräten aus gesendet werden. Zusätzlich verschlüsseln diese Regeln keine E-Mail-Nachrichten, bevor Sie vom Client aus gesendet werden. Weitere Informationen finden Sie unter [Erstellen einer Transportschutzregel](https://technet.microsoft.com/library/dd302432.aspx) in der Exchange-Bibliothek.

-   **DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust)**, die Bedingungssätze enthalten, um E-Mails zu filtern und Maßnahmen zur Verhinderung von Datenverlusten bei vertraulichen oder sensiblen Inhalten zu ergreifen. Vertrauliche oder sensible Inhalte sind z.B. persönliche Informationen oder Kreditkarteninformationen. Richtlinientipps können verwendet werden, wenn sensible Daten erkannt werden, um Benutzer darauf aufmerksam zu machen, dass sie eventuell Schutz anwenden sollten. Weitere Informationen finden Sie unter [Verhinderung von Datenverlust](https://technet.microsoft.com/library/jj150527(v=exchg.160).aspx) in der Exchange-Bibliothek.

-   **Office 365-Nachrichtenverschlüsselung**, die Transportregeln verwendet, um verschlüsselte E-Mails an Personen außerhalb Ihres Unternehmens zu senden, wobei die E-Mail in einem Browser gelesen wird, dessen Oberfläche Outlook im Internet ähnelt. Sie können den Haftungsausschluss- und Kopfzeilentext in den verschlüsselten E-Mails Ihres Unternehmens anpassen und sogar Ihr Firmenlogo hinzufügen. Weitere Informationen finden Sie unter [Office 365-Nachrichtenverschlüsselung](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) auf der Office-Website.

Wenn Sie Exchange lokal verwenden, können Sie IRM-Funktionen mit dem Azure Rights Management-Dienst verwenden, indem Sie den Azure Rights Management-Connector bereitstellen. Dieser Connector fungiert als Relay zwischen den lokalen Servern und dem Azure Rights Management-Dienst.

Wenn Sie bereit sind, Exchange für IRM zu konfigurieren:

- Informationen zu Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Informationen zu Exchange lokal finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online und SharePoint Server

Wenn Sie SharePoint Online oder SharePoint Server verwenden, können Sie Dokumente mithilfe der Information Rights Management-Funktion (IRM) von SharePoint schützen. Mit dieser Funktion können Administratoren Listen und Bibliotheken schützen, damit eine heruntergeladene Datei, die von einem Benutzer ausgecheckt wird, geschützt ist, sodass nur autorisierte Personen sie entsprechend den von Ihnen angegebenen Informationsschutzrichtlinien anzeigen und verwenden können. So kann die Datei beispielsweise schreibgeschützt sein, das Kopieren von Text deaktivieren, das Speichern einer lokalen Kopie oder das Drucken der Datei verhindern.

Word, PowerPoint, Excel und PDF-Dokumente unterstützen diesen IRM-Schutz von SharePoint. Standardmäßig beschränkt sich der Schutz auf die Person, die das Dokument herunterlädt. Sie können diese Standardeinstellung durch eine Konfigurationsoption ändern, die den Schutz auf alle Benutzer mit Zugriff auf das Dokument in SharePoint oder auf eine von Ihnen festgelegte Gruppe erweitert.

Bei SharePoint-Listen und -Bibliotheken wird dieser Schutz immer von einem Administrator und nie von einem Endbenutzer konfiguriert. Sie legen die Berechtigungen auf Websiteebene fest, und diese Berechtigungen werden in der Standardeinstellung von jeder Liste und Bibliothek in dieser Website geerbt. Wenn Sie SharePoint Online verwenden, können Benutzer auch ihre OneDrive for Business-Bibliothek für IRM-Schutz konfigurieren.

Für eine präzisere Kontrolle können Sie eine Liste oder Bibliothek in der Website so konfigurieren, dass sie nicht länger Berechtigungen vom übergeordneten Element erben. Anschließend können Sie IRM-Berechtigungen auf dieser Ebene (Liste oder Bibliothek) konfigurieren, die dann als „Eindeutige Berechtigungen“ bezeichnet werden. Berechtigungen werden jedoch immer auf Containerebene festgelegt. Sie können keine Berechtigungen für einzelne Dateien festlegen. 

Zuerst muss der IRM-Dienst für SharePoint aktiviert werden. Dann geben Sie die IRM-Berechtigungen für eine Bibliothek an. Bei SharePoint Online und OneDrive for Business können Benutzer auch IRM-Berechtigungen für ihre OneDrive for Business-Bibliothek festlegen. SharePoint verwendet keine Richtlinienvorlagen für Rechte. Allerdings stehen SharePoint-Konfigurationseinstellungen zur Wahl, die einigen Einstellungen entsprechen, die Sie in den Vorlagen angeben können.

Wenn Sie SharePoint Server benutzen, können Sie diesen IRM-Schutz durch Bereitstellen des Azure Rights Management-Verbindungsdiensts verwenden. Dieser Verbindungsdienst fungiert als Relay zwischen den lokalen Servern und dem Rights Management-Clouddienst. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Gegenwärtig gibt es einige Beschränkungen bei der Verwendung von SharePoint-IRM:
> 
> - Sie können weder die standardmäßigen noch die benutzerdefinierten Vorlagen verwenden, die Sie im Azure-Portal verwalten. 
> 
> - Dateien mit der Dateinamenerweiterung PPDF für geschützte PDF-Dateien werden nicht unterstützt. Dateien mit der Dateierweiterung PDF, die nativ von Rights Management geschützt wurden, werden unterstützt, wenn Sie einen PDF-Reader verwenden, der eine native Unterstützung von Rights Management bietet.
> 
> - Wenn Sie eine Datei schützen, die Sie dann in einer SharePoint-Bibliothek oder in OneDrive hochladen, können Sie mit dieser Datei Folgendes nicht durchführen: Gemeinsame Dokumentenerstellung, Office Online, Suche, Dokumentvorschau, Vorschauminiatur und eDiscovery.

Wenn Sie den SharePoint IRM-Schutz verwenden, wendet der Azure Rights Management-Dienst Nutzungseinschränkungen und Datenverschlüsselung nicht beim ursprünglichen Erstellen der Dokumente in SharePoint oder beim Hochladen in die Bibliothek an, sondern erst beim Herunterladen der Dokumente aus SharePoint. Informationen zum Schutz der Dokumente vor dem Herunterladen finden Sie in der SharePoint-Dokumentation unter [Datenverschlüsselung in OneDrive for Business und SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) .

Obwohl der folgende Beitrag im Office-Blog nicht mehr ganz neu ist, finden Sie darin möglicherweise weitere nützliche Informationen: [What’s New with Information Rights Management in SharePoint and SharePoint Online (Neuerungen bei Information Rights Management in SharePoint und SharePoint Online)](https://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

Wenn Sie bereit sind, SharePoint für IRM zu konfigurieren:

- Informationen zu SharePoint Online finden Sie unter [SharePoint Online und OneDrive for Business: IRM-Konfiguration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- Informationen zu Sharepoint Server finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).


## <a name="next-steps"></a>Nächste Schritte

Wenn Sie Office 365 verwenden, könnte Sie der Artikelabschnitt [Schutz von Informationen für Office 365](https://technet.microsoft.com/library/dn919927.aspx#BKMK_O365fileprotect) interessieren, der empfohlene Funktionen für den Schutz von Dateien in Office 365 beschreibt.

Informationen dazu, wie andere Anwendungen und Dienste den Azure Rights Management-Dienst von Azure Information Protection unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

Wenn Sie nun die Bereitstellung einschließlich Konfiguration dieser Anwendungen und Dienste durchführen möchten, gehen Sie zu [Roadmap für die Bereitstellung von Azure Information Protection](../plan-design/deployment-roadmap.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]