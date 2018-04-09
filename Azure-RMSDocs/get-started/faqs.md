---
title: Häufig gestellte Fragen zu Azure Information Protection
description: Hier finden Sie einige häufig gestellte Fragen zu Azure Information Protection und dem zugehörigen Dienst zum Schutz von Daten, Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/03/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 37619ad71fea842617556219c1684a3e837c3cc7
ms.sourcegitcommit: 3af39b88d321d75038caad266e906f6e622011d9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2018
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Häufig gestellte Fragen zu Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Haben Sie eine Frage zu Azure Information Protection oder zum Azure Rights Management-Dienst (Azure RMS)? Vielleicht finden Sie hier eine Antwort darauf.

Diese Seiten mit häufig gestellten Fragen werden regelmäßig aktualisiert. Dabei werden die neuen Beiträge in den Ankündigungen zu den monatlichen Dokumentationsupdates im [Azure Information Protection-Blog](https://aka.ms/AIPblog) aufgelistet.

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?

Azure Information Protection stellt Klassifizierungen, Bezeichnungen und den Schutz für Dokumente und E-Mails einer Organisation bereit. Die Schutztechnologie nutzt den Azure Rights Management-Dienst, der nun eine Komponente von Azure Information Protection ist.

## <a name="what-is-the-role-of-identity-management-for-azure-information-protection"></a>Welche Rolle spielt das Identitätsmanagement für Azure Information Protection?

Benutzer benötigen einen gültigen Benutzernamen und ein Kennwort, um auf durch Azure Information Protection geschützte Inhalte zuzugreifen. Weitere Informationen zum Schutz Ihrer Daten mit Azure Information Protection finden Sie unter [Die Rolle von Azure Information Protection beim Schützen von Daten](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?
Informationen dazu finden Sie auf der [Preisseite von Azure Information Protection](https://azure.microsoft.com/en-us/pricing/details/information-protection). 

Wenn Sie ein Office 365-Abonnement mit Azure Rights Management haben, laden Sie das [Datenblatt zur Azure Information Protection-Lizenz](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) herunter, das auch Antworten auf einige häufig gestellte Fragen zur Lizenzierung enthält.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Ist der Azure Information Protection-Client nur für Abonnements geeignet, die Funktionen für Klassifizierung und Bezeichnung umfassen?

Nein. Zwar wird bei den meisten Präsentationen und Demos zum Azure Information Protection-Client gezeigt, wie dieser Klassifizierungen und Bezeichnungen unterstützt, Sie können den Client aber auch in Abonnements verwenden, die zum Datenschutz lediglich den Azure Rights Management-Dienst enthalten.

Wenn der Azure Information Protection-Client für Windows installiert ist, aber keine Azure Information Protection-Richtlinie vorhanden ist, wird der Client automatisch im [reinen Schutzmodus](../rms-client/client-protection-only-mode.md) betrieben. In diesem Modus können Benutzer problemlos Rights Management-Vorlagen und benutzerdefinierte Berechtigungen anwenden. Wenn Sie zu einem späteren Zeitpunkt ein Abonnement erwerben, das Klassifizierungen und Bezeichnungen umfasst, wechselt der Client beim Herunterladen der Azure Informationen Protection-Richtlinie automatisch in den Standardmodus.

Wenn Sie zurzeit die Rights Management-Freigabeanwendung für Windows verwenden, wird empfohlen, diese Anwendung durch den Azure Information Protection-Client zu ersetzen. Die Unterstützung für die Freigabeanwendung endet am 31. Januar 2019. Informationen zum Übergang finden Sie unter [Üblicherweise mit der RMS-Freigabeanwendung ausgeführte Aufgaben](../rms-client/upgrade-client-app.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?

Globale Administratoren für einen Office 365- oder Azure AD-Mandanten können alle administrativen Aufgaben für Azure Information Protection ausführen. Zum Zuweisen von Administratorrechten an andere Benutzer haben Sie folgende Optionen:

- **Information Protection-Administrator**: Diese Azure Active Directory-Administratorrolle erlaubt einem Administrator die Konfiguration aller Aspekte von Azure Information Protection, aber nicht das Konfigurieren anderer Dienste. Ein Administrator mit dieser Rolle kann den Azure Rights Management-Schutzdienst aktivieren und deaktivieren, Schutzeinstellungen und Bezeichnungen konfigurieren und die Azure Information Protection-Richtlinie konfigurieren. Zusätzlich kann ein Administrator mit dieser Rolle alle PowerShell-Cmdlets für den [Azure Information Protection-Client](../rms-client/client-admin-guide-powershell.md) und aus dem [AADRM-Modul](../deploy-use/administer-powershell.md) ausführen. 
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- **Sicherheitsadministrator**: Diese Azure Active Directory-Administratorrolle erlaubt einem Administrator, alle Aspekte von Azure Information Protection im Azure-Portal sowie einige Aspekte anderer Azure-Dienste zu konfigurieren. Ein Administrator mit dieser Rolle kann keine der [PowerShell-Cmdlets aus dem AADRM-Modul](../deploy-use/administer-powershell.md) ausführen.
    
    Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Weitere Informationen zu den Berechtigungen, über die ein Benutzer mit dieser Rolle verfügt, finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

- **Globaler Administrator** und **Connectoradministrator** von Azure Rights Management: Bei diesen Administratorrollen von Azure Rights Management gewährt die erste dem Benutzer die Berechtigung, alle [PowerShell-Cmdlets aus dem AADRM-Modul](../deploy-use/administer-powershell.md) auszuführen, ohne ihm die globalen Administratorrechte für andere Cloud Services zuzuweisen, und die zweite Rolle gewährt die Rechte, nur den RMS-Connector (Rights Management) auszuführen. Keine dieser beiden administrativen Rollen gewährt Rechte für die Verwaltungskonsolen.

    Verwenden Sie das AADRM-PowerShell-Cmdlet [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator), um eine dieser Administratorrollen zuzuweisen.

Einige Dinge sind zu beachten:

- Wenn Sie [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, wird die Möglichkeit zum Verwalten von Azure Information Protection mit Ausnahme des RMS-Connectors durch diese Konfiguration nicht beeinflusst. Wenn sie Onboarding-Steuerelemente beispielsweise so konfiguriert haben, dass die Fähigkeit, Inhalte zu schützen, auf die Gruppe „IT-Abteilung“ beschränkt ist, muss das von Ihnen zum Installieren und Konfigurieren des RMS-Connectors verwendete Konto ein Member dieser Gruppe sein. 

- Benutzer, denen eine administrative Rolle zugewiesen wurde, können den Schutz von Dokumenten oder E-Mails nicht entfernen, die von Azure Information Protection geschützt wurden. Dies können nur Benutzer tun, denen Administratorrechte zugewiesen sind, wenn das Administratorfeature aktiviert ist. Allerdings kann jeder Benutzer, dem Sie Administratorberechtigungen für Azure Information Protection zugewiesen haben, anderen Benutzern Administratorrechte zuweisen, einschließlich ihres eigenen Kontos. Sie können auch das Superuserfeature aktivieren. Diese Aktionen werden in einem Administratorprotokoll aufgezeichnet. Weitere Informationen finden Sie im Abschnitt „Bewährte Sicherheitsmethoden“ unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md). 


## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Unterstützt Azure Information Protection lokale und hybride Szenarios?

Ja. Obwohl Azure Information Protection eine cloudbasierte Lösung ist, können damit Dokumente und E-Mails, die sowohl lokal als auch in der Cloud gespeichert sind, klassifiziert, bezeichnet und geschützt werden.

Wenn Sie über Exchange Server, SharePoint Server und Windows-Dateiserver verfügen, können Sie den [Rights Management-Connector](../deploy-use/deploy-rms-connector.md) bereitstellen, damit diese lokalen Server den Azure Rights Management-Dienst verwenden können, um Ihre E-Mails und Dokumente zu schützen. Sie können Ihre Active Directory-Domänencontroller auch mit Azure AD synchronisieren und zusammenführen, um eine übergangslosere Authentifizierungshandhabung für Benutzer zu erreichen. Dazu können Sie beispielsweise [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)verwenden.

Der Azure Rights Management-Dienst generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf und verwendet daher keine lokale PKI. Weitere Informationen zur Verwendung von Zertifikaten in Azure Rights Management finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsnutzung](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) des Artikels [Funktionsweise von Azure RMS](../understand-explore/how-does-it-work.md).

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Welche Arten von Daten können von Azure Information Protection klassifiziert und geschützt werden?

Azure Information Protection kann E-Mails und Dokumente klassifizieren und schützen, egal ob sie lokal oder in der Cloud gespeichert sind. Diese Dokumente können z.B. Word-Dokumente, Excel-Tabellen, PowerPoint-Präsentationen, PDF-Dokumente, textbasierte Dateien und Bilddateien sein. Eine Liste der unterstützten Dokumenttypen finden Sie in der Liste der [unterstützten Dateitypen](../rms-client/client-admin-guide-file-types.md) im Administratorleitfaden.

Azure Information Protection kann strukturierte Daten, wie z.B. Datenbankdateien, Kalendereinträge, PowerBI-Berichte, Yammer-Beiträge, Sway-Inhalte und OneNote-Notizbücher nicht klassifizieren und schützen.

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?

Das ist richtig. Für die öffentliche Vorschauversion wird jetzt angeboten, bedingten Zugriff auf Azure AD für Azure Information Protection zu konfigurieren.

Wenn ein Benutzer ein durch Azure Information Protection geschütztes Dokument öffnet, können Administratoren jetzt basierend auf der bedingten Standardzugriffssteuerung Benutzern den Zugriff in ihrem Mandanten verweigern oder gewähren. Die mehrstufige Authentifizierung (MFA) ist eine der am häufigsten verlangten Bedingungen. Eine weitere ist, dass Geräte [mit Ihren Intune-Richtlinien kompatibel](/intune/conditional-access-intune-common-ways-use) sein müssen, damit Mobilgeräte zum Beispiel Ihren Kennwortanforderungen entsprechen, und eine Minimalversion eines Betriebssystems sowie Computer müssen mit einer Domäne verbunden sein.

Weitere Informationen und einige detaillierte Beispiele finden Sie in dem folgenden Blogbeitrag: [Conditional Access policies for Azure Information Protection (Richtlinien zum bedingten Zugriff für Azure Information Protection)](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Zusätzliche Informationen:

- Für Windows-Computer: Die Richtlinien zum bedingten Zugriff für Azure Information Protection werden in der aktuellen Vorschauversion geprüft, wenn die [Benutzerumgebung initialisiert wird](../understand-explore/how-does-it-work.md#initializing-the-user-environment) (dieser Vorgang wird auch als Bootstrapping bezeichnet). Danach wird alle 30 Tage eine Prüfung durchgeführt.

- Möglicherweise möchten Sie näher bestimmen, wie oft Ihre Richtlinien zum bedingten Zugriff geprüft werden. Konfigurieren Sie dazu die Tokengültigkeitsdauer. Weitere Informationen finden Sie unter [Konfigurierbare Tokengültigkeitsdauern in Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- Es wird empfohlen, dass Sie keine Administratorkonten zu Ihren Richtlinien zum bedingten Zugriff hinzufügen, da diese Konten nicht auf die Seite „Azure Information Protection“ im Azure-Portal zugreifen können.

- Wenn Sie für den bedingten Zugriff auf mehrere Cloud-Apps zurückgreifen, wird Ihnen unter Umständen **Microsoft Azure Information Protection** nicht in der Auswahlliste angezeigt. Verwenden Sie in diesem Fall das Suchfeld oben in der Liste. Geben Sie „Microsoft Azure Information Protection“ ein, um die verfügbaren Apps zu filtern. Sofern Sie über ein unterstütztes Abonnement verfügen, können Sie nun **Microsoft Azure Information Protection** auswählen. 

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>Was ist der Unterschied zwischen Bezeichnungen in Azure Information Protection und Office 365?

Durch Bezeichnungen in Azure Information Protection können Sie eine konsistente Klassifizierung und Schutzrichtlinie für lokale oder in der Cloud befindliche Dokumente und E-Mails anwenden. Diese Klassifizierung und der Schutz sind unabhängig davon, wo der Inhalt gespeichert ist und wie dieser verschoben wird. Durch [Bezeichnungen in Office 365 Security & Compliance](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) können Sie Dokumente und E-Mails für die Überwachung und die Aufbewahrung klassifizieren, wenn der Inhalt sich in den Office 365-Diensten befindet. 

Aktuell müssen Sie diese Bezeichnungen noch separat anwenden und verwalten, Microsoft arbeitet jedoch an einer umfassenden und einheitlichen Bezeichnungsstrategie für mehrere Dienste, einschließlich Azure Information Protection, Office 365, Microsoft Cloud App Security und Windows Information Protection. Sie haben womöglich gehört, dass diese Strategie als „Microsoft Information Protection“ (MIP) bezeichnet wird. Das gleiche Bezeichnungsschema und der gleiche Bezeichnungsspeicher werden auch für Softwareanbieter verfügbar sein. Weitere Informationen finden Sie im Blogbeitrag [Consistent labeling and protection policies coming to Office 365 and Azure Information Protection (Konsistente Bezeichnungs- und Schutzrichtlinien, die für Office 365 und Azure Information Protection veröffentlicht werden)](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Consistent-labeling-and-protection-policies-coming-to-Office-365/ba-p/161553).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>Was ist der Unterschied zwischen der Windows Server-Dateiklassifizierungsinfrastruktur und der Azure Information Protection-Überprüfung?

Sie konnten für einen gewissen Zeitraum die Windows Server-Dateiklassifizierungsinfrastruktur verwenden, um Dokumente zu klassifizieren und diese dann mithilfe des [Rights Management-Connectors](../deploy-use/deploy-rms-connector.md) (nur Office-Dokumente) oder einem [PowerShell-Skript](../rms-client/configure-fci.md) (alle Dateitypen) zu schützen. 

Sie können die [Azure Information Protection-Überprüfung](../deploy-use/deploy-aip-scanner.md) nun verwenden. Die Überprüfung nutzt den Azure Information Protection-Client und Ihre Azure Information Protection-Richtlinie, um Dokumente (alle Dateitypen) zu bezeichnen, sodass diese Dokumente alle klassifiziert und optional auch geschützt werden.

Zwischen den beiden Lösungen bestehen die folgenden wesentlichen Unterschiede:

|Windows Server-Dateiklassifizierungsinfrastruktur|Azure Information Protection-Überprüfung|
|--------------------------------|-------------------------------------|
|Unterstützte Datenspeicher: <br /><br />– Lokale Ordner unter Windows Server|Unterstützte Datenspeicher: <br /><br />– Lokale Ordner unter Windows Server<br /><br />– Windows-Dateifreigaben und Network Attached Storage<br /><br />– SharePoint Server 2016 und SharePoint Server 2013|
|Betriebsmodus: <br /><br />– Echtzeit|Betriebsmodus: <br /><br />– Füllt Datenspeicher automatisch auf. Dieser Zyklus kann einmal oder wiederholt ausgeführt werden|

Derzeit besteht ein Unterschied beim Festlegen des [Rights Management-Besitzers](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) für Dateien, die in einem lokalen Ordner oder einer Netzwerkfreigabe geschützt sind. Standardmäßig wird für beide Lösungen der Rights Management-Besitzer für das Konto festgelegt, das die Datei schützt. Sie können diese Einstellung aber auch außer Kraft setzen:

- Für die Windows-Dateiklassifizierungsinfrastruktur: Sie können festlegen, dass alle Dateien einen einzigen Rights Management-Besitzer haben, oder Sie können den Rights Management-Besitzer für jede Datei dynamisch festlegen. Um den Rights Management-Besitzer dynamisch festzulegen, verwenden Sie den Parameter **-OwnerMail [Source File Owner Email]** und seinen Wert. Durch diese Konfiguration wird die E-Mail-Adresse des Benutzers von Active Directory mithilfe des Benutzerkontonamens in der Owner-Eigenschaft der Datei abgerufen.

- Für die Azure Information Protection-Überprüfung: Sie können festlegen, dass alle Dateien in einem angegebenen Datenspeicher einen einzigen Rights Management-Besitzer haben, aber Sie können den Rights Management-Besitzer nicht für jede Datei dynamisch festlegen. Um das Konto festzulegen, geben Sie den Parameter **-DefaultOwner** für das [Datenrepositoryprofil](/powershell/module/azureinformationprotection/Set-AIPScannerRepository?view=azureipps#optional-parameters) an.

Wenn die Überprüfung Dateien auf Websites und in Bibliotheken von SharePoint schützt, wird der Rights Management-Besitzer dynamisch für jede Datei mithilfe des SharePoint-Autorenwerts festgelegt.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Ich habe gehört, dass bald eine neue Version von Azure Information Protection verfügbar sein wird. Wann wird diese veröffentlicht?

Die technische Dokumentation enthält keine Informationen zu bevorstehenden Releases. Lesen Sie den [Enterprise Mobility and Security Blog](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) und die neuesten Updates von [MicrosoftMobility@MSFTMobility](https://twitter.com/MSFTMobility) auf Twitter, um diese Art von Informationen sowie Versionsankündigungen zu erhalten. Wenn Sie an einem Office-Release interessiert sind, lesen Sie auch den [Office Blog](https://blogs.office.com/).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Ist Azure Information Protection für mein Land geeignet?

Verschiedene Länder haben unterschiedliche Anforderungen und Bestimmungen. Auf der Seite [Suitability for different countries (Eignung für unterschiedliche Länder)](../understand-explore/compliance.md#suitability-for-different-countries) finden Sie Antworten zu den Fragen für Ihre Organisation.

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Wie kann Azure Information Protection bei der Datenschutz-Grundverordnung (DSGVO) helfen?

In der Blogbeitragsankündigung [Microsoft 365 provides an information protection strategy to help with the GDPR (Microsoft 365 stellt eine Datenschutzstrategie zur Unterstützung mit der DSGVO bereit)](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr) (mit Video) finden Sie Informationen darüber, wie Azure Information Protection Ihnen bei der Umsetzung der Datenschutz-Grundverordnung (DSGVO) helfen kann.

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>Wo finde ich weitere Informationen zu Azure Information Protection – z.B. rechtliche Hinweise, Informationen zur Compliance und SLAs?
Lesen Sie hierzu [Kompatibilitätsinformationen und ergänzende Informationen zu Azure Information Protection](../understand-explore/compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Wie kann ich ein Problem melden oder Feedback zu Azure Information Protection übermitteln?

Wenden Sie sich an Ihre Standardsupportkanäle oder an den [Microsoft Support](information-support.md#to-contact-microsoft-support), um technischen Support zu erhalten.

Feedback in Form von Verbesserungsvorschlägen oder neuen Features: Klicken Sie in der Office-Anwendung auf der Registerkarte **Start** in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen), und anschließend auf **Help and Feedback** (Hilfe und Feedback). Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **Send Us Feedback** (Feedback senden). Durch diese Option wird eine E-Mail-Nachricht geöffnet, die an das Information Protection-Team gesendet werden soll.

Wir laden Sie auch dazu ein, sich mit unserem Engineering-Team auf seiner [Yammer-Website zu Azure Information Protection](https://www.yammer.com/askipteam/) in Verbindung zu setzen. 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Wie gehe ich vor, wenn meine Frage hier nicht behandelt wird?

Prüfen Sie zunächst die folgenden häufig gestellten Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen oder den Schutz von Daten beziehen. Der Azure Rights Management-Dienst (Azure RMS) stellt die Technologie zum Schutz von Daten für Azure Information Protection bereit. Azure RMS kann zusammen mit einer Klassifizierung oder Bezeichnung verwendet werden. Es kann aber auch eigenständig genutzt werden. 

- [Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen](faqs-infoprotect.md)

- [Häufig gestellte Fragen zum Schutz von Daten](faqs-rms.md)

Wenn Ihre Frage hier nicht beantwortet wird, verwenden Sie die Links und Ressourcen, die unter [Informationen zu und Unterstützung von Azure Information Protection](information-support.md) aufgelistet sind.

Darüber hinaus gibt es häufig gestellte Fragen (FAQs) für Benutzer:

- [Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android](../rms-client/mobile-app-faq.md)

- [Häufig gestellte Fragen zur RMS-Freigabeanwendung für Macintosh-Computer und Windows Phone](https://technet.microsoft.com/dn451248)

- [Häufig gestellte Fragen zur Rights Management-Freigabeanwendung für Windows](https://technet.microsoft.com/dn467883)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

