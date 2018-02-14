---
title: "Häufig gestellte Fragen (FAQs) zu Azure RMS: AIP"
description: "Einige häufig gestellte Fragen zum Datenschutzdienst Azure Rights Management (Azure RMS) aus Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/08/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.custom: askipteam
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 776293c73b5ca63d0bfd409d8330bfe8295c792e
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Häufig gestellte Fragen zum Schutz von Daten in Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Haben Sie eine Frage zum Datenschutzdienst Azure Rights Management (Azure RMS) aus Azure Information Protection? Vielleicht finden Sie hier eine Antwort. 

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Müssen Dateien in der Cloud gespeichert sein, um durch Azure Rights Management geschützt zu werden?
Nein, das ist ein weit verbreitetes Missverständnis. Der Azure Rights Management Service (und Microsoft) sieht oder speichert Ihre Daten nicht als Teil des Informationsschutzprozesses. Informationen, die Sie schützen, werden niemals an Azure gesendet oder in Azure gespeichert, es sei denn, Sie speichern sie explizit in Azure oder verwenden einen anderen Clouddienst, der sie in Azure speichert. 

Weitere Informationen finden Sie unter [Wie funktioniert Azure RMS? Ein Blick hinter die Kulissen](../understand-explore/how-does-it-work.md), wenn Sie verstehen möchten, wie eine geheime Cola-Formel, die vor Ort erstellt und gespeichert wird, durch Azure Rights Management Service geschützt wird, aber lokal bleibt.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Was ist der Unterschied zwischen Azure Rights Management-Verschlüsselung und Verschlüsselung in anderen Microsoft-Clouddiensten?

Microsoft stellt mehrere Verschlüsselungstechnologien bereit, die Sie zum Schutz Ihrer Daten in verschiedenen und sich häufig ergänzenden Szenarien verwenden können. Während Office 365 beispielsweise eine Verschlüsselung für die in Office 365 gespeicherten Daten bietet, verschlüsselt Azure Rights Management Service von Azure Information Protection Ihre Daten unabhängig, sodass sie unabhängig davon geschützt sind, wo sie sich befinden oder wie sie übertragen werden.

Diese Verschlüsselungstechnologien ergänzen einander, und ihre Verwendung erfordert, dass sie unabhängig voneinander aktiviert und konfiguriert werden. Wenn Sie so vorgehen, besteht ggf. die Option, einen eigenen Schlüssel für die Verschlüsselung zu verwenden, ein Szenario, das auch als „BYOK“ bezeichnet wird. Die Aktivierung von BYOK für eine dieser Technologien wirkt sich nicht auf die anderen Technologien aus. Sie können BYOK z.B. für Azure Information Protection und nicht für andere Verschlüsselungstechnologien verwenden und umgekehrt. Die Schlüssel, die von diesen verschiedenen Technologien verwendet werden, können gleich oder unterschiedlich sein, je nachdem, wie Sie die Verschlüsselungsoptionen für jeden Dienst konfigurieren.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Was ist der Unterschied zwischen BYOK und HYOK, und wann sollte welche Option verwendet werden?

**Bring Your Own Key** (BYOK) im Kontext von Azure Information Protection bedeutet, dass Sie Ihren eigenen Schlüssel für den Schutz von Azure Rights Management lokal erstellen. Anschließend übertragen Sie diesen Schlüssel an ein Hardwaresicherheitsmodul (HSM) in Azure Key Vault, wo Sie weiterhin Besitzer des Schlüssels sind und diesen verwalten. Wenn Sie nicht so vorgegangen wären, würde der Schutz von Azure Rights Management einen Schlüssel verwenden, der automatisch für Sie in Azure erstellt und verwaltet wird. Diese Standardkonfiguration wird als „von Microsoft verwaltet“ und nicht als „vom Kunden verwaltet“ (Option BYOK) bezeichnet.

Weitere Informationen zu BYOK und dazu, ob Sie diese Schlüsseltopologie für Ihre Organisation auswählen sollten, finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md). 

**Hold Your Own Key** (HYOK) im Kontext von Azure Information Protection eignet sich für einige wenige Organisationen, die über eine Teilmenge von Dokumenten oder E-Mails verfügen, die nicht durch einen Schlüssel geschützt werden können, der in der Cloud gespeichert ist. Für diese Organisationen gilt diese Einschränkung selbst dann, wenn sie den Schlüssel erstellt haben und mit BYOK verwalten. Die Einschränkung kann oft aus rechtlichen oder Konformitätsgründen erfolgen, und die HYOK-Konfiguration sollte nur auf Informationen des Typs „Top Secret“ angewendet werden, die niemals außerhalb der Organisation freigegeben werden, nur im internen Netzwerk genutzt werden und nicht von mobilen Geräten aus zugänglich sein müssen. 

Für diese Ausnahmen (in der Regel weniger als 10 % des gesamten zu schützenden Inhalts) können Unternehmen eine lokale Lösung (Active Directory Rights Management Services) verwenden, um den Schlüssel zu erstellen, der lokal gespeichert bleibt. Mit dieser Lösung erhalten Computer ihre Azure Information Protection-Richtlinie aus der Cloud, aber diese identifizierten Inhalte können durch Verwendung des lokalen Schlüssels geschützt werden.

Weitere Informationen zu HYOK und zu den Grenzen und Einschränkungen von HYOK sowie Hinweise zur Verwendung finden Sie unter [HYOK-Anforderungen (Hold Your Own Key) und -Einschränkungen für den AD RMS-Schutz](../deploy-use/configure-adrms-restrictions.md).

## <a name="can-i-now-use-byok-with-exchange-online"></a>Kann ich BYOK jetzt mit Exchange Online verwenden?

Ja, Sie können BYOK jetzt mit Exchange Online verwenden, wenn Sie die Anweisungen unter [Einrichten neuer Office 365-Nachrichtenverschlüsselungsfunktionen, die auf Azure Information Protection aufbauen](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) befolgen. Diese Anweisungen ermöglichen die neuen Funktionen in Exchange Online, die BYOK für den Schutz von Azure-Informationen unterstützen, sowie die neue Office 365-Nachrichtenverschlüsselung.

Weitere Informationen zu dieser Änderung finden Sie in der Blogankündigung: [Office 365-Nachrichtenverschlüsselung mit den neuen Funktionen](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Wo finde ich Informationen zu Lösungen von Drittanbietern, die in Azure RMS integriert werden können?

Viele Softwareanbieter verfügen bereits über Lösungen oder implementieren Lösungen, die sich in Azure Rights Management integrieren lassen, und die Liste wächst rasant. Sie können die Liste mit den [RMS-basierten Lösungen](requirements-applications.md#rms-enlightened-solutions) überprüfen und die neuesten Updates von [Microsoft Mobility@MSFTMobility](https://twitter.com/MSFTMobility) auf Twitter erhalten. Lesen Sie auch den [Entwicklerleitfaden](../develop/developers-guide.md), und stellen Sie spezifische Integrationsfragen auf der [Yammer ](https://www.yammer.com/AskIPTeam)-Website von Azure Information Protection.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Gibt es ein Management Pack oder einen ähnlichen Überwachungsmechanismus für den RMS-Connector?

Obwohl der Rights Management-Connector Informationen, Warnungen und Fehlermeldungen im Ereignisprotokoll protokolliert, gibt es kein Management Pack, das die Überwachung dieser Ereignisse beinhaltet. Die Liste der Ereignisse und ihrer Beschreibungen mit weiteren Informationen, die Ihnen helfen, Korrekturmaßnahmen zu ergreifen, ist jedoch unter [Überwachen des Azure Rights Management-Connectors](../deploy-use/monitor-rms-connector.md) dokumentiert.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Muss ich ein globaler Administrator sein, um Azure RMS zu konfigurieren, oder kann ich dies an andere Administratoren delegieren?

Globale Administratoren für einen Office 365-Mandanten oder Azure AD-Mandanten können selbstverständlich alle Verwaltungsaufgaben für den Azure Rights Management Service ausführen. Wenn Sie jedoch anderen Benutzern Verwaltungsberechtigungen zuweisen möchten, können Sie zu diesem Zweck das Azure RMS PowerShell-Cmdlet [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) verwenden. Sie können diese administrative Rolle nach Benutzerkonto oder nach Gruppe zuweisen. Es sind zwei Rollen verfügbar: **Globaler Administrator** und **Connectoradministrator**. 

Wie diese Rollennamen vermuten lassen, gewährt die erste Rolle Berechtigungen, um alle Verwaltungsaufgaben für Azure Rights Management auszuführen (ohne einen globalen Administrator für andere Clouddienste zu ernennen), und die zweite Rolle gewährt Berechtigungen, um nur den RMS-Connector auszuführen.

Hinweise, die Sie beachten sollten:

- Nur globale Administratoren für Office 365 und globale Administratoren für Azure AD können das Office 365 Admin Center verwenden, um Azure RMS zu konfigurieren. Wenn Sie das Azure-Portal für Azure Information Protection verwenden, können Sie sich als globaler Administrator oder als Sicherheitsadministrator anmelden.

- Benutzer, denen Sie die globale Administratorrolle für Azure RMS zuweisen, müssen Azure RMS PowerShell-Befehle verwenden, um Azure RMS zu konfigurieren. Weitere Informationen zum Auswählen der richtigen Cmdlets für bestimmte Aufgaben finden Sie unter [Verwalten von Azure Rights Management mit Windows PowerShell](../deploy-use/administer-powershell.md).

- Wenn Sie [Onboarding-Steuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, besitzt diese Konfiguration keinen Einfluss auf die Fähigkeit, Azure RMS zu verwalten (mit Ausnahme des RMS-Connectors). Wenn Sie beispielsweise Onboarding-Steuerelemente so konfiguriert haben, dass die Fähigkeit zum Schutz von Inhalten auf die Gruppe „IT-Abteilung“ beschränkt ist, muss das Konto, mit dem Sie den RMS-Connector installieren und konfigurieren, Mitglied dieser Gruppe sein. 

- Kein Administrator für Azure RMS (z.B. der globale Administrator des Mandanten oder ein globaler Administrator von Azure RMS) kann den Schutz von Dokumenten oder E-Mails, die mit Azure RMS geschützt wurden, automatisch entfernen. Dies ist nur Benutzern möglich, die Administratoren (super user) für Azure RMS sind, wenn das Administratorfeature aktiviert ist. Der globale Administrator des Mandanten und jeder globale Administrator von Azure RMS kann jedoch Benutzer als Administratoren (super user) zuweisen, einschließlich ihres eigenen Kontos. Sie können auch das Administratorfeature (super user) aktivieren. Diese Aktionen werden im Azure RMS-Administratorprotokoll aufgezeichnet. Weitere Informationen finden Sie im Abschnitt zu den bewährte Sicherheitsmethoden unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](../deploy-use/configure-super-users.md). 

>[!NOTE]
> Vorlagen und neue Optionen für die Konfiguration des Azure Rights Management-Schutzes wurden in das Azure-Portal verschoben, das neben dem globalen Administratorzugriff auch Sicherheitsadministratoren unterstützt. 

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Wie erstelle ich eine neue benutzerdefinierte Vorlage im Azure-Portal?

Benutzerdefinierte Vorlagen wurden in das Azure-Portal verschoben, wo Sie sie weiterhin als Vorlagen verwalten oder in Bezeichnungen konvertieren können. Um eine neue Vorlage zu erstellen, erstellen Sie eine neue Bezeichnung und konfigurieren die Datenschutzeinstellungen für Azure RMS. Im Hintergrund wird eine neue Vorlage erstellt, auf die dann Dienste und Anwendungen zugreifen können, die in Rights Management-Vorlagen integriert sind.

Weitere Informationen zu Vorlagen im Azure-Portal finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](../deploy-use/configure-policy-templates.md).

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>Ich habe ein Dokument geschützt und möchte nun die Nutzungsrechte ändern oder Benutzer hinzufügen. Muss ich das Dokument erneut schützen?

Wenn das Dokument mit einer Bezeichnung oder einer Vorlage geschützt wurde, besteht keine Notwendigkeit, das Dokument erneut zu schützen. Ändern Sie die Bezeichnung oder Vorlage, indem Sie Ihre Änderungen an den Nutzungsrechten vornehmen oder neue Gruppen (oder Benutzer) hinzufügen, und speichern und veröffentlichen Sie diese Änderungen dann:

- Wenn ein Benutzer nicht auf das Dokument zugegriffen hat, bevor Sie die Änderungen vorgenommen haben, werden die Änderungen wirksam, sobald der Benutzer das Dokument öffnet. 

- Wenn ein Benutzer bereits auf das Dokument zugegriffen hat, werden diese Änderungen wirksam, wenn seine [Nutzungslizenz](../deploy-use/configure-usage-rights.md#rights-management-use-license) abläuft. Schützen Sie das Dokument nur dann erneut, wenn Sie nicht warten können, bis die Nutzungslizenz abgelaufen ist. Durch das erneute Schützen wird eine neue Version des Dokuments und damit eine neue Nutzungslizenz für den Benutzer erstellt.

Wenn Sie bereits eine Gruppe für die erforderlichen Berechtigungen konfiguriert haben, können Sie alternativ die Gruppenzugehörigkeit ändern, um Benutzer ein- oder auszuschließen, und es ist nicht erforderlich, die Bezeichnung oder die Vorlage zu ändern. Es kann eine kleine Verzögerung bis zum Inkrafttreten der Änderungen geben, da die Gruppenmitgliedschaft durch den Azure Rights Management Service [zwischengespeichert](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection) wird.

Wenn das Dokument mit benutzerdefinierten Berechtigungen geschützt wurde, können Sie die Berechtigungen für das vorhandene Dokument nicht ändern. Sie müssen das Dokument erneut schützen und alle Benutzer und alle Nutzungsrechte angeben, die für diese neue Version des Dokuments erforderlich sind. Um ein geschütztes Dokument erneut zu schützen, müssen Sie über das Nutzungsrecht „Vollzugriff“ verfügen.

Tipp: Verwenden Sie das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus), um zu überprüfen, ob ein Dokument durch eine Vorlage oder durch die Verwendung benutzerdefinierter Berechtigungen geschützt wurde. Es wird immer die Vorlagenbeschreibung **Eingeschränkter Zugriff** für benutzerdefinierte Berechtigungen mit einer eindeutigen Vorlagen-ID angezeigt, die nicht angezeigt wird, wenn Sie [Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate) ausführen.

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Ich verwende eine Hybridbereitstellung von Exchange mit einigen Benutzern unter Exchange Online und anderen unter Exchange Server. Wird dies von Azure RMS unterstützt?
Ja, und der Vorteil besteht darin, dass Benutzer in der Lage sein werden, geschützte E-Mails und Anlagen über die beiden Exchange-Bereitstellungen hinweg nahtlos zu schützen und zu nutzen. Aktivieren Sie für diese Konfiguration [Azure RMS](../deploy-use/activate-service.md) und [IRM für Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), und stellen Sie dann den [RMS-Connector](../deploy-use/deploy-rms-connector.md) für Exchange Server bereit, und konfigurieren Sie ihn.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Wenn ich diesen Schutz für meine Produktionsumgebung verwende, ist mein Unternehmen dann an die Lösung gebunden oder riskiert es, den Zugriff auf Inhalte zu verlieren, die wir mit Azure RMS geschützt haben?
Nein, Sie behalten immer die Kontrolle über Ihre Daten und können weiterhin darauf zugreifen, auch wenn Sie sich entscheiden, Azure Rights Management Service nicht mehr zu nutzen. Weitere Informationen finden Sie unter [Außerbetriebnahme und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md).

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Kann ich steuern, welche Benutzer Azure RMS verwenden können, um Inhalte zu schützen?
Ja, Azure Rights Management Service verfügt für dieses Szenario über Onboarding-Steuerelemente für Benutzer. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine schrittweise Bereitstellung](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) im Artikel [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Kann ich verhindern, dass Benutzer geschützte Dokumente für bestimmte Organisationen freigeben?
Einer der größten Vorteile der Verwendung von Azure Rights Management Service für den Datenschutz besteht darin, dass die Zusammenarbeit zwischen Unternehmen unterstützt wird, ohne dass Sie explizite Vertrauensstellungen für jede Partnerorganisation konfigurieren müssen, da Azure AD die Authentifizierung für Sie übernimmt.

Es gibt keine Verwaltungsoption, die Benutzer daran hindert, Dokumente sicher mit bestimmten Organisationen auszutauschen. Beispielsweise möchten Sie eine Organisation blockieren, der Sie nicht vertrauen oder die ein konkurrierendes Unternehmen darstellt. Es wäre nicht sinnvoll, Azure Rights Management Service daran zu hindern, geschützte Dokumente an Benutzer in diesen Organisationen zu senden, da Ihre Benutzer dann ihre Dokumente ungeschützt freigeben würden, was wahrscheinlich das Letzte ist, was in diesem Szenario passieren soll. Beispielsweise können Sie nicht erkennen, wer vertrauliche Dokumente mit welchen Benutzern in diesen Organisationen teilt, was möglich ist, wenn das Dokument (oder die E-Mail) durch Azure Rights Management Service geschützt ist.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>Wenn ich ein geschütztes Dokument mit jemandem außerhalb meines Unternehmens teile, wie wird dieser Benutzer authentifiziert?

Standardmäßig verwendet Azure Rights Management Service ein Azure Active Directory-Konto und eine zugehörige E-Mail-Adresse für die Benutzerauthentifizierung, wodurch die Zusammenarbeit zwischen Unternehmen für Administratoren nahtlos wird. Wenn die andere Organisation Azure-Dienste verwendet, verfügen Benutzer bereits über Konten in Azure Active Directory, selbst wenn diese Konten lokal erstellt und verwaltet und dann mit Azure synchronisiert werden. Wenn die Organisation über Office 365 verfügt, verwendet dieser Dienst im Hintergrund auch Azure Active Directory für die Benutzerkonten. Wenn die Organisation des Benutzers keine verwalteten Konten in Azure besitzt, können sich Benutzer für [RMS für Einzelpersonen](../understand-explore/rms-for-individuals.md) registrieren, wodurch ein nicht verwalteter Azure-Mandant und ein Verzeichnis für die Organisation mit einem Konto für den Benutzer erstellt werden, sodass dieser Benutzer (und nachfolgende Benutzer) dann für Azure Rights Management Service authentifiziert werden kann.

Die Authentifizierungsmethode für diese Konten kann unterschiedlich sein, je nachdem, wie der Administrator in der anderen Organisation die Azure Active Directory-Konten konfiguriert hat. Beispielsweise könnte er Kennwörter verwenden, die für diese Konten erstellt wurden, Multi-Factor Authentication (MFA), Verbund oder Kennwörter, die in Active Directory Domain Services erstellt und dann mit Azure Active Directory synchronisiert wurden.

Wenn Sie eine E-Mail mit einer Office-Dokumentanlage an einen Benutzer schützen, der kein Konto in Azure AD besitzt, ändert sich die Authentifizierungsmethode. Der Azure Rights Management Service bildet einen Verbund mit einigen beliebten sozialen Netzwerken als Identitätsanbieter, z.B. mit Google Mail. Wenn der E-Mail-Anbieter des Benutzers unterstützt wird, kann sich der Benutzer bei diesem Dienst anmelden, und sein E-Mail-Anbieter ist für die Authentifizierung verantwortlich. Wenn der E-Mail-Anbieter des Benutzers nicht unterstützt wird (oder als Präferenz), kann der Benutzer einen einmaligen Passcode beantragen, der ihn authentifiziert und die E-Mail mit dem geschützten Dokument in einem Webbrowser anzeigt.

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Kann ich externe Benutzer (Personen außerhalb meiner Firma) benutzerdefinierten Vorlagen hinzufügen?

Ja. Mit den [Schutzeinstellungen](../deploy-use/configure-policy-protection.md), die Sie im Azure-Portal konfigurieren können, können Sie für Benutzer und Gruppen außerhalb Ihrer Organisation und sogar für alle Benutzer in einer anderen Organisation Berechtigungen hinzufügen. Wenn die Vorlage nicht ausschließlich für den Versand von E-Mails unter Verwendung der [neuen Funktionen aus der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) verwendet wird, fügen Sie keine Konten aus sozialen Identitäten (wie Google Mail und Microsoft) oder anderen Konten hinzu, die nicht in Azure AD enthalten sind.

Beachten Sie Folgendes: Wenn Sie Azure Information Protection-Bezeichnungen verwenden, müssen Sie Ihre benutzerdefinierte Vorlage zunächst in eine Bezeichnung konvertieren, bevor Sie diese Schutzeinstellungen im Azure-Portal konfigurieren können. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](../deploy-use/configure-policy-templates.md).

Alternativ können Sie mithilfe von PowerShell externe Benutzer benutzerdefinierten Vorlagen (und Bezeichnungen) hinzufügen. Diese Konfiguration erfordert, dass Sie ein Rechtedefinitionsobjekt verwenden, mit dem Sie Ihre Vorlage aktualisieren:

1. Geben Sie die externen E-Mail-Adressen und ihre Rechte in einem Rechtedefinitionsobjekt an, indem Sie mit dem Cmdlet [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) eine Variable erstellen.

2. Übergeben Sie diese Variable mit dem Cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) an den RightsDefinition-Parameter.
    
    Wenn Sie Benutzer einer vorhandenen Vorlage hinzufügen, müssen Sie zusätzlich zu den neuen Benutzern Rechtedefinitionsobjekte für die vorhandenen Benutzer in den Vorlagen definieren. Für dieses Szenario finden Sie möglicherweise **Beispiel 3: Hinzufügen neuer Benutzer und Rechte zu einer benutzerdefinierten Vorlage** aus dem Abschnitt [Beispiele](/powershell/module/aadrm/set-aadrmtemplateproperty#examples) für das Cmdlet hilfreich. 

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Welche Art von Gruppen kann ich mit Azure RMS verwenden?
In den meisten Szenarien können Sie alle Gruppentypen in Azure AD verwenden, die über eine E-Mail-Adresse verfügen. Diese Faustregel gilt immer dann, wenn Sie Nutzungsrechte zuweisen, aber einige Ausnahmen für die Verwaltung von Azure Rights Management Service bestehen. Weitere Informationen finden Sie unter [Azure Information Protection-Anforderungen für Gruppenkonten](../plan-design/prepare.md#azure-information-protection-requirements-for-group-accounts).

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>Wie sende ich eine geschützte E-Mail an ein Google Mail- oder Hotmail-Konto?

Wenn Sie Exchange Online und Azure Rights Management Service nutzen, senden Sie die E-Mail einfach als geschützte Nachricht an den Benutzer. Sie können beispielsweise die neue Schaltfläche **Schützen** in der Befehlsleiste in Outlook im Web auswählen, die Outlook-Schaltfläche **Nicht weiterleiten** oder die Menüoption verwenden. Oder Sie können eine Azure Information Protection-Bezeichnung auswählen, die automatisch „Nicht weiterleiten“ für Sie anwendet und die E-Mail klassifiziert. 

Der Empfänger sieht eine Option, um sich bei seinem Google Mail-, Yahoo- oder Microsoft-Konto anzumelden, und kann dann die geschützte E-Mail lesen. Alternativ können sie die Option für einen einmaligen Passcode auswählen, um die E-Mail in einem Browser zu lesen.

Damit dieses Szenario unterstützt wird, muss Exchange Online für Azure Rights Management Service und die neuen Funktionen in der Office 365-Nachrichtenverschlüsselung aktiviert sein. Weitere Informationen zu dieser Konfiguration finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

Weitere Informationen zu den neuen Funktionen, zu denen auch die Unterstützung aller E-Mail-Konten auf allen Geräten gehört, finden Sie im folgenden Blogbeitrag: [Ankündigung neuer Funktionen, die in der Office 365-Nachrichtenverschlüsselung verfügbar sind](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Welche Geräte und Dateitypen werden von Azure RMS unterstützt?
Eine Liste der Geräte, die Azure Rights Management Service unterstützen, finden Sie unter [Clientgeräte, die Azure Rights Management-Datenschutz unterstützen](../get-started/requirements-client-devices.md). Da zurzeit nicht alle unterstützten Geräte alle Rights-Management-Funktionen unterstützen können, sollten Sie auch die Tabelle für [RMS-basierte Anwendungen](../get-started/requirements-applications.md#rms-enlightened-applications) überprüfen.

Azure Rights Management Service kann alle Dateitypen unterstützen. Für Text-, Bild-, Microsoft Office-Dateien (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen stellt Azure Rights Management nativen Schutz bereit, der sowohl Verschlüsselung als auch Durchsetzung von Rechten (Berechtigungen) umfasst. Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz Dateikapselung und Authentifizierung, um zu überprüfen, ob ein Benutzer berechtigt ist, die Datei zu öffnen.

Eine Liste der Dateinamenerweiterungen, die nativ von Azure Rights Management unterstützt werden, finden Sie unter [Vom Azure Information Protection-Client unterstützte Dateitypen](../rms-client/client-admin-guide-file-types.md). Nicht aufgeführte Dateinamenerweiterungen werden unterstützt, indem der Azure Information Protection-Client verwendet wird, der automatisch generischen Schutz auf diese Dateien anwendet.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Wie konfiguriere ich einen Mac-Computer zum Schützen und Nachverfolgen von Dokumenten?

Stellen Sie zunächst sicher, dass Sie Office für Mac installiert haben, indem Sie den Softwareinstallationslink aus https://portal.office.com verwenden. Vollständige Anweisungen finden Sie unter [Herunterladen und Installieren oder erneutes Installieren von Office 365 oder Office 2016 auf einem PC oder Mac](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658).

Öffnen Sie Outlook, und erstellen Sie ein Profil, indem Sie Ihr Office 365-Geschäfts-, Schul- oder Unikonto verwenden. Erstellen Sie anschließend eine neue Nachricht, und führen Sie die folgenden Schritte aus, um Office so zu konfigurieren, dass Dokumente und E-Mails mithilfe von Azure Rights Management-Service geschützt werden können:

1. Klicken Sie in der neuen Nachricht auf der Registerkarte **Optionen** auf **Berechtigungen**, und klicken Sie dann auf **Anmeldeinformationen überprüfen**.

2. Wenn Sie dazu aufgefordert werden, geben Sie die Details Ihres Office 365-Geschäfts-, Schul- oder Unikontos erneut an, und wählen Sie dann **Anmelden** aus. 
    
    Die Azure Rights Management-Vorlagen werden nun heruntergeladen, und **Anmeldeinformationen überprüfen** wird durch Optionen wie **Keine Einschränkungen**, **Nicht weiterleiten** und alle Azure Rights Management-Vorlagen ersetzt, die für Ihren Mandanten veröffentlicht werden. Sie können diese neue Nachricht jetzt abbrechen.

So schützen Sie eine E-Mail-Nachricht oder ein Dokument: Klicken Sie auf der Registerkarte **Optionen** auf **Berechtigungen**, und wählen Sie eine Option oder eine Vorlage aus, die Ihre E-Mail oder Ihr Dokument schützt.

So verfolgen Sie ein Dokument nach, nachdem Sie es geschützt haben: Auf einem Windows-Computer, auf dem der Azure Information Protection-Client installiert ist, registrieren Sie das Dokument mithilfe einer Office-Anwendung oder des Datei-Explorers bei der Dokumentnachverfolgungs-Website. Anweisungen hierzu finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente](../rms-client/client-track-revoke.md). Auf Ihrem Mac-Computer können Sie nun mit Ihrem Webbrowser zur Dokumentnachverfolgungsseite (https://track.azurerms.com) navigieren, um dieses Dokument nachzuverfolgen und zu widerrufen.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Wenn ich ein durch RMS geschütztes Office-Dokument öffne, wird die zugehörige temporäre Datei ebenfalls durch RMS geschützt?
Nein. In diesem Szenario enthält die zugehörige temporäre Datei keine Daten aus dem ursprünglichen Dokument, sondern nur das, was der Benutzer eingibt, während die Datei geöffnet ist. Im Gegensatz zur ursprünglichen Datei ist die temporäre Datei offensichtlich nicht für die Freigabe vorgesehen und würde auf dem Gerät verbleiben, geschützt durch lokale Sicherheitsmechanismen wie BitLocker und EFS.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>Ein Feature, nach dem ich suche, scheint nicht mit durch SharePoint geschützten Bibliotheken zu funktionieren. Ist Unterstützung für mein Feature geplant?
Zurzeit unterstützt SharePoint durch RMS geschützte Dokumente durch die Verwendung von durch IRM geschützte Bibliotheken, die Rights Management-Vorlagen, Dokumentnachverfolgung und einige andere Funktionen nicht unterstützen. Weitere Informationen finden Sie im Abschnitt [SharePoint Online und SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) im Artikel [Office-Anwendungen und -Dienste](../understand-explore/office-apps-services-support.md).

Wenn Sie an einer bestimmten Funktion interessiert sind, die noch nicht unterstützt wird, sollten Sie die Ankündigungen im [Blog zu Enterprise Mobility + Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) im Auge behalten.

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Wie konfiguriere ich One Drive for Business in SharePoint Online, damit Benutzer ihre Dateien sicher mit Personen innerhalb und außerhalb des Unternehmens teilen können?
Standardmäßig konfigurieren Sie als Office 365-Administrator diese Option nicht, sondern nur die Benutzer.

So wie ein SharePoint-Websiteadministrator IRM für eine SharePoint-Bibliothek, deren Besitzer er ist, aktiviert und konfiguriert, ist OneDrive for Business für Benutzer konzipiert, die IRM für ihre eigene OneDrive for Business-Bibliothek aktivieren und konfigurieren möchten. Mit PowerShell können Sie diese Aufgabe jedoch für sie übernehmen. Anweisungen finden Sie im Abschnitt [SharePoint Online und OneDrive for Business: IRM-Konfiguration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) des Artikels [Office 365: Konfiguration für Clients und Onlinedienste](../deploy-use/configure-office365.md).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Kennen Sie Tipps und Tricks für eine erfolgreiche Bereitstellung?

Nachdem wir viele Bereitstellungen betreut und unseren Kunden, Partnern, Beratern und Supportengineers zugehört haben, ist einer der besten Tipps, die wir aus Erfahrung weitergeben können: **Entwerfen und implementieren Sie einfache Richtlinien**.

Da Azure Information Protection die sichere Freigabe von Daten für jedermann unterstützt, können Sie es sich leisten, ehrgeizig zu sein, wenn es um den Schutz Ihrer Daten geht. Seien Sie jedoch vorsichtig, wenn Sie Einschränkungen der Rechteverwendung konfigurieren. Für viele Unternehmen ist die größte Auswirkung auf das Geschäft die Verhinderung von Datendiebstahl durch die Beschränkung des Zugriffs auf Personen im Unternehmen. Natürlich können Sie viel präziser werden, wenn es erforderlich ist: Sie können verhindern, dass Personen Dokumente drucken, bearbeiten usw. Behalten Sie sich die detaillierteren Einschränkungen jedoch als Ausnahme für Dokumente vor, die wirklich eine hohe Sicherheitsstufe benötigen, und implementieren Sie diese restriktiveren Nutzungsrechte nicht am ersten Tag, sondern planen Sie einen mehrstufigen Ansatz.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Wie erhalten wir erneut Zugriff auf Dateien, die von einem Mitarbeiter geschützt wurden, der das Unternehmen inzwischen verlassen hat?
Verwenden Sie das [Feature Administrator (super user)](../deploy-use/configure-super-users.md), das autorisierten Benutzern das Nutzungsrecht „Vollzugriff“ für alle Dokumente und E-Mails gewährt, die durch Ihren Mandanten geschützt sind. Administratoren (super user) können diesen geschützten Inhalt jederzeit lesen und bei Bedarf den Schutz entfernen oder für verschiedene Benutzer erneut herstellen. Mit diesem Feature können autorisierte Dienste bei Bedarf Dateien indizieren und untersuchen.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Wenn ich den Widerruf auf der Dokumentnachverfolgungsseite teste, sehe ich eine Meldung, die besagt, dass Personen bis zu 30 Tage lang auf das Dokument zugreifen können. Ist dieser Zeitraum konfigurierbar?

Ja. Diese Meldung gibt die [Nutzungslizenz](../deploy-use/configure-usage-rights.md#rights-management-use-license) für diese bestimmte Datei an. 

Wenn Sie eine Datei widerrufen, kann diese Aktion nur erzwungen werden, wenn sich der Benutzer bei Azure Rights Management Service authentifiziert. Wenn eine Datei also eine Gültigkeitsdauer der Nutzungslizenz von 30 Tagen aufweist und der Benutzer das Dokument bereits geöffnet hat, hat dieser Benutzer für die Dauer der Nutzungslizenz weiterhin Zugriff auf das Dokument. Wenn die Nutzungslizenz abläuft, muss sich der Benutzer erneut authentifizieren. Daraufhin wird dem Benutzer der Zugriff verweigert, da das Dokument nun widerrufen ist.

Der Benutzer, der das Dokument geschützt hat (der [Rights Management-Herausgeber](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner)), ist von diesem Widerruf ausgenommen und kann jederzeit auf seine Dokumente zugreifen. 

Der Standardwert für den Gültigkeitszeitraum der Nutzungslizenz für einen Mandanten beträgt 30 Tage. Diese Einstellung kann durch eine restriktivere Einstellung in einer Bezeichnung oder einer Vorlage überschrieben werden. Weitere Informationen zur Nutzungslizenz und deren Konfiguration finden Sie in der Dokumentation zur [Rights Management-Nutzungslizenz](../deploy-use/configure-usage-rights.md#rights-management-use-license).

## <a name="can-rights-management-prevent-screen-captures"></a>Kann Rights Management Bildschirmaufnahmen verhindern?
Durch die Nichtgewährung des [Nutzungsrechts](../deploy-use/configure-usage-rights.md) **Kopieren** kann Rights Management Bildschirmaufnahmen von vielen der gebräuchlichen Bildschirmaufnahmetools auf Windows-Plattformen (Windows 7, Windows 8.1, Windows 10, Windows Phone) und unter Android verhindern. Auf iOS- und Mac-Geräten ist es jedoch nicht möglich, dass eine App Bildschirmaufnahmen verhindert, und Browser (z.B. in Verbindung mit Outlook Web App und Office Online) können ebenfalls keine Bildschirmaufnahmen verhindern.

Das Verhindern von Bildschirmaufnahmen kann helfen, eine versehentliche oder fahrlässige Offenlegung vertraulicher oder sensibler Informationen zu vermeiden. Es gibt aber viele Möglichkeiten, wie ein Benutzer Daten, die auf einem Bildschirm angezeigt werden, gemeinsam nutzen kann, und eine Bildschirmaufnahme anzufertigen, ist nur eine Methode. Beispielsweise kann ein Benutzer, der beabsichtigt, angezeigte Informationen zu teilen, mit seiner Smartphonekamera ein Foto davon machen, die Daten erneut eingeben oder sie einfach mündlich an eine andere Person weitergeben.

Wie diese Beispiele zeigen, kann Technologie allein nicht immer verhindern, dass Benutzer Daten unerlaubt gemeinsam nutzen, selbst wenn alle Plattformen und die gesamte Software die Rights Management-APIs zur Blockierung von Bildschirmaufnahmen unterstützten. Rights Management kann Ihnen dabei helfen, Ihre wichtigen Daten durch die Verwendung von Autorisierung und Nutzungsrichtlinien zu schützen, aber diese Lösung für die Verwaltung von Unternehmensrechten sollte zusammen mit anderen Kontrollmechanismen verwendet werden. Implementieren Sie beispielsweise physische Sicherheit, überprüfen und überwachen Sie sorgfältig Personen, die autorisierten Zugriff auf die Daten Ihres Unternehmens besitzen, und investieren Sie in die Schulung der Benutzer, damit Benutzer verstehen, welche Daten nicht geteilt werden sollten.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Worin besteht der Unterschied zwischen einem Benutzer, der eine E-Mail mit „Nicht weiterleiten“ schützt, und einer Vorlage, die das Recht „Weiterleiten“ nicht enthält?

Trotz des Namens und des Erscheinungsbilds ist **Nicht weiterleiten** nicht das Gegenteil des Rechts „Weiterleiten“ oder einer Vorlage. Es handelt sich dabei um eine Reihe von Rechten, die das Kopieren, Drucken und Speichern von Anlagen sowie die Weiterleitung von E-Mails einschränken. Die Rechte werden auf Benutzer über die ausgewählten Empfänger dynamisch angewendet und nicht statisch vom Administrator zugewiesen. Weitere Informationen finden Sie unter [Option „Nicht weiterleiten“ für E-Mails](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) im Abschnitt [Konfiguration der Nutzungsrechte für Azure Rights Management](../deploy-use/configure-usage-rights.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


