---
title: Häufig gestellte Fragen zu Azure Information Protection
description: Some frequently asked questions about Azure Information Protection and its protection service, Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: f4583260708267575f35d4c67d6cd2afc5add68d
ms.sourcegitcommit: fed1df1858f8316f7dd45e751c6910b444651a87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474337"
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

Announced at Microsoft Ignite 2018 in Orlando, you now have an option to create and configure [sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) in addition to retention labels in one of the admin centers: The Office 365 Security & Compliance Center, the Microsoft 365 security center, or the Microsoft 365 compliance center. You can migrate your existing Azure Information Protection labels to the new unified labeling store, to be used as sensitivity labels with Office apps. 

Weitere Informationen zum Verwalten einheitlicher Bezeichnungen und deren Unterstützung finden Sie im Blogbeitrag [Bekanntgabe der Verfügbarkeit von Information Protection-Funktionen zum Schutz von vertraulichen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

For more information about migrating your existing labels, see [How to migrate Azure Information Protection labels to unified sensitivity labels](configure-policy-migrate-labels.md).

## <a name="how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform"></a>How can I determine if my tenant is on the unified labeling platform?

When your tenant is on the unified labeling platform, sensitivity labels can be used by [clients and services that support unified labeling](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling). If you obtained your subscription for Azure Information Protection in June 2019 or later, your tenant is automatically on the unified labeling platform and no further action is needed. Your tenant might also be on this platform because somebody migrated your Azure Information Protection labels.

To check the status, in the Azure portal, go to **Azure Information Protection** > **Manage** > **Unified labeling**, and view the status of **Unified labeling**:

- If you see **Activated**, your tenant is on the unified labeling platform.

- If you see **Not activated**, your tenant is not on the unified labeling platform. For migration instructions, see [How to migrate Azure Information Protection labels to unified sensitivity labels](configure-policy-migrate-labels.md).

## <a name="whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client"></a>What's the difference between the Azure Information Protection client and the Azure Information Protection unified labeling client?

The **Azure Information Protection client (classic)** has been available since Azure Information Protection was first announced as a new service for classifying and protecting files and emails. This client downloads labels and policy settings from Azure, and you configure the Azure Information Protection policy from the Azure portal. For more information, see [Overview of the Azure Information Protection policy](overview-policy.md). 

The **Azure Information Protection unified labeling client** is a more recent addition, to support the unified labeling store that multiple applications and services support. This client downloads sensitivity labels and policy settings from the following admin centers: The Office 365 Security & Compliance Center, the Microsoft 365 security center, and the Microsoft 365 compliance center. For more information, see [Overview of sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels).

If you're not sure which client to use, see [Choose which Azure Information Protection client to use](./rms-client/use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

### <a name="identify-which-client-you-have-installed"></a>Identify which client you have installed

Both clients, when they are installed, display **Azure Information Protection**. To help you identify which client you have installed, use the **Help and feedback** option to open the **Microsoft Azure Information Protection** dialog box:

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und dann **Hilfe und Feedback** aus.

- From an Office application: From the **Protect** button (the classic client) or **Sensitivity** button (unified labeling client), select **Help and Feedback**.

Use the **Version** number displayed to identify the client:

- A version **1**, for example, **1.53.10.0**, identifies the Azure Information Protection client (classic).

- A version **2**, for example, **2.2.14.0**, identifies the Azure Information Protection unified labeling client.

## <a name="when-is-the-right-time-to-migrate-my-labels"></a>When is the right time to migrate my labels?

Now that the option to migrate labels in the Azure portal is in general availability, we recommend you activate the migration so that you can use your labels as sensitivity labels with [clients and services that support unified labeling](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

For more information and instructions, see [How to migrate Azure Information Protection labels to unified sensitivity labels](configure-policy-migrate-labels.md).

## <a name="after-ive-migrated-my-labels-which-management-portal-do-i-use"></a>Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?

Nachdem Sie Ihre Bezeichnungen im Azure-Portal migriert haben:

- If you have [unified labeling clients and services](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling), go to one of the admin centers (Office 365 Security & Compliance Center, Microsoft 365 security center, or Microsoft 365 compliance center) to publish these labels, and to configure their policy settings. Für zukünftige Bezeichnungsänderungen verwenden Sie eines dieser Admin-Centers. Die Bezeichnungen und Richtlinieneinstellungen werden von Clients für einheitliche Bezeichnungen aus diesen Admin-Centers heruntergeladen.

- If you have the [Azure Information Protection client (classic)](./rms-client/aip-client.md), continue to use the Azure portal to edit your labels and policy settings. The classic client continues to download labels and policy settings from Azure.

- If you have both [unified labeling clients](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling) and [classic clients](./rms-client/aip-client.md), you can use the admin centers or the Azure portal to make label changes. However, for the classic clients to pick up the label changes that you make in the admin centers, you must return to the Azure portal: Use the **Publish** option from the **Azure Information Protection - Unified labeling** pane in the Azure portal. 

Verwenden Sie weiterhin das Azure-Portal für die [zentrale Berichterstellung](reports-aip.md) und die [Überprüfung](deploy-aip-scanner.md).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?

Azure Information Protection stellt Klassifizierungen, Bezeichnungen und den Schutz für Dokumente und E-Mails einer Organisation bereit. Die Schutztechnologie nutzt den Azure Rights Management-Dienst, der nun eine Komponente von Azure Information Protection ist.

## <a name="whats-the-role-of-identity-management-for-azure-information-protection"></a>What's the role of identity management for Azure Information Protection?

Benutzer benötigen einen gültigen Benutzernamen und ein Kennwort, um auf durch Azure Information Protection geschützte Inhalte zuzugreifen. Weitere Informationen zum Schutz Ihrer Daten mit Azure Information Protection finden Sie unter [Die Rolle von Azure Information Protection beim Schützen von Daten](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?

Informationen dazu finden Sie auf der [Preisseite von Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection).

Wenn Sie über ein Office 365-Abonnement verfügen, das Datenschutz mit Azure Rights Management umfasst, laden Sie das [Datenblatt zur Azure Information Protection-Lizenz](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) herunter.

Haben Sie noch Fragen zur Lizenzierung? Möglicherweise finden Sie passende Antworten im Abschnitt [Häufig gestellte Fragen zur Lizenzierung](https://azure.microsoft.com/pricing/details/information-protection#faq).

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Ist der Azure Information Protection-Client nur für Abonnements geeignet, die Funktionen für Klassifizierung und Bezeichnung umfassen?

Nein The Azure Information Protection client (classic) can also be used with subscriptions that include just the Azure Rights Management service to protect data.

When the classic client is installed and it doesn't have an Azure Information Protection policy, this client automatically operates in [protection-only mode](./rms-client/client-protection-only-mode.md). In diesem Modus können Benutzer problemlos Rights Management-Vorlagen und benutzerdefinierte Berechtigungen anwenden. Wenn Sie zu einem späteren Zeitpunkt ein Abonnement erwerben, das Klassifizierungen und Bezeichnungen umfasst, wechselt der Client beim Herunterladen der Azure Informationen Protection-Richtlinie automatisch in den Standardmodus.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?

Globale Administratoren für einen Office 365- oder Azure AD-Mandanten können alle administrativen Aufgaben für Azure Information Protection ausführen. Zum Zuweisen von Administratorrechten an andere Benutzer haben Sie folgende Optionen:

- **Azure Information Protection administrator**: This Azure Active Directory administrator role lets an administrator configure Azure Information Protection but not other services. Ein Administrator mit dieser Rolle kann den Azure Rights Management-Schutzdienst aktivieren und deaktivieren, Schutzeinstellungen und Bezeichnungen konfigurieren und die Azure Information Protection-Richtlinie konfigurieren. In addition, an administrator with this role can run all the PowerShell cmdlets for the [Azure Information Protection client](./rms-client/client-admin-guide-powershell.md) and from the [AIPService module](administer-powershell.md). However, this role doesn't support tracking and revoking documents for users.
    
    > [!NOTE]
    > This role is not supported in the Azure portal if your tenant is on the [unified labeling platform](#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform).
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- **Compliance administrator** or **Compliance data administrator**: These Azure Active Directory administrator roles let an administrator configure Azure Information Protection, which includes activate and deactivate the Azure Rights Management protection service, configure protection settings and labels, and configure the Azure Information Protection policy. In addition, an administrator with either of these roles can run all the PowerShell cmdlets for the [Azure Information Protection client](./rms-client/client-admin-guide-powershell.md) and from the [AIPService module](administer-powershell.md). However, these roles don't support tracking and revoking documents for users.
    
    To assign a user to one of these administrative roles, see [Assign a user to administrator roles in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). To see what other permissions a user with these roles have, see the [Available roles](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) section from the Azure Active Directory documentation.

- **Security reader** or **Global reader**: For [Azure Information Protection analytics](reports-aip.md) only. Mit dieser Azure Active Directory-Administratorrolle kann ein Administrator anzeigen, wie Ihre Bezeichnungen verwendet werden, den Benutzerzugriff auf gekennzeichnete Dokumente und E-Mails und alle Änderungen ihrer Klassifizierung überwachen sowie Dokumente erkennen, die vertrauliche Informationen enthalten, die geschützt werden müssen. Because this feature uses Azure Monitor, you must also have a supporting [RBAC role](reports-aip.md#permissions-required-for-azure-information-protection-analytics).
    
    > [!NOTE]
    > The Security reader and Global reader roles are not supported if your tenant is on the [unified labeling platform](#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform).

- **Security administrator**: This Azure Active Directory administrator role lets an administrator configure Azure Information Protection in the Azure portal, in addition to configuring some aspects of other Azure services. An administrator with this role cannot run any of the [PowerShell cmdlets from the AIPService module](administer-powershell.md), or track and revoke documents for users.
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Weitere Informationen zu den Berechtigungen, über die ein Benutzer mit dieser Rolle verfügt, finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

- Azure Rights Management **Global Administrator** and **Connector Administrator**: For these Azure Rights Management administrator roles, the first grants users permissions to run all [PowerShell cmdlets from the AIPService module](administer-powershell.md) without making them a global administrator for other cloud services, and the second role grants permissions to run only the Rights Management (RMS) connector. Neither of these administrative roles grant permissions to management consoles or tracking and revoking documents for users.
    
    To assign either of these administrative roles, use the AIPService PowerShell cmdlet, [Add-AipServiceRoleBasedAdministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator).

Einige Dinge sind zu beachten:

- Microsoft accounts are not supported for delegated administration of Azure Information Protection, even if these accounts are assigned to one of the administrative roles listed. 

- Wenn Sie [Onboardingsteuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, wird die Möglichkeit zum Verwalten von Azure Information Protection mit Ausnahme des RMS-Connectors durch diese Konfiguration nicht beeinflusst. Wenn sie Onboarding-Steuerelemente beispielsweise so konfiguriert haben, dass die Fähigkeit, Inhalte zu schützen, auf die Gruppe „IT-Abteilung“ beschränkt ist, muss das von Ihnen zum Installieren und Konfigurieren des RMS-Connectors verwendete Konto ein Member dieser Gruppe sein. 

- Benutzer, denen eine administrative Rolle zugewiesen wurde, können den Schutz von Dokumenten oder E-Mails nicht entfernen, die von Azure Information Protection geschützt wurden. Dies können nur Benutzer tun, denen Administratorrechte zugewiesen sind, wenn das Administratorfeature aktiviert ist. Allerdings kann jeder Benutzer, dem Sie Administratorberechtigungen für Azure Information Protection zugewiesen haben, anderen Benutzern Administratorrechte zuweisen, einschließlich ihres eigenen Kontos. Sie können auch das Superuserfeature aktivieren. Diese Aktionen werden in einem Administratorprotokoll aufgezeichnet. For more information, see the security best practices section in [Configuring super users for Azure Information Protection and discovery services or data recovery](configure-super-users.md). 

- If you are migrating your Azure Information Protection labels to the unified labeling store, be sure to read the following section from the label migration documentation: [Administrative roles that support the unified labeling platform](configure-policy-migrate-labels.md#administrative-roles-that-support-the-unified-labeling-platform).

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Unterstützt Azure Information Protection lokale und hybride Szenarios?

Ja. Obwohl Azure Information Protection eine cloudbasierte Lösung ist, können damit Dokumente und E-Mails, die sowohl lokal als auch in der Cloud gespeichert sind, klassifiziert, bezeichnet und geschützt werden.

Wenn Sie über Exchange Server, SharePoint Server und Windows-Dateiserver verfügen, können Sie den [Rights Management-Connector](deploy-rms-connector.md) bereitstellen, damit diese lokalen Server den Azure Rights Management-Dienst verwenden können, um Ihre E-Mails und Dokumente zu schützen. Sie können Ihre Active Directory-Domänencontroller auch mit Azure AD synchronisieren und zusammenführen, um eine nahtlosere Authentifizierung für Benutzer zu erreichen. Dazu können Sie beispielsweise [Azure AD Connect](/azure/active-directory/hybrid/whatis-azure-ad-connect) verwenden.

Der Azure Rights Management-Dienst generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf und verwendet daher keine lokale PKI. Weitere Informationen zur Verwendung von Zertifikaten in Azure Rights Management finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsnutzung](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) des Artikels [Funktionsweise von Azure RMS](./how-does-it-work.md).

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Welche Arten von Daten können von Azure Information Protection klassifiziert und geschützt werden?

Azure Information Protection kann E-Mails und Dokumente klassifizieren und schützen, egal ob sie lokal oder in der Cloud gespeichert sind. Diese Dokumente können z.B. Word-Dokumente, Excel-Tabellen, PowerPoint-Präsentationen, PDF-Dokumente, textbasierte Dateien und Bilddateien sein. Eine Liste der unterstützten Dokumenttypen finden Sie in der Liste der [unterstützten Dateitypen](./rms-client/clientv2-admin-guide-file-types.md) im Administratorleitfaden.

Azure Information Protection cannot classify and protect structured data such as database files, calendar items, Yammer posts, Sway content, and OneNote notebooks.

**Newly announced in preview**: Power BI now supports classification by using sensitivity labels and can apply protection from those labels to data that is exported to the following file formats: .pdf, .xls, and .ppt. For more information, see [Data protection in Power BI (preview)](https://docs.microsoft.com/power-bi/admin/service-security-data-protection-overview).

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?

Das ist richtig. Für die Vorschauversion wird jetzt angeboten, bedingten Zugriff auf Azure AD für Azure Information Protection zu konfigurieren.

Wenn ein Benutzer ein durch Azure Information Protection geschütztes Dokument öffnet, können Administratoren jetzt basierend auf der bedingten Standardzugriffssteuerung Benutzern den Zugriff in ihrem Mandanten verweigern oder gewähren. Die mehrstufige Authentifizierung (MFA) ist eine der am häufigsten verlangten Bedingungen. Eine weitere ist, dass Geräte [mit Ihren Intune-Richtlinien kompatibel](/intune/conditional-access-intune-common-ways-use) sein müssen, damit Mobilgeräte zum Beispiel Ihren Kennwortanforderungen entsprechen, und eine Minimalversion eines Betriebssystems sowie Computer müssen mit einer Domäne verbunden sein.

Weitere Informationen und einige detaillierte Beispiele finden Sie in dem folgenden Blogbeitrag: [Conditional Access policies for Azure Information Protection (Richtlinien zum bedingten Zugriff für Azure Information Protection)](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Zusätzliche Informationen:

- Für Windows-Computer: Die Richtlinien zum bedingten Zugriff für Azure Information Protection werden in der aktuellen Vorschauversion geprüft, wenn die [Benutzerumgebung initialisiert wird](./how-does-it-work.md#initializing-the-user-environment) (dieser Vorgang wird auch als Bootstrapping bezeichnet). Danach wird alle 30 Tage eine Prüfung durchgeführt.

- Möglicherweise möchten Sie näher bestimmen, wie oft Ihre Richtlinien zum bedingten Zugriff geprüft werden. Konfigurieren Sie dazu die Tokengültigkeitsdauer. Weitere Informationen finden Sie unter [Konfigurierbare Tokengültigkeitsdauern in Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- We recommend that you do not add administrator accounts to your conditional access policies because these accounts will not be able to access the Azure Information Protection pane in the Azure portal.

- Wenn Sie MFA in Ihren Richtlinien für bedingten Zugriff für die Zusammenarbeit mit anderen Unternehmen (B2B) verwenden, müssen Sie [Azure AD B2B-Zusammenarbeit](/azure/active-directory/b2b/what-is-b2b) verwenden und Gastkonten für die Benutzer erstellen, mit denen Sie in dem anderen Unternehmen zusammenarbeiten möchten.

- Mit der Vorschauversion für Azure AD, die im Dezember 2018 veröffentlicht wurde, können Sie jetzt Benutzer auffordern, Nutzungsbedingungen zu akzeptieren, bevor sie ein ungeschütztes Dokument zum ersten Mal öffnen. For more information, see the following blog post announcement: [Updates to Azure AD Terms of Use functionality within conditional access](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Updates-to-Azure-AD-Terms-of-Use-functionality-within/ba-p/294822)

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

There is a difference in setting the [Rights Management owner](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) for files that are protected on a local folder or network share. Standardmäßig wird für beide Lösungen der Rights Management-Besitzer für das Konto festgelegt, das die Datei schützt. Sie können diese Einstellung aber auch außer Kraft setzen:

- Für die Windows-Dateiklassifizierungsinfrastruktur: Sie können festlegen, dass alle Dateien einen einzigen Rights Management-Besitzer haben, oder Sie können den Rights Management-Besitzer für jede Datei dynamisch festlegen. Um den Rights Management-Besitzer dynamisch festzulegen, verwenden Sie den Parameter **-OwnerMail [Source File Owner Email]** und seinen Wert. Durch diese Konfiguration wird die E-Mail-Adresse des Benutzers von Active Directory mithilfe des Benutzerkontonamens in der Owner-Eigenschaft der Datei abgerufen.

- For the Azure Information Protection scanner: For newly protected files, you can set the Rights Management owner to be a single account for all files on a specified data store, but you cannot dynamically set the Rights Management owner for each file. Der Rights Management-Besitzer wird für Dateien, die bereits vorher geschützt wurden, nicht geändert. Geben Sie zum Festlegen des Kontos für neu geschützte Dateien die Einstellung **-Default owner** (-Standardbesitzer) im Scannerprofil an. 

Wenn der Scanner Dateien auf Websites und in Bibliotheken von SharePoint schützt, wird der Rights Management-Besitzer dynamisch für jede Datei mithilfe des SharePoint-Editorwerts festgelegt.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Ich habe gehört, dass bald eine neue Version von Azure Information Protection verfügbar sein wird. Wann wird diese veröffentlicht?

Die technische Dokumentation enthält keine Informationen zu bevorstehenden Releases. For this type of information, use the [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?&filters=Azure%20Information%20Protection%2CO365%20Information%20Protection#owRoadmapMainContent), check the [Enterprise Mobility + Security Blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Ist Azure Information Protection für mein Land geeignet?

Verschiedene Länder haben unterschiedliche Anforderungen und Bestimmungen. Auf der Seite [Suitability for different countries (Eignung für unterschiedliche Länder)](./compliance.md#suitability-for-different-countries) finden Sie Antworten zu den Fragen für Ihre Organisation.

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Wie kann Azure Information Protection bei der Datenschutz-Grundverordnung (DSGVO) helfen?

In der Blogbeitragsankündigung [Microsoft 365 provides an information protection strategy to help with the GDPR (Microsoft 365 stellt eine Datenschutzstrategie zur Unterstützung mit der DSGVO bereit)](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr) (mit Video) finden Sie Informationen darüber, wie Azure Information Protection Ihnen bei der Umsetzung der Datenschutz-Grundverordnung (DSGVO) helfen kann.

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

