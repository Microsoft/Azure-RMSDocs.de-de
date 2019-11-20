---
title: Zentrale Berichterstellung für Azure Information Protection
description: Erfahren Sie, wie Sie mithilfe der zentralen Berichterstellung die Übernahme Ihrer Azure Information Protection-Bezeichnungen nachverfolgen und Dateien mit vertraulichen Daten erkennen.
author: cabailey
ms.author: cabailey
ms.date: 11/19/2019
manager: rkarlin
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.subservice: analytics
ms.reviewer: lilukov
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: fbd1d4b2b25f9b681d0d25fac63038104bd4bb27
ms.sourcegitcommit: 13085ecbbd89193e949bd6cb49c448341911a972
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189195"
---
# <a name="central-reporting-for-azure-information-protection"></a>Zentrale Berichterstellung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Dieses Feature befindet sich in der Vorschau und unterliegt Änderungen.

Use Azure Information Protection analytics for central reporting to help you track the adoption of your labels that classify and protect your organization's data. Beachten Sie auch Folgendes:

- Unternehmensweite Überwachung bezeichneter und geschützter Dokumente und E-Mails

- Identifizieren von Dokumenten, die vertrauliche Unternehmensinformationen enthalten

- Überwachen Sie den Benutzerzugriff auf bezeichnete Dokumente und E-Mails, und verfolgen Sie Änderungen an Dokumentklassifizierungen.

- Identifizieren Sie Dokumente, die vertrauliche Informationen enthalten und geschützt werden müssen, da Ihre Organisation andernfalls einem Risiko ausgesetzt ist, und verringern Sie dieses Risiko mithilfe der Empfehlungen.

- Identify when protected documents are accessed by internal or external users from Windows computers, and whether access was granted or denied.

The data that you see is aggregated from your Azure Information Protection clients and scanners, from Microsoft Cloud App Security, from Windows 10 computers using Microsoft Defender Advanced Threat Protection, and from [protection usage logs](log-analyze-usage.md).

Sie können beispielsweise die folgenden Informationen abrufen:

- Im **Nutzungsbericht** (in dem Sie einen Zeitraum auswählen können):
    
    - Welche Bezeichnungen angewendet werden
    
    - Wie viele Dokumente und E-Mails Bezeichnungen aufweisen
    
    - Wie viele Dokumente und E-Mails geschützt werden
    
    - Wie viele Benutzer und Geräte Dokumente bzw. E-Mails mit Bezeichnungen versehen
    
    - Welche Anwendungen zum Bezeichnen verwendet werden

- In den **Aktivitätsprotokollen** (wo Sie einen Zeitraum auswählen können):
    
    - Welche Bezeichnungsaktionen von einem bestimmten Benutzer ausgeführt wurden
    
    - Welche Bezeichnungsaktionen von einem bestimmten Gerät ausgeführt wurden
    
    - Welche Benutzer auf ein bestimmtes bezeichnetes Dokument zugegriffen haben
    
    - Welche Bezeichnungsaktionen für einen bestimmten Dateipfad ausgeführt wurden
    
    - What labeling actions were performed by a specific application, such File Explorer and right-click, PowerShell, the scanner, or Microsoft Cloud App Security
    
    - Which protected documents were accessed successfully by users or denied access to users, even if those users don't have the Azure Information Protection client installed or are outside your organization

    - Drilldown auf gemeldete Dateien, um zusätzliche Informationen in den **Aktivitätsdetails** zu finden

- Im Bericht **Datenermittlung**:

    - What files are on your scanned data repositories, Windows 10 computers, or computers running the Azure Information Protection clients
    
    - Welche Dateien Bezeichnungen aufweisen und geschützt werden sowie den Speicherort der Dateien nach Bezeichnung
    
    - Welche Dateien vertrauliche Daten für bekannte Kategorien enthalten, z.B. Finanzdaten und persönliche Informationen, und den Speicherort von Dateien nach diesen Kategorien

- Aus dem Bericht **Empfehlungen**:
    
    - Identifizieren Sie ungeschützte Dateien, die eine bekannte Art von vertraulichen Informationen enthalten. Mit einer Empfehlung können Sie sofort die entsprechende Bedingung für eine Ihrer Bezeichnungen konfigurieren, um die Bezeichnung automatisch oder nach Empfehlung anzuwenden.
        
        If you follow the recommendation: The next time the files are opened by a user or scanned by the Azure Information Protection scanner, the files can be automatically classified and protected.
    
    - Identifizierten Sie, welche Datenrepositorys über Dateien mit identifizierten vertraulichen Informationen verfügen, aber nicht von Azure Information Protection überprüft werden. Mit einer Empfehlung können Sie den identifizierten Datenspeicher sofort zu einem der Profile Ihres Scanners hinzufügen.
        
        If you follow the recommendation: On the next scanner cycle, the files can be automatically classified and protected.

Die Berichte verwenden [Azure Monitor](/azure/log-analytics/log-analytics-overview), um die Daten in einem Log Analytics-Arbeitsbereich zu speichern, der Ihrer Organisation gehört. Wenn Sie mit der Abfragesprache vertraut sind, können Sie die Abfragen ändern und neue Berichte und Power BI-Dashboards erstellen. You might find the following tutorial helpful to understand the query language: [Get started with Azure Monitor log queries](/azure/azure-monitor/log-query/get-started-queries).

Weitere Informationen finden Sie in den folgenden Blogbeiträgen: 
- [Data discovery, reporting and analytics for all your data with Microsoft Information Protection (Datenermittlung, Berichterstattung und Analysen für alle Daten mit Microsoft Information Protection)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854)

- [Discover and protect sensitive data through Azure Information Protection and Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discover-and-protect-sensitive-data-through-Azure-Information/ba-p/297292)

### <a name="information-collected-and-sent-to-microsoft"></a>Gesammelte und an Microsoft gesendete Informationen

Um diese Berichte zu erstellen, senden die Endpunkte die folgenden Informationen an Microsoft:

- Die Bezeichnungsaktion. Z.B. das Festlegen oder Ändern einer Bezeichnung, das Hinzufügen oder Entfernen von Schutz, automatische und empfohlene Bezeichnungen.

- Den Bezeichnungsnamen vor und nach der Bezeichnungsaktion

- Die Mandanten-ID Ihrer Organisation.

- Die Benutzer-ID (E-Mail-Adresse oder UPN).

- Den Namen des Benutzergeräts

- Für Dokumente: Den Dateipfad und -namen von Dokumenten, die Bezeichnungen aufweisen

- For emails: The email subject and email sender  for emails that are labeled. 

- Die Typen vertraulicher Informationen ([vordefiniert](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) und benutzerdefiniert), die im Inhalt erkannt wurden.

- Die Azure Information Protection-Clientversion.

- Die Client-Betriebssystemversion.

Diese Informationen werden in einem Azure Log Analytics-Arbeitsbereich gespeichert, der Ihrer Organisation gehört, und kann unabhängig von Azure Information Protection von Benutzern eingesehen werden, die über Zugriffsrechte für diesen Arbeitsbereich verfügen. Details hierzu finden Sie im Abschnitt [Erforderliche Berechtigungen für Azure Information Protection-Analysen](#permissions-required-for-azure-information-protection-analytics). Informationen zum Verwalten des Zugriffs auf Ihren Arbeitsbereich finden Sie in der Azure-Dokumentation im Abschnitt [Verwalten des Zugriffs auf den Log Analytics-Arbeitsbereich mit Azure-Berechtigungen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-using-azure-permissions).

To prevent Azure Information Protection clients (classic) from sending this data, set the [policy setting](configure-policy-settings.md) of **Send audit data to Azure Information Protection analytics** to **Off**:

- Die meisten Benutzer können diese Daten senden, und eine Teilmenge von Benutzern kann keine Überwachungsdaten senden: 
    - Set **Send audit data to Azure Information Protection analytics** to **Off** in a scoped policy for the subset of users. Diese Konfiguration ist typisch für Produktionsszenarien.

- So kann nur eine Teilmenge an Benutzern Überwachungsdaten senden: 
    - Set **Send audit data to Azure Information Protection analytics** to **Off** in the global policy, and **On** in a scoped policy for the subset of users. Diese Konfiguration ist typisch für Testszenarien.

To prevent Azure Information Protection unified clients from sending this data, configure a label policy [advanced setting](./rms-client/clientv2-admin-guide-customizations.md#disable-sending-audit-data-to-azure-information-protection-analytics).

#### <a name="content-matches-for-deeper-analysis"></a>Inhaltsübereinstimmungen für umfassendere Analysen

Azure Information Protection lets you collect and store the actual data that's identified as being a sensitive information type (predefined or custom). Dies kann z. B. gefundene Kreditkartennummern sowie Sozialversicherungsnummern, Kennwortnummern und Kontonummern betreffen. The content matches are displayed when you select an entry from **Activity logs**, and view the **Activity Details**. 

By default, Azure Information Protection clients don't send content matches. To change this behavior so that content matches are sent:

- For the classic client, select a checkbox as part of the [configuration](#configure-a-log-analytics-workspace-for-the-reports) for Azure Information Protection analytics. The checkbox is named **Enable deeper analytics into your sensitive data**.
    
    If you want most users who are using this client to send content matches but a subset of users cannot send content matches, select the checkbox and then configure an [advanced client setting](./rms-client/client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users) in a scoped policy for the subset of users.

- For the unified labeling client, configure an [advanced setting](./rms-client/clientv2-admin-guide-customizations.md#send-information-type-matches-to-azure-information-protection-analytics) in a label policy.

## <a name="prerequisites"></a>Voraussetzungen
Damit Sie Azure Information Protection-Berichte anzeigen und eigene Berichte erstellen können, müssen die folgenden Voraussetzungen erfüllt sein.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Azure-Abonnement, das Log Analytics umfasst und sich auf denselben Mandanten wie Azure Information Protection bezieht|Siehe Seite [Azure Monitor – Preise](https://azure.microsoft.com/pricing/details/log-analytics).<br /><br />Wenn Sie kein Azure-Abonnement haben oder Azure Log Analytics derzeit nicht verwenden, finden Sie auf der Preisseite einen Link für eine kostenlose Testversion.|
|For reporting information from labeling clients: <br /><br />- Azure Information Protection clients|Both the unified labeling client and the classic client are supported. <br /><br />If not already installed, you can download and install these clients from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).|
|For reporting information from cloud-based data stores: <br /><br />- Microsoft Cloud App Security |To display information from Microsoft Cloud App Security, configure [Azure Information Protection integration](https://docs.microsoft.com/cloud-app-security/azip-integration).|
|For reporting information from on-premises data stores: <br /><br />- Azure Information Protection scanner |Eine Installationsanleitung für die Überprüfung finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md). |
|For reporting information from Windows 10 computers:  <br /><br />- Minimum build of 1809 with Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)|You must enable the Azure Information Protection integration feature from Microsoft Defender Security Center. For more information, see [Information protection in Windows overview](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview).|

### <a name="permissions-required-for-azure-information-protection-analytics"></a>Erforderliche Berechtigungen für Azure Information Protection-Analysen

Speziell für Azure Information Protection-Analysen können Sie nach der Konfiguration des Azure Log Analytics-Arbeitsbereichs die Azure AD-Administratorrolle „Sicherheitsleseberechtigter“ als Alternative zu den anderen Azure AD-Rollen verwenden, die die Verwaltung von Azure Information Protection im Azure-Portal unterstützen.

Da dieses Feature die Azure Monitor-Plattform verwendet, steuert die rollenbasierte Zugriffssteuerung (Role-Based Access Control, RBAC) für Azure auch den Zugriff auf Ihren Arbeitsbereich. Daher benötigen Sie zum Verwalten von Azure Information Protection-Analysen sowohl eine Azure-Rolle als auch eine Azure AD-Administratorrolle. Wenn Sie noch keine Erfahrung mit Azure-Rollen haben, sollten Sie [Unterschiede zwischen Azure RBAC-Rollen und Azure AD-Administratorrollen](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles) lesen.

Details:

1. One of the following [Azure AD administrator roles](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) to access the Azure Information Protection analytics pane:
    
    - Um Ihren Log Analytics-Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
        - **Azure Information Protection administrator**
        - **Sicherheitsadministrator**
        - **Complianceadministrator**
        - **Compliance data administrator**
        - **Globaler Administrator**
    
    - After the workspace has been created, you can then use the following roles with fewer permissions to view the data collected:
    
        - **Sicherheitsleseberechtigter**
        - **Global reader**
    
    > [!NOTE] 
    > You cannot use the Azure Information Protection administrator role or the Global reader role if your tenant is on the [unified labeling platform](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform).

2. Darüber hinaus benötigen Sie eine der folgenden [Azure Log Analytics-Rollen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-using-azure-permissions) oder standardmäßige [Azure-Rollen](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-rbac-roles), um auf Ihren Azure Log Analytics-Arbeitsbereich zuzugreifen:
    
    - Um einen Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
        - **Log Analytics-Mitwirkender**
        - **Mitwirkender**
        - **Besitzer**
    
    - Nachdem der Arbeitsbereich erstellt wurde, können Sie dann eine der folgenden Rollen mit weniger Berechtigungen verwenden, um die gesammelten Daten anzuzeigen:
    
        - **Log Analytics-Leser**
        - **Leser**

#### <a name="minimum-roles-to-view-the-reports"></a>Mindestens erforderliche Rolle zum Anzeigen von Berichten

Nachdem Sie Ihren Arbeitsbereich für Azure Information Protection-Analysen erstellt haben, benötigen Sie mindestens die beiden folgenden Rollen zum Anzeigen der Berichte der Azure Information Protection-Analysen:

- Azure AD administrator role: **Security reader**
- Azure role: **Log Analytics Reader**

Eine typische Rollenzuordnung für viele Organisationen ist jedoch die Azure AD-Rolle des **Sicherheitsleseberechtigten** und die Azure-Rolle des **Leseberechtigten**.

### <a name="storage-requirements-and-data-retention"></a>Storage requirements and data retention

The amount of data collected and stored in your Azure Information Protection workspace will vary significantly for each tenant, depending on factors such as how many Azure Information Protection clients and other supported endpoints you have, whether you're collecting endpoint discovery data, you've deployed scanners, the number of protected documents that are accessed, and so on.

However, as a starting point, you might find the following estimates useful:

- For audit data generated by Azure Information Protection clients only: 2 GB per 10,000 active users per month.

- For audit data generated by Azure Information Protection clients, scanners, and Microsoft Defender ATP: 20 GB per 10,000 active users per month.

If you use mandatory labeling or you've configured a default label for most users, your rates are likely to be significantly higher.

Azure Monitor Logs has a **Usage and estimated costs** feature to help you estimate and review the amount of data stored, and you can also control the data retention period for your Log Analytics workspace. For more information, see [Manage usage and costs with Azure Monitor Logs](https://docs.microsoft.com/azure/azure-monitor/platform/manage-cost-storage).

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Konfigurieren eines Log Analytics-Arbeitsbereichs für Berichte

1. Wenn dies noch nicht erfolgt ist, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal](https://portal.azure.com) mit einem Konto an, das über die [erforderlichen Berechtigungen für die Azure Information Protection-Analyse](#permissions-required-for-azure-information-protection-analytics) verfügt. Then navigate to the **Azure Information Protection** pane. 
    
    For example, in the search box for resources, services, and docs: Start typing **Information** and select **Azure Information Protection**.
    
2. Navigieren Sie zu den Menüoptionen **Verwalten**, und wählen Sie **Analyse konfigurieren (Vorschau)** aus.

3. On the **Azure Information Protection log analytics** pane, you see a list of any Log Analytics workspaces that are owned by your tenant. Nehmen Sie eine der folgenden Aktionen vor:
    
    - To create a new Log Analytics workspace: Select **Create new workspace**, and on the **Log analytics workspace** pane, supply the requested information.
    
    - Verwenden eines vorhandenen Log Analytics-Arbeitsbereichs: Wählen Sie den gewünschten Arbeitsbereich aus der Liste aus.
    
    Wenn Sie Hilfe beim Erstellen des Log Analytics-Arbeitsbereichs benötigen, lesen Sie sich den Artikel [Erstellen eines Log Analytics-Arbeitsbereichs im Azure-Portal](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace) durch.

4. If you have Azure Information Protection clients (classic), select the checkbox **Enable deeper analytics into your sensitive data** if you want to store the actual data that's identified as being a sensitive information type. For more information about this setting, see the [Content matches for deeper analysis](#content-matches-for-deeper-analysis) section on this page.

5. Wählen Sie **OK** aus.

You're now ready to view the reports.

## <a name="how-to-view-the-reports"></a>Anzeigen von Berichten

From the Azure Information Protection pane, locate the **Dashboards** menu options, and select one of the following options:

- **Nutzungsbericht (Vorschauversion)** : Dieser Bericht informiert Sie darüber, wie Ihre Bezeichnungen verwendet werden.

- **Aktivitätsprotokolle (Vorschau)** : Mithilfe dieses Berichts finden Sie Bezeichnungsaktionen von Benutzern sowie auf Geräten und Dateipfaden. In addition, for protected documents, you can see access attempts (successful or denied) for users both inside and outside your organization, even if they don't have the Azure Information Protection client installed
    
    Dieser Bericht enthält eine Option **Spalten**, mit der Sie mehr Aktivitätsinformationen als in der Standardanzeige anzeigen können. Wenn Sie **Aktivitätsdetails** auswählen, werden weitere Details zu einer Datei angezeigt.

- **Data discovery (Preview)** : Use this report to see information about labeled files found by scanners and supported endpoints.
    
    Tip: From the information collected, you might find users accessing files that contain sensitive information from location that you didn't know about or aren't currently scanning:
    
    - Wenn die Zugriffe vor Ort stattfinden, können Sie die Orte der Azure Information Protection-Überprüfung als zusätzliche Datenrepositorys hinzufügen.
    - Wenn die Zugriffe über die Cloud stattfinden, können Sie die Orte über Microsoft Cloud App Security verwalten. 
    
- **Recommendations (Preview)** : Use this report to identify files that have sensitive information and mitigate your risk by following the recommendations.
    
    Wenn Sie ein Element auswählen, zeigt die Option **Daten anzeigen** die Überwachungsaktivitäten an, die die Empfehlung ausgelöst haben.


## <a name="how-to-modify-the-reports-and-create-custom-queries"></a>Ändern von Berichten und Erstellen benutzerdefinierter Abfragen

Select the query icon in the dashboard to open a **Log Search** pane: 

![Log Analytics-Symbol zum Anpassen von Azure Information Protection-Berichten](./media/log-analytics-icon.png)


Die protokollierten Daten für Azure Information Protection werden in folgender Tabelle gespeichert: **InformationProtectionLogs_CL**

Wenn Sie eigene Abfragen erstellen, verwenden Sie benutzerfreundliche Schemanamen, die als **InformationProtectionEvents**-Funktionen implementiert wurden. Diese Funktionen werden von Attributen abgeleitet, die für benutzerdefinierte Abfragen unterstützt werden (einige Attribute sind nur für den internen Gebrauch bestimmt). Die Namen bleiben unverändert, auch wenn sich die zugrunde liegenden Attribute aufgrund von Neuerungen und neuen Funktionen ändern.

### <a name="friendly-schema-reference-for-event-functions"></a>Benutzerfreundliche Schemareferenz für Ereignisfunktionen

In der folgenden Tabelle finden Sie die Anzeigenamen der Ereignisfunktionen, die Sie für benutzerdefinierte Abfragen mit Azure Information Protection-Analysen verwenden können.

|Spaltenname|Description|
|-----------|-----------|
|Zeit|Event time: UTC in format YYYY-MM-DDTHH:MM:SS|
|Benutzer|User: Format UPN or DOMAIN\USER|
|ItemPath|Full item path or email subject|
|ItemName|File name or email subject |
|Methode|Label assigned method: Manual, Automatic, Recommended, Default, or Mandatory|
|Aktivität|Audit activity: DowngradeLabel, UpgradeLabel, RemoveLabel, NewLabel, Discover, Access, RemoveCustomProtection, ChangeCustomProtection, or NewCustomProtection |
|LabelName|Label name (not localized)|
|LabelNameBefore |Label name before change (not localized) |
|ProtectionType|Protection type [JSON] <br />{ <br />"Type": ["Template", "Custom", "DoNotForward"], <br />  "TemplateID": "GUID" <br /> } <br />|
|ProtectionBefore|Protection type before change [JSON] |
|MachineName |FQDN when available; otherwise host name|
|DeviceRisk|Device risk score from WDATP when available|
|Plattform|Device platform (Win, OSX, Android, iOS) |
|ApplicationName|Application friendly name|
|AIPVersion|Version of the Azure Information Protection client that performed the audit action |
|TenantId|Azure AD-Mandanten-ID |
|AzureApplicationId|Azure AD registered application ID (GUID)|
|ProcessName|Process that hosts MIP SDK|
|LabelId|Label GUID or null|
|IsProtected|Whether protected: Yes/No |
|ProtectionOwner |Rights Management owner in UPN format|
|LabelIdBefore|Label GUID or null before change|
|InformationTypesAbove55|JSON array of [SensitiveInformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) found in data with confidence level 55 or above |
|InformationTypesAbove65|JSON array of [SensitiveInformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) found in data with confidence level 65 or above |
|InformationTypesAbove75|JSON array of [SensitiveInformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) found in data with confidence level 75 or above |
|InformationTypesAbove85|JSON array of [SensitiveInformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) found in data with confidence level 85 or above |
|InformationTypesAbove95|JSON array of [SensitiveInformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) found in data with confidence level 95 or above|
|DiscoveredInformationTypes |JSON array of [SensitiveInformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) found in data and their matched content (if enabled) where an empty array means no information types found, and null means no information available |
|ProtectedBefore|Whether the content was protected before change: Yes/No |
|ProtectionOwnerBefore|Rights Management owner before change |
|UserJustification|Justification when downgrading or removing label|
|LastModifiedBy|User in UPN format who last modified the file. Available for Office and SharePoint Online only|
|LastModifiedDate|UTC in format YYYY-MM-DDTHH:MM:SS: Available for Office & SharePoint Online only |


#### <a name="examples-using-informationprotectionevents"></a>Beispiele für InformationProtectionEvents

Anhand der folgenden Beispiele erfahren Sie, wie Sie das benutzerfreundliche Schema zur Erstellung benutzerdefinierter Abfragen verwenden können.

##### <a name="example-1-return-all-users-who-sent-audit-data-in-the-last-31-days"></a>Example 1: Return all users who sent audit data in the last 31 days 

```
InformationProtectionEvents 
| where Time > ago(31d) 
| distinct User 
```

 
##### <a name="example-2-return-the-number-of-labels-that-were-downgraded-per-day-in-the-last-31-days"></a>Example 2: Return the number of labels that were downgraded per day in the last 31 days 


```
InformationProtectionEvents 
| where Time > ago(31d) 
| where Activity == "DowngradeLabel"  
| summarize Label_Downgrades_per_Day = count(Activity) by bin(Time, 1d) 
 
```
 
##### <a name="example-3-return-the-number-of-labels-that-were-downgraded-from-confidential-by-user-in-the-last-31-days"></a>Example 3: Return the number of labels that were downgraded from Confidential by user, in the last 31 days 

```

InformationProtectionEvents 
| where Time > ago(31d) 
| where Activity == "DowngradeLabel"  
| where LabelNameBefore contains "Confidential" and LabelName !contains "Confidential"  
| summarize Label_Downgrades_by_User = count(Activity) by User | sort by Label_Downgrades_by_User desc 

```

In diesem Beispiel werden herabgestufte Bezeichnungen nur gezählt, wenn der Bezeichnungsname vor der Aktion den Namen **Vertraulich** enthielt und den Namen **Vertraulich** nach der Aktion nicht mehr enthielt. 


## <a name="next-steps"></a>Nächste Schritte
After reviewing the information in the reports, if you are using the Azure Information Protection client, you might decide to make changes to your Azure Information Protection policy. Eine Anleitung dazu finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Wenn Sie ein Microsoft 365-Abonnement haben, können Sie die Nutzung von Bezeichnungen auch im Microsoft 365 Compliance Center und im Microsoft 365 Security Center anzeigen. Weitere Informationen finden Sie unter [Anzeigen der Nutzung der Bezeichnung mit Bezeichnungsanalysen](/microsoft-365/compliance/label-analytics).
