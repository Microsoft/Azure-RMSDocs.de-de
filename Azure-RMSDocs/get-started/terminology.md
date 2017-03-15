---
title: Terminologie zu Azure Information Protection
description: "Sind einige Wörter, Ausdrücke oder Abkürzungen bezüglich Microsoft Azure Information Protection unklar? Hier finden Sie die Definitionen für Begriffe und Abkürzungen, die entweder für Azure Information Protection spezifisch sind oder im Kontext dieses Diensts eine spezielle Bedeutung haben."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5fecc61fb77625047a5ebedad4ff906fe8c27bbe
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="terminology-for-azure-information-protection"></a>Terminologie zu Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Sind einige Wörter, Ausdrücke oder Abkürzungen bezüglich Microsoft Azure Information Protection unklar? Hier finden Sie die Definitionen für Begriffe und Abkürzungen, die entweder für Azure Information Protection spezifisch sind oder im Kontext dieses Diensts eine spezielle Bedeutung haben.

|Ausdruck|Definition|
|--------|--------------|
|AADRM|Der Name des Windows PowerShell-Moduls für den Azure Rights Management-Dienst, der aus der inoffiziellen Abkürzung für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] abgeleitet wurde, als er noch den Namen (Windows) Azure Active Directory Rights Management hatte.|
|Aktivieren|Aktivieren des [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Diensts, damit eine Organisation ihre Dokumente und E-Mails schützen kann. Dieser Vorgang aktiviert außerdem die Features zur Rechteverwaltung in Exchange Online und SharePoint Online.|
|Active Directory-Rechteverwaltungsdienste|Häufig als *AD RMS*abgekürzt.<br /><br />Eine Windows Server-Rolle, die Rights Management-Schutz mithilfe von Verschlüsselung und Richtlinien bereitstellt, die das Schützen von Dokumenten, Dateien und E-Mails unterstützen.|
|AD RMS|Siehe *Active Directory Rights Management Services*.|
|Azure Information Protection|Ein cloudbasierter Dienst, der Klassifizierungen, Bezeichnungen und Schutz verwendet, um Dokumente und E-Mails zu schützen. Azure Rights Management stellt Schutz mithilfe von Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien bereit.|
|Azure Rights Management|Häufig als *Azure RMS*abgekürzt.<br /><br />Ein Azure-Dienst, der von Azure Information Protection verwendet wird und mithilfe von Verschlüsselung und Richtlinien das Schützen von Dokumenten, Dateien und E-Mails unterstützt.  Wird auch als *Azure Rights Management-Dienst*bezeichnet. Es gibt diese früheren Namen:<br /><br />- *Windows Azure Active Directory Rights Management*: Wird häufig als Windows Azure AD Rights Management-Dienst abgekürzt.<br /><br />- *RMS Online*: Der ursprünglich vorgeschlagene Name, der unter Umständen manchmal in Fehlermeldungen und Protokolldateieinträgen angezeigt wird.|
|Azure RMS|Siehe *Azure Rights Management*.|
|BYOK|Siehe *Bring Your Own Key*.|
|Bring Your Own Key|Häufig als *BYOK*abgekürzt.<br /><br />Eine Konfigurations- und Topologieoption, die von Organisationen gewählt wird, die einen eigenen Mandantenschlüssel für Azure Information Protection generieren und verwalten möchten.|
|Inhaltsschlüssel|Ein eindeutiger Schlüssel, der von RMS-aktivierten Anwendungen für jedes Dokument oder jede E-Mail, das bzw. die mithilfe von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] geschützt wird, erstellt wird und hilft, die Gefahr der Aufdeckung von Informationen zu beschränken.|
|Nutzen|Das Aufheben der Sperrung einer Datei, um sie zu lesen oder verwenden, wenn die Datei durch [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] geschützt ist.|
|Deaktivieren|Deaktivieren des Rights Management-Diensts, sodass die Organisation Azure Information Protection nicht mehr verwenden kann.|
|Abteilungsvorlage|Eine Vorlage für Benutzerrechterichtlinien, die Sie erstellen (eine benutzerdefinierte Vorlage) und die so konfiguriert ist, dass sie nicht von allen Benutzern in Ihrer Organisation, sondern nur von ausgewählten Benutzer angezeigt werden kann.|
|RMS-aktivierte Anwendungen|Anwendungen, die Rechteverwaltung systemeigen unterstützen; dazu zählen Office-Anwendungen, wie etwa Word und Excel. Unabhängige Softwarehersteller (ISVs, Independent Software Vendors) und Entwickler können ebenfalls Anwendungen erstellen, die [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] systemeigen unterstützen.|
|Unternehmensrechteverwaltung|Ein branchenüblicher, allgemeiner Ausdruck, der häufig zur Beschreibung von Produkten und Lösungen verwendet wird, die Organisationen beim Schützen sensibler oder wertvoller Informationen durch Einsatz einer Kombination von Verschlüsselung und Richtlinienautorisierungstools unterstützen. Azure Information Protection ist ein Beispiel einer Unternehmens-RMS-Lösung (ERM, Enterprise Rights Management).|
|ERM|Siehe *Unternehmensrechteverwaltung*.|
|Allgemeiner Schutz|Eine Schutzstufe, bei der jeder Dateityp verschlüsselt wird und Unbefugte am Öffnen von Dateien gehindert werden. Nach dem Öffnen sind Dateien ungeschützt und können in Anwendungen verwendet werden, die [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] nicht systemeigen unterstützen.|
|HYOK|Weitere Informationen finden Sie unter *Hold Your Own Key*.|
|Hold Your Own Key|Häufig als *HYOK*abgekürzt.<br /><br />Eine Konfigurations- und Topologieoption für Organisationen, die ihre eigenen Schlüssel generieren und lokal speichern möchten, in der Regel aus behördlichen oder Kompatibilitätsgründen.|
|Datenschutz|Manchmal als *IP*(Information Protection) abgekürzt.<br /><br />Ein branchenweiter allgemeiner Begriff, der sich auf den Schutz von Daten und Dateien vor nicht autorisiertem Zugriff bezieht, selbst nachdem die Daten und Dateien die Organisation durch E-Mails oder die Dokumentfreigabe verlassen haben. Microsoft Azure Information Protection ist ein Beispiel einer Lösung zum Schutz von Daten.|
|Information Rights Management|Häufig als *IRM*abgekürzt.<br /><br />Ein Ausdruck, der in Verbindung mit den Office-Diensten, wie etwa Exchange Server, Word und SharePoint Online, verwendet wird, um die Fähigkeit zur Unterstützung von Microsoft Rights Management Services zu beschreiben.|
|IRM|Siehe *Information Rights Management*.|
|MSDRM|Manchmal als Verweis auf den RMS-Client 1.0 verwendet, der durch den neueren Client MSIPC ersetzt wurde. Dieser ältere Client unterstützt Anwendungen, die mit dem RMS SDK 1.0 entwickelt wurden, und unterstützt Office 2010 und Office 2007, Exchange 2010 und Exchange 2013 und SharePoint 2010 und SharePoint 2007.|
|MSIPC|Manchmal als Verweis auf den RMS-Client 2.0 verwendet, der an die Stelle des älteren RMS-Client, MSDRM, getreten ist. Dieser spätere Client unterstützt Anwendungen, die mit dem RMS SDK 2.0 entwickelt wurden, und außerdem Office 2016 und Office 2013, SharePoint 2013, die RMS-Freigabeanwendung und der Azure Information Protection-Client.|
|Systemeigener Schutz|Eine Schutzstufe, die in allen RMS-aktivierten Anwendungen verfügbar ist und unberechtigte Personen daran hindert, eine Datei zu öffnen. Ferner können stringentere Richtlinien durchgesetzt werden, wie etwa "schreibgeschützt" und "nicht anzeigen". Darüber hinaus bleibt dieser Schutz für die Datei bestehen, auch wenn die Datei an andere Personen weitergeleitet oder an einem öffentlichen Speicherort, auf den andere zugreifen können, gespeichert wird.|
|PFILE|Die Dateierweiterung, die an alle Dateien angehängt wird, die allgemein von einem Rights Management-Dienst geschützt werden.|
|PPDF|Die Dateierweiterung, die der Rights Management-Dienst beim automatischen Erstellen einer PDF-Kopie einer Datei (Word, Excel, PowerPoint oder PDF), die Sie per E-Mail freigeben, anfügt, damit die Datei auf allen Geräten gelesen (aber nicht bearbeitet) werden kann.|
|Berechtigungsstufe|Eine logische Gruppe von Nutzungsrechten. Sie erleichtert es den Endbenutzern und Administratoren, eine Auswahl aus rollenbasierten Konfigurationsoptionen zu treffen. Beispiele: Prüfer und Mitautor.|
|Schützen|Anwenden von Rights Management-Überwachungen auf Dateien oder E-Mail-Nachrichten mithilfe von Verschlüsselungs-, Identitäts- und Access Control-Richtlinien für den Schutz Ihrer Daten.|
|publish|Schützen einer Datei, um sie vor unberechtigtem Zugriff und unberechtigter Verwendung zu schützen.|
|Rights Management-Connector|Ein ausgehendes Proxyrelay, das für lokale Dienste wie Exchange Server und SharePoint bereitgestellt werden kann, um Daten mithilfe von des Azure Rights Management-Diensts zu schützen.|
|Rights Management Services|Der allgemeine Ausdruck, der sich sowohl auf die Cloudversion von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ([!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]) als auch auf die lokale Version von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] (AD RMS) bezieht.|
|Rights Management-Freigabeanwendung|Eine optional herunterladbare Anwendung für Windows und besonders verbreitete mobile Geräte, die das sichere Freigeben von Dateien per Einbindung und per E-Mail unterstützt und jetzt durch den Azure Information Protection-Client ersetzt wurde.|
|RMS|Siehe *Rights Management Services*.|
|RMS-Connector|Siehe *Rights Management-Connector*.|
|RMS for Individuals|Ein kostenloses Abonnement, mit dessen Hilfe ein Benutzer [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] verwenden kann, wenn seine Organisation nicht über ein Abonnement für Office 365 oder Azure Active Directory verfügt.|
|RMS-Freigabeanwendung|Siehe *Rights Management-Freigabeanwendung*.|
|Reiner Schutzmodus|Ein Betriebsmodus für den Azure Information Protection-Client, wenn keine Azure Information Protection-Richtlinie zum Anwenden von Bezeichnungen vorliegt. In diesem Modus werden keine Klassifizierungsbezeichnungen angezeigt, aber Benutzer können weiterhin Rights Management-Schutz anwenden.|
|Administrator|Eine Gruppe besonders vertrauenswürdiger Administratoren, die Dateien, die von der Organisation mithilfe eines Rights Management-Diensts geschützt wurden, entschlüsseln und anschließend öffnen kann. Normalerweise ist diese Zugangsstufe für rechtliche eDiscovery und Überwachungsteams erforderlich.|
|Mandantenschlüssel|Auch als Schlüssel des lizenzgebenden Serverzertifikats bezeichnet (SLC, Server Licensor Certificate).<br /><br />Der eindeutige Schlüssel eines Unternehmens, der den Ursprung des Schutzes für alle Kryptografiefunktionen von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], die mit diesem Mandantenschlüssel verkettet sind, darstellt.|
|Schutz aufheben|Entfernen von Rights Management-Überwachungen aus Dateien oder E-Mail-Nachrichten, in denen Verschlüsselungs-, Identitäts- und Zugriffskontrollrichtlinien verwendet wurden, um Ihre Daten zu schützen.|
|Nutzungslizenz|Ein dokumentspezifisches Zertifikat, das einem Benutzer gewährt wird, wenn er eine Datei oder E-Mail öffnet, die durch einen Rights Management-Dienst geschützt wurde. Dieses Zertifikat enthält Benutzerrechte für die Datei oder E-Mail-Nachricht und den Verschlüsselungsschlüssel, der zum Verschlüsseln des Inhalts und zusätzliche Zugriffseinschränkungen, die in der Richtlinie für das Dokument definiert wurden.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
