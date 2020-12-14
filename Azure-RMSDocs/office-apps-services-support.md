---
title: So unterstützen Office-Apps und -Dienste Azure RMS über AIP
description: Verwendung des Azure Rights Management-Diensts über AIP zum Schutz der Daten Ihrer Organisation durch Endbenutzer-Office-Anwendungen wie Word und Outlook und Office-Dienste wie Exchange und SharePoint.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 05/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.subservice: azurerms
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 37d6eae1559f34bcbc84edecd3cc42926b4888c4
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97381594"
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>So unterstützen Office-Anwendungen und -Dienste Azure Rights Management 

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified Bezeichnung Client und Classic Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). *

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Endbenutzer-Office-Anwendungen und Office-Dienste können den Azure Rights Management-Dienst aus Azure Information Protection zum Schutz der Daten Ihrer Organisation verwenden. Diese Office-Anwendungen sind Word, Excel, PowerPoint und Outlook. Die Office-Dienste sind Exchange und Microsoft SharePoint. Die Office-Konfigurationen, die den Azure Rights Management-Dienst unterstützen, verwenden oft den Begriff **Information Rights Management (IRM)**.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Office-Anwendungen: Word, Excel, PowerPoint, Outlook
Diese Anwendungen unterstützen die integrierte Azure-Rights Management und ermöglichen Benutzern das Anwenden von Schutz auf ein gespeichertes Dokument oder auf eine zu sendende e-Mail-Nachricht. Benutzer können Vorlagen zum Anwenden des Schutzes anwenden. Alternativ können Benutzer für Word, Excel und PowerPoint individuell anpassbare benutzerdefinierte Einstellungen für Zugriff, Rechte und Nutzungseinschränkungen festlegen.

Benutzer können z.B. ein Word-Dokument so konfigurieren, dass es nur von Personen in Ihrer Organisation geöffnet werden kann. Sie können alternativ steuern, ob ein Excel-Arbeitsblatt bearbeitet werden kann oder schreibgeschützt ist oder nicht gedruckt werden kann. Für Dateien mit zeitlicher Relevanz kann eine Ablaufzeit konfiguriert werden, nach deren Erreichen kein Zugriff auf die Datei mehr möglich ist. Diese Konfiguration kann direkt von Benutzern oder durch Anwenden einer Schutzvorlage vorgenommen werden. Für Outlook können Benutzer außerdem die Option **Nicht weiterleiten** auswählen, um Datenlecks zu verhindern.

Wenn Sie bereit sind, Office-Apps zu konfigurieren, sehen Sie [Office-Apps: Konfiguration für Clients](configure-office-apps.md).

Informationen zu relevanten bekannten Problemen finden Sie unter [bekannte Probleme von AIP in Office-Anwendungen](known-issues.md#aip-known-issues-in-office-applications).

## <a name="exchange-online-and-exchange-server"></a>Exchange Online und Exchange Server
Wenn Sie Exchange Online oder Exchange Server verwenden, können Sie Optionen für Azure Information Protection konfigurieren. Mit dieser Konfiguration kann Exchange die folgenden Lösungen zum Schutz bereitstellen:

-   **Exchange ActiveSync IRM**, sodass mobile Geräte E-Mails schützen und geschützte E-Mails nutzen können.

-   Unterstützung des E-Mail-Schutzes für **Outlook im Web**, was auch gleichzeitig für den Outlook-Client angewendet wird. Mit dieser Konfiguration können Benutzer E-Mail-Nachrichten mithilfe von Schutzvorlagen oder Optionen schützen. Benutzer können geschützte E-Mail-Nachrichten, die an sie gesendet werden, lesen und verwenden.

-   **Schutzregeln** für Outlook-Clients, die ein Administrator so konfiguriert, dass sie automatisch Schutzvorlagen auf E-Mails und Optionen für angegebene Empfänger anwenden. Wenn beispielsweise interne E-Mails an Ihre Rechtsabteilung gesendet werden, können sie nur von Mitgliedern der Rechtsabteilung gelesen und nicht weitergeleitet werden. Benutzer sehen den auf die E-Mail angewendeten Schutz vor dem Senden und können diesen standardmäßig entfernen, falls sie ihn für unnötig halten. E-Mails werden vor dem Senden verschlüsselt. Weitere Informationen finden Sie unter [Outlook-Schutzregeln](/exchange/outlook-protection-rules-exchange-2013-help) und [Erstellen einer Outlook-Schutzregel](/exchange/create-an-outlook-protection-rule-exchange-2013-help) in der Exchange-Bibliothek.

-   **Nachrichtenflussregeln**, die von einem Administrator konfiguriert werden, um automatisch Schutzvorlagen auf E-Mail-Nachrichten und Optionen anzuwenden. Diese Regeln basieren auf Eigenschaften wie Sender, Empfänger, Betreff der Nachricht und Inhalt. Diese Regeln ähneln dem Konzept der Schutzregeln, verbieten Benutzern jedoch, den Schutz zu entfernen, da der Schutz vom Exchange-Dienst und nicht vom Client festgelegt wird. Da der Schutz vom Dienst festgelegt wird, ist es nicht wichtig, welches Gerät oder Betriebssystem die Benutzer besitzen. Weitere Informationen finden Sie unter [Nachrichtenflussregeln (Transportregeln) in Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) und [Erstellen einer Transportschutzregel](/exchange/create-a-transport-protection-rule-exchange-2013-help).

-   **DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust)**, die Bedingungssätze enthalten, um E-Mails zu filtern und Maßnahmen zur Verhinderung von Datenverlusten bei vertraulichen oder sensiblen Inhalten zu ergreifen. Eine der Aktion, die Sie angeben können, ist das Anwenden von Verschlüsselung als Schutz, indem Sie eine der folgenden Schutzvorlagen oder Optionen angeben. Richtlinientipps können verwendet werden, wenn sensible Daten erkannt werden, um Benutzer darauf aufmerksam zu machen, dass sie eventuell Schutz anwenden sollten. Weitere Informationen finden Sie unter [Verhinderung von Datenverlust](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) in der Exchange Online-Dokumentation.

-   **Nachrichten Verschlüsselung** , die das Senden einer geschützten e-Mail und geschützter Office-Dokumente als Anlagen an eine beliebige e-Mail-Adresse auf jedem Gerät unterstützt. Eine Webanwendung unterstützt soziale Netzwerke als Identitätsanbieter oder eine beliebige Einmalkennung für Benutzerkonten, für die Azure AD nicht verwendet wird. Weitere Informationen finden Sie unter [Einrichten neuer Microsoft 365 Nachrichten Verschlüsselungsfunktionen, die auf Azure Information Protection basieren](/microsoft-365/compliance/set-up-new-message-encryption-capabilities) , aus der Microsoft 365-Dokumentation. Weitere Informationen zu dieser Konfiguration finden Sie unter [Microsoft 365-Nachrichten Verschlüsselung](/microsoft-365/compliance/ome).

Wenn Sie Exchange lokal verwenden, können Sie IRM-Funktionen mit dem Azure Rights Management-Dienst verwenden, indem Sie den Azure Rights Management-Connector bereitstellen. Dieser Connector fungiert als Relay zwischen den lokalen Servern und dem Azure Rights Management-Dienst.

Weitere Informationen zu den E-Mail-Optionen, die Sie zum Schützen von E-Mails verwenden können, finden Sie unter [Option „Nicht weiterleiten“ für E-Mails](configure-usage-rights.md#do-not-forward-option-for-emails) und [Option „Encrypt Only“ (Nur verschlüsseln) für E-Mails](configure-usage-rights.md#encrypt-only-option-for-emails).

Wenn Sie bereit sind, Exchange zum Schützen von E-Mails zu konfigurieren, dann sehen Sie sich folgende Seiten an:

- Informationen zu Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration).

- Informationen zu Exchange lokal finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

   Weitere Informationen finden Sie unter

- **Client für einheitliche Bezeichnungen**: Konfigurieren Sie Vertraulichkeits Bezeichnungen und Beschriftungs Richtlinien in Ihrem Beschriftungs-Admin Center, einschließlich der Microsoft 365 Security Center, Microsoft 365 Compliance Center oder Microsoft 365 Security & Compliance Center. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/sensitivity-labels).

- **Klassischer Client**. Konfigurieren Sie Schutz Vorlagen im Azure-Portal. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).


## <a name="sharepoint-in-microsoft-365-and-sharepoint-server"></a>SharePoint in Microsoft 365 und SharePoint Server

Wenn Sie SharePoint in Microsoft 365 oder SharePoint Server verwenden, können Sie Dokumente mithilfe des Features für die SharePoint-Verwaltung von Informationsrechten (Information Rights Management, unm) schützen. Mit dieser Funktion können Administratoren Listen und Bibliotheken schützen, damit eine heruntergeladene Datei, die von einem Benutzer ausgecheckt wird, geschützt ist und nur autorisierte Personen sie entsprechend den von Ihnen angegebenen Informationsschutzrichtlinien anzeigen und verwenden können. So kann die Datei beispielsweise schreibgeschützt sein, das Kopieren von Text deaktivieren, das Speichern einer lokalen Kopie oder das Drucken der Datei verhindern.

Word, PowerPoint, Excel und PDF-Dokumente unterstützen diesen IRM-Schutz von SharePoint. Standardmäßig beschränkt sich der Schutz auf die Person, die das Dokument herunterlädt. Sie können diese Standardeinstellung mit einer Konfigurationsoption namens **Gruppenschutz zulassen** ändern, die den Schutz auf eine von Ihnen angegebene Gruppe erweitert. Sie können beispielsweise eine Gruppe angeben, die über die Berechtigung verfügt, Dokumente in der Bibliothek zu bearbeiten, sodass dieselbe Gruppe von Benutzern das Dokument (unabhängig davon, welcher Benutzer es heruntergeladen hat) außerhalb von SharePoint bearbeiten kann. Sie können alternativ auch eine Gruppe angeben, der keine Berechtigungen in SharePoint zugeteilt werden, aber deren Benutzer außerhalb von SharePoint auf das Dokumentation zugreifen müssen. Bei SharePoint-Listen und -Bibliotheken wird dieser Schutz immer von einem Administrator und nie von einem Endbenutzer konfiguriert. Sie legen die Berechtigungen auf Websiteebene fest, und diese Berechtigungen werden in der Standardeinstellung von jeder Liste und Bibliothek in dieser Website geerbt. Wenn Sie SharePoint in Microsoft 365 verwenden, können Benutzer auch Ihre Microsoft onedrive-Bibliothek für den unm-Schutz konfigurieren.

Für eine präzisere Kontrolle können Sie eine Liste oder Bibliothek in der Website so konfigurieren, dass sie nicht länger Berechtigungen vom übergeordneten Element erben. Anschließend können Sie IRM-Berechtigungen auf dieser Ebene (Liste oder Bibliothek) konfigurieren, die dann als „Eindeutige Berechtigungen“ bezeichnet werden. Berechtigungen werden jedoch immer auf Containerebene festgelegt. Sie können keine Berechtigungen für einzelne Dateien festlegen. 

Zuerst muss der IRM-Dienst für SharePoint aktiviert werden. Dann geben Sie die IRM-Berechtigungen für eine Bibliothek an. Für SharePoint und onedrive können Benutzer auch die unm-Berechtigungen für Ihre onedrive-Bibliothek angeben. SharePoint verwendet keine Richtlinienvorlagen für Rechte. Allerdings stehen SharePoint-Konfigurationseinstellungen zur Wahl, die einigen Einstellungen entsprechen, die Sie in den Vorlagen angeben können.

Wenn Sie SharePoint Server benutzen, können Sie diesen IRM-Schutz durch Bereitstellen des Azure Rights Management-Verbindungsdiensts verwenden. Dieser Verbindungsdienst fungiert als Relay zwischen den lokalen Servern und dem Rights Management-Clouddienst. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

> [!NOTE]
> Bei der Verwendung von SharePoint-IRiM gibt es einige Einschränkungen:
> 
> - Sie können weder die standardmäßigen noch die benutzerdefinierten Schutzvorlagen verwenden, die Sie im Azure-Portal verwalten. 
> 
> - Dateien mit der Dateinamenerweiterung PPDF für geschützte PDF-Dateien werden nicht unterstützt. Weitere Informationen zum Anzeigen geschützter PDF-Dokumente finden Sie unter [Reader für geschützte PDF-Dokumente für Microsoft Azure Information Protection](./rms-client/protected-pdf-readers.md).
> 
> - Die gleichzeitige gemeinsame Bearbeitung eines Dokuments durch mehrere Personen wird nicht unterstützt. Um ein Dokument in einer durch IRM geschützten Bibliothek zu bearbeiten, müssen Sie es zuerst auschecken und herunterladen und können es dann in Ihrer Office-Anwendung bearbeiten. Daher kann nur jeweils eine Person ein Dokument bearbeiten.

Wenn Sie für Bibliotheken, die nicht durch einen unm-Schutz geschützt sind, den Schutz nur auf eine Datei anwenden, die Sie dann in SharePoint oder onedrive hochladen, können Sie die folgenden Aktionen nicht ausführen: Co-Authoring, Office für das Web, Search, Dokument Vorschau, Miniaturansicht, eDiscovery und Verhinderung von Datenverlust (DLP).

> [!IMPORTANT]
> SharePoint-IRiM kann in Kombination mit Vertraulichkeits Bezeichnungen verwendet werden, die den Schutz anwenden. Wenn Sie beide Funktionen gleichzeitig verwenden, ändert sich das Verhalten für geschützte Dateien. Weitere Informationen finden Sie unter [Aktivieren von Vertraulichkeits Bezeichnungen für Office-Dateien in SharePoint und onedrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files).

Wenn Sie den SharePoint IRM-Schutz verwenden, wendet der Azure Rights Management-Dienst Nutzungseinschränkungen und Datenverschlüsselung nicht beim ursprünglichen Erstellen der Dokumente in SharePoint oder beim Hochladen in die Bibliothek an, sondern erst beim Herunterladen der Dokumente aus SharePoint. Informationen dazu, wie Dokumente vor dem herunterladen geschützt werden, finden Sie in der SharePoint-Dokumentation unter [Datenverschlüsselung in onedrive und SharePoint](/microsoft-365/compliance/data-encryption-in-odb-and-spo?redirectSourcePath=%252fen-us%252farticle%252f6501b5ef-6bf7-43df-b60d-f65781847d6c) .

Der folgende Beitrag aus dem Microsoft 365-Blog ist zwar nicht mehr neu, enthält jedoch einige zusätzliche Informationen, die Sie möglicherweise nützlich finden: [Neuerungen bei den Informationen Rights Management in SharePoint](https://www.microsoft.com/microsoft-365/blog/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/) .

Weitere Änderungen finden [Sie unter Updates für SharePoint-Sicherheit,-Verwaltung und-Migration](https://techcommunity.microsoft.com/t5/Microsoft-SharePoint-Blog/Updates-to-SharePoint-security-administration-and-migration/ba-p/549585).

Wenn Sie bereit sind, SharePoint für IRM zu konfigurieren:

- Informationen zu SharePoint in Microsoft 365 finden Sie unter [SharePoint in Microsoft 365 und onedrive: unm-Konfiguration](configure-office365.md#sharepoint-in-microsoft-365-and-onedrive-irm-configuration).

- Informationen zu Sharepoint Server finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).


## <a name="next-steps"></a>Nächste Schritte

Wenn Sie Microsoft 365 haben, sind Sie möglicherweise daran interessiert, [Datei Schutzlösungen in Microsoft 365](/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365fileprotect)zu überprüfen, die empfohlene Funktionen zum Schutz von Dateien in Microsoft 365 bereitstellen.

Informationen dazu, wie andere Anwendungen und Dienste den Azure Rights Management-Dienst von Azure Information Protection unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

Wenn Sie bereit sind, die Bereitstellung zu starten, einschließlich der Konfiguration dieser Anwendungen und Dienste, lesen Sie die [Dokumentation zur AIP-Bereitstellung für Klassifizierung, Bezeichnung und Schutz](deployment-roadmap-classify-label-protect.md).