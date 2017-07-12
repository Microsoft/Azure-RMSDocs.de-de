---
title: Office-Apps und -Dienste mit Azure Information Protection
description: Verwendung des Azure Rights Management-Diensts zum Schutz der Daten Ihrer Organisation durch Endbenutzer-Office-Anwendungen (z.B. Word, Excel, PowerPoint und Outlook) und Office-Dienste (z.B. Exchange und SharePoint).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 7fe044ab9b8e253e3095af5828a33926271bc42b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="office-applications-and-services" class="xliff"></a>

# Office-Anwendungen und -Dienste

>*Gilt für: Azure Information Protection, Office 365*

Endbenutzer-Office-Anwendungen (z.B. Word, Excel, PowerPoint und Outlook) und Office-Dienste (z.B. Exchange und SharePoint) können den Azure Rights Management-Dienst aus Azure Information Protection zum Schutz der Daten Ihrer Organisation verwenden.

<a id="office-applications-word-excel-powerpoint-outlook" class="xliff"></a>

## Office-Anwendungen: Word, Excel, PowerPoint, Outlook
Diese Anwendungen bieten systemeigene Unterstützung für Rights Management durch Verwendung von IRM (Information Rights Management, Verwaltung von Informationsrechten) und ermöglichen Benutzern das Schützen eines gespeicherten Dokuments oder einer zu sendenden E-Mail. Benutzer können Vorlagen verwenden oder für Word, Excel und PowerPoint sehr individuell anpassbare benutzerdefinierte Einstellungen für den Zugriff, die Rechte und die Nutzungseinschränkungen festlegen. 

So können Benutzer ein Word-Dokument beispielsweise so konfigurieren, dass nur Personen in Ihrer Organisation darauf zugreifen können. Sie können ebenso kontrollieren, ob eine Excel-Tabelle bearbeitet werden kann, ihren Modus auf schreibgeschützt ändern oder das Drucken der Tabelle verhindern. Für Dateien mit zeitlicher Relevanz kann eine Ablaufzeit konfiguriert werden (direkt von Benutzern oder durch Anwenden einer Vorlage), nach deren Erreichen kein Zugriff auf die Datei mehr möglich ist. In Outlook können Benutzer zusätzlich zu einer Vorlage die Option **Nicht weiterleiten** auswählen, um zur Vermeidung von Datenlecks beizutragen.

Zusätzlich zur systemeigenen Unterstützung von IRM unterstützen diese Anwendungen die Azure Information Protection-Leiste, die mit dem [Azure Information Protection-Client](../rms-client/aip-client.md) installiert wird. Auf dieser Leiste werden Bezeichnungen angezeigt, die Benutzern das automatische Anwenden von Rights Management-Schutz auf Dokumente und E-Mails erleichtert, die vertrauliche Daten enthalten.

Wenn Sie bereit sind, Office-Apps und den Azure Information Protection-Client zu konfigurieren:

- Weitere Informationen zum Konfigurieren von Office-Apps finden Sie unter [Office-Apps: Konfiguration für Clients](../deploy-use/configure-office-apps.md).

- Weitere Informationen zum Installieren und Konfigurieren des Azure Information Protection-Clients finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](../deploy-use/configure-client.md).

<a id="exchange-online-and-exchange-server" class="xliff"></a>

## Exchange Online und Exchange Server
Wenn Sie Exchange Online oder Exchange Server verwenden, können Sie IRM-Integration (Verwaltung von Informationsrechten) verwenden, die zusätzliche Informationsschutzlösungen bereitstellt:

-   **Exchange ActiveSync IRM** , sodass mobile Geräte E-Mails schützen und geschützte E-Mails nutzen können.

-   RMS-Unterstützung für die **Outlook Web App**, ähnlich implementiert wie der Outlook-Client, sodass Benutzer E-Mails per Vorlagen oder durch Angabe einzelner Optionen schützen und Benutzer geschützte E-Mails, die an sie gesendet werden, lesen und verwenden können.

-   **Schutzregeln** für Outlook-Clients, die ein Administrator so konfiguriert, dass sie automatisch Rights Management-Vorlagen auf E-Mails für angegebene Empfänger anwenden. Wenn beispielsweise interne E-Mails an Ihre Rechtsabteilung gesendet werden, können sie nur von Mitgliedern der Rechtsabteilung gelesen und nicht weitergeleitet werden. Benutzer sehen den auf die E-Mail angewendeten Schutz vor dem Senden und können diesen standardmäßig entfernen, falls sie ihn für unnötig halten. E-Mails werden vor dem Senden verschlüsselt. Weitere Informationen finden Sie unter [Outlook-Schutzregeln](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) und [Erstellen einer Outlook-Schutzregel](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) in der Exchange-Bibliothek.

-   **Transportregeln**, die ein Administrator so konfiguriert, dass automatisch auf Grundlage von Eigenschaften wie Absender, Empfänger, Nachrichtenbetreff und Inhalt Rights Management-Vorlagen auf E-Mails angewendet werden. Diese Regeln ähneln dem Konzept nach Schutzregeln, doch können Benutzer den Schutz nicht entfernen, sie können auf Outlook Web Access und auf von mobilen Geräten gesendete E-Mails angewendet werden, und die E-Mails werden vor dem Senden vom Client nicht verschlüsselt. Weitere Informationen finden Sie unter [Erstellen einer Transportschutzregel](https://technet.microsoft.com/library/dd302432.aspx) in der Exchange-Bibliothek.

-   **DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust)** , die Bedingungssätze enthalten, um E-Mails zu filtern und Maßnahmen zur Verhinderung von Datenverlusten bei vertraulichen oder sensiblen Inhalten zu ergreifen (z. B. personenbezogene Daten oder Kreditkarteninformationen). Richtlinientipps können verwendet werden, wenn sensible Daten erkannt werden, um Benutzer darauf aufmerksam zu machen, dass sie eventuell Informationsschutz anwenden sollten, basierend auf den in der E-Mail enthaltenen Informationen. Weitere Informationen finden Sie unter [Verhinderung von Datenverlust](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) in der Exchange-Bibliothek.

-   **Office 365-Nachrichtenverschlüsselung** , die Transportregeln verwendet, um verschlüsselte E-Mails an Personen außerhalb Ihres Unternehmens zu senden, wobei die E-Mail in einem Browser gelesen wird, dessen Oberfläche Outlook Web App ähnelt. Sie können den Haftungsausschluss- und Kopfzeilentext in den verschlüsselten E-Mails Ihres Unternehmens anpassen und sogar Ihr Firmenlogo hinzufügen. Weitere Informationen finden Sie unter [Office 365-Nachrichtenverschlüsselung](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) auf der Office-Website.

Wenn Sie Exchange Server verwenden, können Sie die Informationsschutzfeatures mit dem Azure Rights Management-Dienst verwenden, indem Sie den RMS-Connector bereitstellen, der als Relay zwischen lokalen Servern und dem Azure Rights Management-Dienst fungiert.

Wenn Sie bereit sind, Exchange für IRM zu konfigurieren:

- Informationen zu Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Informationen zu Exchange lokal finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).


<a id="sharepoint-online-and-sharepoint-server" class="xliff"></a>

## SharePoint Online und SharePoint Server

Wenn Sie SharePoint Online oder SharePoint Server verwenden, können Sie Ihre Dokumente mithilfe der Verwaltung von Informationsrechten (Information Rights Management, IRM) schützen. Mit dieser Konfiguration können Administratoren Listen und Bibliotheken schützen, damit eine heruntergeladene Datei, die von einem Benutzer ausgecheckt wird, geschützt ist, sodass nur autorisierte Personen sie entsprechend den von Ihnen angegebenen Informationsschutzrichtlinien anzeigen und verwenden können. So kann die Datei beispielsweise schreibgeschützt sein, das Kopieren von Text deaktivieren, das Speichern einer lokalen Kopie oder das Drucken der Datei verhindern.

Standardmäßig beschränkt sich der Schutz auf die Person, die das Dokument herunterlädt. Sie können dies jedoch durch eine Konfigurationsoption ändern, die den Schutz auf alle Benutzer mit Zugriff auf das Dokument in SharePoint oder auf eine von Ihnen festgelegte Gruppe erweitert.

Bei SharePoint-Listen und -Bibliotheken wird der Informationsschutz immer von einem Administrator und nie von einem Endbenutzer konfiguriert. Sie legen die Berechtigungen auf Websiteebene fest, und diese Berechtigungen werden in der Standardeinstellung von jeder Liste und Bibliothek in dieser Website geerbt. Wenn Sie SharePoint Online verwenden, können Benutzer auch ihre OneDrive for Business-Bibliothek für IRM-Schutz konfigurieren.

Für eine präzisere Kontrolle können Sie eine Liste oder Bibliothek in der Website so konfigurieren, dass sie nicht länger Berechtigungen vom übergeordneten Element erben. Anschließend können Sie IRM-Berechtigungen auf dieser Ebene (Liste oder Bibliothek) konfigurieren, die dann als „Eindeutige Berechtigungen“ bezeichnet werden. Berechtigungen werden jedoch immer auf Containerebene festgelegt. Sie können keine Berechtigungen für einzelne Dateien festlegen. 

Zuerst muss der IRM-Dienst für SharePoint aktiviert werden. Dann geben Sie die IRM-Berechtigungen für eine Bibliothek an. Bei SharePoint Online und OneDrive for Business können Benutzer auch IRM-Berechtigungen für ihre OneDrive for Business-Bibliothek festlegen. SharePoint verwendet keine Richtlinienvorlagen für Rechte. Allerdings stehen SharePoint-Konfigurationseinstellungen zur Wahl, die einigen Einstellungen entsprechen, die Sie in den Vorlagen angeben können.

Wenn Sie SharePoint Server benutzen, können Sie diesen IRM-Schutz durch Bereitstellen des Azure Rights Management-Verbindungsdiensts verwenden. Dieser Verbindungsdienst fungiert als Relay zwischen den lokalen Servern und dem Rights Management-Clouddienst. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Gegenwärtig gibt es einige Beschränkungen bei der Verwendung von SharePoint-IRM:
> 
> - Sie können weder die standardmäßigen noch die benutzerdefinierten Vorlagen verwenden, die Sie im klassischen Azure-Portal verwalten. 
> 
> - Dateien mit der Dateinamenerweiterung PPDF für geschützte PDF-Dateien werden nicht unterstützt. Dateien mit der Dateierweiterung PDF, die nativ von Rights Management geschützt wurden, werden unterstützt, wenn Sie einen PDF-Reader verwenden, der eine native Unterstützung von Rights Management bietet.


Wenn Sie IRM-Schutz verwenden, wendet der Azure Rights Management-Dienst Nutzungseinschränkungen und Datenverschlüsselung nicht beim ursprünglichen Erstellen der Dokumente in SharePoint oder beim Hochladen in die Bibliothek an, sondern erst beim Herunterladen der Dokumente aus SharePoint. Informationen zum Schutz der Dokumente vor dem Herunterladen finden Sie in der SharePoint-Dokumentation unter [Datenverschlüsselung in OneDrive for Business und SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) .

Obwohl der folgende Beitrag im Office-Blog nicht mehr ganz neu ist, finden Sie darin möglicherweise weitere nützliche Informationen: [What’s New with Information Rights Management in SharePoint and SharePoint Online (Neuerungen bei Information Rights Management in SharePoint und SharePoint Online)](https://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

Wenn Sie bereit sind, SharePoint für IRM zu konfigurieren:

- Informationen zu SharePoint Online finden Sie unter [SharePoint Online und OneDrive for Business: IRM-Konfiguration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- Informationen zu Sharepoint Server finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).


<a id="next-steps" class="xliff"></a>

## Nächste Schritte

Informationen dazu, wie andere Anwendungen und Dienste den Azure Rights Management-Dienst von Azure Information Protection unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

Wenn Sie nun die Bereitstellung einschließlich Konfiguration dieser Anwendungen und Dienste durchführen möchten, gehen Sie zu [Roadmap für die Bereitstellung von Azure Information Protection](/plan-design/deployment-roadmap.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]