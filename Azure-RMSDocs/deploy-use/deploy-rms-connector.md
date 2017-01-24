---
title: Bereitstellen des Azure Rights Management-Connectors | Azure Information Protection
description: "Hier finden Sie Anweisungen zur Bereitstellung des RMS-Connectors, der den Dienst zum Schutz von Daten für bestehende lokale Bereitstellungen, die Exchange Server, SharePoint Server oder Windows Server und die Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI) ausführen, bereitstellt."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: eaa1d7a0a74fa68f9bf1d15f348dbb45d14cee9a


---

# <a name="deploying-the-azure-rights-management-connector"></a>Bereitstellen des Azure Rights Management-Verbindungsdiensts

>*Gilt für: Azure Information Protection, Windows Server 2012, Windows Server 2012 R2*

Hier erhalten Sie Informationen zum Azure Rights Management-Connector und dazu, wie Sie ihn erfolgreich für Ihre Organisation bereitstellen. Der Connector bietet Datenschutz für bestehende lokale Bereitstellungen, die **Microsoft Exchange Server**, **SharePoint Server** oder Dateiserver nutzen, die Windows Server und die **Dateiklassifizierungsinfrastruktur** (File Classification Infrastructure, FCI) ausführen.

> [!TIP]
> Ein allgemeines Beispielszenario mit Screenshots finden Sie im Abschnitt [Automatischer Schutz von Dateien auf Dateiservern, auf denen Windows Server und Dateiklassifizierungsinfrastruktur ausgeführt wird](../understand-explore/what-admins-users-see.md#automatically-protecting-files-on-file-servers-running-windows-server-and-file-classification-infrastructure) im Artikel [Azure RMS in Aktion](../understand-explore/what-admins-users-see.md).

## <a name="overview-of-the-microsoft-rights-management-connector"></a>Übersicht über den Microsoft Rights Management-Verbindungsdienst
Mit dem Microsoft Rights Management-Connector können Sie schnell vorhandene lokale Server für die Verwendung ihrer IRM-Funktionalität mit dem cloudbasierten Microsoft Rights Management Service (Azure RMS) aktivieren. Mit dieser Funktionalität können IT-Abteilungen und Benutzer Dokumente und Bilder, sowohl innerhalb als auch außerhalb der Organisation, ganz einfach schützen, ohne zusätzliche Infrastruktur installieren oder Vertrauensstellungen mit anderen Organisationen einrichten zu müssen. 

Der RMS-Verbindungsdienst ist ein kleiner Dienst, der lokal auf Servern installiert wird, die unter Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 ausgeführt werden. Zusätzlich zum Ausführen des Connectors auf physischen Computern können Sie ihn auch auf virtuellen Computern ausführen, einschließlich virtuellen Azure IaaS-Computern. Nachdem Sie den Connector bereitgestellt haben, fungiert er wie in der folgenden Abbildung dargestellt als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und dem Clouddienst. Die Pfeile zeigen die Richtung an, in der Netzwerkverbindungen initiiert werden.

![RMS-Connectorarchitektur (Übersicht)](../media/RMS_connector.png)


### <a name="on-premises-servers-supported"></a>Unterstützung lokaler Server

Der RMS-Verbindungsdienst unterstützt die folgenden lokalen Server: Exchange Server, SharePoint Server und Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden, um Richtlinien zu klassifizieren und auf Office-Dokumente in einem Ordner anzuwenden. 

> [!NOTE]
> Wenn Sie alle Dateitypen (nicht nur Office-Dokumente) mit der Dateiklassifizierungsinfrastruktur schützen möchten, verwenden Sie nicht den RMS-Connector, sondern die [RMS-Schutz-Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).

Informationen zu den Versionen dieser lokalen Server, die vom RMS-Connector unterstützt werden, finden Sie unter [Lokale Server, die Azure RMS unterstützen](..\get-started\requirements-servers.md).


### <a name="support-for-hybrid-scenarios"></a>Unterstützung für Hybridszenarios

Sie können den RMS-Connector auch dann verwenden, wenn einige Benutzer Verbindungen mit Onlinediensten in einem Hybridszenario herstellen. Beispielsweise könnte es sein, dass für die Postfächer einiger Benutzer Exchange Online und für die Postfächer einiger anderer Benutzer Exchange Server verwendet wird. Nachdem Sie den RMS-Connector (RMS-Verbindungsdienst) installiert haben, können alle Benutzer E-Mails und Anlagen mithilfe von Azure RMS schützen und nutzen, und der Informationsschutz zwischen den beiden Bereitstellungskonfigurationen funktioniert nahtlos.

### <a name="support-for-customer-managed-keys-byok"></a>Unterstützung für von Kunden verwaltete Schlüssel (BYOK)

Wenn Sie Ihren eigenen Mandantenschlüssel für Azure RMS verwalten (das „Bring Your Own Key“- oder BYOK-Szenario), greifen der RMS-Connector und die lokalen Server, die ihn verwenden, nicht auf das Hardwaresicherheitsmodul (HSM) zu, das Ihren Mandantenschlüssel enthält. Dies liegt daran, dass alle kryptografischen Vorgänge, bei denen der Mandantenschlüssel zum Einsatz kommt, in Azure RMS und nicht lokal ausgeführt werden.

Weitere Informationen über dieses Szenario, in dem Sie Ihren Mandantenschlüssel verwalten, finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design\plan-implement-tenant-key.md).

## <a name="prerequisites-for-the-rms-connector"></a>Voraussetzungen für den RMS-Verbindungsdienst
Stellen Sie vor der Installation des RMS-Verbindungsdiensts sicher, dass folgende Voraussetzungen erfüllt sind.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Der RMS-Verbindungsdienst (RMS) ist aktiviert.|[Aktivieren von Azure Rights Management](activate-service.md)|
|Verzeichnissynchronisierung zwischen Ihren lokalen Active Directory-Gesamtstrukturen und Azure Active Directory|Nachdem RMS aktiviert wurde, muss Azure Active Directory so konfiguriert werden, dass es mit den Benutzern und Gruppen in Ihrer Active Directory-Datenbank arbeitet.<br /><br />**Wichtig**: Dieser Verzeichnissynchronisierungsschritt ist erforderlich, damit der RMS-Verbindungsdienst funktioniert, und zwar auch bei einem Testnetzwerk. Auch wenn Sie Office 365 und Azure Active Directory verwenden können, indem Sie manuell in Azure Active Directory erstellte Konten verwenden, erfordert der Verbindungsdienst, dass die Konten in Azure Active Directory mit den Active Directory-Domänendiensten synchronisiert werden. Die manuelle Kennwortsynchronisierung ist nicht ausreichend.<br /><br />Weitere Informationen finden Sie in den folgenden Ressourcen:<br /><br />[Integrieren Ihrer lokalen Identitäten in Azure Active Directory](/active-directory/active-directory-aadconnect)<br /><br />[Vergleich von Integrationstools für Hybrididentitätsverzeichnisse](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison)|
|Optional, aber empfohlen:<br /><br />Aktivieren Sie den Verbund zwischen Ihrem lokalen Active Directory und Azure Active Directory.|Sie können den Identitätsverbund zwischen Ihrem lokalen Verzeichnis und Azure Active Directory aktivieren. Diese Konfiguration ermöglicht eine nahtlosere Benutzererfahrung durch Verwendung des einmaligen Anmeldens beim RMS-Verbindungsdienst. Ohne einmaliges Anmelden werden Benutzer zur Eingabe ihrer Anmeldeinformationen aufgefordert, bevor sie rechtegeschützte Inhalte verwenden können.<br /><br />Anleitungen zum Konfigurieren des Verbunds mithilfe der Active Directory-Verbunddienste (AD FS) zwischen den Active Directory-Domänendiensten und Azure Active Directory finden Sie in der [Prüfliste: Verwenden von AD FS zur Implementierung und Verwaltung des einmaligen Anmeldens](http://technet.microsoft.com/library/jj205462.aspx) in der Windows Server-Bibliothek.|
|Mindestens zwei Mitgliedscomputer, auf denen der RMS-Verbindungsdienst installiert wird:<br /><br />- Ein physischer oder virtueller 64-Bit-Computer unter einem der folgenden Betriebssysteme: Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2.<br /><br />- Mindestens 1 GB RAM<br /><br />- Mindestens 64 GB Datenträgerspeicherplatz<br /><br />- Mindestens eine Netzwerkschnittstelle<br /><br />- Zugriff auf das Internet über eine Firewall (oder einen Webproxy) ohne Anforderung einer Authentifizierung<br /><br />- Muss sich in einer Gesamtstruktur oder Domäne befinden, die eine Vertrauensstellung zu anderen organisationsinternen Gesamtstrukturen hat, die Installationen von Exchange- oder SharePoint-Servern enthalten, die Sie mit dem RMS-Connector verwenden möchten.|Für Fehlertoleranz und Hochverfügbarkeit müssen Sie den RMS-Verbindungsdienst auf mindestens zwei Computern installieren.<br /><br />**Tipp**: Wenn Sie Outlook Web Access oder mobile Geräte verwenden, die Exchange ActiveSync IRM nutzen, und es wichtig ist, dass Sie den Zugriff auf mit Azure RMS geschützte E-Mails und Anlagen aufrechterhalten, empfiehlt sich Folgendes: Stellen Sie eine Gruppe von Verbindungsdienstservern mit Lastenausgleich bereit, um hohe Verfügbarkeit zu gewährleisten.<br /><br />Sie benötigen keine dedizierten Server zum Ausführen des Verbindungsdiensts, Sie müssen ihn jedoch auf einem anderen Computer als die Server installieren, die den Verbindungsdienst verwenden werden.<br /><br />**Wichtig**: Installieren Sie den Verbindungsdienst nicht auf einem Computer, auf dem Exchange Server, SharePoint Server oder ein Dateiserver ausgeführt wird, der für die Dateiklassifizierungsinfrastruktur konfiguriert ist, wenn Sie die Funktionalität dieser Dienste mit Azure RMS verwenden möchten. Darüber hinaus dürfen Sie diesen Verbindungsdienst nicht auf einem Domänencontroller installieren.|

## <a name="steps-to-deploy-the-rms-connector"></a>Schritte zur Bereitstellung des RMS-Connectors

Der Connector führt keine automatische Prüfung aller [Voraussetzungen](deploy-rms-connector.md#prerequisites-for-the-rms-connector) durch, die für eine erfolgreiche Bereitstellung erforderlich sind. Stellen Sie daher vor dem Start sicher, dass diese erfüllt sind. Für die Bereitstellung müssen Sie den Connector installieren und konfigurieren und dann die Server konfigurieren, die den Connector verwenden sollen. 

-   **Schritt 1:**  [Installieren des RMS-Verbindungsdiensts](install-configure-rms-connector.md#installing-the-rms-connector)

-   **Schritt 2:**  [Eingeben von Anmeldeinformationen](install-configure-rms-connector.md#entering-credentials)

-   **Schritt 3:**  [Autorisieren von Servern für die Verwendung des RMS-Verbindungsdiensts](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector)

-   **Schritt 4:**  [Konfigurieren von Lastenausgleich und Hochverfügbarkeit](install-configure-rms-connector.md#configuring-load-balancing-and-high-availability)

-   Optional: [Konfigurieren des RMS-Verbindungsdiensts für die Verwendung von HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https)

-   Optional: [Konfigurieren des RMS-Verbindungsdiensts für einen Webproxyserver](install-configure-rms-connector.md#configuring-the-rms-connector-for-a-web-proxy-server)

-   Optional: [Installieren des Administrationstool des RMS-Verbindungsdiensts auf administrativen Computern](install-configure-rms-connector.md#installing-the-rms-connector-administration-tool-on-administrative-computers)

-   **Schritt 5:**  [Konfigurieren von Servern für die Verwendung des RMS-Verbindungsdiensts](configure-servers-rms-connector.md)

    -   [Konfigurieren eines Exchange-Servers für die Verwendung des Verbindungsdiensts](configure-servers-rms-connector.md#configuring-an-exchange-server-to-use-the-connector)

    -   [Konfigurieren eines SharePoint-Servers für die Verwendung des Verbindungsdiensts](configure-servers-rms-connector.md#configuring-a-sharepoint-server-to-use-the-connector)

    -   [Konfigurieren eines Dateiservers, der die Dateiklassifizierungsinfrastruktur verwendet, für die Verwendung des Verbindungsdiensts](configure-servers-rms-connector.md#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)


## <a name="next-steps"></a>Nächste Schritte

Weiter zu Schritt 1: [Installieren und Konfigurieren des Azure Rights Management-Connectors](install-configure-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


