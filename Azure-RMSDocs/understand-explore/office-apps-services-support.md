---
# required metadata

title: Office-Anwendungen und -Dienste | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Office-Anwendungen und -Dienste

*Gilt für: Azure Rights Management, Office 365*

Für Endbenutzer-Office-Anwendungen (z.B. Word, Excel, PowerPoint und Outlook) und Office-Dienste (z.B. Exchange und SharePoint) kann Microsoft Azure Rights Management verwendet werden, um die Daten Ihrer Organisation zu schützen.

## Office-Anwendungen: Word, Excel, PowerPoint, Outlook
Diese Anwendungen bieten systemeigene Unterstützung für Rights Management durch Verwendung von IRM (Information Rights Management, Verwaltung von Informationsrechten) und ermöglichen Benutzern das Schützen eines gespeicherten Dokuments oder einer zu sendenden E-Mail. Benutzer können Vorlagen anwenden oder stark angepasste Einstellungen für Zugriff, Rechte und Nutzungseinschränkungen verwenden. 

Beispielsweise können Benutzer eine Datei so konfigurieren, dass nur Personen in Ihrer Organisation darauf zugreifen können, oder kontrollieren, ob die Datei bearbeitet werden kann, oder die Datei auf schreibgeschützt einschränken oder das Drucken der Datei verhindern. Für Dateien mit zeitlicher Relevanz kann eine Ablaufzeit konfiguriert werden (direkt von Benutzern oder durch Anwenden einer Vorlage), nach deren Erreichen kein Zugriff auf die Datei mehr möglich ist. Für Outlook können Benutzer außerdem die Option **Nicht weiterleiten** auswählen, um Datenlecks zu verhindern.

## Exchange Online und Exchange Server
Wenn Sie Exchange Online oder Exchange Server verwenden, können Sie IRM-Integration (Verwaltung von Informationsrechten) verwenden, die zusätzliche Informationsschutzlösungen bereitstellt:

-   **Exchange ActiveSync IRM** , sodass mobile Geräte E-Mails schützen und geschützte E-Mails nutzen können.

-   RMS-Unterstützung für die **Outlook Web App**, ähnlich implementiert wie der Outlook-Client, sodass Benutzer E-Mails per Vorlagen oder durch Angabe einzelner Optionen schützen und Benutzer geschützte E-Mails, die an sie gesendet werden, lesen und verwenden können.

-   **Schutzregeln** für Outlook-Clients, die ein Administrator so konfiguriert, dass sie automatisch RMS-Vorlagen auf E-Mails für angegebene Empfänger anwenden. Wenn beispielsweise interne E-Mails an Ihre Rechtsabteilung gesendet werden, können sie nur von Mitgliedern der Rechtsabteilung gelesen und nicht weitergeleitet werden. Benutzer sehen den auf die E-Mail angewendeten Schutz vor dem Senden und können diesen standardmäßig entfernen, falls sie ihn für unnötig halten. E-Mails werden vor dem Senden verschlüsselt. Weitere Informationen finden Sie unter [Outlook-Schutzregeln](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) und [Erstellen einer Outlook-Schutzregel](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) in der Exchange-Bibliothek.

-   **Transportregeln** , die ein Administrator so konfiguriert, dass automatisch auf Grundlage von Eigenschaften wie Absender, Empfänger, Nachrichtenbetreff und Inhalt RMS-Vorlagen auf E-Mails angewendet werden. Diese Regeln ähneln dem Konzept nach Schutzregeln, doch können Benutzer den Schutz nicht entfernen, sie können auf Outlook Web Access und auf von mobilen Geräten gesendete E-Mails angewendet werden, und die E-Mails werden vor dem Senden vom Client nicht verschlüsselt. Weitere Informationen finden Sie unter [Erstellen einer Transportschutzregel](https://technet.microsoft.com/library/dd302432.aspx) in der Exchange-Bibliothek.

-   **DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust)** , die Bedingungssätze enthalten, um E-Mails zu filtern und Maßnahmen zur Verhinderung von Datenverlusten bei vertraulichen oder sensiblen Inhalten zu ergreifen (z. B. personenbezogene Daten oder Kreditkarteninformationen). Richtlinientipps können verwendet werden, wenn sensible Daten erkannt werden, um Benutzer darauf aufmerksam zu machen, dass sie eventuell Informationsschutz anwenden sollten, basierend auf den in der E-Mail enthaltenen Informationen. Weitere Informationen finden Sie unter [Verhinderung von Datenverlust](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) in der Exchange-Bibliothek.

-   **Office 365-Nachrichtenverschlüsselung** , die Transportregeln verwendet, um verschlüsselte E-Mails an Personen außerhalb Ihres Unternehmens zu senden, wobei die E-Mail in einem Browser gelesen wird, dessen Oberfläche Outlook Web App ähnelt. Sie können den Haftungsausschluss- und Kopfzeilentext in den verschlüsselten E-Mails Ihres Unternehmens anpassen und sogar Ihr Firmenlogo hinzufügen. Weitere Informationen finden Sie unter [Office 365-Nachrichtenverschlüsselung](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) auf der Office-Website.

Wenn Sie Exchange Server verwenden, können Sie die Informationsschutzfeatures mit [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] verwenden, indem Sie den RMS-Verbindungsdienst bereitstellen, der als Relay zwischen lokalen Servern und dem RMS-Cloud-Dienst fungiert. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Connectors](../deploy-use/deploy-rms-connector.md)..

## SharePoint Online und SharePoint Server
Wenn Sie SharePoint Online oder SharePoint Server verwenden, können Sie IRM-Integration verwenden, wodurch Administratoren Listen und Bibliotheken schützen können, damit eine Datei, die von einem Benutzer ausgecheckt wird, geschützt ist, sodass nur autorisierte Personen sie entsprechend der von Ihnen angegebenen Informationsschutzregeln anzeigen und verwenden können. So kann die Datei beispielsweise schreibgeschützt sein, das Kopieren von Text deaktivieren, das Speichern einer lokalen Kopie oder das Drucken der Datei verhindern.

Bei Listen und Bibliotheken wird der Informationsschutz immer von einem Administrator und nie von einem Endbenutzer angewendet. Außerdem wird er auf Listen- oder Bibliotheksebene für alle Dokumente in dem betreffenden Container angewendet statt auf einzelne Dateien.  Wenn Sie SharePoint Online verwenden, können die Benutzer IRM auch auf ihre OneDrive for Business-Bibliothek anwenden.

Zuerst muss der IRM-Dienst für SharePoint aktiviert werden. Dann geben Sie die Verwaltung von Informationsrechten für eine Bibliothek an. Im Falle von SharePoint Online und OneDrive for Business können die Benutzer IRM auch für ihre OneDrive for Business-Bibliothek festlegen. SharePoint verwendet keine Richtlinienvorlagen für Rechte. Allerdings stehen SharePoint-Konfigurationseinstellungen zur Wahl, die größtenteils den Einstellungen entsprechen, die Sie in Vorlagen angeben können.

Wenn Sie SharePoint Server verwenden, können Sie die Informationsschutzfeatures mit [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] verwenden, indem Sie den RMS-Verbindungsdienst bereitstellen, der als Relay zwischen lokalen Servern und dem RMS-Cloud-Dienst fungiert. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Connectors](../deploy-use/deploy-rms-connector.md)..

> [!NOTE]
> Gegenwärtig gibt es einige Beschränkungen bei der Verwendung von IRM mit SharePoint:
> 
> -   Sie können weder die standardmäßigen noch die benutzerdefinierten Vorlagen verwenden, die Sie im klassischen Azure-Portal verwalten.
> -   Dateien mit der Dateinamenerweiterung PPDF für geschützte PDF-Dateien werden nicht unterstützt. Dateien mit der Dateinamenerweiterung PDF, die systemintern von RMS geschützt wurden, werden unterstützt, wenn Sie einen PDF-Reader verwenden, der eine systemeigene Unterstützung von RMS bietet.
> -   Da Office auf mobilen Geräten RMS noch nicht unterstützt, muss auf diesen Geräten ein Browser zum Anzeigen von mit RMS geschützten Dateien verwendet werden, und die Dateien sind schreibgeschützt.

Azure RMS wendet Nutzungseinschränkungen und Datenverschlüsselung nicht beim ursprünglichen Erstellen der Dokumente in SharePoint oder beim Hochladen in die Bibliothek an, sondern erst beim Herunterladen der Dokumente aus SharePoint. Informationen zum Schutz der Dokumente vor dem Herunterladen finden Sie in der SharePoint-Dokumentation unter [Datenverschlüsselung in OneDrive for Business und SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) .

Weitere Informationen zu Azure RMS in Verbindung mit SharePoint finden Sie im folgenden Beitrag im Office-Blog: [Neuerungen bei Information Rights Management in SharePoint und SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## Nächste Schritte

Informationen dazu, wie andere Anwendungen und Dienste Azure Rights Management unterstützen, finden Sie unter [Unterstützung von Azure Rights Management durch Anwendungen](applications-support.md)..

<!--HONumber=Apr16_HO4-->


