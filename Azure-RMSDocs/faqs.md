---
title: Häufig gestellte Fragen zu Azure Information Protection
description: Einige häufig gestellte Fragen zu Azure Information Protection und dem dazugehörigen Schutzdienst, Azure Rights Management (Azure RMS).
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/23/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: 82280d50bdd16139e53d4906e908f7efcb9b6281
ms.sourcegitcommit: 16d2c7477b96c5e8f6e4328a61fe1dc3d12c878d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86927385"
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Häufig gestellte Fragen zu Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Haben Sie eine Frage zu Azure Information Protection oder zum Azure Rights Management-Dienst (Azure RMS)? Vielleicht finden Sie hier eine Antwort.

<!-- These FAQ pages are updated regularly, with new additions listed in the monthly documentation update announcements on the [Azure Information Protection technical blog](https://aka.ms/AIPblog).-->

## <a name="whats-the-difference-between-azure-information-protection-and-microsoft-information-protection"></a>Was ist der Unterschied zwischen Azure Information Protection und Microsoft Information Protection?

Im Gegensatz zu Azure Information Protection ist [Microsoft Information Protection](https://www.microsoft.com/security/business/information-protection) kein Abonnement oder Produkt, das Sie kaufen können. Stattdessen handelt es sich um ein Framework für Produkte und integrierte Funktionen, mit denen Sie die sensiblen Informationen Ihrer Organisation schützen können.

**Zu den Microsoft Information Protection-Produkten gehören:**
- Azure Information Protection
- Office 365 Information Protection, z. b. Office 365 DLP
- Windows Information Protection
- Microsoft Cloud App Security

**Zu den Funktionen von Microsoft Information Protection gehören:**
- Unified Label-Verwaltung
- In Office-Apps integrierte Endbenutzer-Beschriftungen
- Die Fähigkeit von Windows, einheitliche Bezeichnungen zu verstehen und Schutz auf Daten anzuwenden
- Das Microsoft Information Protection SDK
- Funktionalität in Adobe Acrobat Reader zum Anzeigen von beschrifteten und geschützten PDF-Informationen

Weitere Informationen finden [Sie unter Information Protection-Funktionen zum Schutz Ihrer sensiblen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>Worin besteht der Unterschied zwischen Bezeichnungen in Azure Information Protection und Bezeichnungen in Office 365?

Ursprünglich waren in Office 365 nur Bezeichnungs [Bezeichnungen](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) enthalten, mit denen Sie Dokumente und e-Mails für die Überwachung und Aufbewahrung klassifizieren konnten, als dieser Inhalt in den Office 365-Diensten gespeichert war. 

Im Gegensatz dazu wenden Azure Information Protection Bezeichnungen aktiviert eine konsistente Klassifizierung und Schutzrichtlinie für Dokumente und e-Mails an, unabhängig davon, ob Sie lokal oder in der Cloud gespeichert wurden.

Office 365 wurde auf der Microsoft Ignite 2018 in Orlando angekündigt und verfügt nun über die Möglichkeit, [Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)zusätzlich zu den Aufbewahrungs Bezeichnungen zu erstellen und zu konfigurieren. Vertraulichkeits Bezeichnungen können in den folgenden admin Centers erstellt und konfiguriert werden:

- Office 365 Security & Compliance Center
- Microsoft 365 Security Center
- Microsoft 365 Compliance Center

Verwenden Sie Azure Information Protection Bezeichnungen als Vertraulichkeits Bezeichnungen mit Office 365-apps [, indem Sie Ihre AIP-Bezeichnungen zum vereinheitlichten Bezeichnungs Speicher migrieren](configure-policy-migrate-labels.md).

Weitere Informationen zu Unified-Bezeichnungs Verwaltung und-Unterstützung finden [Sie unter Ankündigen der Verfügbarkeit von Datenschutzfunktionen zum Schutz Ihrer sensiblen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

## <a name="how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform"></a>Wie kann ich feststellen, ob mein Mandant auf der Unified-Bezeichnung-Plattform ist?

Wenn sich Ihr Mandant auf der Unified Label-Plattform befindet, werden Vertraulichkeits Bezeichnungen unterstützt, die von [Clients und Diensten verwendet werden können, die eine einheitliche Bezeichnung unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling). Wenn Sie Ihr Abonnement für Azure Information Protection im Juni 2019 oder höher erhalten haben, befindet sich Ihr Mandant automatisch auf der Unified-Bezeichnung-Plattform, und es ist keine weitere Aktion erforderlich. Ihr Mandant kann sich auch auf dieser Plattform befinden, da die Azure Information Protection Bezeichnungen migriert wurden.

Wenn sich Ihr Mandant nicht auf der Unified-Beschriftungs Plattform befindet, wird das folgende Informations Banner in der Azure-Portal auf den **Azure Information Protection** Bereichen angezeigt:

![Banner für Migrations Informationen](media/migration-status-banner.png)

Sie können auch prüfen, indem Sie zu **Azure Information Protection**  >  Unified-**Manage**  >  **Bezeichnung**verwalten wechseln und den **einheitlichen** Bezeichnungs Status anzeigen:

|Status |Beschreibung  |
|---------|---------|
|**Aktiviert**     |  Ihr Mandant befindet sich auf der Unified-Beschriftungs Plattform. </br>Sie können Bezeichnungen im Microsoft 365 Compliance Center [erstellen, konfigurieren und veröffentlichen](/microsoft-365/compliance/create-sensitivity-labels) .       |
|**Nicht aktiviert**    |  Ihr Mandant befindet sich nicht auf der Unified-Beschriftungs Plattform. </br>Migrations Anweisungen und Anleitungen finden Sie unter [Migrieren von Azure Information Protection Bezeichnungen zu Unified Sensitivität-Bezeichnungen](configure-policy-migrate-labels.md).       |

## <a name="whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients"></a>Worin besteht der Unterschied zwischen den Azure Information Protection klassischen und vereinheitlichten Bezeichnungs Clients?

Der ursprüngliche Client, der als *Azure Information Client* oder der *klassische* Client bezeichnet wird, lädt Bezeichnungen und Richtlinien Einstellungen von Azure herunter und ermöglicht es Ihnen, die [AIP-Richtlinie](overview-policy.md) aus dem Azure-Portal zu konfigurieren.

Der *Unified* -Bezeichnungs Client ist eine neuere Ergänzung und unterstützt den vereinheitlichten Bezeichnungs Speicher, der von mehreren Anwendungen und Diensten verwendet wird. Der Unified Label-Client lädt [Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) und Richtlinien Einstellungen aus den folgenden admin Centers herunter:

- Office 365 Security & Compliance Center
- Microsoft 365 Security Center
- Microsoft 365 Compliance Center

Wenn Sie ein Administrator sind und nicht sicher sind, welcher Client verwendet werden soll, finden Sie unter [auswählen des zu verwendenden Azure Information Protection Clients](./rms-client/use-client.md#choose-which-labeling-client-to-use-for-windows-computers)Weitere Informationen.

### <a name="identify-the-client-you-have-installed"></a>Identifizieren Sie den Client, den Sie installiert haben.

Wenn Sie ein Benutzer sind, der überprüfen möchte, ob der klassische oder einheitliche Bezeichnungs Client installiert ist, klicken Sie auf **Hilfe und Feedback** , um das Dialogfeld **Microsoft Azure Information Protection** anzuzeigen. 

Beispiel:

:::image type="content" source="media/client-about.png" alt-text="Ermitteln, ob der klassische oder der einheitliche Client installiert ist":::

Die Versionsnummer gibt den Client wie folgt an:

- In den Versionen **1. x** wird angegeben, dass Sie über den klassischen Client verfügen. Beispiel: **1.54.59.0**
- In Version **2. x** wird angegeben, dass Sie über den Unified-Bezeichnungs Client verfügen. Beispiel: **2.6.111.0**

Greifen Sie auf dieses Dialogfeld mit einer der folgenden Methoden zu:

- Klicken Sie im Datei-Explorer mit der rechten Maustaste auf eine Datei, Dateien oder einen Ordner, **und**wählen Sie  >  **Hilfe und Feedback**klassifizieren und schützen aus.
- In Office-Anwendungen hat der klassische Client die Schaltfläche **schützen** , und der Unified-Bezeichnung-Client hat eine **Vertraulichkeits** Schaltfläche. Wählen Sie eine dieser Schaltflächen aus, und klicken Sie dann auf **Hilfe und Feedback**.

## <a name="when-is-the-right-time-to-migrate-my-labels"></a>Wann ist der richtige Zeitpunkt für die Migration meiner Bezeichnungen?

Es wird empfohlen, dass Sie Ihre Azure Information Protection Bezeichnungen zu der Unified Label-Plattform migrieren, sodass Sie Sie als Vertraulichkeits Bezeichnungen mit anderen [Clients und Diensten verwenden können, die vereinheitlichte Bezeichnungen unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

Weitere Informationen und Anweisungen finden Sie unter [Migrieren von Azure Information Protection Bezeichnungen zu Unified Sensitivität-Bezeichnungen](configure-policy-migrate-labels.md).

## <a name="after-ive-migrated-my-labels-which-management-portal-do-i-use"></a>Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?

Nachdem Sie Ihre Bezeichnungen in der Azure-Portal migriert haben, können Sie Sie abhängig von den installierten Clients weiterhin an einem der folgenden Speicherorte verwalten:

|Client  |Column2  |
|---------|---------|
|[Einheitliche Bezeichnung für Clients und Dienste](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling)    |  Wenn Sie nur Unified Label-Clients installiert haben, verwalten Sie Ihre Bezeichnungen in einem der Admin Center: Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center. Die Bezeichnungen und Richtlinieneinstellungen werden von Clients für einheitliche Bezeichnungen aus diesen Admin-Centers heruntergeladen. </br></br>Anweisungen finden Sie unter [Erstellen und Konfigurieren von Vertraulichkeits Bezeichnungen und ihren Richtlinien](/microsoft-365/compliance/create-sensitivity-labels).     |
|Nur [klassischer Client](./rms-client/aip-client.md)  | Wenn Sie Ihre Bezeichnungen migriert haben, der klassische Client aber immer noch installiert ist, verwenden Sie weiterhin die Azure-Portal, um Bezeichnungen und Richtlinien Einstellungen zu bearbeiten. Der klassische Client lädt weiterhin Bezeichnungen und Richtlinien Einstellungen von Azure herunter.
|Sowohl der klassische AIP- [Client](./rms-client/aip-client.md) als auch [Unified](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling) -Bezeichnungs Clients     | Wenn Sie beide Clients installiert haben, verwenden Sie die admin Centers oder die Azure-Portal, um Bezeichnungs Änderungen vorzunehmen. </br></br>Damit die klassischen Clients in den Admin Centers vorgenommene Bezeichnungs Änderungen abrufen können, kehren Sie zum Azure-Portal zurück, um Sie zu veröffentlichen. Wählen Sie im Bereich Azure-Portal > **Azure Information Protection-Unified-Bezeichnung** die Option **veröffentlichen**aus.  </br></br> Verwenden Sie weiterhin das Azure-Portal für die [zentrale Berichterstellung](reports-aip.md) und die [Überprüfung](deploy-aip-scanner.md).     |

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?

Azure Information Protection (AIP) bietet Klassifizierung, Bezeichnung und Schutz für Dokumente und e-Mails einer Organisation.

Der Inhalt wird mithilfe des Azure-Rights Management Dienstanbieter geschützt, der nun eine Komponente von aip ist. 

Weitere Informationen finden Sie unter [wie werden Daten geschützt](what-is-information-protection.md#how-aip-protects-your-data) und [Was ist Azure Rights Management?](what-is-azure-rms.md).

## <a name="whats-the-role-of-identity-management-for-azure-information-protection"></a>Was ist die Rolle der Identitätsverwaltung für Azure Information Protection?

Die Identitätsverwaltung ist eine wichtige Komponente von AIP, da Benutzer über einen gültigen Benutzernamen und ein Kennwort für den Zugriff auf geschützte Inhalte verfügen müssen.

Weitere Informationen zum Schutz Ihrer Daten mit Azure Information Protection finden Sie unter [Die Rolle von Azure Information Protection beim Schützen von Daten](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?

Weitere Informationen zu AIP-Abonnements finden Sie in der Abonnement-und Featureliste auf der [Azure Information Protection-Preis](https://azure.microsoft.com/pricing/details/information-protection) Seite.

Wenn Sie über ein Office 365-Abonnement verfügen, das Azure Rights Management Datenschutz umfasst, laden Sie das [Azure Information Protection Lizenzierungs DataSet](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) herunter, um weitere Informationen zur Integration von AIP zu erhalten.

Haben Sie noch Fragen zur Lizenzierung? Möglicherweise finden Sie passende Antworten im Abschnitt [Häufig gestellte Fragen zur Lizenzierung](https://azure.microsoft.com/pricing/details/information-protection#faq).

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Ist der Azure Information Protection-Client nur für Abonnements geeignet, die Funktionen für Klassifizierung und Bezeichnung umfassen?

Nein. Der klassische AIP-Client kann auch mit Abonnements verwendet werden, die nur den Azure Rights Management-Dienst zum Schutz von Daten enthalten.

Wenn der klassische Client ohne eine Azure Information Protection Richtlinie installiert wird, wird der Client automatisch im reinen [Schutzmodus](./rms-client/client-protection-only-mode.md)betrieben, sodass Benutzer Rights Management Vorlagen und benutzerdefinierte Berechtigungen anwenden können. 

Wenn Sie zu einem späteren Zeitpunkt ein Abonnement erwerben, das Klassifizierungen und Bezeichnungen umfasst, wechselt der Client beim Herunterladen der Azure Informationen Protection-Richtlinie automatisch in den Standardmodus.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?

Globale Administratoren für einen Office 365- oder Azure AD-Mandanten können alle administrativen Aufgaben für Azure Information Protection ausführen. 

Wenn Sie jedoch anderen Benutzern Administrator Berechtigungen zuweisen möchten, verwenden Sie dazu die folgenden Rollen:

- [Azure Information Protection-Administrator](#azure-information-protection-administrator)
- [Administrator für Compliance-oder Kompatibilitäts Daten](#compliance-administrator-or-compliance-data-administrator)
- [Sicherheits Leser oder globaler Reader](#security-reader-or-global-reader)
- [Sicherheitsadministrator](#security-administrator)
- [Azure Rights Management globaler Administrator und Connector-Administrator](#azure-rights-management-global-administrator-and-connector-administrator)

Beachten Sie außerdem Folgendes, wenn Sie administrative Aufgaben und Rollen verwalten:

|Thema  |Details  |
|---------|---------|
|**Unterstützte Kontotypen**     | Microsoft-Konten werden für die delegierte Administration von Azure Information Protection nicht unterstützt, auch wenn diese Konten einer der aufgeführten Administrator Rollen zugewiesen sind.         |
|**Onboarding-Steuerelemente**     |Wenn Sie [Onboardingsteuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, wird die Möglichkeit zum Verwalten von Azure Information Protection mit Ausnahme des RMS-Connectors durch diese Konfiguration nicht beeinflusst. </br></br>Wenn Sie z. b. onboardingsteuerelemente konfiguriert haben, sodass die Möglichkeit zum Schützen von Inhalten auf die *IT-Abteilungs* Gruppe beschränkt ist, muss das Konto, das zum Installieren und Konfigurieren des RMS-Verbindungs Dienst verwendet wird, ein Mitglied dieser Gruppe sein.          |
|**Entfernen des Schutzes**     |  Administratoren können nicht automatisch den Schutz von Dokumenten oder e-Mails entfernen, die durch Azure Information Protection geschützt wurden. </br></br>Nur Benutzer, die als Super Benutzer zugewiesen sind, können den Schutz entfernen, und zwar nur, wenn die Administrator Funktion aktiviert ist. </br></br>Alle Benutzer mit Administrator Berechtigungen für Azure Information Protection können die Administrator Funktion aktivieren und Benutzer als Administratoren zuweisen, einschließlich ihres eigenen Kontos. </br></br>Diese Aktionen werden in einem Administratorprotokoll aufgezeichnet. </br></br>Weitere Informationen finden Sie im Abschnitt bewährte Sicherheitsmethoden unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](configure-super-users.md). 
       |
|**Migrieren zum vereinheitlichten Bezeichnungs Speicher**      |  Wenn Sie die Azure Information Protection Bezeichnungen in den einheitlichen Bezeichnungs Speicher migrieren, lesen Sie den folgenden Abschnitt aus der Dokumentation zur Bezeichnung Migration: </br>[Administrative Rollen, die die vereinheitlichte Bezeichnung-Plattform unterstützen](configure-policy-migrate-labels.md#administrative-roles-that-support-the-unified-labeling-platform).
       |

### <a name="azure-information-protection-administrator"></a>Azure Information Protection-Administrator

Mit dieser Azure Active Directory Administrator Rolle kann ein Administrator Azure Information Protection, aber keine anderen Dienste konfigurieren. 

Administratoren mit dieser Rolle können folgende Aktionen ausführen:

- Aktivieren und Deaktivieren des Azure Rights Management Protection Service
- Konfigurieren von Schutzeinstellungen und Bezeichnungen
- Konfigurieren der Azure Information Protection-Richtlinie
- Führen Sie alle PowerShell-Cmdlets für den [Azure Information Protection Client](./rms-client/client-admin-guide-powershell.md) und das [aipservice-Modul](administer-powershell.md) aus.
    
Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

> [!NOTE]
> Diese Rolle bietet keine Unterstützung für das Nachverfolgen und Sperren von Dokumenten für Benutzer. Sie wird im Azure-Portal nicht unterstützt, wenn sich Ihr Mandant auf der [Unified-Bezeichnung-Plattform](#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)befindet.
    
### <a name="compliance-administrator-or-compliance-data-administrator"></a>Administrator für Compliance-oder Kompatibilitäts Daten

Diese Azure Active Directory Administrator Rollen ermöglichen Administratoren Folgendes:

- Konfigurieren von Azure Information Protection, einschließlich aktivieren und Deaktivieren des Azure Rights Management Protection Service
- Konfigurieren von Schutzeinstellungen und Bezeichnungen
- Konfigurieren der Azure Information Protection-Richtlinie
- Führen Sie alle PowerShell-Cmdlets für den [Azure Information Protection Client](./rms-client/client-admin-guide-powershell.md) und das [aipservice-Modul](administer-powershell.md)aus. 

Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). 

Weitere Informationen zu den Berechtigungen, die ein Benutzer mit diesen Rollen besitzt, finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

> [!NOTE]
> Diese Rollen unterstützen nicht das Nachverfolgen und widerrufen von Dokumenten für Benutzer.
>     
    
### <a name="security-reader-or-global-reader"></a>Sicherheits Leser oder globaler Reader

Diese Rollen werden nur für [Azure Information Protection Analyse](reports-aip.md) verwendet und ermöglichen Administratoren Folgendes:

- Anzeigen der Verwendung ihrer Bezeichnungen
- Überwachen des Benutzer Zugriffs auf bezeichnete Dokumente und e-Mails
- An der Klassifizierung vorgenommene Änderungen anzeigen
- Identifizieren Sie Dokumente, die vertrauliche Informationen enthalten, die geschützt werden müssen. 

Da dieses Feature Azure Monitor verwendet, müssen Sie auch über eine unterstützende [RBAC-Rolle](reports-aip.md#permissions-required-for-azure-information-protection-analytics)verfügen.

### <a name="security-administrator"></a>Sicherheitsadministrator

Mit dieser Azure Active Directory Administrator Rolle können Administratoren Azure Information Protection in der Azure-Portal und einige Aspekte anderer Azure-Dienste konfigurieren. 

Administratoren mit dieser Rolle können keine [PowerShell-Cmdlets aus dem aipservice-Modul](administer-powershell.md)ausführen oder Dokumente für Benutzer nachverfolgen und widerrufen.
    
Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). 

Weitere Informationen zu den Berechtigungen, über die ein Benutzer mit dieser Rolle verfügt, finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

### <a name="azure-rights-management-global-administrator-and-connector-administrator"></a>Azure Rights Management globaler Administrator und Connector-Administrator

Mit der Rolle "globaler Administrator" können Benutzer alle [PowerShell-Cmdlets aus dem aipservice-Modul](administer-powershell.md) ausführen, ohne Sie als globaler Administrator für andere Clouddienste zu erstellen.

Mit der Rolle "Connector-Administrator" können Benutzer nur den Rights Management (RMS)-Connector ausführen. 

Diese Administrator Rollen gewähren keinen Berechtigungen für Verwaltungs Konsolen oder unterstützen das Nachverfolgen und widerrufen von Dokumenten für Benutzer.
    
Wenn Sie eine dieser administrativen Rollen zuweisen möchten, verwenden Sie das PowerShell-Cmdlet "aipservice", " [Add-aipservicerolebasedadministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator)".

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Unterstützt Azure Information Protection lokale und hybride Szenarios?

Ja. Obwohl Azure Information Protection eine cloudbasierte Lösung ist, können damit Dokumente und E-Mails, die sowohl lokal als auch in der Cloud gespeichert sind, klassifiziert, bezeichnet und geschützt werden.

Wenn Sie über Exchange Server, SharePoint Server und Windows-Dateiserver verfügen, verwenden Sie eine oder beide der folgenden Methoden:

- Stellen Sie den [Rights Management Connector](deploy-rms-connector.md) bereit, sodass diese lokalen Server den Azure Rights Management-Dienst zum Schutz Ihrer e-Mails und Dokumente verwenden können.
- Synchronisieren Sie Ihre Active Directory Domänen Controller mit Azure AD, um eine nahtlose Authentifizierung für Benutzer zu ermöglichen. Verwenden Sie z. b. [Azure AD Connect](/azure/active-directory/hybrid/whatis-azure-ad-connect).

Der Azure Rights Management-Dienst generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf, sodass keine lokale PKI verwendet wird. 

Weitere Informationen zur Verwendung von Zertifikaten in Azure Rights Management finden Sie in der exemplarischen Vorgehens [Weise zur Funktionsweise von Azure RMS: erste Verwendung, Inhalts Schutz, Inhalts Verbrauch](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption).

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Welche Arten von Daten können von Azure Information Protection klassifiziert und geschützt werden?

Azure Information Protection kann E-Mails und Dokumente klassifizieren und schützen, egal ob sie lokal oder in der Cloud gespeichert sind. Diese Dokumente können z.B. Word-Dokumente, Excel-Tabellen, PowerPoint-Präsentationen, PDF-Dokumente, textbasierte Dateien und Bilddateien sein. 

Weitere Informationen finden Sie [unter Unterstützte vollständige Listen Dateitypen](./rms-client/clientv2-admin-guide-file-types.md).

> [!NOTE]
> Azure Information Protection können keine strukturierten Daten (z. b. Datenbankdateien, Kalender Elemente, Yammer-Beiträge, Sway-Inhalte und OneNote-Notebooks) klassifizieren und schützen.
> 

> [!TIP]
> Power BI unterstützt jetzt die Klassifizierung mithilfe von Vertraulichkeits Bezeichnungen und kann den Schutz von diesen Bezeichnungen auf Daten anwenden, die in die folgenden Dateiformate exportiert werden: PDF, XLS und. ppt. Weitere Informationen finden Sie unter [Datenschutz in Power BI (Vorschau)](https://docs.microsoft.com/power-bi/admin/service-security-data-protection-overview).
> 
## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?

Das ist richtig. Für die Vorschauversion wird jetzt angeboten, bedingten Zugriff auf Azure AD für Azure Information Protection zu konfigurieren.

Wenn ein Benutzer ein durch Azure Information Protection geschütztes Dokument öffnet, können Administratoren jetzt basierend auf der bedingten Standardzugriffssteuerung Benutzern den Zugriff in ihrem Mandanten verweigern oder gewähren. Die mehrstufige Authentifizierung (MFA) ist eine der am häufigsten verlangten Bedingungen. Eine weitere ist, dass Geräte [mit Ihren Intune-Richtlinien kompatibel](/intune/conditional-access-intune-common-ways-use) sein müssen, damit Mobilgeräte zum Beispiel Ihren Kennwortanforderungen entsprechen, und eine Minimalversion eines Betriebssystems sowie Computer müssen mit einer Domäne verbunden sein.

Weitere Informationen und einige detaillierte Beispiele finden Sie in dem folgenden Blogbeitrag: [Conditional Access policies for Azure Information Protection (Richtlinien zum bedingten Zugriff für Azure Information Protection)](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Zusätzliche Informationen:

|Thema  |Details  |
|---------|---------|
|**Auswertungs Häufigkeit**    | Bei Windows-Computern und der aktuellen Vorschauversion werden die Richtlinien für den bedingten Zugriff für Azure Information Protection ausgewertet, wenn die [Benutzerumgebung initialisiert wird](./how-does-it-work.md#initializing-the-user-environment) (dieser Prozess wird auch als bootstrapping bezeichnet), und dann alle 30 Tage.</br></br>Um zu optimieren, wie oft Ihre Richtlinien für den bedingten Zugriff ausgewertet werden, konfigurieren Sie die Gültigkeits [Dauer des](/azure/active-directory/active-directory-configurable-token-lifetimes)Tokens.       |
|**Administratorkonten**     |Es wird empfohlen, dass Sie Ihren Richtlinien für den bedingten Zugriff keine Administrator Konten hinzufügen, da diese Konten nicht auf den Bereich Azure Information Protection im Azure-Portal zugreifen können.         |
|**MFA-und B2B-Zusammenarbeit**     | Wenn Sie MFA in Ihren Richtlinien für bedingten Zugriff für die Zusammenarbeit mit anderen Unternehmen (B2B) verwenden, müssen Sie [Azure AD B2B-Zusammenarbeit](/azure/active-directory/b2b/what-is-b2b) verwenden und Gastkonten für die Benutzer erstellen, mit denen Sie in dem anderen Unternehmen zusammenarbeiten möchten.        |
|**Eingabe Aufforderungen für Nutzungsbedingungen**     |  Mit der Azure AD Vorschauversion vom Dezember 2018 können Sie [Benutzer auffordern, Nutzungsbedingungen zu akzeptieren](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Updates-to-Azure-AD-Terms-of-Use-functionality-within/ba-p/294822) , bevor Sie ein geschütztes Dokument zum ersten Mal öffnen.       |
|**Cloud-Apps**     |  Wenn Sie für den bedingten Zugriff auf mehrere Cloud-Apps zurückgreifen, wird Ihnen unter Umständen **Microsoft Azure Information Protection** nicht in der Auswahlliste angezeigt. </br></br>Verwenden Sie in diesem Fall das Suchfeld oben in der Liste. Geben Sie „Microsoft Azure Information Protection“ ein, um die verfügbaren Apps zu filtern. Sofern Sie über ein unterstütztes Abonnement verfügen, können Sie nun **Microsoft Azure Information Protection** auswählen.        |


## <a name="i-see-azure-information-protection-is-listed-as-a-security-provider-for-microsoft-graph-securityhow-does-this-work-and-what-alerts-will-i-receive"></a>Ich sehe, dass Azure Information Protection als Sicherheitsanbieter für Microsoft Graph Security aufgeführt wird. Wie funktioniert das, und welche Warnungen erhalte ich?

Das ist richtig. Als Angebot für die öffentliche Vorschauversion können Sie jetzt eine **Warnung zu anomalem Datenzugriff in Azure Information Protection** erhalten. Diese Warnung wird bei ungewöhnlichen Versuchen ausgelöst, auf Daten zuzugreifen, die von Azure Information Protection geschützt werden. Ein Beispiel hierfür ist der Zugriff auf eine ungewöhnlich große Datenmenge zu einer ungewöhnlichen Tageszeit oder von einem unbekannten Standort aus.

Anhand solcher Warnungen können Sie fortgeschrittene datenbezogene Angriffe und Bedrohungen durch Insider in Ihrer Umgebung erkennen. Diese Warnungen verwenden Machine Learning, um ein Verhaltensprofil der Benutzer zu erstellen, die auf Ihre geschützten Daten zugreifen. 

Die Azure Information Protection-Warnungen sind über die [Microsoft Graph Security-API](https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/security-api-overview) verfügbar, oder Sie können Azure Monitor verwenden, um Warnungen an SIEM-Lösungen wie z.B. Splunk und IBM Qradar zu [streamen](https://developer.microsoft.com/graph/docs/concepts/security_siemintegration).

Weitere Informationen zur Microsoft Graph Security-API finden Sie in der [Übersicht zur Microsoft Graph Security-API](https://developer.microsoft.com/graph/docs/concepts/security-concept-overview).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>Worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?

Die Windows Server-Dateiklassifizierungsinfrastruktur war eine Option, um Dokumente zu klassifizieren und diese dann mithilfe des [Rights Management-Connectors](deploy-rms-connector.md) (nur Office-Dokumente) oder einem [PowerShell-Skript](./rms-client/configure-fci.md) (alle Dateitypen) zu schützen. 

Jetzt können Sie die empfohlene [Azure Information Protection-Überprüfung](deploy-aip-scanner.md) verwenden. Die Überprüfung nutzt den Azure Information Protection-Client und Ihre Azure Information Protection-Richtlinie, um Dokumente (alle Dateitypen) zu bezeichnen, sodass diese Dokumente alle klassifiziert und optional auch geschützt werden.

Zwischen den beiden Lösungen bestehen die folgenden wesentlichen Unterschiede:

|  |Windows Server-Dateiklassifizierungsinfrastruktur  |Azure Information Protection-Überprüfung  |
|---------|---------|---------|
|**Unterstützte Datenspeicher**    | Lokale Ordner unter Windows Server        | – Windows-Dateifreigaben und Network Attached Storage<br /></br>– SharePoint Server 2016 und SharePoint Server 2013 SharePoint Server 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.        |
|**Betriebsmodus**     |Echtzeit         |Die Datenspeicher werden systematisch einmal oder wiederholt durchsucht.         |
|**Unterstützte Dateitypen**     | – Standardmäßig werden alle Dateitypen geschützt. <br /><br />– Bestimmte Dateitypen können vom Schutz ausgeschlossen werden, indem Sie die Registrierung bearbeiten.|Unterstützung für Dateitypen: <br /><br />– Die Office-Dateiformate und PDF-Dokumente werden standardmäßig geschützt. <br /><br />– Weitere Dateitypen können ebenfalls geschützt werden, indem Sie die Registrierung bearbeiten.|

### <a name="setting-rights-management-owners"></a>Festlegen von Rights Management Besitzern

Standardmäßig wird für die Windows Server-FCI und den Azure Information Protection Scanner der [Rights Management Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) auf das Konto festgelegt, mit dem die Datei geschützt wird.

Überschreiben Sie die Standardeinstellungen wie folgt:

- **Windows Server-FCI**: Legen Sie für den Rights Management Besitzer ein einzelnes Konto für alle Dateien fest, oder legen Sie den Rights Management Besitzer für jede Datei dynamisch fest. 

    Um den Rights Management-Besitzer dynamisch festzulegen, verwenden Sie den Parameter **-OwnerMail [Source File Owner Email]** und seinen Wert. Durch diese Konfiguration wird die E-Mail-Adresse des Benutzers von Active Directory mithilfe des Benutzerkontonamens in der Owner-Eigenschaft der Datei abgerufen.

- **Azure Information Protection Scanner:** Legen Sie für neu geschützte Dateien für den Rights Management Besitzer ein einzelnes Konto für alle Dateien in einem angegebenen Datenspeicher fest, indem Sie die Einstellung **-Standard Besitzer** im Überprüfungs Profil angeben. 

    Das dynamische Festlegen des Rights Management Besitzers für jede Datei wird nicht unterstützt, und der Besitzer der Rights Management wird für zuvor geschützte Dateien nicht geändert. 

    > [!NOTE]
    > Wenn der Scanner Dateien auf Websites und in Bibliotheken von SharePoint schützt, wird der Rights Management-Besitzer dynamisch für jede Datei mithilfe des SharePoint-Editorwerts festgelegt.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Ich habe gehört, dass ein neues Release bald verfügbar ist, für Azure Information Protection – wann wird es veröffentlicht?

Die technische Dokumentation enthält keine Informationen zu bevorstehenden Releases. Informationen zu dieser Art von Informationen finden Sie in der [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?&filters=Azure%20Information%20Protection%2CO365%20Information%20Protection#owRoadmapMainContent)im [Enterprise Mobility + Security Blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Ist Azure Information Protection für mein Land geeignet?

Verschiedene Länder haben unterschiedliche Anforderungen und Bestimmungen. Auf der Seite [Suitability for different countries (Eignung für unterschiedliche Länder)](./compliance.md#suitability-for-different-countries) finden Sie Antworten zu den Fragen für Ihre Organisation.

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Wie kann Azure Information Protection bei der Datenschutz-Grundverordnung (DSGVO) helfen?

Informationen darüber, wie Azure Information Protection Ihnen bei der Umsetzung der Datenschutz-Grundverordnung (DSGVO) helfen kann, finden Sie im folgenden Blogbeitrag (inklusive Video): 

[Microsoft 365 bietet eine Strategie zum Schutz von Daten, um die dsgvo zu unterstützen.](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr)

## <a name="where-can-i-find-supporting-information-for-azureinformation-protectionsuch-as-legal-compliance-and-slas"></a>Wo finde ich weitere Informationen zu Azure Information Protection, z.B. rechtliche Hinweise, Informationen zur Compliance und SLAs?
Lesen Sie hierzu [Kompatibilitätsinformationen und ergänzende Informationen zu Azure Information Protection](./compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Wie kann ich ein Problem melden oder Feedback zu Azure Information Protection übermitteln?

Wenden Sie sich an Ihre Standardsupportkanäle oder an den [Microsoft Support](information-support.md#to-contact-microsoft-support), um technischen Support zu erhalten.

Wir laden Sie auch dazu ein, sich mit unserem Engineering-Team auf seiner [Yammer-Website zu Azure Information Protection](https://www.yammer.com/askipteam/) in Verbindung zu setzen. 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Was kann ich tun, wenn meine Frage hier nicht angezeigt wird?

Überprüfen Sie zunächst die unten aufgeführten häufig gestellten Fragen, die für die Klassifizierung und Bezeichnung spezifisch sind bzw. für die Datensicherheit spezifisch sind. Der [Azure Rights Management-Dienst (Azure RMS)](what-is-azure-rms.md) stellt die Datenschutztechnologie für Azure Information Protection bereit. Azure RMS kann zusammen mit einer Klassifizierung oder Bezeichnung verwendet werden. Es kann aber auch eigenständig genutzt werden. 

- [Häufig gestellte Fragen zur Klassifizierung und Kennzeichnung](faqs-infoprotect.md)

- [Häufig gestellte Fragen zum Datenschutz](faqs-rms.md)

Wenn Ihre Frage nicht beantwortet wird, lesen Sie die Links und Ressourcen, die unter [Informationen und Support für Azure Information Protection](information-support.md)aufgeführt sind.

Darüber hinaus gibt es häufig gestellte Fragen (FAQs) für Benutzer:

- [Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android](./rms-client/mobile-app-faq.md)

- [Häufig gestellte Fragen (FAQ) zur RMS-Freigabeanwendung für Mac-Computer](https://technet.microsoft.com/dn451248)

