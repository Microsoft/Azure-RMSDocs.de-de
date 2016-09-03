---
title: "Welche Probleme werden von Azure RMS gelöst? | Azure RMS"
description: "Anhand der folgenden Tabelle können Sie Geschäftsanforderungen oder -probleme bestimmen, die Ihre Organisation möglicherweise hat, und können ermitteln, wie sich diese Probleme mit Azure RMS lösen lassen."
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b551c62d-5ac6-4359-85b3-90693e77b37f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7b194493073bcd76fa7a7d06bb31a7811e8cc3e
ms.openlocfilehash: 7aec5c26acb78cd85eee614a603745f3ee5938a2


---


# Welche Probleme werden von Azure RMS gelöst?

>*Gilt für: Azure Rights Management, Office 365*

Anhand der folgenden Tabelle können Sie Geschäftsanforderungen oder -probleme bestimmen, die Ihre Organisation möglicherweise hat, und können ermitteln, wie sich diese Probleme mit Azure RMS lösen lassen.

|Anforderung oder Problem|Gelöst durch Azure RMS|
|--------------------------|-----------------------|
|Schützen von Dateien beliebigen Typs|√ In früheren Implementierungen von Azure Rights Management können nur Office-Dateien geschützt werden, wozu systemeigener Schutz verwendet wird. Nun bedeutet [generischer Schutz](../rms-client/sharing-app-dialog-box.md#what-s-the-difference-between-generic-protection-and-built-in-native-protection), dass alle Dateitypen unterstützt werden.|
|Schützen von Dateien überall|√ Wenn eine Datei an einem Speicherort gespeichert wird ([direkter Schutz](../rms-client/sharing-app-protect-in-place.md)), bleibt die Datei geschützt, auch wenn sie in einen Speicher kopiert wird, der nicht unter der Kontrolle der IT ist, z. B. in einen Cloud-Speicherdienst.|
|Sicheres Freigeben von Dateien per E-Mail|√ Wenn eine Datei per E-Mail geteilt wird ([Geschützt freigeben](../rms-client/sharing-app-protect-by-email.md)), wird die Datei als Anlage einer E-Mail-Nachricht geschützt, mit einer Anleitung ,wie sie geöffnet wird. Der Text der E-Mail ist nicht verschlüsselt, sodass der Empfänger diese Anweisungen immer lesen kann. Da das als Anlage angehängte Dokument aber geschützt ist, kann es nur von autorisierten Benutzern geöffnet werden, auch wenn die E-Mail oder das Dokument an andere Personen weitergeleitet wird.|
|Überprüfung und Überwachung|√ Sie können die [Nutzung Ihrer geschützten Dateien selbst dann noch überprüfen und überwachen](../deploy-use/log-analyze-usage.md), wenn diese Dateien die Grenzen Ihrer Organisation verlassen haben.<br /><br />Sie arbeiten z. B. für Contoso, Ltd. Sie arbeiten mit drei Mitarbeitern von Fabrikam, Inc. an einem gemeinsamen Projekt. Sie senden diesen 3 Personen ein Dokument per E-Mail, das Sie schützen und mit einem Schreibschutz versehen. Azure RMS-Überprüfung kann die folgenden Informationen bereitstellen:<br /><br />- Ob und wann die von Ihnen angegebenen Fabrikam-Personen das Dokument geöffnet haben.<br /><br />- Ob andere Personen, die Sie nicht angegeben haben, versucht haben, das Dokument zu öffnen (und dabei gescheitert sind): Das Dokument wurde möglicherweise weitergeleitet oder in einem freigegebenen Speicherort gespeichert, auf den andere Personen Zugriff haben.<br /><br />- Ob eine der angegebenen Personen versucht hat (und gescheitert ist), das Dokument zu drucken oder zu ändern.|
|Unterstützung für häufig verwendete Geräte, nicht nur Windows-Computer|√ Zu den [unterstützten Geräten](../get-started/requirements-client-devices.md) gehören:<br /><br />- Windows-Computer und -Telefone<br /><br />- Mac-Computer<br /><br />- iOS-Tablets und -Telefone<br /><br />- Android-Tablets und -Telefone|
|Unterstützung von Business-to-Business-Zusammenarbeit|√ Weil Azure RMS ein Cloud-Dienst ist, ist es nicht erforderlich, explizit Vertrauensstellungen zu anderen Organisationen zu konfigurieren, bevor Sie geschützte Inhalte mit diesen gemeinsam nutzen können. Sofern diese Organisationen bereits ein Office 365- oder Azure AD-Verzeichnis haben, wird Zusammenarbeit zwischen Organisationen automatisch unterstützt. Ist dies nicht der Fall, können sich Benutzer für das kostenlose [RMS for Individuals](rms-for-individuals.md)-Abonnement registrieren.|
|Unterstützung sowohl für lokale Dienste als auch für Office 365|√ Azure RMS arbeitet [nahtlos mit Office 365](office-apps-services-support.md) zusammen. Außerdem können Sie Azure RMS mit den folgenden lokalen Diensten verwenden, wenn Sie den[RMS-Connector](../deploy-use/deploy-rms-connector.md) bereitstellen:<br /><br />- Exchange Server<br /><br />- SharePoint Server<br /><br />- Windows Server mit Dateiklassifizierungsinfrastruktur|
|Einfache Aktivierung|√ Zum [Aktivieren des Rechteverwaltungsdiensts](../deploy-use/activate-service.md) für Benutzer sind nur einige Mausklicks im klassischen Azure-Portal erforderlich.|
|Fähigkeit, nach Bedarf über die gesamte Organisation zu skalieren|√ Weil Azure RMS als Cloud-Dienst mit der Azure-Flexibilität für zentrales und horizontales Hochskalieren ausgeführt wird, müssen Sie keine zusätzlichen lokalen Server bereitstellen.|
|Fähigkeit, einfache und flexible Richtlinien zu erstellen|√ [Angepasste Vorlagen für Benutzerrechterichtlinien](../deploy-use/configure-custom-templates.md) bieten schnelle und einfache Lösungen, mit denen Administratoren Richtlinien anwenden und Benutzer das richtige Maß an Schutz für jedes Dokument anwenden sowie den Zugriff auf Personen in der eigenen Organisation beschränken können.<br /><br />Soll beispielsweise ein unternehmensweites Strategiepapier für alle Mitarbeiter freigegeben werden, könnten Sie eine Schreibschutzrichtlinie für alle internen Mitarbeiter anwenden. Für ein Dokument mit sensibleren Daten, etwa einen Finanzbericht, könnten Sie den Zugriff auf Führungskräfte beschränken.|
|Breite Anwendungsunterstützung|√ Azure RMS ist eng auf Microsoft Office-Anwendungen und -Dienste abgestimmt und ermöglicht durch Verwenden der RMS-Freigabe-Anwendung erweiterte Unterstützung für andere Anwendungen.<br /><br />√ Mit dem [Microsoft Rights Management SDK](../develop/developers-guide.md#software-development-kits) erhalten Ihre internen Entwickler sowie Softwarehersteller APIs, mit denen sie angepasste Anwendungen schreiben können, die Azure RMS unterstützen.<br /><br />Weitere Informationen finden Sie unter [Sonstige Anwendungen, die die RMS-APIs unterstützen](api-support.md).|
|IT-Abteilung muss Kontrolle über die Daten behalten|√ Organisationen können ihren eigenen Mandantenschlüssel verwalten, die „[Bring Your Own Key](../plan-design/plan-implement-tenant-key.md)“ (BYOK)-Lösung nutzen und ihren Mandantenschlüssel in Hardwaresicherheitsmodulen (HSMs) speichern.<br /><br />√ Unterstützung der Überwachung und [Verwendungsprotokollierung](../deploy-use/log-analyze-usage.md), sodass Sie Geschäftsabläufe analysieren, Missbrauch erkennen und (falls ein Informationsleck vorliegt) forensische Analysen durchführen können.<br /><br />√ Delegierter Zugriff mithilfe der [Administratorfunktion](../deploy-use/configure-super-users.md) stellt sicher, dass die IT-Abteilung stets auf geschützte Inhalte zugreifen kann, selbst wenn ein Dokument von einem Mitarbeiter geschützt wurde, der die Organisation bereits verlassen hat. Bei Peer-zu-Peer-Verschlüsselungslösungen besteht dagegen das Risiko, dass Zugriff auf Unternehmensdaten verloren geht.<br /><br />√ Synchronisieren [nur der Verzeichnisattribute, die Azure RMS benötigt](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms), um eine allgemeine Identität für Ihre lokalen Active Directory-Konten zu unterstützen, indem ein [Verzeichnissynchronisierungstool](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison) wie Azure AD Connect verwendet wird.<br /><br />√ Aktivieren des einmaligen Anmelden, ohne Kennwörter in die Cloud zu replizieren, mithilfe von AD FS.<br /><br />√ Organisationen haben immer die Möglichkeit, Azure RMS nicht mehr zu verwenden, ohne den Zugriff auf Inhalte zu verlieren, die zuvor von Azure RMS geschützt wurden. Weitere Informationen zur Außerbetriebsetzung finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md). Organisationen, die Active Directory Rights Management Services (AD RMS) bereitgestellt haben, können darüber hinaus [zu Azure RMS migrieren](../plan-design/migrate-from-ad-rms-to-azure-rms.md) , ohne den Zugriff auf Daten zu verlieren, die zuvor durch AD RMS geschützt waren.|
> [!TIP]
> Wenn Sie mit der lokalen Version von Rights Management, Active Directory Rights Management Services (AD RMS), vertraut sind, ist die Vergleichstabelle in [Vergleich zwischen Azure Rights Management und AD RMS](compare-azure-rms-ad-rms.md) möglicherweise für Sie interessant.

## Sicherheits-, Compliance- und gesetzliche Anforderungen
Azure RMS unterstützt die folgenden Sicherheits-, Compliance- und gesetzlichen Anforderungen:

√ Verwendung von Kryptografie gemäß Industriestandard und Unterstützung von FIPS 140-2. Weitere Informationen finden Sie unter [Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellängen](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

√ Unterstützung für Thales Hardwaresicherheitsmodule (HSMs), damit Sie Ihren Mandantenschlüssel in Microsoft Azure-Rechenzentren speichern können. Azure RMS verwendet getrennte Security Worlds für seine Rechenzentren in Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien, sodass Ihre Schlüssel nur in Ihrer Region verwendet werden können.

√ Zertifiziert für Folgendes:

-   ISO/IEC 27001:2013 (enthält [ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   SOC 2 SSAE 16/ISAE 3402 Attestations

-   HIPAA BAA

-   EU-Modellklauseln

-   FedRAMP als Teil von Azure Active Directory in Office 365-Zertifizierung, ausgestellt von FedRAMP Agency Authority to Operate durch HHS

-   PCI DSS Level 1

Weitere Informationen zu diesen externen Zertifizierungen finden Sie im [Azure Trust Center](http://azure.microsoft.com/support/trust-center/compliance/).

## Nächste Schritte

Informationen dazu, wie Azure RMS für Administratoren und Benutzern aussieht, finden Sie unter [Azure RMS in Aktion](what-admins-users-see.md).

Wenn Sie eher an technischen Informationen zur Funktionsweise von Azure RMS interessiert sind, finden Sie diese unter [Funktionsweise von Azure RMS](how-does-it-work.md). 


<!--HONumber=Aug16_HO4-->


