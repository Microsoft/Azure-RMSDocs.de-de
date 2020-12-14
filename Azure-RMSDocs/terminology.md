---
title: Terminologie für Azure Information Protection (AIP)
description: Verwechselt durch ein Wort, einen Ausdruck oder ein Akronym, das sich auf Microsoft Azure Information Protection (AIP) bezieht? Hier finden Sie die Definition für Begriffe und Abkürzungen, die entweder für AIP spezifisch sind oder eine bestimmte Bedeutung haben, wenn Sie im Kontext dieses diensdienstanbieter verwendet werden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: af5c035a19847eca18a9686cc32895c363c0a926
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384555"
---
# <a name="terminology-for-azure-information-protection"></a>Terminologie zu Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Sind einige Wörter, Ausdrücke oder Abkürzungen bezüglich Microsoft Azure Information Protection unklar? Hier finden Sie die Definitionen für Begriffe und Abkürzungen, die entweder für Azure Information Protection spezifisch sind oder im Kontext dieses Diensts eine spezielle Bedeutung haben.

## <a name="word-phrase-or-acronym"></a>Wort, Ausdruck oder Akronym

[A](#a)  |  [B](#b)  |  [C](#c)  |  [D](#d)  |  [E](#e)  |  [G](#g)  |  [H](#h)  |  [I](#i)  |  [K](#k)  |  [L](#l)  |  [M](#m) [N](#n)  |  [O](#o)  |  [P](#p)  |  [R](#r)  |  [S](#s)  |  [T](#t)  |  [U](#u)

### <a name="a"></a>Ein
|Begriff|Definition|
|--------|--------------|
|**AADRM**|Der Name des ersten PowerShell-Moduls für den Schutzdienst (Azure Rights Management), das von der inoffiziellen Abkürzung für Azure Rights Management abgeleitet wurde, als es zuvor (Windows) Azure Active Directory Rights Management hieß. </br></br>Dieses PowerShell-Modul wird jetzt durch das aipservice-Modul ersetzt.|
|**Aktivieren**|Aktivieren Sie den Azure Rights Management Protection-Dienst, damit eine Organisation Ihre Dokumente und e-Mails schützen kann. </br></br>Diese Aktion ermöglicht außerdem die unm-Features in Exchange Online und Microsoft SharePoint.|
|**Active Directory-Rechteverwaltungsdienste**|Häufig als *AD RMS* abgekürzt.<br /><br />Eine Windows Server-Rolle, die Rights Management-Schutz mithilfe von Verschlüsselung und Richtlinien zum Schutz von Dokumenten, Dateien und E-Mails bereitstellt.|
|**AD RMS**|Siehe *Active Directory Rights Management Services*.|
|**AIP** |Siehe *Azure Information Protection*.|
|**Aipservice**|Der aktuelle Name des PowerShell-Moduls für den Schutzdienst, der durch das ältere aadrm-Modul ersetzt.|
|**AzureInformationProtection**|Der Name des PowerShell-Moduls für den Azure Information Protection klassischen oder vereinheitlichten Bezeichnungs Client.|
|**Azure Information Protection**|Ein cloudbasierter Dienst, der Bezeichnungen zum Klassifizieren und Schützen von Dokumenten und E-Mails verwendet. </br></br> Azure Rights Management stellt Schutz mithilfe von Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien bereit.|
|**Azure Information Protection des klassischen Clients**|Manchmal mit *klassischem Client* abgekürzt.<br /><br />Die ursprüngliche Clientseite Azure Information Protection, mit der Benutzer, Administratoren und Dienste die Bezeichnungen und Einstellungen Ihrer Azure Information Protection Richtlinie verwenden können. </br></br> Wird nun durch den Azure Information Protection Unified Bezeichnung-Client ersetzt.|
|**Azure Information Protection-Bezeichnung**|Ein Element, das immer einen Klassifizierungswert auf Dokumente und E-Mails anwendet und sie auch schützen kann. </br></br>Wenn eine Bezeichnung angewendet wird, wird die Bezeichnungsinformation in den Metadaten für Anwendungen und Dienste gespeichert, damit diese gelesen und (optional) auf sie reagiert werden kann.|
|**Azure Information Protection-Richtlinie**|Vom Administrator definierte Konfiguration für Clients und Dienste, die Azure Information Protection-Bezeichnungen und -Richtlinieneinstellungen verwenden.|
|**Azure Information Protection-Überprüfung**|Ein Dienst, der unter Windows Server ausgeführt wird und das ermitteln, klassifizieren und schützen von Dokumenten auf Netzwerkfreigaben und SharePoint-Server Websites und-Bibliotheken ermöglicht.|
|**Azure Information Protection-Client für einheitliche Bezeichnungen**|Manchmal als einheitlicher Bezeichnungs *Client* abgekürzt.<br /><br />Der-Client für Windows-Computer, mit denen Benutzer, Administratoren und Dienste die Vertraulichkeits Bezeichnungen und Bezeichnungs Richtlinien Einstellungen aus dem Office 365 Security & Compliance Center, dem Microsoft 365 Security Center und dem Microsoft 365 Compliance Center verwenden können. </br></br>Ersetzt den Azure Information Protection klassischen Client.|
|**Azure RMS**|Siehe *Azure Rights Management*.|
|**Azure Information Protection Viewer**|Eine auf Windows-Computern und mobilen Geräten ausgeführte App zum Anzeigen geschützter Dateien.|
|**Azure Rights Management**|Wird auch als *Azure Rights Management Service* bezeichnet und häufig als *Azure RMS* abgekürzt.<br /><br />Ein Azure-Dienst, der von Azure Information Protection verwendet wird und mithilfe von Verschlüsselung und Richtlinien das Schützen von Dokumenten, Dateien und E-Mails unterstützt. </br></br>Es gibt diese früheren Namen:<br /><br />- *Windows Azure Active Directory Rights Management*: Wird häufig als Windows Azure AD Rights Management-Dienst abgekürzt.<br /><br />- *RMS Online*: Der ursprünglich vorgeschlagene Name, der unter Umständen manchmal in Fehlermeldungen und Protokolldateieinträgen angezeigt wird.|
| | |

### <a name="b"></a>B

|Begriff|Definition|
|--------|--------------|
|**Bring your own Key**|Häufig als *BYOK* abgekürzt.<br /><br />Eine Konfigurations- und Topologieoption, die von Organisationen gewählt wird, die einen eigenen Mandantenschlüssel für Azure Information Protection generieren und verwalten möchten.|
|**integrierte Bezeichnung**|Eine Microsoft 365-APP oder-Dienstfunktion zur Unterstützung von Vertraulichkeits Bezeichnungen, ohne dass ein zusätzlicher Bezeichnungs Client installiert werden muss. Wird auch als *native Bezeichnung* bezeichnet.|
|**BYOK**|Siehe *Bring Your Own Key*.|
| | |

### <a name="c"></a>C

|Begriff|Definition|
|--------|--------------|
|**Verzehr**|**Nur im Kontext des Schutzes**: </br>Ein Dokument oder eine E-Mail zu lesen oder zu verwenden, wenn dieser Inhalt durch einen Rights Management-Dienst geschützt ist. </br>Bei einem Dokument umfasst das Nutzen die Bearbeitung und das Hinzufügen von neuem Inhalt zu einem geschützten Dokument. Bei einer E-Mail-Nachricht umfasst das Nutzen die Beantwortung einer geschützten Nachricht.<br /><br/>**Im Kontext der Bezeichnung (mit oder ohne Schutz)**: </br>Um die Bezeichnungsinformationen zu lesen und ggf. darauf zu reagieren, die in den Metadaten der Dateien und E-Mails gespeichert sind.|
|**Inhalts Schlüssel**|Ein eindeutiger Schlüssel, der von RMS-aktivierten Anwendungen für jedes Dokument oder jede E-Mail, das bzw. die von Rights Management geschützt wird, erstellt wird und hilft, die Gefahr der Veröffentlichung von Informationen zu beschränken.|
| | |

### <a name="d"></a>D

|Begriff|Definition|
|--------|--------------|
|**Deaktivieren**|Deaktivieren des Rights Management-Diensts, sodass die Organisation Azure Information Protection nicht mehr verwenden kann.|
|**Standardvorlage**|Eine Schutzvorlage, die automatisch für Sie erstellt wird, wenn Sie ein Abonnement für Azure Information Protection beziehen, damit Sie sofort damit beginnen können, Dokumente und E-Mails mit vertraulichen Informationen zu schützen.|
|**Abteilungsvorlage**|Eine Schutzvorlage, die Sie erstellen, und die so konfiguriert ist, dass sie nicht von allen Benutzern in Ihrer Organisation, sondern nur von ausgewählten Benutzern angezeigt werden kann. Auch bekannt als *bereichsbezogene Vorlage*.|
|**Doppelte Schlüssel Verschlüsselung** |Diese Methode wird auch als *DKE* bezeichnet und ist eine Methode zum Sichern von Inhalten, die zwei Schlüssel verwendet: eine in Azure und eine andere, die der custern innehat. </br></br>DKE wird nur von AIP Unified Client unterstützt und wird in Microsoft 365 konfiguriert. |
| | |

### <a name="e"></a>E

|Begriff|Definition|
|--------|--------------|
|**RMS-aktivierte Anwendungen**|Anwendungen, die Rechteverwaltung systemeigen unterstützen; dazu zählen Office-Anwendungen, wie etwa Word und Excel. </br></br>Unabhängige Softwarehersteller (ISVs, Independent Software Vendors) und Entwickler können ebenfalls Anwendungen erstellen, die Rights Management nativ unterstützen.|
|**Unternehmens-RMS**|Ein branchenüblicher, allgemeiner Ausdruck, der häufig zur Beschreibung von Produkten und Lösungen verwendet wird, die Organisationen beim Schützen sensibler oder wertvoller Informationen durch Einsatz einer Kombination von Verschlüsselung und Richtlinienautorisierungstools unterstützen. </br></br>Azure Information Protection ist ein Beispiel einer Unternehmens-RMS-Lösung (ERM, Enterprise Rights Management).|
|**ERM**|Siehe *Unternehmens-RMS*.|
| | |

### <a name="g"></a>G

|Begriff|Definition|
|--------|--------------|
|**generischer Schutz**|Eine Schutzstufe, bei der jeder Dateityp verschlüsselt wird und Unbefugte am Öffnen von Dateien gehindert werden. </br></br>Nach dem Öffnen sind Dateien ungeschützt und können in Anwendungen verwendet werden, die Rights Management nicht nativ unterstützen.|
| | |

### <a name="h"></a>H

|Begriff|Definition|
|--------|--------------|
|**halten Sie Ihren eigenen Schlüssel**|Häufig als *HYOK* abgekürzt.<br /><br />Eine Konfigurations- und Topologieoption für Organisationen, die ihre eigenen Schlüssel generieren und lokal speichern möchten, in der Regel aus behördlichen oder Kompatibilitätsgründen. </br></br>Hyok wird nur vom klassischen AIP-Client unterstützt.|
|**HYOK**|Weitere Informationen finden Sie unter *Hold Your Own Key*.|
| | |

### <a name="i"></a>I

|Begriff|Definition|
|--------|--------------|
|**Informationsschutz**|Manchmal als *IP* (Information Protection) abgekürzt.<br /><br />Ein branchenweiter allgemeiner Begriff, der sich auf den Schutz von Daten und Dateien vor nicht autorisiertem Zugriff bezieht, selbst nachdem die Daten und Dateien die Organisation durch E-Mails oder die Dokumentfreigabe verlassen haben. </br></br>Microsoft Azure Information Protection ist ein Beispiel einer Lösung zum Schutz von Daten.|
|**Informationen Rights Management**|Häufig als *IRM* abgekürzt.<br /><br />Ein Begriff, der in Verbindung mit Office-Diensten wie Exchange Server, Word und SharePoint verwendet wird, um die Fähigkeit zur Unterstützung der Microsoft Rights Management Services zu beschreiben.|
|**IRM**|Siehe *Information Rights Management*.|
| | |


### <a name="k"></a>K

|Begriff|Definition|
|--------|--------------|
|**Key-Objekt**|Im Kontext des Mandantenschlüssels ist dies eine Entität, die Metadaten enthält, die vom Azure Rights Management-Dienst für kryptografische Operationen benötigt wird.|
| | |

### <a name="l"></a>L

|Begriff|Definition|
|--------|--------------|
|**label**|Siehe *Azure Information Protection-Bezeichnung*.|
| | |

### <a name="m"></a>M

|Begriff|Definition|
|--------|--------------|
|**Microsoft Information Protection**| Manchmal als *MIP* abgekürzt.<br /><br /> Ein Framework für Produkte und integrierte Funktionen, die denselben Bezeichnungs Speicher verwenden ("einheitliche Bezeichnungen") und den Schutz der sensiblen Daten Ihrer Organisation erleichtern.|
|**MIP**| Siehe *Microsoft Information Protection*|
|**MSDRM**|Manchmal als Verweis auf den RMS-Client 1.0 verwendet, der durch den neueren Client MSIPC ersetzt wurde. </br></br>Dieser ältere Client unterstützt Anwendungen, die mit dem RMS SDK 1.0 entwickelt wurden, und unterstützt Office 2010 und Office 2007, Exchange 2010 und Exchange 2013 und SharePoint 2010 und SharePoint 2007.|
|**MSIPC**|Manchmal als Verweis auf den RMS-Client 2.0 verwendet, der an die Stelle des älteren RMS-Client, MSDRM, getreten ist. </br></br>Dieser neuere Client unterstützt Anwendungen, die mit dem RMS SDK 2.0 entwickelt wurden, und außerdem Office 365 ProPlus, Office 2019, Office 2016, Office 2013, SharePoint 2013 und den Azure Information Protection-Client.|
| | |

### <a name="n"></a>N

|Begriff|Definition|
|--------|--------------|
|**Systemeigener Schutz**|Eine Schutzstufe, die in allen RMS-aktivierten Anwendungen verfügbar ist und unberechtigte Personen daran hindert, eine Datei zu öffnen. Ferner können stringentere Richtlinien durchgesetzt werden, wie etwa "schreibgeschützt" und "nicht anzeigen". </br></br>Darüber hinaus bleibt dieser Schutz für die Datei bestehen, auch wenn die Datei an andere Personen weitergeleitet oder an einem öffentlichen Speicherort, auf den andere zugreifen können, gespeichert wird.|
| | |

### <a name="o"></a>O

|Begriff|Definition|
|--------|--------------|
|**Office-Nachrichtenverschlüsselung**|Häufig als *OME* abgekürzt<br /><br />Die neuen Funktionen zur Verschlüsselung von Office 365-Nachrichten verfügen über eine integrierte Integration in den Azure Rights Management-Dienst, um den gleichen e-Mail-Schutz für interne und externe Benutzer, die automatische Aktualisierung von Vorlagen und die Unterstützung des Byok-Szenarios (Bring your own Key) bereitzustellen. </br></br>Die vorherige OME-Implementierung war nur für externe Empfänger gedacht, erforderte eine Regel für den E-Mail-Übertragung und bot keine BYOK-Unterstützung.|
| | |

### <a name="p"></a>P

|Begriff|Definition|
|--------|--------------|
|**Pfile-Datei**|Die Dateierweiterung, die an alle Dateien angehängt wird, die allgemein von einem Rights Management-Dienst geschützt werden.|
|**Berechtigungsstufe**|Eine logische Gruppe von Nutzungsrechten. Sie erleichtert es den Endbenutzern und Administratoren, eine Auswahl aus rollenbasierten Konfigurationsoptionen zu treffen. Beispiele: Prüfer und Mitautor.|
|**schützen**|Anwenden von Rights Management-Überwachungen auf Dateien oder E-Mail-Nachrichten mithilfe von Verschlüsselungs-, Identitäts- und Access Control-Richtlinien für den Schutz Ihrer Daten.|
|**nur Schutzmodus**|Ein Betriebsmodus für den Azure Information Protection-Client, wenn keine Azure Information Protection-Richtlinie zum Anwenden von Bezeichnungen vorliegt. </br></br>In diesem Modus werden keine Klassifizierungsbezeichnungen angezeigt, aber Benutzer können weiterhin Rights Management-Schutz anwenden.|
|**Schutzvorlage**|Auch bekannt als *Vorlage für Benutzerrechterichtlinien*, *Rights Management-Vorlage* und *RMS-Vorlage*.<br /><br />Eine Gruppe von Schutzeinstellungen, die von einem Administrator verwaltet werden und die definierten Nutzungsrechte für autorisierte Benutzer sowie Zugriffssteuerungen für Ablauf und Offlinezugriff enthalten. |
|**veröffentlichen**|Schützen einer Datei, um sie vor unberechtigtem Zugriff und unberechtigter Verwendung zu schützen. </br></br>Wird auch in Verbindung mit Schutzvorlagen und der Azure Information Protection-Richtlinie als Begriff verwendet, um diese Elemente für die Verwendung durch Clients und Dienste verfügbar zu machen.|
| | |

### <a name="r"></a>R

|Begriff|Definition|
|--------|--------------|
|**Rights Management-Connector**|Ein ausgehendes Proxyrelay, das für lokale Dienste wie Exchange Server und SharePoint bereitgestellt werden kann, um Daten mithilfe von des Azure Rights Management-Diensts zu schützen.|
|**Rights Management-Aussteller**|Das Konto, das ein Dokument oder eine E-Mail schützt.|
|**Rights Management-Besitzer**|Das Konto, das volle Zugriffsrechte über ein geschütztes Dokument oder eine geschützte E-Mail behält, da es automatisch das Nutzungsrecht über den Vollzugriff auf Rights Management erhält, und von allen Ablaufdaten oder Offline-Einstellungen ausgenommen ist.|
|**Rights Management Dienste**|Der allgemeine Ausdruck, der sowohl für die Cloudversion von Rights Management (Azure Rights Management) als auch für die lokale Version von Rights Management (AD RMS) gilt.|
|**Rights Management-Freigabeanwendung**|Nun durch den Azure Information Protection-Client ersetzt.|
|**RMS**|Sie *Rights Management Services*.|
|**RMS-Connector**|Siehe *Rights Management-Connector*.|
|**RMS for Individuals**|Ein kostenloses Abonnement, mit dessen Hilfe ein Benutzer Rights Management verwenden kann, wenn seine Organisation nicht über ein Abonnement für Office 365 oder Azure Active Directory verfügt.|
|**RMS-Freigabeanwendung**|Siehe *Rights Management-Freigabeanwendung*.|
|**RMS-Vorlage**|Siehe *Schutzvorlage*.|

### <a name="s"></a>E

|Begriff|Definition|
|--------|--------------|
|**gen**|Siehe *Azure Information Protection-Überprüfung*.|
|**Administrator**|Eine Gruppe besonders vertrauenswürdiger Administratoren, die Dateien, die von der Organisation mithilfe eines Rights Management-Diensts geschützt wurden, entschlüsseln und anschließend öffnen kann. </br></br>Normalerweise ist diese Zugangsstufe für rechtliche eDiscovery und Überwachungsteams erforderlich.|

### <a name="t"></a>T

|Begriff|Definition|
|--------|--------------|
|**Mandanten Schlüssel**|Wird auch als *SLC-Schlüssel (Server Lizenzgeber Certificate)* bezeichnet.<br /><br />Der eindeutige Schlüssel eines Unternehmens, der den Ursprung des Schutzes für alle Kryptografiefunktionen von Rights Management darstellt, die mit diesem Mandantenschlüssel verkettet sind.|

### <a name="u"></a>U

|Begriff|Definition|
|--------|--------------|
|**einheitliche Bezeichnung**| Auch bekannt als *einheitliche Vertraulichkeits Bezeichnung*.<br /><br /> Eine Bezeichnung, die von apps, Clients und Diensten, die das Microsoft Information Protection Framework unterstützen, angewendet werden kann, um Klassifizierung und optional Schutz anzuwenden. </br></br>In Office-Apps und-Diensten werden Unified Labels als Vertraulichkeits Bezeichnungen implementiert.|
|**Schutz aufheben**|Entfernen Sie Schutzüberwachungen aus Dateien oder E-Mail-Nachrichten, in denen Verschlüsselungs-, Identitäts-, Nutzungsrechte- und Zugriffskontrollrichtlinien verwendet wurden, um Ihre Daten zu schützen.|
|**Nutzungslizenz**|Ein dokumentspezifisches Zertifikat, das einem Benutzer gewährt wird, wenn er eine Datei oder E-Mail öffnet, die durch einen Rights Management-Dienst geschützt wurde. </br></br>Dieses Zertifikat enthält Benutzerrechte für die Datei oder E-Mail-Nachricht und den Verschlüsselungsschlüssel, der zum Verschlüsseln des Inhalts und zusätzliche Zugriffseinschränkungen, die in der Richtlinie für das Dokument definiert wurden.|

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu AIP-Namen finden Sie unter [Azure Information Protection-auch bekannt als...](aka.md).