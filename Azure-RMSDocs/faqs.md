---
title: Häufig gestellte Fragen zu Azure Information Protection
description: Einige häufig gestellte Fragen zu Azure Information Protection und dem dazugehörigen Schutzdienst, Azure Rights Management (Azure RMS).
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/02/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: c42f2459861b7b7167469ddadd7c3ff399d47f48
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97381958"
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Häufig gestellte Fragen zu Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Haben Sie eine Frage zu Azure Information Protection oder zum Azure Rights Management-Dienst (Azure RMS)? Vielleicht finden Sie hier eine Antwort.

## <a name="whats-the-difference-between-azure-information-protection-and-microsoft-information-protection"></a>Was ist der Unterschied zwischen Azure Information Protection und Microsoft Information Protection?

Im Gegensatz zu Azure Information Protection ist [Microsoft Information Protection](https://www.microsoft.com/security/business/information-protection) kein Abonnement oder Produkt, das Sie kaufen können. Stattdessen handelt es sich um ein Framework für Produkte und integrierte Funktionen, mit denen Sie die sensiblen Informationen Ihrer Organisation schützen können.

Zu den **Microsoft Information Protection-Produkten gehören**:
- Azure Information Protection
- Microsoft 365 Information Protection, z. b. Microsoft 365 DLP
- Windows Information Protection
- Microsoft Cloud App Security

Zu den **Funktionen von Microsoft Information Protection gehören**:
- Unified Label-Verwaltung
- In Office-Apps integrierte Endbenutzer-Beschriftungen
- Die Fähigkeit von Windows, einheitliche Bezeichnungen zu verstehen und Schutz auf Daten anzuwenden
- Das Microsoft Information Protection SDK
- Funktionalität in Adobe Acrobat Reader zum Anzeigen von beschrifteten und geschützten PDF-Informationen

Weitere Informationen finden [Sie unter Information Protection-Funktionen zum Schutz Ihrer sensiblen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

## <a name="whats-the-difference-between-labels-in-microsoft-365-and-labels-in-azure-information-protection"></a>Worin besteht der Unterschied zwischen Bezeichnungen in Microsoft 365 und Bezeichnungen in Azure Information Protection?

Ursprünglich verfügten Microsoft 365 nur über [Beibehaltungs Bezeichnungen](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30), mit denen Sie Dokumente und e-Mails für die Überwachung und Aufbewahrung klassifizieren konnten, als dieser Inhalt in Microsoft 365 Services gespeichert war. 

Im Gegensatz dazu konnten Azure Information Protection Bezeichnungen, die zum Zeitpunkt der Verwendung des klassischen AIP-Clients in der Azure-Portal konfiguriert wurden, eine konsistente Klassifizierung und Schutzrichtlinie für Dokumente und e-Mails anwenden, unabhängig davon, ob Sie lokal oder in der Cloud gespeichert wurden.

Microsoft 365 unterstützt jetzt neben Aufbewahrungs Bezeichnungen auch [Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) . Vertraulichkeits Bezeichnungen können in den folgenden admin Centers erstellt und konfiguriert werden:

- Office 365 Security & Compliance Center
- Microsoft 365 Security Center
- Microsoft 365 Compliance Center

Wenn Sie im Azure-Portal ältere AIP-Bezeichnungen konfiguriert haben, empfiehlt es sich, diese zu Vertraulichkeits Bezeichnungen und zum vereinheitlichten Bezeichnungs Client zu migrieren. Weitere Informationen finden Sie unter [Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen](tutorial-migrating-to-ul.md).

Weitere Informationen finden Sie unter [Bekanntgabe der Verfügbarkeit von Information Protection-Funktionen zum Schutz von vertraulichen Daten](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

## <a name="how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform"></a>Wie kann ich feststellen, ob mein Mandant auf der Unified-Bezeichnung-Plattform ist?

Wenn sich Ihr Mandant auf der Unified Label-Plattform befindet, werden Vertraulichkeits Bezeichnungen unterstützt, die von [Clients und Diensten verwendet werden können, die eine einheitliche Bezeichnung unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling). Wenn Sie Ihr Abonnement für Azure Information Protection im Juni 2019 oder höher erhalten haben, befindet sich Ihr Mandant automatisch auf der Unified-Bezeichnung-Plattform, und es ist keine weitere Aktion erforderlich. Ihr Mandant kann sich auch auf dieser Plattform befinden, da die Azure Information Protection Bezeichnungen migriert wurden.

Wenn sich Ihr Mandant nicht auf der Unified-Beschriftungs Plattform befindet, wird das folgende Informations Banner in der Azure-Portal auf den **Azure Information Protection** Bereichen angezeigt:

![Banner für Migrations Informationen](media/migration-status-banner.png)

Sie können auch prüfen, indem Sie zu **Azure Information Protection**  >  Unified-  >  **Bezeichnung** verwalten wechseln und den **einheitlichen** Bezeichnungs Status anzeigen:

|Status |Beschreibung  |
|---------|---------|
|**Aktiviert**     |  Ihr Mandant befindet sich auf der Unified-Beschriftungs Plattform. <br />Sie können Bezeichnungen im Microsoft 365 Compliance Center [erstellen, konfigurieren und veröffentlichen](/microsoft-365/compliance/create-sensitivity-labels) .       |
|**Nicht aktiviert**    |  Ihr Mandant befindet sich nicht auf der Unified-Beschriftungs Plattform. <br />Migrations Anweisungen und Anleitungen finden Sie unter [Migrieren von Azure Information Protection Bezeichnungen zu Unified Sensitivität-Bezeichnungen](configure-policy-migrate-labels.md).       |
| | |

## <a name="whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients"></a>Worin besteht der Unterschied zwischen den Azure Information Protection klassischen und vereinheitlichten Bezeichnungs Clients?

Der Legacy-Azure Information Protection Client (als *klassischer* Client bezeichnet) lädt Bezeichnungen und Richtlinien Einstellungen von Azure herunter und ermöglicht es Ihnen, die [AIP-Richtlinie](overview-policy.md) aus dem Azure-Portal zu konfigurieren.

Der *Unified* -Bezeichnungs Client ist der aktuellste Client mit den neuesten Updates und unterstützt die einheitliche Beschriftungs Plattform, die von mehreren Anwendungen und Diensten verwendet wird. Der Unified Label-Client lädt [Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) und Richtlinien Einstellungen aus den folgenden admin Centers herunter:

- Office 365 Security & Compliance Center
- Microsoft 365 Security Center
- Microsoft 365 Compliance Center

Wenn Sie Administrator sind, finden Sie weitere Informationen unter [Auswählen der Windows-Bezeichnung](rms-client/use-client.md#choose-your-windows-labeling-solution).

### <a name="classic-client-deprecation"></a>Veraltung des klassischen Clients

Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden die **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. 

Nach der Veraltung wird der Client weiterhin erwartungsgemäß ausgeführt. Allerdings können Administratoren die Richtlinien im Portal nicht aktualisieren, und es werden keine Korrekturen oder Änderungen für den klassischen Client bereitgestellt.

Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn Sie den klassischen Client zurzeit bereitgestellt haben, wird empfohlen, ein Upgrade auf den Unified-Bezeichnungs Client auszuführen. Weitere Informationen finden Sie unter.

- [Tutorial: Migrieren vom klassischen Client zum Unified-Bezeichnungs Client](tutorial-migrating-to-ul.md)
- [Vorgehensweise beim Migrieren von Azure Information Protection Bezeichnungen zu vereinheitlichten Vertraulichkeits Bezeichnungen](configure-policy-migrate-labels.md)
### <a name="identify-the-client-you-have-installed"></a>Identifizieren Sie den Client, den Sie installiert haben.

Wenn Sie ein Benutzer sind, der wissen möchte, ob der klassische oder der Unified-Bezeichnung-Client installiert ist, können Sie einen der folgenden Schritte ausführen:

- Überprüfen Sie in Ihren Office-Apps, ob die Symbolleisten Schaltfläche **Sensitivität** oder **Schutz** Der Unified-Bezeichnungs Client zeigt die **Vertraulichkeits** :::image type="icon" source="media/i-sensitivity.PNG" border="false"::: Schaltfläche an, während der klassische Client die Schaltfläche **schützen** anzeigt. 

- Überprüfen Sie die Versionsnummer für die Azure Information Protection Anwendung, die Sie installiert haben.

    - In den Versionen **1. x** wird angegeben, dass Sie über den klassischen Client verfügen. Beispiel: **1.54.59.0**
    - In Version **2. x** wird angegeben, dass Sie über den Unified-Bezeichnungs Client verfügen. Beispiel: **2.8.85.0**

    Scrollen Sie z. b. im Bereich **Windows-Einstellungen > apps und Features** nach unten zur **Microsoft Azure Information Protection** Anwendung, und überprüfen Sie die Versionsnummer.

    :::image type="content" source="media/client-about.png" alt-text="Überprüfen Sie die Azure Information Protection Client Version.":::

## <a name="when-is-the-right-time-to-migrate-my-labels"></a>Wann ist der richtige Zeitpunkt für die Migration meiner Bezeichnungen?

Es wird empfohlen, dass Sie Ihre Azure Information Protection Bezeichnungen zu der Unified Label-Plattform migrieren, sodass Sie Sie als Vertraulichkeits Bezeichnungen mit anderen [Clients und Diensten verwenden können, die vereinheitlichte Bezeichnungen unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

Weitere Informationen und Anweisungen finden Sie unter [Migrieren von Azure Information Protection Bezeichnungen zu Unified Sensitivität-Bezeichnungen](configure-policy-migrate-labels.md).

## <a name="after-ive-migrated-my-labels-which-management-portal-do-i-use"></a>Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?

Nachdem Sie Ihre Bezeichnungen in der Azure-Portal migriert haben, können Sie Sie abhängig von den installierten Clients weiterhin an einem der folgenden Speicherorte verwalten:

|Client  |Beschreibung  |
|---------|---------|
|[Einheitliche Bezeichnung für Clients und Dienste](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling)    |  Wenn Sie nur Unified Label-Clients installiert haben, verwalten Sie Ihre Bezeichnungen in einem der Admin Center: Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center. Die Bezeichnungen und Richtlinieneinstellungen werden von Clients für einheitliche Bezeichnungen aus diesen Admin-Centers heruntergeladen. <br /><br />Anweisungen finden Sie unter [Erstellen und Konfigurieren von Vertraulichkeits Bezeichnungen und ihren Richtlinien](/microsoft-365/compliance/create-sensitivity-labels).     |
|Nur [klassischer Client](./rms-client/aip-client.md)  | Wenn Sie Ihre Bezeichnungen migriert haben, der klassische Client aber immer noch installiert ist, verwenden Sie weiterhin die Azure-Portal, um Bezeichnungen und Richtlinien Einstellungen zu bearbeiten. Der klassische Client lädt weiterhin Bezeichnungen und Richtlinien Einstellungen von Azure herunter.
|Sowohl der klassische AIP- [Client](./rms-client/aip-client.md) als auch [Unified](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling) -Bezeichnungs Clients     | Wenn Sie beide Clients installiert haben, verwenden Sie die admin Centers oder die Azure-Portal, um Bezeichnungs Änderungen vorzunehmen. <br /><br />Damit die klassischen Clients in den Admin Centers vorgenommene Bezeichnungs Änderungen abrufen können, kehren Sie zum Azure-Portal zurück, um Sie zu veröffentlichen. Wählen Sie im Bereich Azure-Portal > **Azure Information Protection-Unified-Bezeichnung** die Option **veröffentlichen** aus.  <br /><br /> Verwenden Sie weiterhin das Azure-Portal für die [zentrale Berichterstellung](reports-aip.md) und die [Überprüfung](deploy-aip-scanner.md).     |
| | |

## <a name="do-i-need-to-re-encrypt-my-files-after-moving-to-sensitivity-labels-and-the-unified-labeling-platform"></a>Muss ich meine Dateien nach dem Wechsel zu Vertraulichkeits Bezeichnungen und der vereinheitlichten Beschriftungs Plattform erneut verschlüsseln?

Nein, Sie müssen Ihre Dateien nach dem Wechsel zu Vertraulichkeits Bezeichnungen und der Unified Label-Plattform nach der Migration vom klassischen AIP-Client und den im Azure-Portal verwalteten Bezeichnungen nicht erneut verschlüsseln.

Nachdem Sie die Migration durchführen, können Sie Ihre Bezeichnungen verwalten und Richtlinien von ihrer Bezeichnung Admin Center, einschließlich Microsoft Security Center, Microsoft Compliance Center oder Microsoft Security & Compliance Center, bezeichnen. 

Weitere Informationen finden Sie unter Informationen [zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) in der Microsoft 365-Dokumentation und im Blog zum Grundlegendes zur [Migration vereinheitlichte](https://techcommunity.microsoft.com/t5/microsoft-security-and/understanding-unified-labeling-migration/ba-p/783185) Bezeichnungen.


## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?

Azure Information Protection (AIP) bietet Klassifizierung, Bezeichnung und Schutz für Dokumente und e-Mails einer Organisation.

Der Inhalt wird mithilfe des Azure-Rights Management Dienstanbieter geschützt, der nun eine Komponente von aip ist. 

Weitere Informationen finden Sie unter [wie AIP schützt Ihre Daten](aip-classification-and-protection.md#how-aip-protects-your-data) und [Was ist Azure Rights Management?](what-is-azure-rms.md).

## <a name="whats-the-role-of-identity-management-for-azure-information-protection"></a>Was ist die Rolle der Identitätsverwaltung für Azure Information Protection?

Die Identitätsverwaltung ist eine wichtige Komponente von AIP, da Benutzer über einen gültigen Benutzernamen und ein Kennwort für den Zugriff auf geschützte Inhalte verfügen müssen.

Weitere Informationen zum Schutz Ihrer Daten mit Azure Information Protection finden Sie unter [Die Rolle von Azure Information Protection beim Schützen von Daten](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?

Weitere Informationen zu AIP-Abonnements finden Sie in der Abonnement-und Featureliste auf der [Azure Information Protection-Preis](https://azure.microsoft.com/pricing/details/information-protection) Seite.

Wenn Sie über ein Microsoft 365 Abonnement verfügen, das Azure Rights Management Datenschutz umfasst, laden Sie das Datenblatt für die [Azure Information Protection Lizenzierung](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) herunter, um weitere Informationen zur Integration von AIP zu erhalten.

Haben Sie noch Fragen zur Lizenzierung? Möglicherweise finden Sie passende Antworten im Abschnitt [Häufig gestellte Fragen zur Lizenzierung](https://azure.microsoft.com/pricing/details/information-protection#faq).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?

Globale Administratoren für einen Microsoft 365 Mandanten oder Azure AD Mandanten können natürlich alle administrativen Aufgaben für Azure Information Protection ausführen. 

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
|**Onboarding-Steuerelemente**     |Wenn Sie [Onboardingsteuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, wird die Möglichkeit zum Verwalten von Azure Information Protection mit Ausnahme des RMS-Connectors durch diese Konfiguration nicht beeinflusst. <br /><br />Wenn Sie z. b. onboardingsteuerelemente konfiguriert haben, sodass die Möglichkeit zum Schützen von Inhalten auf die *IT-Abteilungs* Gruppe beschränkt ist, muss das Konto, das zum Installieren und Konfigurieren des RMS-Verbindungs Dienst verwendet wird, ein Mitglied dieser Gruppe sein.          |
|**Entfernen des Schutzes**     |  Administratoren können nicht automatisch den Schutz von Dokumenten oder e-Mails entfernen, die durch Azure Information Protection geschützt wurden. <br /><br />Nur Benutzer, die als Super Benutzer zugewiesen sind, können den Schutz entfernen, und zwar nur, wenn die Administrator Funktion aktiviert ist. <br /><br />Alle Benutzer mit Administrator Berechtigungen für Azure Information Protection können die Administrator Funktion aktivieren und Benutzer als Administratoren zuweisen, einschließlich ihres eigenen Kontos.<br /><br />Diese Aktionen werden in einem Administratorprotokoll aufgezeichnet. <br /><br />Weitere Informationen finden Sie im Abschnitt bewährte Sicherheitsmethoden unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](configure-super-users.md). <br><br>**Tipp**: Wenn Ihre Inhalte in SharePoint oder onedrive gespeichert sind, können Administratoren das [Unlock-sensitivitylabelverschlüsseltedfile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedfile) -Cmdlet ausführen, um die Vertraulichkeits Bezeichnung und die Verschlüsselung zu entfernen. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files#remove-encryption-for-a-labeled-document). |
|**Migrieren zum vereinheitlichten Bezeichnungs Speicher**      |  Wenn Sie die Azure Information Protection Bezeichnungen in den einheitlichen Bezeichnungs Speicher migrieren, lesen Sie den folgenden Abschnitt aus der Dokumentation zur Bezeichnung Migration: <br />[Administrative Rollen, die die vereinheitlichte Bezeichnung-Plattform unterstützen](configure-policy-migrate-labels.md#administrative-roles-that-support-the-unified-labeling-platform). |
| | |
### <a name="azure-information-protection-administrator"></a>Azure Information Protection-Administrator

Mit dieser Azure Active Directory Administrator Rolle kann ein Administrator Azure Information Protection, aber keine anderen Dienste konfigurieren. 

Administratoren mit dieser Rolle können folgende Aktionen ausführen:

- Aktivieren und Deaktivieren des Azure Rights Management Protection Service
- Konfigurieren von Schutzeinstellungen und Bezeichnungen
- Konfigurieren der Azure Information Protection-Richtlinie
- Führen Sie alle PowerShell-Cmdlets für den [Azure Information Protection Client](./rms-client/clientv2-admin-guide-powershell.md) und das [aipservice-Modul](administer-powershell.md) aus.
    
Informationen darüber, wie Sie einem Benutzer diese Administratorrolle zuweisen, finden Sie unter [Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

> [!NOTE]
> Diese Rolle bietet keine Unterstützung für das Nachverfolgen und Sperren von Dokumenten für Benutzer. Sie wird im Azure-Portal nicht unterstützt, wenn sich Ihr Mandant auf der [Unified-Bezeichnung-Plattform](#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)befindet.
    
### <a name="compliance-administrator-or-compliance-data-administrator"></a>Administrator für Compliance-oder Kompatibilitäts Daten

Diese Azure Active Directory Administrator Rollen ermöglichen Administratoren Folgendes:

- Konfigurieren von Azure Information Protection, einschließlich aktivieren und Deaktivieren des Azure Rights Management Protection Service
- Konfigurieren von Schutzeinstellungen und Bezeichnungen
- Konfigurieren der Azure Information Protection-Richtlinie
- Führen Sie alle PowerShell-Cmdlets für den [Azure Information Protection Client](./rms-client/clientv2-admin-guide-powershell.md) und das [aipservice-Modul](administer-powershell.md)aus. 

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
> Power BI unterstützt die Klassifizierung mithilfe von Vertraulichkeits Bezeichnungen und kann den Schutz von diesen Bezeichnungen auf Daten anwenden, die in die folgenden Dateiformate exportiert werden: PDF, XLS und. ppt. Weitere Informationen finden Sie unter [Datenschutz in Power BI (Vorschauversion)](/power-bi/admin/service-security-data-protection-overview).
> 
## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?

Ja, als Vorschau Angebot können Sie Azure AD bedingten Zugriff für Azure Information Protection konfigurieren.

Wenn ein Benutzer ein durch Azure Information Protection geschütztes Dokument öffnet, können Administratoren jetzt basierend auf der bedingten Standardzugriffssteuerung Benutzern den Zugriff in ihrem Mandanten verweigern oder gewähren. Die mehrstufige Authentifizierung (MFA) ist eine der am häufigsten verlangten Bedingungen. Eine weitere ist, dass Geräte [mit Ihren Intune-Richtlinien kompatibel](/intune/protect/conditional-access-intune-common-ways-use) sein müssen, damit Mobilgeräte zum Beispiel Ihren Kennwortanforderungen entsprechen, und eine Minimalversion eines Betriebssystems sowie Computer müssen mit einer Domäne verbunden sein.

Weitere Informationen und einige detaillierte Beispiele finden Sie in dem folgenden Blogbeitrag: [Conditional Access policies for Azure Information Protection (Richtlinien zum bedingten Zugriff für Azure Information Protection)](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Zusätzliche Informationen:

|Thema  |Details  |
|---------|---------|
|**Auswertungshäufigkeit**    | Bei Windows-Computern und der aktuellen Vorschauversion werden die Richtlinien für den bedingten Zugriff für Azure Information Protection ausgewertet, wenn die [Benutzerumgebung initialisiert wird](./how-does-it-work.md#initializing-the-user-environment) (dieser Prozess wird auch als bootstrapping bezeichnet), und dann alle 30 Tage.<br /><br />Um zu optimieren, wie oft Ihre Richtlinien für den bedingten Zugriff ausgewertet werden, konfigurieren Sie die Gültigkeits [Dauer des](/azure/active-directory/active-directory-configurable-token-lifetimes)Tokens.       |
|**Administratorkonten**     |Es wird empfohlen, dass Sie Ihren Richtlinien für den bedingten Zugriff keine Administrator Konten hinzufügen, da diese Konten nicht auf den Bereich Azure Information Protection im Azure-Portal zugreifen können.         |
|**MFA-und B2B-Zusammenarbeit**     | Wenn Sie MFA in Ihren Richtlinien für bedingten Zugriff für die Zusammenarbeit mit anderen Unternehmen (B2B) verwenden, müssen Sie [Azure AD B2B-Zusammenarbeit](/azure/active-directory/b2b/what-is-b2b) verwenden und Gastkonten für die Benutzer erstellen, mit denen Sie in dem anderen Unternehmen zusammenarbeiten möchten.        |
|**Eingabe Aufforderungen für Nutzungsbedingungen**     |  Mit der Azure AD Vorschauversion vom Dezember 2018 können Sie [Benutzer auffordern, Nutzungsbedingungen zu akzeptieren](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Updates-to-Azure-AD-Terms-of-Use-functionality-within/ba-p/294822) , bevor Sie ein geschütztes Dokument zum ersten Mal öffnen.       |
|**Cloud-Apps**     |  Wenn Sie für den bedingten Zugriff auf mehrere Cloud-Apps zurückgreifen, wird Ihnen unter Umständen **Microsoft Azure Information Protection** nicht in der Auswahlliste angezeigt. <br /><br />Verwenden Sie in diesem Fall das Suchfeld oben in der Liste. Geben Sie „Microsoft Azure Information Protection“ ein, um die verfügbaren Apps zu filtern. Sofern Sie über ein unterstütztes Abonnement verfügen, können Sie nun **Microsoft Azure Information Protection** auswählen.        |
| | |

> [!NOTE]
> Die Azure Information Protection Unterstützung für den bedingten Zugriff befindet sich derzeit in der Vorschau Phase. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 
> 

## <a name="i-see-azure-information-protection-is-listed-as-a-security-provider-for-microsoft-graph-securityhow-does-this-work-and-what-alerts-will-i-receive"></a>Ich sehe, dass Azure Information Protection als Sicherheitsanbieter für Microsoft Graph Security aufgeführt wird. Wie funktioniert das, und welche Warnungen erhalte ich?

Das ist richtig. Als Angebot für die öffentliche Vorschauversion können Sie jetzt eine **Warnung zu anomalem Datenzugriff in Azure Information Protection** erhalten. Diese Warnung wird bei ungewöhnlichen Versuchen ausgelöst, auf Daten zuzugreifen, die von Azure Information Protection geschützt werden. Ein Beispiel hierfür ist der Zugriff auf eine ungewöhnlich große Datenmenge zu einer ungewöhnlichen Tageszeit oder von einem unbekannten Standort aus.

Anhand solcher Warnungen können Sie fortgeschrittene datenbezogene Angriffe und Bedrohungen durch Insider in Ihrer Umgebung erkennen. Diese Warnungen verwenden Machine Learning, um ein Verhaltensprofil der Benutzer zu erstellen, die auf Ihre geschützten Daten zugreifen. 

Die Azure Information Protection-Warnungen sind über die [Microsoft Graph Security-API](/graph/api/resources/security-api-overview) verfügbar, oder Sie können Azure Monitor verwenden, um Warnungen an SIEM-Lösungen wie z.B. Splunk und IBM Qradar zu [streamen](/graph/security-integration).

Weitere Informationen zur Microsoft Graph Security-API finden Sie in der [Übersicht zur Microsoft Graph Security-API](/graph/security-concept-overview).

> [!NOTE]
> Die Azure Information Protection Unterstützung für Microsoft Graph Sicherheit befindet sich derzeit in der Vorschau Phase. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 
> 

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Ich habe gehört, dass ein neues Release bald verfügbar ist, für Azure Information Protection – wann wird es veröffentlicht?

Die technische Dokumentation enthält keine Informationen zu bevorstehenden Releases. Informationen zu dieser Art von Informationen finden Sie in der [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?&filters=Azure%20Information%20Protection%2CO365%20Information%20Protection#owRoadmapMainContent)im [Enterprise Mobility + Security Blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Ist Azure Information Protection für mein Land geeignet?

Verschiedene Länder haben unterschiedliche Anforderungen und Bestimmungen. Auf der Seite [Suitability for different countries (Eignung für unterschiedliche Länder)](./compliance.md#suitability-for-different-countries) finden Sie Antworten zu den Fragen für Ihre Organisation.

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Wie kann Azure Information Protection bei der Datenschutz-Grundverordnung (DSGVO) helfen?

[!INCLUDE [gdpr-hybrid-note](includes/gdpr-hybrid-note.md)]

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>Wo finde ich weitere Informationen zu Azure Information Protection – z.B. rechtliche Hinweise, Informationen zur Konformität und SLAs?
Lesen Sie hierzu [Kompatibilitätsinformationen und ergänzende Informationen zu Azure Information Protection](./compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Wie kann ich ein Problem melden oder Feedback zu Azure Information Protection übermitteln?

Wenden Sie sich an Ihre Standardsupportkanäle oder an den [Microsoft Support](information-support.md#to-contact-microsoft-support), um technischen Support zu erhalten.

Wir laden Sie auch dazu ein, sich mit unserem Engineering-Team auf seiner [Yammer-Website zu Azure Information Protection](https://www.yammer.com/askipteam/) in Verbindung zu setzen. 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Was kann ich tun, wenn meine Frage hier nicht angezeigt wird?

Überprüfen Sie zunächst die unten aufgeführten häufig gestellten Fragen, die für die Klassifizierung und Bezeichnung spezifisch sind bzw. für die Datensicherheit spezifisch sind. Der [Azure Rights Management-Dienst (Azure RMS)](what-is-azure-rms.md) stellt die Datenschutztechnologie für Azure Information Protection bereit. Azure RMS kann zusammen mit einer Klassifizierung oder Bezeichnung verwendet werden. Es kann aber auch eigenständig genutzt werden. 

- [Häufig gestellte Fragen zur Klassifizierung und Kennzeichnung](faqs-infoprotect.md)

- [Häufig gestellte Fragen zum Datenschutz](faqs-rms.md)

- [Häufig gestellte Fragen zum klassischen Client](faqs-classic.md)

Wenn Ihre Frage nicht beantwortet wird, lesen Sie die Links und Ressourcen, die unter [Informationen und Support für Azure Information Protection](information-support.md)aufgeführt sind.
