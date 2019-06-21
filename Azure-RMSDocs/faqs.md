---
title: Häufig gestellte Fragen zu Azure Information Protection
description: Hier finden Sie einige häufig gestellte Fragen zu Azure Information Protection und dem zugehörigen Dienst zum Schutz von Daten, Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/21/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: 1e0933a88afc355dbcbab0dc667e28f49f10c0b9
ms.sourcegitcommit: 599306e271392afa4bc05c87982549785ce1860e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2019
ms.locfileid: "67305777"
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

Wie auf der Microsoft Ignite 2018 in Orlando angekündigt, ist nun eine Option zum Erstellen und Konfigurieren von [Vertraulichkeitsbezeichnungen](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) zusätzlich zu den Aufbewahrungsbezeichnungen in einem der Admin-Centers verfügbar: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, oder das Microsoft 365 Compliance Center. Sie können Ihre vorhandenen Azure Information Protection migrieren, Bezeichnungen, um die neue einheitliche Bezeichnungen speichern als vertraulichkeitsbezeichnungen mit Office 365 verwendet werden soll. 

Weitere Informationen zum Verwalten einheitlicher Bezeichnungen und deren Unterstützung finden Sie im Blogbeitrag [Bekanntgabe der Verfügbarkeit von Information Protection-Funktionen zum Schutz von vertraulichen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

Weitere Information zum Migrieren vorhandener Bezeichnungen erwarten Sie unter [Migrieren von Azure Information Protection-Bezeichnungen zu Office 365](configure-policy-migrate-labels.md).

## <a name="whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client"></a>Was ist der Unterschied zwischen dem Azure Information Protection-Client und die Azure Information Protection unified bezeichnungs-Client?

Die **Azure Information Protection-Client (klassisch)** ist seit verfügbar, da Azure Information Protection als einen neuen Dienst zum Klassifizieren und Schützen von Dateien und e-Mails erstmals angekündigt wurde. Dieser Client wird Bezeichnungen und Einstellungen von Azure heruntergeladen, und konfigurieren Sie die Azure Information Protection-Richtlinie im Azure-Portal. Weitere Informationen finden Sie unter [Überblick über die Azure Information Protection-Richtlinie](overview-policy.md). 

Die **Azure Information Protection – einheitliche bezeichnungs Client** ist eine neuere Ergänzung, Unterstützung für die die einheitliche Bezeichnung speichern, mehrere Anwendungen und Dienste unterstützen. Dieser Client downloads vertraulichkeitsbezeichnungen Einstellungen und Richtlinien aus den folgenden Admin Center: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, und das Microsoft 365 Compliance Center. Weitere Informationen finden Sie unter [Überblick über die vertraulichkeitsbezeichnungen](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels).

Wenn Sie nicht sicher, welche Client zur Verwendung sind, finden Sie unter [Auswählen der zu verwendenden Azure Information Protection Client](./rms-client/use-client.md#choose-which-azure-information-protection-client-to-use).

### <a name="identify-which-client-you-have-installed"></a>Identifizieren Sie die Clients, die Sie installiert haben

Beide Clients, wenn sie installiert sind, zeigt **Azure Information Protection**. Um zu identifizieren, welche Clients Sie installiert haben, verwenden die **Hilfe und Feedback** Option zum Öffnen der **Microsoft Azure Information Protection** Dialogfeld:

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und anschließend **Hilfe und Feedback** aus.

- Aus einer officeanwendung: Von der **schützen** Schaltfläche (klassische Client) oder **Vertraulichkeit** Schaltfläche (einheitliche bezeichnungs-Client), wählen **Hilfe und Feedback**.

Verwenden der **Version** Anzahl angezeigt, um den Client zu identifizieren:

- Eine Version **1**, z. B. **1.48.204.0**, wird vom Azure Information Protection-Client (klassisch) identifiziert.

- Eine Version **2**, z. B. **2.0.778.0**, wird vom Azure Information Protection unified bezeichnungs-Client identifiziert.

## <a name="when-is-the-right-time-to-migrate-my-labels-to-office-365"></a>Wann ist der richtige Zeitpunkt, um meine Bezeichnungen zu Office 365 zu migrieren?

Nun, da die Option zum Migrieren von Bezeichnungen im Azure-Portal im allgemeinen Verfügbarkeit ist, es wird empfohlen, damit Sie Ihre Bezeichnungen als vertraulichkeitsbezeichnungen mit verwenden können, aktivieren die Migration [Clients und Diensten, die Unterstützung für die einheitliche Bezeichnung](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling) .

Weitere Informationen und Anweisungen hierzu finden Sie unter [Migrieren von Azure Information Protection-Bezeichnungen zu Office 365-vertraulichkeitsbezeichnungen](configure-policy-migrate-labels.md).

## <a name="after-ive-migrated-my-labels-which-management-portal-do-i-use"></a>Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?

Nachdem Sie Ihre Bezeichnungen im Azure-Portal migriert haben:

- Wenn man [unified bezeichnen, Clients und Diensten](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling), wechseln Sie zu der die Admin Center (Office 365 Security & Compliance Center, Microsoft 365-Security-Center oder Microsoft 365 Compliance Center) diese Bezeichnungen zu veröffentlichen und zu Konfigurieren Sie ihre Richtlinieneinstellungen. Für zukünftige Bezeichnungsänderungen verwenden Sie eines dieser Admin-Centers. Die Bezeichnungen und Richtlinieneinstellungen werden von Clients für einheitliche Bezeichnungen aus diesen Admin-Centers heruntergeladen.

- Wenn Sie über [Azure Information Protection-Clients](./rms-client/aip-client.md) verfügen, verwenden Sie zur Bearbeitung Ihrer Bezeichnungen und Richtlinieneinstellungen weiter das Azure-Portal. Azure Information Protection-Clients werden weiterhin die Bezeichnungen und Richtlinieneinstellungen aus Azure herunterladen.

- Wenn Sie sowohl über [Clients für einheitliche Bezeichnungen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling) als auch über [Azure Information Protection-Clients](./rms-client/aip-client.md) verfügen, können Sie die Admin-Centers oder das Azure-Portal verwenden, um Bezeichnungsänderungen vorzunehmen. Damit jedoch Azure Information Protection-Clients die von Ihnen in den Admin-Centers vorgenommenen Bezeichnungsänderungen übernehmen, müssen Sie wieder das Azure-Portal verwenden: Verwenden Sie die Option **Veröffentlichen** auf dem Blatt **Azure Information Protection - Unified labeling** (Azure Information Protection – einheitliche Bezeichnungen) im Azure-Portal. 

Verwenden Sie weiterhin das Azure-Portal für die [zentrale Berichterstellung](reports-aip.md) und die [Überprüfung](deploy-aip-scanner.md).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?

Azure Information Protection stellt Klassifizierungen, Bezeichnungen und den Schutz für Dokumente und E-Mails einer Organisation bereit. Die Schutztechnologie nutzt den Azure Rights Management-Dienst, der nun eine Komponente von Azure Information Protection ist.

## <a name="whats-the-role-of-identity-management-for-azure-information-protection"></a>Was ist die Rolle des Identitätsmanagement für Azure Information Protection?

Benutzer benötigen einen gültigen Benutzernamen und ein Kennwort, um auf durch Azure Information Protection geschützte Inhalte zuzugreifen. Weitere Informationen zum Schutz Ihrer Daten mit Azure Information Protection finden Sie unter [Die Rolle von Azure Information Protection beim Schützen von Daten](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?

Informationen dazu finden Sie auf der [Preisseite von Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection).

Wenn Sie über ein Office 365-Abonnement verfügen, das Datenschutz mit Azure Rights Management umfasst, laden Sie das [Datenblatt zur Azure Information Protection-Lizenz](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) herunter.

Haben Sie noch Fragen zur Lizenzierung? Möglicherweise finden Sie passende Antworten im Abschnitt [Häufig gestellte Fragen zur Lizenzierung](https://azure.microsoft.com/pricing/details/information-protection#faq).

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Ist der Azure Information Protection-Client nur für Abonnements geeignet, die Funktionen für Klassifizierung und Bezeichnung umfassen?

Nein. Zwar wird bei den meisten Präsentationen und Demos zum Azure Information Protection-Client gezeigt, wie dieser Klassifizierungen und Bezeichnungen unterstützt, Sie können den Client aber auch in Abonnements verwenden, die zum Datenschutz lediglich den Azure Rights Management-Dienst enthalten.

Wenn der Azure Information Protection-Client für Windows installiert ist, aber keine Azure Information Protection-Richtlinie vorhanden ist, wird der Client automatisch im [reinen Schutzmodus](./rms-client/client-protection-only-mode.md) betrieben. In diesem Modus können Benutzer problemlos Rights Management-Vorlagen und benutzerdefinierte Berechtigungen anwenden. Wenn Sie zu einem späteren Zeitpunkt ein Abonnement erwerben, das Klassifizierungen und Bezeichnungen umfasst, wechselt der Client beim Herunterladen der Azure Informationen Protection-Richtlinie automatisch in den Standardmodus.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?

Globale Administratoren für einen Office 365- oder Azure AD-Mandanten können alle administrativen Aufgaben für Azure Information Protection ausführen. Zum Zuweisen von Administratorrechten an andere Benutzer haben Sie folgende Optionen:

- **Azure Information Protection-Administrator**: Diese Azure Active Directory-Administrator-Rolle kann es sich um ein Administrator mit dem Azure Information Protection, aber nicht für andere Dienste zu konfigurieren. Ein Administrator mit dieser Rolle kann den Azure Rights Management-Schutzdienst aktivieren und deaktivieren, Schutzeinstellungen und Bezeichnungen konfigurieren und die Azure Information Protection-Richtlinie konfigurieren. Zusätzlich kann ein Administrator mit dieser Rolle alle PowerShell-Cmdlets für den [Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md) und aus dem [AADRM-Modul](administer-powershell.md) ausführen. Diese Rolle unterstützt jedoch nicht nachverfolgen und Sperren von Dokumenten für Benutzer.
    
    > [!NOTE]
    > Nachdem Sie [Ihren Mandanten zum Speicher für einheitliche Bezeichnungen migriert haben](configure-policy-migrate-labels.md), wird diese Rolle für das Azure-Portal nicht mehr unterstützt.
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- **Complianceadministrator** oder **Daten complianceadministrator**: Diese Azure Active Directory-Administratorrollen können einen Administrator konfigurieren Sie Azure Information Protection, einschließlich aktivieren und deaktivieren Sie den Azure Rights Management-Datenschutzdienst, schutzeinstellungen und Bezeichnungen und konfigurieren Sie die Azure Information Protection-Richtlinie. Darüber hinaus kann ein Administrator mit einer dieser Rollen ausführen alle PowerShell-Cmdlets für die [Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md) und von der [AADRM-Modul](administer-powershell.md). Diese Rollen unterstützen jedoch nicht nachverfolgen und Sperren von Dokumenten für Benutzer.
    
    Um einem Benutzer eine dieser Administratorrollen zuzuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Um anzuzeigen, was andere Berechtigungen ein Benutzer sich bei diesen Rollen haben, finden Sie unter den [verfügbaren Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) Abschnitt in der Azure Active Directory-Dokumentation.

- **Sicherheitsleseberechtigter**: Nur für [Azure Information Protection-Analysen](reports-aip.md). Mit dieser Azure Active Directory-Administratorrolle kann ein Administrator anzeigen, wie Ihre Bezeichnungen verwendet werden, den Benutzerzugriff auf gekennzeichnete Dokumente und E-Mails und alle Änderungen ihrer Klassifizierung überwachen sowie Dokumente erkennen, die vertrauliche Informationen enthalten, die geschützt werden müssen. Da dieses Feature Azure Log Analytics verwendet, benötigen Sie außerdem eine unterstützende [RBAC-Rolle](reports-aip.md#permissions-required-for-azure-information-protection-analytics).

- **Sicherheitsadministrator**: Diese Azure Active Directory-Administrator-Rolle kann es sich um ein Administrator mit dem Azure Information Protection im Azure-Portal sowie einige Aspekte anderer Azure-Dienste zu konfigurieren. Ein Administrator mit dieser Rolle kann nicht ausgeführt, eines der [PowerShell-Cmdlets aus dem AADRM-Modul](administer-powershell.md), oder Nachverfolgen und Widerrufen von Dokumenten für Benutzer.
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Weitere Informationen zu den Berechtigungen, über die ein Benutzer mit dieser Rolle verfügt, finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

- **Globaler Administrator** und **Connector-Administrator** von Azure Rights Management: Bei diesen Administratorrollen von Azure Rights Management gewährt die erste Rolle dem Benutzer die Berechtigung, alle [PowerShell-Cmdlets aus dem AADRM-Modul](administer-powershell.md) auszuführen, ohne ihm die globalen Administratorrechte für andere Clouddienste zuzuweisen, und die zweite Rolle gewährt Rechte, nur den RMS-Connector (Rights Management) auszuführen. Weder dieser Administratorrollen Gewähren von Berechtigungen für die Verwaltungskonsolen oder Nachverfolgen und Sperren von Dokumenten für Benutzer zu unterstützen.

    Verwenden Sie das AADRM-PowerShell-Cmdlet [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator), um eine dieser Administratorrollen zuzuweisen.

Einige Dinge sind zu beachten:

- Wenn Sie [Onboardingsteuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, wird die Möglichkeit zum Verwalten von Azure Information Protection mit Ausnahme des RMS-Connectors durch diese Konfiguration nicht beeinflusst. Wenn sie Onboarding-Steuerelemente beispielsweise so konfiguriert haben, dass die Fähigkeit, Inhalte zu schützen, auf die Gruppe „IT-Abteilung“ beschränkt ist, muss das von Ihnen zum Installieren und Konfigurieren des RMS-Connectors verwendete Konto ein Member dieser Gruppe sein. 

- Benutzer, denen eine administrative Rolle zugewiesen wurde, können den Schutz von Dokumenten oder E-Mails nicht entfernen, die von Azure Information Protection geschützt wurden. Dies können nur Benutzer tun, denen Administratorrechte zugewiesen sind, wenn das Administratorfeature aktiviert ist. Allerdings kann jeder Benutzer, dem Sie Administratorberechtigungen für Azure Information Protection zugewiesen haben, anderen Benutzern Administratorrechte zuweisen, einschließlich ihres eigenen Kontos. Sie können auch das Superuserfeature aktivieren. Diese Aktionen werden in einem Administratorprotokoll aufgezeichnet. Weitere Informationen finden Sie im Abschnitt „Bewährte Sicherheitsmethoden“ unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](configure-super-users.md). 

- Wenn Sie Ihre Azure Information Protection-Bezeichnungen in den einheitlichen bezeichnungs Speicher migrieren, achten Sie darauf, dass Sie im folgenden Abschnitt in der Dokumentation zur Migration Bezeichnung zu lesen: [Wichtige Informationen zu Administratorrollen.](configure-policy-migrate-labels.md#important-information-about-administrative-roles)

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Unterstützt Azure Information Protection lokale und hybride Szenarios?

Ja. Obwohl Azure Information Protection eine cloudbasierte Lösung ist, können damit Dokumente und E-Mails, die sowohl lokal als auch in der Cloud gespeichert sind, klassifiziert, bezeichnet und geschützt werden.

Wenn Sie über Exchange Server, SharePoint Server und Windows-Dateiserver verfügen, können Sie den [Rights Management-Connector](deploy-rms-connector.md) bereitstellen, damit diese lokalen Server den Azure Rights Management-Dienst verwenden können, um Ihre E-Mails und Dokumente zu schützen. Sie können Ihre Active Directory-Domänencontroller auch mit Azure AD synchronisieren und zusammenführen, um eine nahtlosere Authentifizierung für Benutzer zu erreichen. Dazu können Sie beispielsweise [Azure AD Connect](/azure/active-directory/hybrid/whatis-azure-ad-connect) verwenden.

Der Azure Rights Management-Dienst generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf und verwendet daher keine lokale PKI. Weitere Informationen dazu, wie Azure Rights Management Zertifikate verwendet, finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsaufnahme](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) im Artikel [Funktionsweise von Azure RMS](./how-does-it-work.md).

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Welche Arten von Daten können von Azure Information Protection klassifiziert und geschützt werden?

Azure Information Protection kann E-Mails und Dokumente klassifizieren und schützen, egal ob sie lokal oder in der Cloud gespeichert sind. Diese Dokumente können z.B. Word-Dokumente, Excel-Tabellen, PowerPoint-Präsentationen, PDF-Dokumente, textbasierte Dateien und Bilddateien sein. Eine Liste der unterstützten Dokumenttypen finden Sie in der Liste der [unterstützten Dateitypen](./rms-client/client-admin-guide-file-types.md) im Administratorleitfaden.

Azure Information Protection kann nicht klassifizieren und schützen strukturierte Daten wie z. B. Datenbankdateien, Kalendereinträge, Power BI-Berichte, Yammer-Beiträge, Sway-Inhalte und OneNote-Notizbücher.

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

Derzeit besteht ein Unterschied beim Festlegen des [Rights Management-Besitzers](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) für Dateien, die in einem lokalen Ordner oder einer Netzwerkfreigabe geschützt sind. Standardmäßig wird für beide Lösungen der Rights Management-Besitzer für das Konto festgelegt, das die Datei schützt. Sie können diese Einstellung aber auch außer Kraft setzen:

- Für die Windows Server-Dateiklassifizierungsinfrastruktur: Sie können festlegen, dass alle Dateien einen einzigen Rights Management-Besitzer haben, oder Sie können den Rights Management-Besitzer für jede Datei dynamisch festlegen. Um den Rights Management-Besitzer dynamisch festzulegen, verwenden Sie den Parameter **-OwnerMail [Source File Owner Email]** und seinen Wert. Durch diese Konfiguration wird die E-Mail-Adresse des Benutzers von Active Directory mithilfe des Benutzerkontonamens in der Owner-Eigenschaft der Datei abgerufen.

- Für die Azure Information Protection-Überprüfung: Sie können für erst seit Kurzem geschützte Dateien festlegen, dass alle Dateien in einem angegebenen Datenspeicher einen einzigen Rights Management-Besitzer haben, aber Sie können diesen nicht für jede Datei dynamisch festlegen. Der Rights Management-Besitzer wird für Dateien, die bereits vorher geschützt wurden, nicht geändert. Geben Sie zum Festlegen des Kontos für neu geschützte Dateien die Einstellung **-Default owner** (-Standardbesitzer) im Scannerprofil an. 

Wenn der Scanner Dateien auf Websites und in Bibliotheken von SharePoint schützt, wird der Rights Management-Besitzer dynamisch für jede Datei mithilfe des SharePoint-Editorwerts festgelegt.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Ich habe gehört, dass bald eine neue Version von Azure Information Protection verfügbar sein wird. Wann wird diese veröffentlicht?

Die technische Dokumentation enthält keine Informationen zu bevorstehenden Releases. Solche Informationen sowie Releaseankündigungen finden Sie im Blog [Enterprise Mobility + Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services).

Wenn Sie sich für ein bestimmtes Office-Release interessieren, lesen Sie auch den [Office 365-Blog](https://techcommunity.microsoft.com/t5/Office-365-Blog/bg-p/Office365Blog) und den [Office-Apps-Blog](https://techcommunity.microsoft.com/t5/Office-Apps-Blog/bg-p/OfficeAppsBlog).

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

