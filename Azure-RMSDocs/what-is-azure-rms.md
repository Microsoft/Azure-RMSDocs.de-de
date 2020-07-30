---
title: Übersicht über Azure Rights Management Protection-aip
description: Informationen über Azure Rights Management (Azure RMS) und die Schutztechnologie von Azure Information Protection.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/21/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: aeeebcd7-6646-4405-addf-ee1cc74df5df
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: 1a239e489dee616ba13050a9fa6614d85bee1429
ms.sourcegitcommit: d1f6f10c9cb95de535d8121e90b211f421825caf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87297866"
---
# <a name="what-is-azure-rights-management"></a>Was ist Azure Rights Management?

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Azure Rights Management (Azure RMS) ist die Schutztechnologie von [Azure Information Protection](what-is-information-protection.md).

Azure RMS ist ein cloudbasierter Schutzdienst, bei dem Verschlüsselungs-, Identitäts-und Autorisierungs Richtlinien verwendet werden, um Dateien und e-Mails auf mehreren Geräten, einschließlich Smartphones, Tablets und PCs, zu schützen. Schutzeinstellungen verbleiben in Ihren Daten, auch wenn Sie die Grenzen Ihrer Organisation verlassen, sodass Ihre Inhalte sowohl innerhalb als auch außerhalb Ihrer Organisation geschützt bleiben.

Die folgende Abbildung zeigt, wie Azure RMS Schutz für Office 365 sowie lokale Server und Dienste bereitstellt. Der Schutz wird auch von gängigen Endbenutzer Geräten unterstützt, auf denen Windows, macOS, IOS und Android ausgeführt wird.

![Azure RMS – Funktionsweise](./media/AzRMS_elements.png)

Verwenden Sie Azure RMS mit Office 365-Abonnements oder-Abonnements für Azure Information Protection. Weitere Informationen zu den einzelnen Abonnementtypen und den unterstützten Funktionen finden Sie auf der [Azure Information Protection Preis](https://azure.microsoft.com/pricing/details/information-protection/) Website.

### <a name="sample-azure-rms-use-case"></a>Anwendungsfall für Beispiel Azure RMS

Mitarbeiter können ein Dokument per e-Mail an ein Partnerunternehmen senden oder ein Dokument auf dem cloudlaufwerk speichern.

Die Verwendung des permanenten Schutzes von Azure RMS hilft, Unternehmensdaten zu schützen, und kann auch für Konformität, gesetzliche Ermittlungsanforderungen oder bewährte Methoden für die Informationsverwaltung erforderlich sein.

Mit Azure RMS wird sichergestellt, dass autorisierte Personen und Dienste (z. b. suchen und Indizierung) weiterhin die geschützten Daten lesen und überprüfen können.

Die Gewährleistung des kontinuierlichen Zugriffs für autorisierte Personen und Dienste, auch bekannt als "Argumentation over Data", ist ein wichtiges Element bei der Kontrolle über die Daten Ihrer Organisation. Diese Funktion kann mit anderen Lösungen zum Schutz von Daten, die Peer-zu-Peer-Verschlüsselung verwenden, nicht problemlos erreicht werden. 

## <a name="business-problems-solved-by-azure-rights-management"></a>Von Azure Rights Management gelöste Geschäftsprobleme

Verwenden Sie die folgenden Listen und Tabellen, um Geschäftsanforderungen oder-Probleme zu identifizieren, die Ihre Organisation möglicherweise beim Schützen von Dokumenten und e-Mails hat, und wie die Azure Rights Management-Technologie Ihren Anforderungen gerecht werden kann.

- [Schutz Features](#protection-features)
- [Funktionen zur Zusammenarbeit](#collaboration-features)
- [Platt Form Unterstützungs Features](#platform-support-features)
- [Infrastruktur Features](#infrastructure-features)

> [!TIP]
> Wenn Sie mit der lokalen Version von Rights Management, Active Directory Rights Management Services (AD RMS), vertraut sind, sind Sie möglicherweise an der Vergleichstabelle unter [Vergleich von Azure Rights Management und AD RMS](compare-on-premise.md)interessiert.

### <a name="protection-features"></a>Schutz Features

|Funktion  |BESCHREIBUNG  |
|---------|---------|
|**Schützen mehrerer Dateitypen**     | In frühen Implementierungen von Rights Management konnten nur Office-Dateien mithilfe des systemeigenen Rights Management Schutzes geschützt werden. </br></br>Der generische Schutz, der erstmals von der Rights Management Freigabe Anwendung bereitgestellt wurde und jetzt vom Azure Information Protection-Client angeboten wird, bedeutet, dass weitere [Dateitypen](./rms-client/client-admin-guide-file-types.md) unterstützt werden.        |
|**Schützen Sie Dateien überall**. | Wenn eine Datei [geschützt](./rms-client/client-classify-protect.md)ist, bleibt der Schutz für die Datei bestehen, auch wenn Sie gespeichert oder in einen Speicher kopiert wird, der nicht von der IT gesteuert wird, z. b. in einem cloudspeicherdienst.|
|     |         |


### <a name="collaboration-features"></a>Funktionen zur Zusammenarbeit

|Funktion  |BESCHREIBUNG  |
|---------|---------|
|**Sicheres Freigeben von Informationen**     |  [Geschützte Dateien](./rms-client/client-classify-protect.md) können sicher für andere Benutzer freigegeben werden, z. b. eine Anlage an eine e-Mail oder eine Verknüpfung zu einer SharePoint-Website. </br></br> Wenn die vertraulichen Informationen in einer e-Mail-Nachricht angezeigt werden, schützen Sie die e-Mail, oder verwenden Sie die Option " **nicht weiterleiten** " in Outlook.       |
|**Unterstützung von Business-to-Business-Zusammenarbeit**     |  Da es sich bei Azure Rights Management um einen clouddienst handelt, ist es nicht erforderlich, Vertrauens Stellungen mit anderen Organisationen explizit zu konfigurieren, bevor Sie geschützte Inhalte für Sie freigeben können. </br></br>Die Zusammenarbeit mit anderen Organisationen, die bereits über Office 365 oder ein Azure AD Verzeichnis verfügen, wird automatisch unterstützt. </br></br>Für Organisationen ohne Office 365 oder ein Azure AD Verzeichnis können sich Benutzer für das kostenlose [RMS for Individuals](rms-for-individuals.md) Abonnement registrieren oder eine Microsoft-Konto für [Unterstützte Anwendungen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)verwenden.       |
| | |

> [!TIP]
> Wenn Sie geschützte Dateien anfügen, anstatt eine vollständige e-Mail-Nachricht zu schützen, können Sie den e-Mail-Text nicht verschlüsseln. 
>
> Beispielsweise können Sie Anweisungen für die erstmalige Verwendung einschließen, wenn die e-Mail außerhalb Ihrer Organisation gesendet wird. Wenn Sie eine geschützte Datei anfügen, können die grundlegenden Anweisungen von allen Benutzern gelesen werden, aber nur autorisierte Benutzer können das Dokument öffnen, auch wenn die e-Mail oder das Dokument an andere Personen weitergeleitet wird.

### <a name="platform-support-features"></a>Platt Form Unterstützungs Features

Azure RMS unterstützt eine breite Palette von Plattformen und Anwendungen, einschließlich:

|Funktion  |BESCHREIBUNG  |
|---------|---------|
|**Häufig verwendete Geräte** </br>nicht nur Windows-Computer     | [Client Geräte](requirements.md#client-devices) umfassen Folgendes: </br></br>- Windows-Computer und -Telefone </br>- Mac-Computer </br>- iOS-Tablets und -Telefone </br>- Android-Tablets und -Telefone        |
|**Lokale Dienste**     | Wenn Sie den [RMS-Connector](deploy-rms-connector.md)bereitstellen, können Sie nicht nur [nahtlos mit Office 365](office-apps-services-support.md)arbeiten, sondern auch Azure Rights Management mit den folgenden lokalen Diensten verwenden: </br></br>- Exchange Server </br>- SharePoint Server </br>– Windows Server mit Dateiklassifizierungsinfrastruktur        |
|**Anwendungs Erweiterbarkeit**     |Azure Rights Management verfügt über eine enge Integration in Microsoft Office Anwendungen und Dienste und erweitert die Unterstützung für andere Anwendungen mithilfe des [Azure Information Protection-Clients](./rms-client/aip-client.md ). </br></br>Mit den [Azure Information Protection sdert](./develop/developers-guide.md) verfügen Ihre internen Entwickler und Softwarehersteller über APIs zum Schreiben von benutzerdefinierten Anwendungen, die Azure Information Protection unterstützen. </br></br>Weitere Informationen finden Sie unter [Sonstige Anwendungen, die die Rights Management-APIs unterstützen](api-support.md).         |
| | |

### <a name="infrastructure-features"></a>Infrastruktur Features

Azure RMS bietet die folgenden Features zur Unterstützung von IT-Abteilungen und Infrastruktur Organisationen:

- **Erstellen Sie einfache und flexible Richtlinien**. [Angepasste Vorlagen](configure-policy-templates.md) für den Schutz bieten Administratoren eine schnelle und einfache Lösung für die Anwendung von Richtlinien, und Benutzer können die richtige Schutz Ebene für die einzelnen Dokumente anwenden und den Zugriff auf Personen in Ihrer Organisation einschränken. Beispiel:

    - Wenn ein unternehmensweites Strategiepapier für alle Mitarbeiter freigegeben werden soll, wenden Sie eine schreibgeschützte Richtlinie auf alle internen Mitarbeiter an. 
    - Bei einem sensitiven Dokument, z. b. einem Finanzbericht, beschränken Sie den Zugriff nur auf Führungskräfte.

- **Einfache Aktivierung**. Bei neuen Abonnements erfolgt die Aktivierung automatisch. Für vorhandene Abonnements erfordert [das Aktivieren des Rights Management Dienstanbieter](activate-service.md) nur ein paar Mausklicks in Ihrem Verwaltungs Portal oder zwei PowerShell-Befehle.

- **Überwachungs-und Überwachungsdienste**. [Überwachen und überwachen](log-analyze-usage.md) Sie die Nutzung ihrer geschützten Dateien, auch wenn diese Dateien die Grenzen Ihrer Organisation verlassen haben. 

    Wenn z. b. ein Mitarbeiter von "Azure von Azure" an einem gemeinsamen Projekt mit drei Personen von Fabrikam, *Inc. arbeitet*, sendet er möglicherweise seine Fabrikam-Partner an ein Dokument, das geschützt und auf schreibgeschützt beschränkt ist. 

    Azure RMS-Überprüfung kann die folgenden Informationen bereitstellen:

    - Gibt an, ob die Fabrikam-Partner das Dokument geöffnet haben, und wann. 
    - Ob andere Personen, die nicht angegeben wurden, versucht haben, das Dokument zu öffnen, und nicht. Dies kann vorkommen, wenn die e-Mail weitergeleitet oder an einem freigegebenen Speicherort gespeichert wurde.

    Darüber hinaus können Benutzer und Administratoren über die [Website zur Dokumentenverfolgung](./rms-client/client-track-revoke.md) den Zugriff auf geschützte Dokumente nachverfolgen und bei Bedarf widerrufen.

- **Möglichkeit der Skalierung in Ihrer Organisation**. Da Azure-Rights Management als clouddienst mit der Azure-Elastizität zum zentralen hoch-und Herunterskalieren ausgeführt wird, müssen Sie keine zusätzlichen lokalen Server bereitstellen oder bereitstellen.

- **Behalten Sie die Kontrolle über die Daten**. Organisationen können von IT-Steuerungsfunktionen profitieren, wie z. b.:

    |Funktion  |BESCHREIBUNG  |
    |---------|---------|
    |Mandanten Schlüsselverwaltung    |   Verwalten Sie Ihren eigenen Mandanten Schlüssel mithilfe der Lösung "[Bring your own Key](plan-implement-tenant-key.md)" (Byok), indem Sie Ihren Mandanten Schlüssel in Hardware Sicherheits Modulen (HSMs) speichern.      |
    |Überwachung und Verwendungs Protokollierung    |   Verwenden Sie die Funktionen für die Überwachung und [Verwendungs Protokollierung](log-analyze-usage.md) , um geschäftliche Einblicke zu analysieren, auf Missbrauch zu überwachen und forensische Analysen für Informationsverluste auszuführen.      |
    |Zugriffs Delegierung     |  Delegieren des Zugriffs mit der Administrator [Funktion](configure-super-users.md), um sicherzustellen, dass er immer auf geschützte Inhalte zugreifen kann, auch wenn ein Dokument von einem Mitarbeiter geschützt wurde, der die Organisation verlässt. </br> Bei Peer-zu-Peer-Verschlüsselungslösungen besteht dagegen das Risiko, dass Zugriff auf Unternehmensdaten verloren geht.       |
    |Active Directory-Synchronisierung     |   Synchronisieren Sie [nur die Verzeichnis Attribute](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized#azure-rms) , die Azure RMS zur Unterstützung einer allgemeinen Identität für Ihre lokalen Active Directory Konten benötigt, indem Sie [eine Hybrid-Identitäts Lösung](/azure/active-directory/hybrid/)wie Azure AD Connect verwenden.      |
    |Einmaliges Anmelden     | Aktivieren Sie das einmalige Anmelden, ohne Kenn Wörter in der Cloud zu replizieren, indem Sie AD FS verwenden.        |
    |Migration von AD RMS |Wenn Sie Active Directory Rights Management Services (AD RMS) bereitgestellt haben, [Migrieren Sie zum Azure-Rights Management Dienst](migrate-from-ad-rms-to-azure-rms.md) , ohne den Zugriff auf Daten zu verlieren, die zuvor durch AD RMS geschützt waren. |
    | | |


> [!NOTE]
> Organisationen haben immer die Möglichkeit, den Azure Rights Management-Dienst zu verwenden, ohne den Zugriff auf Inhalte zu verlieren, die zuvor durch Azure Rights Management geschützt waren. 
> 
> Weitere Informationen finden Sie unter Außerbetriebsetzen [und Deaktivieren von Azure-Rights Management](decommission-deactivate.md). 
> 



## <a name="security-compliance-and-regulatory-requirements"></a>Sicherheits-, Konformitäts- und gesetzliche Anforderungen
Azure Rights Management unterstützt die folgenden Sicherheits-, Konformitäts-und gesetzlichen Anforderungen:

- **Verwendung von Industriestandard-Kryptografie und unterstützt die Verwendung von fps 140-2.** Weitere Informationen finden Sie unter [Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellängen](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

- **Unterstützung für das HSM (Hardware Security Module) der nCipher-Hardware** , um ihren Mandanten Schlüssel in Microsoft Azure Rechenzentren zu speichern. 

    Azure Rights Management verwendet getrennte Security Worlds für seine Rechenzentren in Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien, sodass Ihre Schlüssel nur in Ihrer Region verwendet werden können.

- **Zertifizierung für die folgenden Standards:**

    -   ISO/IEC 27001:2013 (./includes [ISO/IEC 27018](https://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))
    -   SOC 2 SSAE 16/ISAE 3402 Attestations
    -   HIPAA BAA
    -   EU-Modellklauseln
    -   FedRAMP als Teil von Azure Active Directory in Office 365-Zertifizierung, ausgestellt von FedRAMP Agency Authority to Operate durch HHS
    -   PCI-DSS Level 1

Weitere Informationen zu diesen externen Zertifizierungen finden Sie in der [Azure Trust Center](https://azure.microsoft.com/support/trust-center/compliance/).

## <a name="next-steps"></a>Nächste Schritte

Weitere technische Informationen zur Funktionsweise des Azure Rights Management-Diensts finden Sie diese unter [Funktionsweise von Azure RMS](how-does-it-work.md)
