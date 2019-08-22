---
title: Häufig gestellte Fragen zu Azure Information Protection
description: Einige häufig gestellte Fragen zu Azure Information Protection und dem dazugehörigen Schutzdienst, Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 08/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: d2f3616d64a0405d1a0caf452d3491ee7a1fcac1
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884773"
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Häufig gestellte Fragen zu Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Haben Sie eine Frage zu Azure Information Protection oder zum Azure Rights Management-Dienst (Azure RMS)? Vielleicht finden Sie hier eine Antwort darauf.

Diese Seiten mit häufig gestellten Fragen werden regelmäßig aktualisiert. Dabei werden die neuen Beiträge in den Ankündigungen zu den monatlichen Dokumentationsupdates im [Azure Information Protection-Blog](https://aka.ms/AIPblog) aufgelistet.

## <a name="whats-the-difference-between-azure-information-protection-and-microsoft-information-protection"></a>Was ist der Unterschied zwischen Azure Information Protection und Microsoft Information Protection?

Im Gegensatz zu Azure Information Protection ist Microsoft Information Protection kein Abonnement und kein Produkt, das Sie erwerben können. Stattdessen handelt es sich um ein Framework für Produkte und integrierte Funktionen, mit denen Sie die vertraulichen Informationen Ihres Unternehmens schützen können:

- Zu den einzelnen Produkten in diesem Framework gehören Azure Information Protection, Office 365 Information Protection (z.B. Office 365 DLP), Windows Information Protection und Microsoft Cloud App Security. 

- Die integrierten Features in diesem Framework umfassen die Verwaltung einheitlicher Bezeichnungen, in Office-Apps integrierte Funktionen für Endbenutzerbezeichnungen, das Erfassen einheitlicher Bezeichnungen und Anwenden von Schutz auf Daten durch Windows, das Microsoft Information Protection SDK und die neuen Adobe Acrobat Reader-Funktionen zum Anzeigen bezeichneter und geschützter PDFs.

Weitere Informationen finden Sie unter [Bekanntgabe der Verfügbarkeit von Information Protection-Funktionen zum Schutz von vertraulichen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>Was ist der Unterschied zwischen Bezeichnungen in Azure Information Protection und Office 365?

Ursprünglich hat Office 365 nur über [Aufbewahrungsbezeichnungen](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) verfügt, mit denen Sie Dokumente und E-Mails für die Überwachung und die Aufbewahrung klassifizieren können, wenn der Inhalt sich in Office 365-Diensten befindet. Im Gegensatz dazu können Sie mit Bezeichnungen in Azure Information Protection eine konsistente Klassifizierung und Schutzrichtlinie für lokale oder in der Cloud befindliche Dokumente und E-Mails anwenden.

Wie auf der Microsoft Ignite 2018 in Orlando angekündigt, ist nun eine Option zum Erstellen und Konfigurieren von [Vertraulichkeitsbezeichnungen](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) zusätzlich zu den Aufbewahrungsbezeichnungen in einem der Admin-Centers verfügbar: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, oder das Microsoft 365 Compliance Center. Sie können Ihre vorhandenen Azure Information Protection Bezeichnungen zum neuen Unified Label-Speicher migrieren, der als Vertraulichkeits Bezeichnungen mit Office-Apps verwendet werden soll. 

Weitere Informationen zum Verwalten einheitlicher Bezeichnungen und deren Unterstützung finden Sie im Blogbeitrag [Bekanntgabe der Verfügbarkeit von Information Protection-Funktionen zum Schutz von vertraulichen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

Weitere Informationen zum Migrieren vorhandener Bezeichnungen finden Sie unter [Migrieren von Azure Information Protection Bezeichnungen zu Unified Sensitivität-Bezeichnungen](configure-policy-migrate-labels.md).

## <a name="how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform"></a>Wie kann ich feststellen, ob mein Mandant auf der Unified-Bezeichnung-Plattform ist?

Wenn sich Ihr Mandant auf der Unified Label-Plattform befindet, können Vertraulichkeits Bezeichnungen von [Clients und Diensten verwendet werden, die eine einheitliche Bezeichnung unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling). Wenn Sie Ihr Abonnement für Azure Information Protection im Juni 2019 oder höher erhalten haben, befindet sich Ihr Mandant automatisch auf der Unified-Bezeichnung-Plattform, und es ist keine weitere Aktion erforderlich. Ihr Mandant kann sich auch auf dieser Plattform befinden, da die Azure Information Protection Bezeichnungen migriert wurden.

Um den Status zu überprüfen, wechseln Sie in der Azure-Portal zu **Azure Information Protection** > **Unified-Bezeichnung** **Verwalten** > , und zeigen Sie den Status der **vereinheitlichten Bezeichnung**an:

- Wenn Sie **aktiviert**sehen, befindet sich Ihr Mandant auf der Unified-Beschriftungs Plattform.

- Wenn Sie **nicht aktiviert**sehen, befindet sich Ihr Mandant nicht auf der Unified-Beschriftungs Plattform. Migrations Anweisungen finden Sie unter [Migrieren von Azure Information Protection Bezeichnungen zu vereinheitlichten Vertraulichkeits Bezeichnungen](configure-policy-migrate-labels.md).

## <a name="whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client"></a>Worin besteht der Unterschied zwischen dem Azure Information Protection Client und dem Azure Information Protection Unified-Bezeichnungs Client?

Der **Azure Information Protection Client (klassisch)** ist verfügbar, seit Azure Information Protection erstmals als neuer Dienst für die Klassifizierung und den Schutz von Dateien und e-Mails angekündigt wurde. Dieser Client lädt Bezeichnungen und Richtlinien Einstellungen von Azure herunter und konfiguriert die Azure Information Protection Richtlinie aus der Azure-Portal. Weitere Informationen finden Sie unter [Übersicht über die Azure Information Protection-Richtlinie](overview-policy.md). 

Der **Azure Information Protection Unified Bezeichnung-Client** ist eine neuere Ergänzung, um den einheitlichen Bezeichnungs Speicher zu unterstützen, der von mehreren Anwendungen und Diensten unterstützt wird. Dieser Client lädt Vertraulichkeits Bezeichnungen und Richtlinien Einstellungen von den folgenden admin Centers herunter: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, und das Microsoft 365 Compliance Center. Weitere Informationen finden Sie unter [Übersicht über Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels).

Wenn Sie nicht sicher sind, welcher Client verwendet werden soll, finden Sie unter [auswählen des zu verwendenden Azure Information Protection Clients](./rms-client/use-client.md#choose-which-azure-information-protection-client-to-use)Weitere Informationen.

### <a name="identify-which-client-you-have-installed"></a>Identifizieren des installierten Clients

Beide Clients werden bei der Installation **Azure Information Protection**angezeigt. Verwenden Sie die Option **Hilfe und Feedback** , um das Dialogfeld **Microsoft Azure Information Protection** zu öffnen, damit Sie den installierten Client leichter identifizieren können:

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und anschließend **Hilfe und Feedback** aus.

- Aus einer Office-Anwendung: Wählen Sie über die Schaltfläche **schützen** (klassischer Client) oder Vertraulichkeits Schaltfläche (einheitlicher Bezeichnungs Client) die Option **Hilfe und Feedback**aus.

Verwenden Sie die angezeigte **Versions** Nummer, um den Client zu identifizieren:

- Eine Version **1**, z. b. **1.53.10.0**, identifiziert den Azure Information Protection Client (klassisch).

- Eine Version **2**, z. b. **2.2.14.0**, identifiziert den Azure Information Protection Unified-Bezeichnungs Client.

## <a name="when-is-the-right-time-to-migrate-my-labels"></a>Wann ist der richtige Zeitpunkt für die Migration meiner Bezeichnungen?

Nun, da die Option zum Migrieren von Bezeichnungen in der Azure-Portal allgemein verfügbar ist, empfiehlt es sich, die Migration zu aktivieren, sodass Sie Ihre Bezeichnungen als Vertraulichkeits Bezeichnungen mit [Clients und Diensten verwenden können, die vereinheitlichte Bezeichnungen unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

Weitere Informationen und Anweisungen finden Sie unter [Migrieren von Azure Information Protection Bezeichnungen zu Unified Sensitivität-Bezeichnungen](configure-policy-migrate-labels.md).

## <a name="after-ive-migrated-my-labels-which-management-portal-do-i-use"></a>Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?

Nachdem Sie Ihre Bezeichnungen im Azure-Portal migriert haben:

- Wenn Sie [Clients und Dienste mit einheitlicher Bezeichnung](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling)versehen haben, wechseln Sie zu einem der Admin Center (Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center), um diese Bezeichnungen zu veröffentlichen und ihre Richtlinie zu konfigurieren. Einstellungen. Für zukünftige Bezeichnungsänderungen verwenden Sie eines dieser Admin-Centers. Die Bezeichnungen und Richtlinieneinstellungen werden von Clients für einheitliche Bezeichnungen aus diesen Admin-Centers heruntergeladen.

- Wenn Sie über den [Azure Information Protection-Client (klassisch)](./rms-client/aip-client.md)verfügen, verwenden Sie weiterhin die Azure-Portal, um die Bezeichnungen und Richtlinien Einstellungen zu bearbeiten. Der klassische Client lädt weiterhin Bezeichnungen und Richtlinien Einstellungen von Azure herunter.

- Wenn Sie über [einheitliche](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling) Bezeichnungs-und [klassische Clients](./rms-client/aip-client.md)verfügen, können Sie die Verwaltungs Center oder den Azure-Portal verwenden, um Bezeichnungen zu ändern. Damit die klassischen Clients jedoch die Bezeichnungs Änderungen übernehmen, die Sie in den Admin Center vornehmen, müssen Sie zum Azure-Portal zurückkehren: Verwenden Sie die Option **Veröffentlichen** auf dem Blatt **Azure Information Protection - Unified labeling** (Azure Information Protection – einheitliche Bezeichnungen) im Azure-Portal. 

Verwenden Sie weiterhin das Azure-Portal für die [zentrale Berichterstellung](reports-aip.md) und die [Überprüfung](deploy-aip-scanner.md).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?

Azure Information Protection stellt Klassifizierungen, Bezeichnungen und den Schutz für Dokumente und E-Mails einer Organisation bereit. Die Schutztechnologie nutzt den Azure Rights Management-Dienst, der nun eine Komponente von Azure Information Protection ist.

## <a name="whats-the-role-of-identity-management-for-azure-information-protection"></a>Was ist die Rolle der Identitätsverwaltung für Azure Information Protection?

Benutzer benötigen einen gültigen Benutzernamen und ein Kennwort, um auf durch Azure Information Protection geschützte Inhalte zuzugreifen. Weitere Informationen zum Schutz Ihrer Daten mit Azure Information Protection finden Sie unter [Die Rolle von Azure Information Protection beim Schützen von Daten](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?

Informationen dazu finden Sie auf der [Preisseite von Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection).

Wenn Sie über ein Office 365-Abonnement verfügen, das Datenschutz mit Azure Rights Management umfasst, laden Sie das [Datenblatt zur Azure Information Protection-Lizenz](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) herunter.

Haben Sie noch Fragen zur Lizenzierung? Möglicherweise finden Sie passende Antworten im Abschnitt [Häufig gestellte Fragen zur Lizenzierung](https://azure.microsoft.com/pricing/details/information-protection#faq).

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Ist der Azure Information Protection-Client nur für Abonnements geeignet, die Funktionen für Klassifizierung und Bezeichnung umfassen?

Nein. Der Azure Information Protection-Client (klassisch) kann auch mit Abonnements verwendet werden, die nur den Azure Rights Management-Dienst zum Schutz von Daten enthalten.

Wenn der klassische Client installiert ist und keine Azure Information Protection Richtlinie vorhanden ist, wird dieser Client automatisch im reinen [Schutzmodus](./rms-client/client-protection-only-mode.md)ausgeführt. In diesem Modus können Benutzer problemlos Rights Management-Vorlagen und benutzerdefinierte Berechtigungen anwenden. Wenn Sie zu einem späteren Zeitpunkt ein Abonnement erwerben, das Klassifizierungen und Bezeichnungen umfasst, wechselt der Client beim Herunterladen der Azure Informationen Protection-Richtlinie automatisch in den Standardmodus.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?

Globale Administratoren für einen Office 365- oder Azure AD-Mandanten können alle administrativen Aufgaben für Azure Information Protection ausführen. Zum Zuweisen von Administratorrechten an andere Benutzer haben Sie folgende Optionen:

- **Azure Information Protection-Administrator**: Mit dieser Azure Active Directory Administrator Rolle kann ein Administrator Azure Information Protection, aber keine anderen Dienste konfigurieren. Ein Administrator mit dieser Rolle kann den Azure Rights Management-Schutzdienst aktivieren und deaktivieren, Schutzeinstellungen und Bezeichnungen konfigurieren und die Azure Information Protection-Richtlinie konfigurieren. Außerdem kann ein Administrator mit dieser Rolle alle PowerShell-Cmdlets für den [Azure Information Protection Client](./rms-client/client-admin-guide-powershell.md) und das [aipservice-Modul](administer-powershell.md)ausführen. Diese Rolle unterstützt jedoch nicht das Nachverfolgen und widerrufen von Dokumenten für Benutzer.
    
    > [!NOTE]
    > Nachdem Sie [Ihren Mandanten zum Speicher für einheitliche Bezeichnungen migriert haben](configure-policy-migrate-labels.md), wird diese Rolle für das Azure-Portal nicht mehr unterstützt.
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- Administrator für **Compliance** -oder Kompatibilitäts **Daten**: Mit diesen Azure Active Directory Administrator Rollen können Administratoren Azure Information Protection konfigurieren. hierzu gehört auch das Aktivieren und Deaktivieren des Azure Rights Management Protection-diensdienstanbieter, das Konfigurieren von Schutzeinstellungen und-Bezeichnungen sowie das Konfigurieren des Azure Information Protection Richtlinie. Außerdem kann ein Administrator mit einer dieser Rollen alle PowerShell-Cmdlets für den [Azure Information Protection Client](./rms-client/client-admin-guide-powershell.md) und das [aipservice-Modul](administer-powershell.md)ausführen. Diese Rollen unterstützen jedoch nicht das Nachverfolgen und widerrufen von Dokumenten für Benutzer.
    
    Informationen zum Zuweisen eines Benutzers zu einer dieser administrativen Rollen finden Sie unter [Zuweisen eines Benutzers zu Administrator Rollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Weitere Informationen zu den Berechtigungen, die ein Benutzer mit diesen Rollen besitzt, finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

- **Sicherheitsleseberechtigter**: Nur für [Azure Information Protection-Analysen](reports-aip.md). Mit dieser Azure Active Directory-Administratorrolle kann ein Administrator anzeigen, wie Ihre Bezeichnungen verwendet werden, den Benutzerzugriff auf gekennzeichnete Dokumente und E-Mails und alle Änderungen ihrer Klassifizierung überwachen sowie Dokumente erkennen, die vertrauliche Informationen enthalten, die geschützt werden müssen. Da dieses Feature Azure Log Analytics verwendet, benötigen Sie außerdem eine unterstützende [RBAC-Rolle](reports-aip.md#permissions-required-for-azure-information-protection-analytics).

- **Sicherheitsadministrator**: Mit dieser Azure Active Directory Administrator Rolle kann ein Administrator Azure Information Protection im Azure-Portal konfigurieren, zusätzlich zur Konfiguration einiger Aspekte anderer Azure-Dienste. Ein Administrator mit dieser Rolle kann keine [PowerShell-Cmdlets aus dem aipservice-Modul](administer-powershell.md)ausführen oder Dokumente für Benutzer nachverfolgen und widerrufen.
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Weitere Informationen zu den Berechtigungen, über die ein Benutzer mit dieser Rolle verfügt, finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

- **Globaler Administrator** und **Connector-Administrator** von Azure Rights Management: Für diese Azure Rights Management-Administrator Rollen erteilt der erste Benutzerberechtigungen zum Ausführen aller [PowerShell-Cmdlets aus dem aipservice-Modul](administer-powershell.md) , ohne Sie als globaler Administrator für andere Clouddienste zu erstellen, und die zweite Rolle gewährt Berechtigungen zum Ausführen nur des Rights Management-Connector (RMS). Keines dieser administrativen Rollen gewährt Verwaltungs Konsolen Berechtigungen oder das Nachverfolgen und widerrufen von Dokumenten für Benutzer.
    
    Wenn Sie eine dieser administrativen Rollen zuweisen möchten, verwenden Sie das PowerShell-Cmdlet "aipservice", " [Add-aipservicerolebasedadministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator)".

Einige Dinge sind zu beachten:

- Microsoft-Konten werden für die delegierte Administration von Azure Information Protection nicht unterstützt, auch wenn diese Konten einer der aufgeführten Administrator Rollen zugewiesen sind. 

- Wenn Sie [Onboardingsteuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, wird die Möglichkeit zum Verwalten von Azure Information Protection mit Ausnahme des RMS-Connectors durch diese Konfiguration nicht beeinflusst. Wenn sie Onboarding-Steuerelemente beispielsweise so konfiguriert haben, dass die Fähigkeit, Inhalte zu schützen, auf die Gruppe „IT-Abteilung“ beschränkt ist, muss das von Ihnen zum Installieren und Konfigurieren des RMS-Connectors verwendete Konto ein Member dieser Gruppe sein. 

- Benutzer, denen eine administrative Rolle zugewiesen wurde, können den Schutz von Dokumenten oder E-Mails nicht entfernen, die von Azure Information Protection geschützt wurden. Dies können nur Benutzer tun, denen Administratorrechte zugewiesen sind, wenn das Administratorfeature aktiviert ist. Allerdings kann jeder Benutzer, dem Sie Administratorberechtigungen für Azure Information Protection zugewiesen haben, anderen Benutzern Administratorrechte zuweisen, einschließlich ihres eigenen Kontos. Sie können auch das Superuserfeature aktivieren. Diese Aktionen werden in einem Administratorprotokoll aufgezeichnet. Weitere Informationen finden Sie im Abschnitt bewährte Sicherheitsmethoden unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](configure-super-users.md). 

- Wenn Sie die Azure Information Protection Bezeichnungen in den einheitlichen Bezeichnungs Speicher migrieren, lesen Sie den folgenden Abschnitt aus der Dokumentation zur Bezeichnung Migration: [Administrative Rollen, die die vereinheitlichte Bezeichnung-Plattform unterstützen](configure-policy-migrate-labels.md#administrative-roles-that-support-the-unified-labeling-platform).

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Unterstützt Azure Information Protection lokale und hybride Szenarios?

Ja. Obwohl Azure Information Protection eine cloudbasierte Lösung ist, können damit Dokumente und E-Mails, die sowohl lokal als auch in der Cloud gespeichert sind, klassifiziert, bezeichnet und geschützt werden.

Wenn Sie über Exchange Server, SharePoint Server und Windows-Dateiserver verfügen, können Sie den [Rights Management-Connector](deploy-rms-connector.md) bereitstellen, damit diese lokalen Server den Azure Rights Management-Dienst verwenden können, um Ihre E-Mails und Dokumente zu schützen. Sie können Ihre Active Directory-Domänencontroller auch mit Azure AD synchronisieren und zusammenführen, um eine nahtlosere Authentifizierung für Benutzer zu erreichen. Dazu können Sie beispielsweise [Azure AD Connect](/azure/active-directory/hybrid/whatis-azure-ad-connect) verwenden.

Der Azure Rights Management-Dienst generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf und verwendet daher keine lokale PKI. Weitere Informationen dazu, wie Azure Rights Management Zertifikate verwendet, finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsaufnahme](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) im Artikel [Funktionsweise von Azure RMS](./how-does-it-work.md).

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Welche Arten von Daten können von Azure Information Protection klassifiziert und geschützt werden?

Azure Information Protection kann E-Mails und Dokumente klassifizieren und schützen, egal ob sie lokal oder in der Cloud gespeichert sind. Diese Dokumente können z.B. Word-Dokumente, Excel-Tabellen, PowerPoint-Präsentationen, PDF-Dokumente, textbasierte Dateien und Bilddateien sein. Eine Liste der unterstützten Dokumenttypen finden Sie in der Liste der [unterstützten Dateitypen](./rms-client/client-admin-guide-file-types.md) im Administratorleitfaden.

Azure Information Protection können keine strukturierten Daten (z. b. Datenbankdateien, Kalender Elemente, Power BI Berichte, Yammer-Beiträge, Sway-Inhalte und OneNote-Notizbücher) klassifizieren und schützen.

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?

Das ist richtig. Für die Vorschauversion wird jetzt angeboten, bedingten Zugriff auf Azure AD für Azure Information Protection zu konfigurieren.

Wenn ein Benutzer ein durch Azure Information Protection geschütztes Dokument öffnet, können Administratoren jetzt basierend auf der bedingten Standardzugriffssteuerung Benutzern den Zugriff in ihrem Mandanten verweigern oder gewähren. Die mehrstufige Authentifizierung (MFA) ist eine der am häufigsten verlangten Bedingungen. Eine weitere ist, dass Geräte [mit Ihren Intune-Richtlinien kompatibel](/intune/conditional-access-intune-common-ways-use) sein müssen, damit Mobilgeräte zum Beispiel Ihren Kennwortanforderungen entsprechen, und eine Minimalversion eines Betriebssystems sowie Computer müssen mit einer Domäne verbunden sein.

Weitere Informationen und einige exemplarische Vorgehensweisen finden Sie im folgenden Blogbeitrag: [Conditional Access policies for Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/) (Bedingte Zugriffsrichtlinien für Azure Information Protection).

Zusätzliche Informationen:

- Für Windows-Computer: Die Richtlinien zum bedingten Zugriff für Azure Information Protection werden in der aktuellen Vorschauversion ausgewertet, wenn die [Benutzerumgebung initialisiert wird](./how-does-it-work.md#initializing-the-user-environment) (dieser Vorgang wird auch als Bootstrapping bezeichnet). Danach wird alle 30 Tage eine Prüfung durchgeführt.

- Möglicherweise möchten Sie näher bestimmen, wie oft Ihre Richtlinien zum bedingten Zugriff geprüft werden. Konfigurieren Sie dazu die Tokengültigkeitsdauer. Weitere Informationen finden Sie unter [Konfigurierbare Tokengültigkeitsdauern in Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- Es wird empfohlen, dass Sie keine Administratorkonten zu Ihren Richtlinien zum bedingten Zugriff hinzufügen, da diese Konten nicht auf die Seite „Azure Information Protection“ im Azure-Portal zugreifen können.

- Wenn Sie MFA in Ihren Richtlinien für bedingten Zugriff für die Zusammenarbeit mit anderen Unternehmen (B2B) verwenden, müssen Sie [Azure AD B2B-Zusammenarbeit](/azure/active-directory/b2b/what-is-b2b) verwenden und Gastkonten für die Benutzer erstellen, mit denen Sie in dem anderen Unternehmen zusammenarbeiten möchten.

- Mit der Vorschauversion für Azure AD, die im Dezember 2018 veröffentlicht wurde, können Sie jetzt Benutzer auffordern, Nutzungsbedingungen zu akzeptieren, bevor sie ein ungeschütztes Dokument zum ersten Mal öffnen. Weitere Informationen finden Sie im folgenden Blogbeitrag: [Updates to Azure AD Terms of Use functionality within conditional access (Updates zur Azure AD-Funktion für Nutzungsbedingungen für bedingten Zugriff)](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Updates-to-Azure-AD-Terms-of-Use-functionality-within/ba-p/294822)

- Wenn Sie für den bedingten Zugriff auf mehrere Cloud-Apps zurückgreifen, wird Ihnen unter Umständen **Microsoft Azure Information Protection** nicht in der Auswahlliste angezeigt. Verwenden Sie in diesem Fall das Suchfeld oben in der Liste. Geben Sie „Microsoft Azure Information Protection“ ein, um die verfügbaren Apps zu filtern. Sofern Sie über ein unterstütztes Abonnement verfügen, können Sie nun **Microsoft Azure Information Protection** auswählen. 

## <a name="i-see-azure-information-protection-is-listed-as-a-security-provider-for-microsoft-graph-securityhow-does-this-work-and-what-alerts-will-i-receive"></a>Ich sehe, dass Azure Information Protection als Sicherheitsanbieter für Microsoft Graph Security aufgeführt wird. Wie funktioniert das, und welche Warnungen erhalte ich?

Das ist richtig. Als Angebot für die öffentliche Vorschauversion können Sie jetzt eine **Warnung zu anomalem Datenzugriff in Azure Information Protection** erhalten. Diese Warnung wird bei ungewöhnlichen Versuchen ausgelöst, auf Daten zuzugreifen, die von Azure Information Protection geschützt werden. Ein Beispiel hierfür ist der Zugriff auf eine ungewöhnlich große Datenmenge zu einer ungewöhnlichen Tageszeit oder von einem unbekannten Standort aus.

Anhand solcher Warnungen können Sie fortgeschrittene datenbezogene Angriffe und Bedrohungen durch Insider in Ihrer Umgebung erkennen. Diese Warnungen verwenden Machine Learning, um ein Verhaltensprofil der Benutzer zu erstellen, die auf Ihre geschützten Daten zugreifen. 

Die Azure Information Protection-Warnungen sind über die [Microsoft Graph Security-API](https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/security-api-overview) verfügbar, oder Sie können Azure Monitor verwenden, um Warnungen an SIEM-Lösungen wie z.B. Splunk und IBM Qradar zu [streamen](https://developer.microsoft.com/graph/docs/concepts/security_siemintegration).

Weitere Informationen zur Microsoft Graph Security-API finden Sie in der [Übersicht zur Microsoft Graph Security-API](https://developer.microsoft.com/graph/docs/concepts/security-concept-overview).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>Was ist der Unterschied zwischen der Windows Server-Dateiklassifizierungsinfrastruktur und der Azure Information Protection-Überprüfung?

Die Windows Server-Dateiklassifizierungsinfrastruktur war eine Option, um Dokumente zu klassifizieren und diese dann mithilfe des [Rights Management-Connectors](deploy-rms-connector.md) (nur Office-Dokumente) oder einem [PowerShell-Skript](./rms-client/configure-fci.md) (alle Dateitypen) zu schützen. 

Jetzt können Sie die empfohlene [Azure Information Protection-Überprüfung](deploy-aip-scanner.md) verwenden. Die Überprüfung nutzt den Azure Information Protection-Client und Ihre Azure Information Protection-Richtlinie, um Dokumente (alle Dateitypen) zu bezeichnen, sodass diese Dokumente alle klassifiziert und optional auch geschützt werden.

Zwischen den beiden Lösungen bestehen die folgenden wesentlichen Unterschiede:

|Windows Server-Dateiklassifizierungsinfrastruktur|Azure Information Protection-Überprüfung|
|--------------------------------|-------------------------------------|
|Unterstützte Datenspeicher: <br /><br />– Lokale Ordner unter Windows Server|Unterstützte Datenspeicher: <br /><br />– Lokale Ordner unter Windows Server<br /><br />– Windows-Dateifreigaben und Network Attached Storage<br /><br />– SharePoint Server 2016 und SharePoint Server 2013 SharePoint Server 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.|
|Betriebsmodus: <br /><br />– Echtzeit|Betriebsmodus: <br /><br />– Füllt Datenspeicher automatisch auf. Dieser Zyklus kann einmal oder wiederholt ausgeführt werden|
|Unterstützung für Dateitypen: <br /><br />– Standardmäßig werden alle Dateitypen geschützt. <br /><br />– Bestimmte Dateitypen können vom Schutz ausgeschlossen werden, indem Sie die Registrierung bearbeiten.|Unterstützung für Dateitypen: <br /><br />– Die Office-Dateiformate und PDF-Dokumente werden standardmäßig geschützt. <br /><br />– Weitere Dateitypen können ebenfalls geschützt werden, indem Sie die Registrierung bearbeiten.|

Beim Festlegen des [Rights Management Besitzers](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) für Dateien, die in einem lokalen Ordner oder einer Netzwerkfreigabe geschützt sind, gibt es einen Unterschied. Standardmäßig wird für beide Lösungen der Rights Management-Besitzer für das Konto festgelegt, das die Datei schützt. Sie können diese Einstellung aber auch außer Kraft setzen:

- Für die Windows Server-Dateiklassifizierungsinfrastruktur: Sie können festlegen, dass alle Dateien einen einzigen Rights Management-Besitzer haben, oder Sie können den Rights Management-Besitzer für jede Datei dynamisch festlegen. Um den Rights Management-Besitzer dynamisch festzulegen, verwenden Sie den Parameter **-OwnerMail [Source File Owner Email]** und seinen Wert. Durch diese Konfiguration wird die E-Mail-Adresse des Benutzers von Active Directory mithilfe des Benutzerkontonamens in der Owner-Eigenschaft der Datei abgerufen.

- Für die Azure Information Protection-Überprüfung: Sie können für erst seit Kurzem geschützte Dateien festlegen, dass alle Dateien in einem angegebenen Datenspeicher einen einzigen Rights Management-Besitzer haben, aber Sie können diesen nicht für jede Datei dynamisch festlegen. Der Rights Management-Besitzer wird für Dateien, die bereits vorher geschützt wurden, nicht geändert. Geben Sie zum Festlegen des Kontos für neu geschützte Dateien die Einstellung **-Default owner** (-Standardbesitzer) im Scannerprofil an. 

Wenn der Scanner Dateien auf Websites und in Bibliotheken von SharePoint schützt, wird der Rights Management-Besitzer dynamisch für jede Datei mithilfe des SharePoint-Editorwerts festgelegt.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Ich habe gehört, dass bald eine neue Version von Azure Information Protection verfügbar sein wird. Wann wird diese veröffentlicht?

Die technische Dokumentation enthält keine Informationen zu bevorstehenden Releases. Informationen zu dieser Art von Informationen finden Sie in der [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?&filters=Azure%20Information%20Protection%2CO365%20Information%20Protection#owRoadmapMainContent)im [Enterprise Mobility + Security Blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Ist Azure Information Protection für mein Land geeignet?

Verschiedene Länder haben unterschiedliche Anforderungen und Bestimmungen. Auf der Seite [Suitability for different countries (Eignung für unterschiedliche Länder)](./compliance.md#suitability-for-different-countries) finden Sie Antworten zu den Fragen für Ihre Organisation.

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Wie kann Azure Information Protection bei der Datenschutz-Grundverordnung (DSGVO) helfen?

Informationen darüber, wie Azure Information Protection Ihnen bei der Umsetzung der Datenschutz-Grundverordnung (DSGVO) helfen kann, finden Sie im folgenden Blogbeitrag (inklusive Video): [Microsoft 365 provides an information protection strategy to help with the GDPR (Microsoft 365 stellt eine Datenschutzstrategie zum Einhalten der DSGVO bereit)](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr).

## <a name="where-can-i-find-supporting-information-for-azureinformation-protectionsuch-as-legal-compliance-and-slas"></a>Wo finde ich weitere Informationen zu Azure Information Protection, z.B. rechtliche Hinweise, Informationen zur Compliance und SLAs?
Lesen Sie hierzu [Kompatibilitätsinformationen und ergänzende Informationen zu Azure Information Protection](./compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Wie kann ich ein Problem melden oder Feedback zu Azure Information Protection übermitteln?

Wenden Sie sich an Ihre Standardsupportkanäle oder an den [Microsoft Support](information-support.md#to-contact-microsoft-support), um technischen Support zu erhalten.

Wir laden Sie auch dazu ein, sich mit unserem Engineering-Team auf seiner [Yammer-Website zu Azure Information Protection](https://www.yammer.com/askipteam/) in Verbindung zu setzen. 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Wie gehe ich vor, wenn meine Frage hier nicht behandelt wird?

Prüfen Sie zunächst die folgenden häufig gestellten Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen oder den Schutz von Daten beziehen. Der Azure Rights Management-Dienst (Azure RMS) stellt die Technologie zum Schutz von Daten für Azure Information Protection bereit. Azure RMS kann zusammen mit einer Klassifizierung oder Bezeichnung verwendet werden. Es kann aber auch eigenständig genutzt werden. 

- [Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen](faqs-infoprotect.md)

- [Häufig gestellte Fragen zum Schutz von Daten](faqs-rms.md)

Wenn Ihre Frage hier nicht beantwortet wird, verwenden Sie die Links und Ressourcen, die unter [Informationen zu und Unterstützung von Azure Information Protection](information-support.md) aufgelistet sind.

Darüber hinaus gibt es häufig gestellte Fragen (FAQs) für Benutzer:

- [Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android](./rms-client/mobile-app-faq.md)

- [Häufig gestellte Fragen (FAQ) zur RMS-Freigabeanwendung für Mac-Computer](https://technet.microsoft.com/dn451248)

