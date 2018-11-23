---
title: Von Azure Rights Management gelöste Probleme – AIP
description: Identifizieren Sie Anforderungen oder Probleme, die möglicherweise in Ihrer Organisation vorliegen, und erfahren Sie, wie sich diese mit der Azure RMS-Technologie beheben lassen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: b551c62d-5ac6-4359-85b3-90693e77b37f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 879f9ed918880442826cd2a7b5baf9e8b8e34b61
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151808"
---
# <a name="what-problems-does-azure-rms-solve"></a>Welche Probleme werden von Azure RMS gelöst?

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Anhand der folgenden Tabelle können Sie Geschäftsanforderungen oder -probleme bestimmen, die Ihre Organisation möglicherweise beim Schützen von Dokumenten und E-Mails hat, und Sie können ermitteln, wie sich diese Probleme mit der Azure Rights Management-Technologie (Azure RMS) beheben lassen.

Azure RMS ist die Schutztechnologie von [Azure Information Protection](what-is-information-protection.md).

|Anforderung oder Problem|Gelöst durch Azure RMS|
|--------------------------|-----------------------|
|Schützen mehrerer Dateitypen|√ In frühen Implementierungen von Rights Management konnten nur Office-Dateien geschützt werden, wozu ein nativer Rights Management-Schutz verwendet wird. **Generischer Schutz**, der zuerst von der Rights Management-Freigabeanwendung und jetzt vom Azure Information Protection-Client bereitgestellt wird, bedeutet, dass mehr [Dateitypen](./rms-client/client-admin-guide-file-types.md) unterstützt werden.|
|Schützen von Dateien überall|√ Wenn eine Datei [geschützt](./rms-client/client-classify-protect.md) ist, bleibt die Datei geschützt, auch wenn sie gespeichert oder in einen Speicher kopiert wird, der nicht unter der Kontrolle der IT ist, z. B. in einen Cloudspeicherdienst.|
|Sicheres Freigeben von Informationen|√ Wenn eine Datei [geschützt](./rms-client/client-classify-protect.md) ist, kann sie sicher für andere Benutzer freigegeben werden. Beispielsweise eine Anlage einer E-Mail oder ein Link zu einer SharePoint-Website. Wenn sich die vertraulichen Informationen in einer E-Mail befinden, können Sie die E-Mail schützen oder einfach die Option „Nicht weiterleiten“ von Outlook verwenden. <br /><br />Der Vorteil beim Anhängen einer geschützten Datei gegenüber dem Schutz der ganzen E-Mail besteht darin, dass der E-Mail-Text nicht verschlüsselt wird. Daher können Sie Anweisungen für die erstmalige Verwendung hinzufügen, wenn die E-Mail an eine Adresse außerhalb Ihrer Organisation gesendet wird. Die Anweisungen können von jedem gelesen werden, aber da das angehängte Dokument geschützt ist, können nur autorisierte Benutzer das Dokument öffnen, auch wenn die E-Mail oder das Dokument an andere Personen weitergeleitet wird.|
|Überprüfung und Überwachung|√ Sie können die [Nutzung Ihrer geschützten Dateien selbst dann noch überprüfen und überwachen](log-analyze-usage.md), wenn diese Dateien die Grenzen Ihrer Organisation verlassen haben.<br /><br />Sie arbeiten z. B. für Contoso, Ltd. Sie arbeiten mit drei Mitarbeitern von Fabrikam, Inc. an einem gemeinsamen Projekt. Sie senden diesen drei Personen ein Dokument per E-Mail, das Sie schützen und mit einem Schreibschutz versehen. Die Azure Rights Management-Überprüfung kann die folgenden Informationen bereitstellen:<br /><br />- Ob und wann die von Ihnen angegebenen Fabrikam-Personen das Dokument geöffnet haben.<br /><br />- Ob andere Personen, die Sie nicht angegeben haben, versucht haben, das Dokument zu öffnen (und dabei gescheitert sind): Das Dokument wurde möglicherweise weitergeleitet oder in einem freigegebenen Speicherort gespeichert, auf den andere Personen Zugriff haben.<br /><br />- Ob eine der angegebenen Personen versucht hat (und gescheitert ist), das Dokument zu drucken oder zu ändern.<br /><br />Darüber hinaus können Benutzer und Administratoren über die [Website zur Dokumentenverfolgung](./rms-client/client-track-revoke.md) den Zugriff auf geschützte Dokumente nachverfolgen und bei Bedarf widerrufen.|
|Unterstützung für häufig verwendete Geräte, nicht nur Windows-Computer|√ Zu den [unterstützten Geräten](./requirements-client-devices.md) gehören:<br /><br />- Windows-Computer und -Telefone<br /><br />- Mac-Computer<br /><br />- iOS-Tablets und -Telefone<br /><br />- Android-Tablets und -Telefone|
|Unterstützung von Business-to-Business-Zusammenarbeit|√ Weil Azure Rights Management ein Clouddienst ist, ist es nicht erforderlich, explizit Vertrauensstellungen zu anderen Organisationen zu konfigurieren, bevor Sie geschützte Inhalte mit diesen gemeinsam nutzen können. Sofern diese Organisationen bereits ein Office 365- oder Azure AD-Verzeichnis haben, wird Zusammenarbeit zwischen Organisationen automatisch unterstützt. Wenn dies nicht der Fall ist, können Benutzer sich für ein kostenloses [Microsoft Rights Management for Individuals](rms-for-individuals.md)-Abonnement registrieren oder ein Microsoft-Konto für [Anwendungen verwenden, die diese Authentifizierung für Azure Information Protection unterstützen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).|
|Unterstützung sowohl für lokale Dienste als auch für Office 365|√ Azure RMS arbeitet [nahtlos mit Office 365](office-apps-services-support.md) zusammen. Außerdem können Sie Azure Rights Management mit den folgenden lokalen Diensten verwenden, wenn Sie den [RMS-Connector](deploy-rms-connector.md) bereitstellen:<br /><br />- Exchange Server<br /><br />- SharePoint Server<br /><br />- Windows Server mit Dateiklassifizierungsinfrastruktur|
|Einfache Aktivierung|√ Bei neuen Abonnements erfolgt die Aktivierung automatisch. Bei vorhandenen Abonnement erfordert die [Aktivierung des Rights Management-Diensts](activate-service.md) nur ein paar Mausklicks in Ihrem Verwaltungsportal. Falls Sie die Befehlszeilensteuerung bevorzugen, können Sie auch zwei PowerShell-Befehle verwenden.|
|Fähigkeit, nach Bedarf über die gesamte Organisation zu skalieren|√ Weil Azure Rights Management als Clouddienst mit der Azure-Flexibilität für zentrales und horizontales Hochskalieren ausgeführt wird, müssen Sie keine zusätzlichen lokalen Server bereitstellen.|
|Fähigkeit, einfache und flexible Richtlinien zu erstellen|√ [Angepasste Vorlagen für den Schutz](configure-policy-templates.md) bieten schnelle und einfache Lösungen, mit denen Administratoren Richtlinien anwenden und Benutzer das richtige Maß an Schutz für jedes Dokument anwenden sowie den Zugriff auf Personen in der eigenen Organisation beschränken können.<br /><br />Soll beispielsweise ein unternehmensweites Strategiepapier für alle Mitarbeiter freigegeben werden, könnten Sie eine Schreibschutzrichtlinie für alle internen Mitarbeiter anwenden. Für ein Dokument mit sensibleren Daten, etwa einen Finanzbericht, könnten Sie den Zugriff auf Führungskräfte beschränken.|
|Breite Anwendungsunterstützung|√ Azure Rights Management ist eng auf Microsoft Office-Anwendungen und -Dienste abgestimmt und ermöglicht durch Verwenden des [Azure Information Protection-Clients](./rms-client/aip-client.md ) erweiterte Unterstützung für andere Anwendungen.<br /><br />√ Mit den [Azure Information Protection SDKs](./develop/developers-guide.md) erhalten Ihre internen Entwickler sowie Softwarehersteller APIs, mit denen sie angepasste Anwendungen schreiben können, die Azure Information Protection unterstützen.<br /><br />Weitere Informationen finden Sie unter [Sonstige Anwendungen, die die Rights Management-APIs unterstützen](api-support.md).|
|IT-Abteilung muss Kontrolle über die Daten behalten|√ Organisationen können ihren eigenen Mandantenschlüssel verwalten, die „[Bring Your Own Key](plan-implement-tenant-key.md)“ (BYOK)-Lösung nutzen und ihren Mandantenschlüssel in Hardwaresicherheitsmodulen (HSMs) speichern.<br /><br />√ Unterstützung der Überwachung und [Verwendungsprotokollierung](log-analyze-usage.md), sodass Sie Geschäftsabläufe analysieren, Missbrauch erkennen und (falls ein Informationsleck vorliegt) forensische Analysen durchführen können.<br /><br />√ Delegierter Zugriff mithilfe der [Administratorfunktion](configure-super-users.md) stellt sicher, dass die IT-Abteilung stets auf geschützte Inhalte zugreifen kann, selbst wenn ein Dokument von einem Mitarbeiter geschützt wurde, der die Organisation bereits verlassen hat. Bei Peer-zu-Peer-Verschlüsselungslösungen besteht dagegen das Risiko, dass Zugriff auf Unternehmensdaten verloren geht.<br /><br />√ Synchronisieren [nur der Verzeichnisattribute, die Azure RMS benötigt](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms), um eine allgemeine Identität für Ihre lokalen Active Directory-Konten zu unterstützen, indem ein [Verzeichnissynchronisierungstool](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison) wie Azure AD Connect verwendet wird.<br /><br />√ Aktivieren des einmaligen Anmelden, ohne Kennwörter in die Cloud zu replizieren, mithilfe von AD FS.<br /><br />√ Organisationen haben immer die Möglichkeit, den Azure Rights Management-Dienst nicht mehr zu verwenden, ohne den Zugriff auf Inhalte zu verlieren, die zuvor von Azure Rights Management geschützt wurden. Weitere Informationen zur Außerbetriebsetzung finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](decommission-deactivate.md). Organisationen, die Active Directory Rights Management Services (AD RMS) bereitgestellt haben, können darüber hinaus [zum Azure Rights Management-Dienst migrieren](migrate-from-ad-rms-to-azure-rms.md), ohne den Zugriff auf Daten zu verlieren, die zuvor durch AD RMS geschützt waren.|
> [!TIP]
> Wenn Sie mit der lokalen Version von Rights Management, Active Directory Rights Management Services (AD RMS), vertraut sind, ist die Vergleichstabelle in [Vergleich zwischen Azure Rights Management und AD RMS](compare-on-premise.md) möglicherweise für Sie interessant.

## <a name="security-compliance-and-regulatory-requirements"></a>Sicherheits-, Konformitäts- und gesetzliche Anforderungen
Azure Rights Management unterstützt die folgenden Sicherheits-, Compliance- und gesetzlichen Anforderungen:

√ Verwendung von Kryptografie gemäß Industriestandard und Unterstützung von FIPS 140-2. Weitere Informationen finden Sie unter [Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellängen](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

√ Unterstützung für Thales Hardwaresicherheitsmodule (HSMs), damit Sie Ihren Mandantenschlüssel in Microsoft Azure-Rechenzentren speichern können. Azure Rights Management verwendet getrennte Security Worlds für seine Rechenzentren in Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien, sodass Ihre Schlüssel nur in Ihrer Region verwendet werden können.

√ Zertifiziert für Folgendes:

-   ISO/IEC 27001:2013 (./enthält [ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   SOC 2 SSAE 16/ISAE 3402 Attestations

-   HIPAA BAA

-   EU-Modellklauseln

-   FedRAMP als Teil von Azure Active Directory in Office 365-Zertifizierung, ausgestellt von FedRAMP Agency Authority to Operate durch HHS

-   PCI DSS Level 1

Weitere Informationen zu diesen externen Zertifizierungen finden Sie im [Azure Trust Center](http://azure.microsoft.com/support/trust-center/compliance/).

## <a name="next-steps"></a>Nächste Schritte

Weitere technische Informationen zur Funktionsweise des Azure Rights Management-Diensts finden Sie diese unter [Funktionsweise von Azure RMS](how-does-it-work.md)