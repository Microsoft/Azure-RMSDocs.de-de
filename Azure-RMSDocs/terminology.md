---
title: Terminologie zu Azure Information Protection
description: Sind einige Wörter, Ausdrücke oder Abkürzungen bezüglich Microsoft Azure Information Protection unklar? Hier finden Sie die Definitionen für Begriffe und Abkürzungen, die entweder für Azure Information Protection spezifisch sind oder im Kontext dieses Diensts eine spezielle Bedeutung haben.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/24/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9d9aad27d0c76552dbf7234bf5849eeb72058cae
ms.sourcegitcommit: 1c1d7067ae7aa8b822bb4ecd23cd7a644989e38c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55067950"
---
# <a name="terminology-for-azure-information-protection"></a>Terminologie zu Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Sind einige Wörter, Ausdrücke oder Abkürzungen bezüglich Microsoft Azure Information Protection unklar? Hier finden Sie die Definitionen für Begriffe und Abkürzungen, die entweder für Azure Information Protection spezifisch sind oder im Kontext dieses Diensts eine spezielle Bedeutung haben.

|Ausdruck|Definition|
|--------|--------------|
|AADRM|Der Name des PowerShell-Moduls für den Azure Rights Management-Dienst, der aus der inoffiziellen Abkürzung für Azure Rights Management abgeleitet wurde, als er noch den Namen (Windows) Azure Active Directory Rights Management hatte.|
|Aktivieren|Aktivieren des Azure Rights Management-Diensts, damit eine Organisation ihre Dokumente und E-Mails schützen kann. Dieser Vorgang aktiviert außerdem die IRM-Features in Exchange Online und SharePoint Online.|
|Active Directory-Rechteverwaltungsdienste|Häufig als *AD RMS* abgekürzt.<br /><br />Eine Windows Server-Rolle, die Rights Management-Schutz mithilfe von Verschlüsselung und Richtlinien zum Schutz von Dokumenten, Dateien und E-Mails bereitstellt.|
|AD RMS|Siehe *Active Directory Rights Management Services*.|
AzureInformationProtection|Der Name des PowerShell-Moduls für den Azure Information Protection-Client.
|Azure Information Protection|Ein cloudbasierter Dienst, der Bezeichnungen zum Klassifizieren und Schützen von Dokumenten und E-Mails verwendet. Azure Rights Management stellt Schutz mithilfe von Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien bereit.|
Azure Information Protection-Client|Die Clientseite von Azure Information Protection, wo Benutzer, Administratoren und Dienste die Bezeichnungen und Einstellungen aus der Azure Information Protection-Richtlinie verwenden können.|
|Azure Information Protection-Bezeichnung|Ein Element, das einen Klassifizierungswert auf Dokumente und E-Mails anwendet und sie optional schützen kann.|
|Azure Information Protection-Richtlinie|Vom Administrator definierte Konfiguration für Clients und Dienste, die Azure Information Protection-Bezeichnungen und -Richtlinieneinstellungen verwenden.|
|Azure Information Protection-Überprüfung|Ein auf Windows Server ausgeführter Dienst, mit dem Sie Dokumente auf lokalen Ordnern, Netzwerkfreigaben sowie SharePoint Server-Websites und -Bibliotheken ermitteln, klassifizieren und schützen können.|
|Azure Information Protection-Viewer|Eine auf Windows-Computern und mobilen Geräten ausgeführte App zum Anzeigen geschützter Dateien.|
|Azure Rights Management|Häufig als *Azure RMS* abgekürzt.<br /><br />Ein Azure-Dienst, der von Azure Information Protection verwendet wird und mithilfe von Verschlüsselung und Richtlinien das Schützen von Dokumenten, Dateien und E-Mails unterstützt.  Wird auch als *Azure Rights Management-Dienst*bezeichnet. Es gibt diese früheren Namen:<br /><br />- *Microsoft Azure Active Directory Rights Management*: Häufig abgekürzt zu Windows Azure AD Rights Management-Dienste.<br /><br />- *RMS Online*: Die ursprünglich vorgeschlagene Name, der möglicherweise manchmal in Fehlermeldungen und Protokolldateieinträgen angezeigt wird.|
|Azure RMS|Siehe *Azure Rights Management*.|
|Standardvorlage|Eine Schutzvorlage, die automatisch für Sie erstellt wird, wenn Sie ein Abonnement für Azure Information Protection beziehen, damit Sie sofort damit beginnen können, Dokumente und E-Mails mit vertraulichen Informationen zu schützen.|
|BYOK|Siehe *Bring Your Own Key*.|
|Bring Your Own Key|Häufig als *BYOK*abgekürzt.<br /><br />Eine Konfigurations- und Topologieoption, die von Organisationen gewählt wird, die einen eigenen Mandantenschlüssel für Azure Information Protection generieren und verwalten möchten.|
|Inhaltsschlüssel|Ein eindeutiger Schlüssel, der von RMS-aktivierten Anwendungen für jedes Dokument oder jede E-Mail, das bzw. die von Rights Management geschützt wird, erstellt wird und hilft, die Gefahr der Veröffentlichung von Informationen zu beschränken.|
|Nutzen|Ein Dokument oder eine E-Mail zu lesen oder zu verwenden, wenn dieser Inhalt durch Rights Management geschützt ist. Bei einem Dokument umfasst das Nutzen die Bearbeitung und das Hinzufügen von neuem Inhalt zu einem geschützten Dokument. Bei einer E-Mail-Nachricht umfasst das Nutzen die Beantwortung einer geschützten Nachricht.|
|Deaktivieren|Deaktivieren des Rights Management-Diensts, sodass die Organisation Azure Information Protection nicht mehr verwenden kann.|
|Abteilungsvorlage|Eine Schutzvorlage, die Sie erstellen, und die so konfiguriert ist, dass sie nicht von allen Benutzern in Ihrer Organisation, sondern nur von ausgewählten Benutzern angezeigt werden kann. Auch bekannt als *bereichsbezogene Vorlage*.|
|RMS-aktivierte Anwendungen|Anwendungen, die Rechteverwaltung systemeigen unterstützen; dazu zählen Office-Anwendungen, wie etwa Word und Excel. Unabhängige Softwarehersteller (ISVs, Independent Software Vendors) und Entwickler können ebenfalls Anwendungen erstellen, die Rights Management nativ unterstützen.|
|Unternehmensrechteverwaltung|Ein branchenüblicher, allgemeiner Ausdruck, der häufig zur Beschreibung von Produkten und Lösungen verwendet wird, die Organisationen beim Schützen sensibler oder wertvoller Informationen durch Einsatz einer Kombination von Verschlüsselung und Richtlinienautorisierungstools unterstützen. Azure Information Protection ist ein Beispiel einer Unternehmens-RMS-Lösung (ERM, Enterprise Rights Management).|
|ERM|Siehe *Unternehmensrechteverwaltung*.|
|Allgemeiner Schutz|Eine Schutzstufe, bei der jeder Dateityp verschlüsselt wird und Unbefugte am Öffnen von Dateien gehindert werden. Nach dem Öffnen sind Dateien ungeschützt und können in Anwendungen verwendet werden, die Rights Management nicht nativ unterstützen.|
|HYOK|Weitere Informationen finden Sie unter *Hold Your Own Key*.|
|Hold Your Own Key|Häufig als *HYOK*abgekürzt.<br /><br />Eine Konfigurations- und Topologieoption für Organisationen, die ihre eigenen Schlüssel generieren und lokal speichern möchten, in der Regel aus behördlichen oder Kompatibilitätsgründen.|
|Schlüsselobjekt|Im Kontext des Mandantenschlüssels ist dies eine Entität, die Metadaten enthält, die vom Azure Rights Management-Dienst für kryptografische Operationen benötigt wird.|
|label|Siehe *Azure Information Protection-Bezeichnung*.|
|Datenschutz|Manchmal als *IP*(Information Protection) abgekürzt.<br /><br />Ein branchenweiter allgemeiner Begriff, der sich auf den Schutz von Daten und Dateien vor nicht autorisiertem Zugriff bezieht, selbst nachdem die Daten und Dateien die Organisation durch E-Mails oder die Dokumentfreigabe verlassen haben. Microsoft Azure Information Protection ist ein Beispiel einer Lösung zum Schutz von Daten.|
|Information Rights Management|Häufig als *IRM*abgekürzt.<br /><br />Ein Ausdruck, der in Verbindung mit den Office-Diensten, wie etwa Exchange Server, Word und SharePoint Online, verwendet wird, um die Fähigkeit zur Unterstützung von Microsoft Rights Management Services zu beschreiben.|
|IRM|Siehe *Information Rights Management*.|
|Office-Nachrichtenverschlüsselung|Häufig als *OME* abgekürzt<br /><br />Die neuen Office 365-Funktionen für die Nachrichtenverschlüsselung sind nativ in Azure Rights Management integriert. So sind E-Mails von internen und externen Benutzern gleichermaßen geschützt, Vorlagen werden automatisch aktualisiert und das BYOK-Szenario wird unterstützt. Die vorherige OME-Implementierung war nur für externe Empfänger gedacht, erforderte eine Regel für den E-Mail-Übertragung und bot keine BYOK-Unterstützung.|
|MSDRM|Manchmal als Verweis auf den RMS-Client 1.0 verwendet, der durch den neueren Client MSIPC ersetzt wurde. Dieser ältere Client unterstützt Anwendungen, die mit dem RMS SDK 1.0 entwickelt wurden, und unterstützt Office 2010 und Office 2007, Exchange 2010 und Exchange 2013 und SharePoint 2010 und SharePoint 2007.|
|MSIPC|Manchmal als Verweis auf den RMS-Client 2.0 verwendet, der an die Stelle des älteren RMS-Client, MSDRM, getreten ist. Dieser spätere Client unterstützt Anwendungen, die mit dem RMS SDK 2.0 entwickelt wurden, und außerdem Office 365 ProPlus, Office 2019, Office 2016, Office 2013, SharePoint 2013, die RMS-Freigabeanwendung und den Azure Information Protection-Client.|
|Systemeigener Schutz|Eine Schutzstufe, die in allen RMS-aktivierten Anwendungen verfügbar ist und unberechtigte Personen daran hindert, eine Datei zu öffnen. Ferner können stringentere Richtlinien durchgesetzt werden, wie etwa "schreibgeschützt" und "nicht anzeigen". Darüber hinaus bleibt dieser Schutz für die Datei bestehen, auch wenn die Datei an andere Personen weitergeleitet oder an einem öffentlichen Speicherort, auf den andere zugreifen können, gespeichert wird.|
|PFILE|Die Dateierweiterung, die an alle Dateien angehängt wird, die allgemein von einem Rights Management-Dienst geschützt werden.|
|Berechtigungsstufe|Eine logische Gruppe von Nutzungsrechten. Sie erleichtert es den Endbenutzern und Administratoren, eine Auswahl aus rollenbasierten Konfigurationsoptionen zu treffen. Beispiele: Prüfer und Mitautor.|
|Schützen|Anwenden von Rights Management-Überwachungen auf Dateien oder E-Mail-Nachrichten mithilfe von Verschlüsselungs-, Identitäts- und Access Control-Richtlinien für den Schutz Ihrer Daten.|
|Schutzvorlage|Auch bekannt als *Vorlage für Benutzerrechterichtlinien*, *Rights Management-Vorlage* und *RMS-Vorlage*.<br /><br />Eine Gruppe von Schutzeinstellungen, die von einem Administrator verwaltet werden und die definierten Nutzungsrechte für autorisierte Benutzer sowie Zugriffssteuerungen für Ablauf und Offlinezugriff enthalten. |
|publish|Schützen einer Datei, um sie vor unberechtigtem Zugriff und unberechtigter Verwendung zu schützen. Wird auch in Verbindung mit Schutzvorlagen und der Azure Information Protection-Richtlinie als Begriff verwendet, um diese Elemente für die Verwendung durch Clients und Dienste verfügbar zu machen.|
|Rights Management-Connector|Ein ausgehendes Proxyrelay, das für lokale Dienste wie Exchange Server und SharePoint bereitgestellt werden kann, um Daten mithilfe des Azure Rights Management-Diensts zu schützen.|
|Rights Management-Aussteller|Das Konto, das ein Dokument oder eine E-Mail schützt.|
|Rights Management-Besitzer|Das Konto, das volle Zugriffsrechte über ein geschütztes Dokument oder eine geschützte E-Mail behält, da es automatisch das Nutzungsrecht über den Vollzugriff auf Rights Management erhält, und von allen Ablaufdaten oder Offline-Einstellungen ausgenommen ist.|
|Rights Management Services|Der allgemeine Ausdruck, der sowohl für die Cloudversion von Rights Management (Azure Rights Management) als auch für die lokale Version von Rights Management (AD RMS) gilt.|
|Rights Management-Freigabeanwendung|Eine optional herunterladbare Anwendung für Windows und mobile Geräte, die das sichere Freigeben von Dateien per Einbindung und per E-Mail unterstützt und jetzt durch den Azure Information Protection-Client ersetzt wurde.|
|RMS|Siehe *Rights Management Services*.|
|RMS-Connector|Siehe *Rights Management-Connector*.|
|RMS for Individuals|Ein kostenloses Abonnement, mit dessen Hilfe ein Benutzer Rights Management verwenden kann, wenn seine Organisation nicht über ein Abonnement für Office 365 oder Azure Active Directory verfügt.|
|RMS-Freigabeanwendung|Siehe *Rights Management-Freigabeanwendung*.|
|RMS-Vorlage|Siehe *Schutzvorlage*.|
|Reiner Schutzmodus|Ein Betriebsmodus für den Azure Information Protection-Client, wenn keine Azure Information Protection-Richtlinie zum Anwenden von Bezeichnungen vorliegt. In diesem Modus werden keine Klassifizierungsbezeichnungen angezeigt, aber Benutzer können weiterhin Rights Management-Schutz anwenden.|
|Scanner|Siehe *Azure Information Protection-Überprüfung*.|
|Administrator|Eine Gruppe besonders vertrauenswürdiger Administratoren, die Dateien, die von der Organisation mithilfe eines Rights Management-Diensts geschützt wurden, entschlüsseln und anschließend öffnen kann. Normalerweise ist diese Zugangsstufe für rechtliche eDiscovery und Überwachungsteams erforderlich.|
|Mandantenschlüssel|Auch als Schlüssel des lizenzgebenden Serverzertifikats bezeichnet (SLC, Server Licensor Certificate).<br /><br />Der eindeutige Schlüssel eines Unternehmens, der den Ursprung des Schutzes für alle Kryptografiefunktionen von Rights Management darstellt, die mit diesem Mandantenschlüssel verkettet sind.|
|Schutz aufheben|Entfernen Sie Schutzüberwachungen aus Dateien oder E-Mail-Nachrichten, in denen Verschlüsselungs-, Identitäts-, Nutzungsrechte- und Zugriffskontrollrichtlinien verwendet wurden, um Ihre Daten zu schützen.|
|Nutzungslizenz|Ein dokumentspezifisches Zertifikat, das einem Benutzer gewährt wird, wenn er eine Datei oder E-Mail öffnet, die durch einen Rights Management-Dienst geschützt wurde. Dieses Zertifikat enthält Benutzerrechte für die Datei oder E-Mail-Nachricht und den Verschlüsselungsschlüssel, der zum Verschlüsseln des Inhalts und zusätzliche Zugriffseinschränkungen, die in der Richtlinie für das Dokument definiert wurden.|

