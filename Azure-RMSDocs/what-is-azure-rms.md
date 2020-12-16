---
title: Übersicht über den Schutz durch Azure Rights Management – AIP
description: Informationen über Azure Rights Management (Azure RMS) und die Schutztechnologie von Azure Information Protection.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/08/2020
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
ms.openlocfilehash: de6aa96fefb8dbd2fd10c8ea265e509f20aef2d4
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384450"
---
# <a name="what-is-azure-rights-management"></a>Was ist Azure Rights Management?

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Azure Rights Management (Azure RMS) ist die Schutztechnologie von [Azure Information Protection](what-is-information-protection.md).

Azure RMS ist ein cloudbasierter Schutzdienst, der Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien zum Schützen von Dateien und E-Mails auf Smartphones, Tablets und PCs verwendet. Die Schutzeinstellungen verbleiben bei Ihren Daten, auch wenn diese die Grenzen Ihrer Organisation verlassen. So bleiben Ihre Inhalte sowohl innerhalb als auch außerhalb Ihrer Organisation geschützt.

Die folgende Abbildung zeigt, wie Azure RMS Schutz für Microsoft 365 sowie lokale Server und Dienste bereitstellt. Außerdem wird die Schutzlösung von gängigen Endbenutzergeräten unterstützt, auf denen Windows, macOS, iOS oder Android ausgeführt wird.

![Azure RMS – Funktionsweise](./media/AzRMS_elements.png)

Verwenden Sie Azure RMS mit Microsoft 365-Abonnements oder Abonnements für Azure Information Protection. Weitere Informationen zu den einzelnen Abonnementtypen und den unterstützten Features finden Sie auf der Website mit den [Preisen zu Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).

### <a name="sample-azure-rms-use-case"></a>Anwendungsfall zu Azure RMS

Mitarbeiter können z. B. ein Dokument per E-Mail an ein Partnerunternehmen senden oder ein Dokument auf einem Cloudlaufwerk speichern.

Die Verwendung des permanenten Schutzes von Azure RMS hilft, Unternehmensdaten zu schützen, und kann auch für Konformität, gesetzliche Ermittlungsanforderungen oder bewährte Methoden für die Informationsverwaltung erforderlich sein.

Azure RMS stellt sicher, dass autorisierte Benutzer und Dienste (wie die Suche und die Indizierung) weiterhin die geschützten Daten lesen und untersuchen können.

Die Gewährleistung eines kontinuierlichen Zugriffs für autorisierte Personen und Dienste, auch bekannt als „Schlussfolgern über Daten“ (reasoning over data), ist für die Kontrolle über die Daten Ihrer Organisation von entscheidender Bedeutung. Diese Funktion lässt sich mit anderen Schutzlösungen, die die Peer-zu-Peer-Verschlüsselung verwenden, nicht leicht erreichen. 

## <a name="business-problems-solved-by-azure-rights-management"></a>Von Azure Rights Management gelöste Geschäftsprobleme

Anhand der folgenden Listen und Tabellen können Sie Geschäftsanforderungen oder -probleme bestimmen, die Ihre Organisation möglicherweise beim Schützen von Dokumenten und E-Mails hat. Zudem können Sie ermitteln, wie Sie die Azure Rights Management-Technologie für Ihre Zwecke nutzen können.

- [Schutzfunktionen](#protection-features)
- [Funktionen zur Zusammenarbeit](#collaboration-features)
- [Funktionen für die Plattformunterstützung](#platform-support-features)
- [Infrastrukturfunktionen](#infrastructure-features)

> [!TIP]
> Wenn Sie mit der lokalen Version von Rights Management, Active Directory Rights Management Services (AD RMS), vertraut sind, ist die Vergleichstabelle in [Vergleich zwischen Azure Rights Management und AD RMS](compare-on-premise.md) möglicherweise für Sie interessant.

### <a name="protection-features"></a>Schutzfunktionen

|Funktion  |BESCHREIBUNG  |
|---------|---------|
|**Schützen mehrerer Dateitypen**     | In frühen Implementierungen von Rights Management konnten nur Office-Dateien mithilfe eines integrierten Rights Management-Schutzes geschützt werden. </br></br>Azure Information Protection bietet Unterstützung für zusätzliche Dateitypen. Weitere Informationen finden Sie unter [Unterstützte Dateitypen](rms-client/clientv2-admin-guide-file-types.md).         |
|**Schützen von Dateien überall**. | Wenn eine Datei [geschützt](./rms-client/clientv2-classify-protect.md) ist, bleibt die Datei geschützt, auch wenn sie gespeichert oder in einen Speicher kopiert wird, der nicht unter der Kontrolle der IT ist, z. B. in einen Cloudspeicherdienst.|
|     |         |


### <a name="collaboration-features"></a>Funktionen zur Zusammenarbeit

|Funktion  |BESCHREIBUNG  |
|---------|---------|
|**Sicheres Freigeben von Informationen**     |  [Geschützte Dateien](./rms-client/clientv2-classify-protect.md) können sicher mit anderen geteilt werden, z. B. als Anlage einer E-Mail oder als Link zu einer SharePoint-Website. </br></br> Wenn sich die vertraulichen Informationen in einer E-Mail befinden, schützen Sie die E-Mail oder verwenden Sie die Option **Nicht weiterleiten** von Outlook.       |
|**Unterstützung von Business-to-Business-Zusammenarbeit**     |  Weil Azure Rights Management ein Clouddienst ist, ist es nicht erforderlich, explizit Vertrauensstellungen zu anderen Organisationen zu konfigurieren, bevor Sie geschützte Inhalte mit diesen gemeinsam nutzen können. </br></br>Die Zusammenarbeit zwischen Organisationen, die bereits ein Microsoft 365- oder Azure AD-Verzeichnis haben, wird automatisch unterstützt. </br></br>Für Organisationen ohne Microsoft 365- oder Azure AD-Verzeichnis können sich Benutzer für das kostenlose [RMS for Individuals](rms-for-individuals.md)-Abonnement anmelden oder ein Microsoft-Konto für [unterstützte Anwendungen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) verwenden.       |
| | |

> [!TIP]
> Wenn Sie geschützte Dateien anfügen, anstatt die gesamte E-Mail-Nachricht zu schützen, können Sie den E-Mail-Text unverschlüsselt lassen. 
>
> Sie können z. B. Anweisungen für die erstmalige Verwendung hinzufügen, wenn Sie die E-Mail extern versenden. Wenn Sie eine geschützte Datei anfügen, kann jeder die grundlegenden Anweisungen lesen, aber nur autorisierte Benutzer können das Dokument öffnen, auch wenn die E-Mail oder das Dokument an andere Personen weitergeleitet wird.

### <a name="platform-support-features"></a>Funktionen für die Plattformunterstützung

Azure RMS unterstützt viele unterschiedliche Plattformen und Anwendungen wie die Folgenden:

|Funktion  |BESCHREIBUNG  |
|---------|---------|
|**Häufig verwendete Geräte** </br>nicht nur Windows-Computer     | Zu den [Clientgeräten](requirements.md#client-devices) gehören: </br></br>- Windows-Computer und -Telefone </br>- Mac-Computer </br>- iOS-Tablets und -Telefone </br>- Android-Tablets und -Telefone        |
|**Lokale Dienste**     | Azure RMS arbeitet [nahtlos mit Office 365](office-apps-services-support.md) zusammen. Außerdem lässt sich Azure Rights Management mit den folgenden lokalen Diensten verwenden, wenn Sie den [RMS-Connector](deploy-rms-connector.md) bereitstellen: </br></br>- Exchange Server </br>- SharePoint Server </br>- Windows Server mit Dateiklassifizierungsinfrastruktur        |
|**Anwendungserweiterbarkeit**     |Azure Rights Management ist eng auf Microsoft Office-Anwendungen und -Dienste abgestimmt und ermöglicht durch Verwenden des [Azure Information Protection-Clients](./rms-client/use-client.md ) erweiterte Unterstützung für andere Anwendungen. </br></br>Mit den [Azure Information Protection SDKs](./develop/developers-guide.md) erhalten Ihre internen Entwickler sowie Softwarehersteller APIs, mit denen sie angepasste Anwendungen schreiben können, die Azure Information Protection unterstützen. </br></br>Weitere Informationen finden Sie unter [Sonstige Anwendungen, die die Rights Management-APIs unterstützen](api-support.md).         |
| | |

### <a name="infrastructure-features"></a>Infrastrukturfunktionen

Azure RMS bietet die folgenden Features zur Unterstützung von IT-Abteilungen und Infrastrukturorganisationen:

- [Erstellen einfacher und flexibler Richtlinien](#create-simple-and-flexible-policies)
- [Einfache Aktivierung](#easy-activation)
- [Überprüfungs- und Überwachungsdienste](#auditing-and-monitoring-services)
- [Skalierung für die gesamte Organisation](#ability-to-scale-across-your-organization)
- [Behalten der Kontrolle über die Daten](#maintain-it-control-over-data)

> [!NOTE]
> Organisationen haben immer die Möglichkeit, den Azure Rights Management-Dienst nicht mehr zu verwenden, ohne den Zugriff auf Inhalte zu verlieren, die zuvor von Azure Rights Management geschützt wurden. 
> 
> Weitere Informationen finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](decommission-deactivate.md). 
> 

#### <a name="create-simple-and-flexible-policies"></a>Erstellen einfacher und flexibler Richtlinien

Angepasste Vorlagen für den Schutz bieten schnelle und einfache Lösungen, mit denen Administratoren Richtlinien anwenden und Benutzer das richtige Maß an Schutz für jedes Dokument anwenden sowie den Zugriff auf Personen in der eigenen Organisation beschränken können. 

Soll beispielsweise ein unternehmensweites Strategiedokument für alle Mitarbeiter freigegeben werden, wenden Sie eine Schreibschutzrichtlinie für alle internen Mitarbeiter an. Für ein Dokument mit sensibleren Daten, etwa einen Finanzbericht, beschränken Sie den Zugriff auf Führungskräfte.

Konfigurieren Sie Ihre Bezeichnungsrichtlinien im Admin Center für Bezeichnungen:

- **Client für einheitliche Bezeichnungen** Verwenden Sie das Microsoft 365 Security Center, das Microsoft 365 Compliance Center oder das Microsoft 365 Security & Compliance Center.

    Weitere Informationen finden unter [Dokumentation zu Vertraulichkeitsbezeichnungen für Microsoft 365](/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do).        

- **Klassischer Client**: Verwenden Sie das Azure-Portal. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).      


#### <a name="easy-activation"></a>Einfache Aktivierung

Bei neuen Abonnements erfolgt die Aktivierung automatisch. Bei vorhandenen Abonnement erfordert die [Aktivierung des Rights Management-Diensts](activate-service.md) nur ein paar Mausklicks in Ihrem Verwaltungsportal oder zwei PowerShell-Befehle.

#### <a name="auditing-and-monitoring-services"></a>Überprüfungs- und Überwachungsdienste

[Überprüfen und Überwachen Sie die Nutzung](log-analyze-usage.md) Ihrer geschützten Dateien selbst dann noch, wenn diese Dateien die Grenzen Ihrer Organisation verlassen haben. 

Wenn beispielsweise ein Mitarbeiter von Contoso, Ltd. an einem gemeinsamen Projekt mit drei Personen von Fabrikam, Inc. arbeitet, könnte er seinen Fabrikam-Partnern ein Dokument zusenden, das geschützt ist und beschränkten (*schreibgeschützten*) Zugriff hat. 

Azure RMS-Überprüfung kann die folgenden Informationen bereitstellen:

- Ob und wann die Fabrikam-Partner das Dokument geöffnet haben. 

- Ob andere Personen, die nicht angegeben wurden, versucht haben, das Dokument zu öffnen, und es nicht geschafft haben. Dies kann passieren, wenn die E-Mail an einen gemeinsamen Speicherort weitergeleitet oder dort gespeichert wurde.

> [!NOTE]
> Nur für Benutzer des klassischen Clients: Die [Website zur Nachverfolgung von Dokumenten](./rms-client/client-track-revoke.md) ermöglicht Benutzern und Administratoren das Nachverfolgen und bei Bedarf das Widerrufen des Zugriffs auf geschützte Dokumente.
> 

#### <a name="ability-to-scale-across-your-organization"></a>Skalierung für die gesamte Organisation

Weil Azure Rights Management als Clouddienst mit der Flexibilität von Azure für zentrales Hoch- und Herunterskalieren ausgeführt wird, müssen Sie keine zusätzlichen lokalen Server bereitstellen.

#### <a name="maintain-it-control-over-data"></a>Behalten der Kontrolle über die Daten

Organisationen können IT-Steuerungsfunktionen nutzen, wie z. B.:

|Funktion  |Beschreibung  |
|---------|---------|
|**Mandantenschlüsselverwaltung**    | Verwenden Sie Lösungen für die Mandantenschlüsselverwaltung, z. B. BYOK (Bring Your Own Key) oder DKE (Double Key Encryption, doppelte Schlüsselverschlüsselung). <br><br>Weitere Informationen finden Sie unter: <br>- [Planen und Implementieren des AIP-Mandantenschlüssels](plan-implement-tenant-key.md) <br>- [DKE in der Microsoft 365-Dokumentation](/microsoft-365/compliance/double-key-encryption)|
|**Überwachung und Verwendungsprotokollierung**    |   Verwenden Sie die Features für Überwachung und [Verwendungsprotokollierung](log-analyze-usage.md), um Geschäftsabläufe zu analysieren, Missbrauch zu erkennen und forensische Analysen für Informationslecks durchführen zu können.      |
|**Zugriffsdelegierung**     |  Delegieren Sie den Zugriff mithilfe des [Administratorfeatures](configure-super-users.md), damit die IT-Abteilung stets auf geschützte Inhalte zugreifen kann, selbst wenn ein Dokument von einem Mitarbeiter geschützt wurde, der die Organisation bereits verlassen hat. </br> Bei Peer-zu-Peer-Verschlüsselungslösungen besteht dagegen das Risiko, dass Zugriff auf Unternehmensdaten verloren geht.       |
|**Active Directory-Synchronisierung**     |   Synchronisieren Sie [nur der Verzeichnisattribute, die Azure RMS benötigt](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized#azure-rms), um eine allgemeine Identität für Ihre lokalen Active Directory-Konten zu unterstützen, indem eine [hybride Identitätslösung](/azure/active-directory/hybrid/) wie Azure AD Connect verwendet wird.      |
|**Einmaliges Anmelden**     | Aktivieren Sie einmaliges Anmelden, ohne Kennwörter in die Cloud zu replizieren, mithilfe von AD FS.        |
|**Migration von AD RMS** |Wenn Sie Active Directory Rights Management Services (AD RMS) bereitgestellt haben, können Sie darüber hinaus [zum Azure Rights Management-Dienst migrieren](migrate-from-ad-rms-to-azure-rms.md), ohne den Zugriff auf Daten zu verlieren, die zuvor durch AD RMS geschützt waren. |
| | |

## <a name="security-compliance-and-regulatory-requirements"></a>Sicherheits-, Konformitäts- und gesetzliche Anforderungen
Azure Rights Management unterstützt die folgenden Sicherheits-, Compliance- und gesetzlichen Anforderungen:

- **Verwendung von Kryptografie gemäß Industriestandard und Unterstützung von FIPS 140-2.** Weitere Informationen finden Sie unter [Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellängen](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

- **Unterstützung für nCipher nShield-Hardwaresicherheitsmodule (HSM)** , damit Sie Ihren Mandantenschlüssel in Microsoft Azure-Rechenzentren speichern können. 

    Azure Rights Management verwendet getrennte Security Worlds für seine Rechenzentren in Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien, sodass Ihre Schlüssel nur in Ihrer Region verwendet werden können.

- **Zertifizierung für die folgenden Standards:**

    -   ISO/IEC 27001:2013 (./enthält [ISO/IEC 27018](https://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))
    -   SOC 2 SSAE 16/ISAE 3402 Attestations
    -   HIPAA BAA
    -   EU-Modellklauseln
    -   FedRAMP als Teil von Azure Active Directory in Office 365-Zertifizierung, ausgestellt von FedRAMP Agency Authority to Operate durch HHS
    -   PCI-DSS Level 1

Weitere Informationen zu diesen externen Zertifizierungen finden Sie im [Azure Trust Center](https://azure.microsoft.com/support/trust-center/compliance/).

## <a name="next-steps"></a>Nächste Schritte

Weitere technische Informationen zur Funktionsweise des Azure Rights Management-Diensts finden Sie diese unter [Funktionsweise von Azure RMS](how-does-it-work.md)
