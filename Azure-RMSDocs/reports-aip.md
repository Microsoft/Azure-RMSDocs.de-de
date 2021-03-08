---
title: Analyse und Zentrale Berichterstellung für Azure Information Protection (AIP)
description: Erfahren Sie, wie Sie die Verwendung von Azure Information Protection (AIP) und die Zentrale Berichterstellung zum Nachverfolgen der Verwendung von Bezeichnungen und zum Identifizieren von Dateien mit sensiblen Informationen verwenden.
author: batamig
ms.author: bagol
ms.date: 03/01/2021
manager: rkarlin
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.subservice: analytics
ms.reviewer: lilukov
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 7d86ee43b7ccc60922dea88c76e9e0aa68474d26
ms.sourcegitcommit: 8a45d209273d748ee0f2a96c97893288c0b7efa5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102446948"
---
# <a name="analytics-and-central-reporting-for-azure-information-protection-public-preview"></a>Analyse und Zentrale Berichterstellung für Azure Information Protection (öffentliche Vorschau)

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

In diesem Artikel wird beschrieben, wie Sie Azure Information Protection (AIP)-Analyse für die Zentrale Berichterstellung verwenden, die Ihnen helfen kann, die Übernahme ihrer Bezeichnungen zu verfolgen, mit denen die Daten Ihrer Organisation klassifiziert und geschützt werden. 

Mit AIP Analytics können Sie auch die folgenden Schritte ausführen:

- Unternehmensweite Überwachung bezeichneter und geschützter Dokumente und E-Mails

- Identifizieren von Dokumenten, die vertrauliche Unternehmensinformationen enthalten

- Überwachen Sie den Benutzerzugriff auf bezeichnete Dokumente und E-Mails, und verfolgen Sie Änderungen an Dokumentklassifizierungen.

- Identifizieren Sie Dokumente, die vertrauliche Informationen enthalten und geschützt werden müssen, da Ihre Organisation andernfalls einem Risiko ausgesetzt ist, und verringern Sie dieses Risiko mithilfe der Empfehlungen.

- Identifizieren Sie, ob interne oder externe Benutzer von Windows-Computern auf geschützte Dokumente zugreifen und ob der Zugriff gewährt oder verweigert wurde.

Die Daten, die Sie sehen, werden von ihren Azure Information Protection-Clients und-Scannern, von Microsoft Cloud App Security, von Windows 10-Computern mit Microsoft Defender Advanced Threat Protection und von [Schutz Verwendungs Protokollen](log-analyze-usage.md)aggregiert. 

Azure Information Protection Analytics für die Zentrale Berichterstellung befindet sich derzeit in der Vorschau Phase. Die [ergänzenden Bestimmungen für Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) enthalten zusätzliche rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden bzw. anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 


## <a name="aip-reporting-data"></a>AIP-Berichtsdaten

Beispielsweise werden in der Azure Information Protection Analytics for Central Reporting die folgenden Daten angezeigt:

|Bericht  |Angezeigte Beispiel Daten |
|---------|---------|
|**Nutzungsbericht**     |  Wählen Sie einen Zeitraum aus, um Folgendes anzuzeigen: <br /><br />     -Welche Bezeichnungen angewendet werden <br /><br />-Wie viele Dokumente und e-Mails werden bezeichnet? <br /><br />-Wie viele Dokumente und e-Mails werden geschützt? <br /><br />-Anzahl der Benutzer und der Anzahl der Geräte, die Dokumente und e-Mails bezeichnen <br /><br />-Welche Anwendungen zur Bezeichnung verwendet werden     |
|**Aktivitätsprotokolle**     | Wählen Sie einen Zeitraum aus, um Folgendes anzuzeigen: <br /><br />      -Welche zuvor von Scanner ermittelten Dateien aus dem gescannten Repository gelöscht wurden <br /> <br /> -Welche Bezeichnungs Aktionen wurden von einem bestimmten Benutzer ausgeführt? <br /><br /> -Welche Bezeichnungs Aktionen wurden von einem bestimmten Gerät ausgeführt?<br /> <br />    -Benutzer, auf die ein bestimmtes beschrifteten Dokument zugegriffen hat<br /> <br />-Welche Bezeichnungs Aktionen wurden für einen bestimmten Dateipfad ausgeführt?<br /> <br />-Welche Bezeichnungs Aktionen wurden von einer bestimmten Anwendung ausgeführt, z. b. im Datei-Explorer und mit der rechten Maustaste, PowerShell, der Überprüfung oder Microsoft Cloud App Security <br /> <br />-Welche geschützten Dokumente wurden von Benutzern erfolgreich aufgerufen oder der Zugriff auf Benutzer verweigert, auch wenn diese Benutzer den Azure Information Protection-Client nicht installiert haben oder sich außerhalb Ihrer Organisation befinden. <br /> <br />-Drilldown zu gemeldeten Dateien zum Anzeigen von **Aktivitäts Details** für zusätzliche Informationen      |
|**Daten Ermittlungsbericht**     |      -Welche Dateien befinden sich in den überprüften Daten Depots, Windows 10-Computern oder Computern, auf denen die Azure Information Protection Clients ausgeführt werden <br /><br />-Welche Dateien sind gekennzeichnet und geschützt, und der Speicherort der Dateien nach Bezeichnungen <br /><br />-Welche Dateien vertrauliche Informationen für bekannte Kategorien enthalten, wie z. b. Finanzdaten und persönliche Informationen, sowie den Speicherort der Dateien nach diesen Kategorien       |
|**Empfehlungs Bericht**     | -Identifizieren Sie ungeschützte Dateien, die einen bekannten vertraulichen Informationstyp enthalten. Mit einer Empfehlung können Sie sofort die entsprechende Bedingung für eine Ihrer Bezeichnungen konfigurieren, um die Bezeichnung automatisch oder nach Empfehlung anzuwenden. **<br /> Wenn Sie der Empfehlung folgen: Wenn** die Dateien das nächste Mal von einem Benutzer geöffnet oder vom Azure Information Protection Scanner gescannt werden, können die Dateien automatisch klassifiziert und geschützt werden. <br /><br /> -Welche Daten Depots Dateien mit identifizierten vertraulichen Informationen haben, aber nicht vom Azure Information Protection gescannt werden. Mit einer Empfehlung können Sie den identifizierten Datenspeicher sofort zu einem der Profile Ihres Scanners hinzufügen. <br />   **Wenn Sie der Empfehlung folgen**: beim nächsten Scanner können die Dateien automatisch klassifiziert und geschützt werden.        |
| | |

Die Berichte verwenden [Azure Monitor](/azure/log-analytics/log-analytics-overview), um die Daten in einem Log Analytics-Arbeitsbereich zu speichern, der Ihrer Organisation gehört. Wenn Sie mit der Abfragesprache vertraut sind, können Sie die Abfragen ändern und neue Berichte und Power BI-Dashboards erstellen. Das folgende Tutorial ist möglicherweise hilfreich, um die Abfragesprache zu verstehen: [Get Started with Azure Monitor Log Queries](/azure/azure-monitor/log-query/get-started-queries).

Weitere Informationen finden Sie in den folgenden Blogbeiträgen: 
- [Data discovery, reporting and analytics for all your data with Microsoft Information Protection (Datenermittlung, Berichterstattung und Analysen für alle Daten mit Microsoft Information Protection)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854)

- [Ermitteln und schützen von sensiblen Daten über Azure Information Protection und Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discover-and-protect-sensitive-data-through-Azure-Information/ba-p/297292)

### <a name="information-collected-and-sent-to-microsoft"></a>Gesammelte und an Microsoft gesendete Informationen

Um diese Berichte zu erstellen, senden die Endpunkte die folgenden Informationen an Microsoft:

- Die Bezeichnungsaktion. Z.B. das Festlegen oder Ändern einer Bezeichnung, das Hinzufügen oder Entfernen von Schutz, automatische und empfohlene Bezeichnungen.

- Den Bezeichnungsnamen vor und nach der Bezeichnungsaktion

- Die Mandanten-ID Ihrer Organisation.

- Die Benutzer-ID (E-Mail-Adresse oder UPN).

- Den Namen des Benutzergeräts

- Die IP-Adresse des Geräts des Benutzers. 

- Der relevante Prozess Name, z. b. **Outlook** oder **MSIP. app**.

- Der Name der Anwendung, die die Bezeichnung ausgeführt hat, z. b. **Outlook** oder der **Datei-Explorer** .

- Für Dokumente: Den Dateipfad und -namen von Dokumenten, die Bezeichnungen aufweisen

- Für e-Mails: der e-Mail-Betreff und der e-Mail-Absender für e-Mails mit der Bezeichnung. 

- Die Typen vertraulicher Informationen ([vordefiniert](/office365/securitycompliance/what-the-sensitive-information-types-look-for) und benutzerdefiniert), die im Inhalt erkannt wurden.

- Die Azure Information Protection-Clientversion.

- Die Client-Betriebssystemversion.

Diese Informationen werden in einem Azure Log Analytics-Arbeitsbereich gespeichert, der Ihrer Organisation gehört, und kann unabhängig von Azure Information Protection von Benutzern eingesehen werden, die über Zugriffsrechte für diesen Arbeitsbereich verfügen. 

Weitere Informationen finden Sie unter:

- [Erforderliche Berechtigungen für Azure Information Protection-Analysen](#permissions-required-for-azure-information-protection-analytics)
- [Verwalten des Zugriffs auf den Log Analytics-Arbeitsbereich mit Azure-Berechtigungen](/azure/azure-monitor/platform/manage-access#manage-access-using-azure-permissions)
- [Azure Information Protection Überwachungs Protokoll Verweis](audit-logs.md)

#### <a name="prevent-the-aip-clients-from-sending-auditing-data"></a>Verhindern, dass die AIP-Clients Überwachungsdaten senden

**Client für einheitliche Bezeichnungen** 

Um zu verhindern, dass der Azure Information Protection Unified Label-Client Überwachungsdaten sendet, konfigurieren Sie eine [Erweiterte Einstellung](./rms-client/clientv2-admin-guide-customizations.md#disable-sending-audit-data-to-azure-information-protection-analytics)für die Bezeichnung "Bezeichnung".

**Klassischer Client**

Um zu verhindern, dass die Azure Information Protection des klassischen Clients diese Daten sendet, legen Sie die [Richtlinien Einstellung](configure-policy-settings.md) Überwachungs **Daten an Azure Information Protection Analytics senden** auf **aus** fest:

|Anforderung  |Instructions  |
|---------|---------|
|**So konfigurieren Sie die meisten Benutzer für das Senden von Daten mit einer Teilmenge von Benutzern, die keine Daten senden können**     |  Legen Sie in einer Bereichs bezogenen Richtlinie für die Teilmenge der Benutzer das Senden von Überwachungs **Daten an Azure Information Protection Analytics** auf **Off** fest. <br><br> Diese Konfiguration ist typisch für Produktionsszenarien.     |
|**So konfigurieren Sie nur eine Teilmenge von Benutzern, die Daten senden**     |  Legen Sie in der globalen Richt **Linie und in** einer Bereichs bezogenen Richtlinie für die Teilmenge der Benutzer das Senden von Überwachungs **Daten an Azure Information Protection Analytics** auf **Off** fest. <br><br>Diese Konfiguration ist typisch für Testszenarien.       |
| | |

#### <a name="content-matches-for-deeper-analysis"></a>Inhaltsübereinstimmungen für umfassendere Analysen

Mit Azure Information Protection können Sie die eigentlichen Daten erfassen und speichern, die als sensible Informationstypen (vordefiniert oder Benutzer definiert) identifiziert werden. Dies kann z. B. gefundene Kreditkartennummern sowie Sozialversicherungsnummern, Kennwortnummern und Kontonummern betreffen. Die Inhalts Übereinstimmungen werden angezeigt, wenn Sie einen Eintrag aus den **Aktivitäts Protokollen** auswählen und die **Aktivitäts Details** anzeigen. 

Standardmäßig werden von Azure Information Protection Clients keine Inhalts Übereinstimmungen gesendet. So ändern Sie dieses Verhalten, damit Inhalts Übereinstimmungen gesendet werden:

|Client  |Instructions  |
|---------|---------|
|**Client für einheitliche Bezeichnungen**      |  Konfigurieren Sie eine [Erweiterte Einstellung](./rms-client/clientv2-admin-guide-customizations.md#send-information-type-matches-to-azure-information-protection-analytics) in einer Bezeichnungs Richtlinie.       |
|**Klassischer Client**      |   Aktivieren Sie ein Kontrollkästchen als Teil der [Konfiguration](#configure-a-log-analytics-workspace-for-the-reports) für Azure Information Protection Analytics. Das Kontrollkästchen heißt **tiefere Analysen in Ihre sensiblen Daten**. <br><br> Wenn Sie möchten, dass die meisten Benutzer, die diesen Client verwenden, Inhalts Übereinstimmungen senden, aber eine Teilmenge der Benutzer keine Inhalts Übereinstimmungen senden kann, aktivieren Sie das Kontrollkästchen, und konfigurieren Sie dann eine [Erweiterte Client Einstellung](./rms-client/client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users) in einer Bereichs bezogenen Richtlinie für die Teilmenge der Benutzer     |
|     |         |


## <a name="prerequisites"></a>Voraussetzungen
Damit Sie Azure Information Protection-Berichte anzeigen und eigene Berichte erstellen können, müssen die folgenden Voraussetzungen erfüllt sein.

|Anforderung  |Details  |
|---------|---------|
|**Ein Azure-Abonnement**     |   Ihr Azure-Abonnement muss Log Analytics auf demselben Mandanten wie Azure Information Protection enthalten. <br><br> Weitere Informationen finden Sie auf der Seite [Azure Monitor Preise](https://azure.microsoft.com/pricing/details/log-analytics) . <br><br>Wenn Sie kein Azure-Abonnement haben oder Azure Log Analytics derzeit nicht verwenden, finden Sie auf der Preisseite einen Link für eine kostenlose Testversion.   |
| **Überwachungs Protokoll-URL Netzwerk Konnektivität** | AIP muss in der Lage sein, auf die folgenden URLs zuzugreifen, um AIP-Überwachungs Protokolle zu unterstützen:<br>- `https://*.events.data.microsoft.com` <br>- `https://*.aria.microsoft.com` (Nur Android-Gerätedaten)
|**Azure Information Protection-Client**    |Für die Berichterstellung vom Client. <br><br>Wenn Sie noch keinen-Client installiert haben, können Sie den Unified-Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunterladen und installieren.      <br><br>**Hinweis**: sowohl der Unified-Bezeichnung-Client als auch der klassische Client werden unterstützt. Zum Bereitstellen des klassischen AIP-Clients eröffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.     |
|**Azure Information Protection lokaler Scanner**    | Für die Berichterstellung aus lokalen Daten speichern. <br><br>      Weitere Informationen finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).   |
|**Microsoft Cloud App Security (MCAS)**     | Zur Berichterstellung aus cloudbasierten Daten speichern. <br><br>Weitere Informationen finden Sie unter [Azure Information Protection Integration](/cloud-app-security/azip-integration) in der MCAS-Dokumentation.        |
|**Minimaler Build von 1809 mit Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)**     | Für die Berichterstellung von Windows 10-Computern. <br>  <br>   Sie müssen das Azure Information Protection-Integrations Feature von Microsoft Defender Security Center aktivieren. <br><br>Weitere Informationen finden Sie unter [Übersicht über den Datenschutz in Windows](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview).   |
|     |         |


### <a name="permissions-required-for-azure-information-protection-analytics"></a>Erforderliche Berechtigungen für Azure Information Protection-Analysen

Speziell für Azure Information Protection-Analysen können Sie nach der Konfiguration des Azure Log Analytics-Arbeitsbereichs die Azure AD-Administratorrolle „Sicherheitsleseberechtigter“ als Alternative zu den anderen Azure AD-Rollen verwenden, die die Verwaltung von Azure Information Protection im Azure-Portal unterstützen. Diese zusätzliche Rolle wird nur unterstützt, wenn Ihr Mandant nicht auf der [Unified-Bezeichnung-Plattform](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)ist.

Da Azure Information Protection Analytics die Azure-Überwachung verwendet, steuert die rollenbasierte Zugriffs Steuerung (RBAC) für Azure auch den Zugriff auf Ihren Arbeitsbereich. Daher benötigen Sie zum Verwalten von Azure Information Protection-Analysen sowohl eine Azure-Rolle als auch eine Azure AD-Administratorrolle. Wenn Sie noch keine Erfahrung mit Azure-Rollen haben, sollten Sie [Unterschiede zwischen Azure RBAC-Rollen und Azure AD-Administratorrollen](/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles) lesen.

Weitere Informationen finden Sie unter

- [Erforderliche Azure AD Administrator Rollen](#required-azure-ad-administrator-roles)
- [Erforderliche Azure-Log Analytics Rollen](#required-azure-log-analytics-roles)
- [Mindestens erforderliche Rolle zum Anzeigen von Berichten](#minimum-roles-to-view-the-reports)

#### <a name="required-azure-ad-administrator-roles"></a>Erforderliche Azure AD Administrator Rollen

Sie müssen über eine der folgenden [Azure AD Administrator Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) verfügen, um auf den Bereich Azure Information Protection Analytics zugreifen zu können:

- Um Ihren Log Analytics-Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
    - **Azure Information Protection-Administrator**
    - **Sicherheitsadministrator**
    - **Complianceadministrator**
    - **Compliancedatenadministrator**
    - **Globaler Administrator**
    
- Nachdem der Arbeitsbereich erstellt wurde, können Sie die folgenden Rollen mit weniger Berechtigungen verwenden, um die gesammelten Daten anzuzeigen:
    
    - **Sicherheitsleseberechtigter**
    - **Globaler Reader**

#### <a name="required-azure-log-analytics-roles"></a>Erforderliche Azure-Log Analytics Rollen

Sie müssen über eine der folgenden [Azure Log Analytics-Rollen](/azure/azure-monitor/platform/manage-access#manage-access-using-azure-permissions) oder Azure-Standard [Rollen](/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-rbac-roles) verfügen, um auf Ihren Azure Log Analytics-Arbeitsbereich zuzugreifen:
    
- Um einen Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
    - **Log Analytics-Mitwirkender**
    - **Mitwirkender**
    - **Besitzer**
    
- Nachdem der Arbeitsbereich erstellt wurde, können Sie dann eine der folgenden Rollen mit weniger Berechtigungen verwenden, um die gesammelten Daten anzuzeigen:
    
    - **Log Analytics-Leser**
    - **Leser**

#### <a name="minimum-roles-to-view-the-reports"></a>Mindestens erforderliche Rolle zum Anzeigen von Berichten

Nachdem Sie Ihren Arbeitsbereich für Azure Information Protection-Analysen erstellt haben, benötigen Sie mindestens die beiden folgenden Rollen zum Anzeigen der Berichte der Azure Information Protection-Analysen:

- Azure AD Administrator Rolle: **Sicherheits Leser**
- Azure-Rolle: **Log Analytics Reader**

Eine typische Rollenzuordnung für viele Organisationen ist jedoch die Azure AD-Rolle des **Sicherheitsleseberechtigten** und die Azure-Rolle des **Leseberechtigten**.

### <a name="storage-requirements-and-data-retention"></a>Speicheranforderungen und Daten Aufbewahrung

Die Menge der Daten, die in Ihrem Azure Information Protection Arbeitsbereich erfasst und gespeichert werden, variiert für jeden Mandanten erheblich. Dies hängt von Faktoren ab, wie z. b. wie viele Azure Information Protection Clients und andere unterstützte Endpunkte vorhanden sind, ob Sie die Endpunkt Ermittlungs Daten sammeln, Scanner bereitgestellt haben, auf welche Anzahl geschützter Dokumente zugegriffen wird usw.

Als Ausgangspunkt kann es jedoch hilfreich sein, die folgenden Schätzwerte zu finden:

- Nur für Überwachungsdaten, die von Azure Information Protection Clients generiert werden: 2 GB pro 10.000 aktive Benutzer pro Monat.

- Für Überwachungsdaten, die von Azure Information Protection Clients, Scannern und Microsoft Defender ATP generiert werden: 20 GB pro 10.000 aktive Benutzer pro Monat.

Wenn Sie eine obligatorische Bezeichnung verwenden oder für die meisten Benutzer eine Standard Bezeichnung konfiguriert haben, sind ihre Tarife wahrscheinlich deutlich höher.

Azure Monitor Protokolle verfügt über die Funktion " **Nutzung und geschätzte Kosten** ", mit deren Hilfe Sie die Menge der gespeicherten Daten schätzen und überprüfen können. Außerdem können Sie die Daten Beibehaltungs Dauer für den Log Analytics Arbeitsbereich steuern. Weitere Informationen finden Sie unter [Verwalten von Nutzung und Kosten mit Azure Monitor Protokollen](/azure/azure-monitor/platform/manage-cost-storage).

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Konfigurieren eines Log Analytics-Arbeitsbereichs für Berichte

1. Wenn dies noch nicht erfolgt ist, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal](https://portal.azure.com) mit einem Konto an, das über die [erforderlichen Berechtigungen für die Azure Information Protection-Analyse](#permissions-required-for-azure-information-protection-analytics) verfügt. Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
1. Navigieren Sie zu den Menü Optionen **Verwalten** , und wählen Sie **Analyse konfigurieren (Vorschau)** aus.

1. Im Bereich **Azure Information Protection Log Analytics** wird eine Liste aller Log Analytics Arbeitsbereiche angezeigt, die sich im Besitz Ihres Mandanten befinden. Führen Sie eines der folgenden Verfahren aus:
    
    - So **Erstellen Sie einen neuen Log Analytics Arbeitsbereich**: Wählen Sie **neuen Arbeitsbereich erstellen** aus, und geben Sie im **Bereich Log Analytics-Arbeitsbereich** die angeforderten Informationen an.
    
    - **Um einen vorhandenen Log Analytics-Arbeitsbereich zu verwenden,** wählen Sie den Arbeitsbereich aus der Liste aus.
    
    Wenn Sie Hilfe beim Erstellen des Log Analytics-Arbeitsbereichs benötigen, lesen Sie sich den Artikel [Erstellen eines Log Analytics-Arbeitsbereichs im Azure-Portal](/azure/log-analytics/log-analytics-quick-create-workspace) durch.

1. **Nur klassischer AIP-Client**: Aktivieren Sie das Kontrollkästchen **tiefer gehende Analysen in Ihre sensiblen Daten aktivieren** , wenn Sie die eigentlichen Daten speichern möchten, die als sensible Informationen identifiziert werden. 

    Weitere Informationen zu dieser Einstellung finden Sie im Abschnitt [Inhalts Übereinstimmungen für eine tiefere Analyse](#content-matches-for-deeper-analysis) auf dieser Seite.

1. Klicken Sie auf **OK**.

Sie sind jetzt bereit, die Berichte anzuzeigen.

## <a name="view-the-aip-analytics-reports"></a>Anzeigen der AIP-Analyseberichte

Suchen Sie im Bereich Azure Information Protection die Menü Optionen **Dashboards** , und wählen Sie eine der folgenden Optionen aus:

|Bericht  |BESCHREIBUNG  |
|---------|---------|
|**Verwendungs Bericht (Vorschau)**     |  Dieser Bericht informiert Sie darüber, wie Ihre Bezeichnungen verwendet werden.       |
|**Aktivitäts Protokolle (Vorschau)**     |  Mithilfe dieses Berichts finden Sie Bezeichnungsaktionen von Benutzern sowie auf Geräten und Dateipfaden. Außerdem können Sie für geschützte Dokumente für Benutzer sowohl innerhalb als auch außerhalb Ihrer Organisation Zugriffsversuche (erfolgreich oder verweigert) erkennen, auch wenn Sie den Azure Information Protection-Client nicht installiert haben. <br><br>  Dieser Bericht enthält eine Option **Spalten**, mit der Sie mehr Aktivitätsinformationen als in der Standardanzeige anzeigen können. Wenn Sie **Aktivitätsdetails** auswählen, werden weitere Details zu einer Datei angezeigt.     |
|**Daten Ermittlung (Vorschau)**     |    Verwenden Sie diesen Bericht, um Informationen über bezeichnete Dateien anzuzeigen, die durch die Überprüfung und von unterstützten Endpunkten gefunden wurden.  <br><br>**Tipp**: aus den gesammelten Informationen können Benutzer auf Dateien zugreifen, die vertrauliche Informationen von einem Speicherort enthalten, von dem Sie nicht wissen, was Sie gerade nicht kennen oder überprüfen: <br><br>-Wenn die Standorte lokal sind, sollten Sie die Speicherorte als zusätzliche datenpositorys für den Azure Information Protection Scanner hinzufügen. <br>  -Wenn sich die Standorte in der Cloud befinden, können Sie Microsoft Cloud App Security verwenden, um Sie zu verwalten.    |
|**Empfehlungen (Vorschau)**     | Verwenden Sie diesen Bericht, um Dateien zu identifizieren, die vertrauliche Informationen enthalten, und minimieren Sie das Risiko mithilfe der Empfehlungen.  <br><br> Wenn Sie ein Element auswählen, zeigt die Option **Daten anzeigen** die Überwachungsaktivitäten an, die die Empfehlung ausgelöst haben.     |
|     |         |


## <a name="modify-the-aip-analytics-reports-and-create-custom-queries"></a>Ändern der AIP-Analyseberichte und Erstellen von benutzerdefinierten Abfragen

Wählen Sie im Dashboard das Abfrage Symbol aus, um einen Bereich für die **Protokoll Suche** zu öffnen: 

![Log Analytics-Symbol zum Anpassen von Azure Information Protection-Berichten](./media/log-analytics-icon.png)


Die protokollierten Daten für Azure Information Protection werden in folgender Tabelle gespeichert: **InformationProtectionLogs_CL**

Wenn Sie eigene Abfragen erstellen, verwenden Sie benutzerfreundliche Schemanamen, die als **InformationProtectionEvents**-Funktionen implementiert wurden. Diese Funktionen werden von Attributen abgeleitet, die für benutzerdefinierte Abfragen unterstützt werden (einige Attribute sind nur für den internen Gebrauch bestimmt). Die Namen bleiben unverändert, auch wenn sich die zugrunde liegenden Attribute aufgrund von Neuerungen und neuen Funktionen ändern.

### <a name="friendly-schema-reference-for-event-functions"></a>Benutzerfreundliche Schemareferenz für Ereignisfunktionen

In der folgenden Tabelle finden Sie die Anzeigenamen der Ereignisfunktionen, die Sie für benutzerdefinierte Abfragen mit Azure Information Protection-Analysen verwenden können.

|Spaltenname|BESCHREIBUNG|
|-----------|-----------|
|**Time**|Ereignis Zeit: UTC im Format yyyy-mm-ddThh: mm: SS|
|**Benutzer**|Benutzer: UPN oder Domäne \ Benutzer formatieren|
|**ItemPath**|Vollständiger Element Pfad oder e-Mail-Betreff|
|**ItemName**|Datei Name oder e-Mail-Betreff |
|**Methode**|Zugewiesene Methode für Bezeichnung: manuell, automatisch, empfohlen, Standard oder obligatorisch|
|**Aktivität**|Audit Activity: downgradelta Abel, upgradelta Abel, removelabel, newlabel, Discover, Access, removecustomprotection, changecustomprotection, newcustomprotection oder fileremoved |
|**ResultStatus**|Ergebnis Status der Aktion:<br /><br /> Erfolgreich oder Fehler (nur von AIP-Scanner gemeldet)|
|**ErrorMessage_s**|Enthält Details zu Fehlermeldungen, wenn ResultStatus = failed lautet. Nur von AIP-Scanner gemeldet|
|**Bezeichnungsname**|Name der Bezeichnung (nicht lokalisiert)|
|**Labelnamebefore** |Name der Bezeichnung vor der Änderung (nicht lokalisiert) |
|**ProtectionType**|Schutztyp [JSON] <br />{ <br />"Type": ["Template", "Custom", "DoNotForward"], <br />  "TemplateID": "GUID" <br /> } <br />|
|**Schutz vor**|Schutztyp vor Änderung [JSON] |
|**MachineName** |Vollständig verfügbarer voll qualifizierter Name Andernfalls Hostname|
|**Devicerisk**|Geräte Risikobewertung aus wdatp, wenn verfügbar|
|**Plattform**|Geräteplattform (Win, OSX, Android, IOS) |
|**ApplicationName**|Anzeige Name der Anwendung|
|**Aipversion**|Die Version des Azure Information Protection Clients, der die Überwachungsaktion ausgeführt hat. |
|**TenantId**|Azure AD-Mandanten-ID |
|**Azureapplicationid**|Azure AD registrierte Anwendungs-ID (GUID)|
|**ProcessName**|Prozess, der MIP SDK hostet|
|**LabelId**|GUID der Bezeichnung oder NULL|
|**Isprotehiert**|Ob geschützt: Ja/Nein |
|**Schutz Besitzer** |Rights Management Besitzer im UPN-Format|
|**Labelidbefore**|GUID der Bezeichnung oder NULL vor der Änderung|
|**InformationTypesAbove55**|JSON-Array von [sensitiveinformation](/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 55 oder höher |
|**InformationTypesAbove65**|JSON-Array von [sensitiveinformation](/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 65 oder höher |
|**InformationTypesAbove75**|JSON-Array von [sensitiveinformation](/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 75 oder höher |
|**InformationTypesAbove85**|JSON-Array von [sensitiveinformation](/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 85 oder höher |
|**InformationTypesAbove95**|JSON-Array von [sensitiveinformation](/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 95 oder höher|
|**Discoveredinformationtypes** |JSON-Array von [sensitiveinformation](/microsoft-365/compliance/what-the-sensitive-information-types-look-for) , das in Daten und dem zugehörigen Inhalt gefunden wurde (sofern aktiviert). ein leeres Array bedeutet, dass keine Informationstypen gefunden werden, und NULL bedeutet, dass keine Informationen verfügbar sind. |
|**Protectedbefore**|Ob der Inhalt vor der Änderung geschützt wurde: Ja/Nein |
|**Schutz Eigentümer vor**|Rights Management Besitzer vor der Änderung |
|**Userbegrün dung**|Begründung beim Herabstufen oder Entfernen der Bezeichnung|
|**LastModifiedBy**|Benutzer im UPN-Format, von dem die Datei zuletzt geändert wurde. Nur für Office und SharePoint verfügbar|
|**LastModifiedDate & gt**|UTC im Format yyyy-mm-ddThh: mm: SS: nur für Office und SharePoint verfügbar |
| | |
#### <a name="examples-using-informationprotectionevents"></a>Beispiele für InformationProtectionEvents

Anhand der folgenden Beispiele erfahren Sie, wie Sie das benutzerfreundliche Schema zur Erstellung benutzerdefinierter Abfragen verwenden können.

##### <a name="example-1-return-all-users-who-sent-audit-data-in-the-last-31-days"></a>Beispiel 1: Zurückgeben aller Benutzer, die Überwachungsdaten in den letzten 31 Tagen gesendet haben 

```
InformationProtectionEvents 
| where Time > ago(31d) 
| distinct User 
```

 
##### <a name="example-2-return-the-number-of-labels-that-were-downgraded-per-day-in-the-last-31-days"></a>Beispiel 2: Zurückgeben der Anzahl der Bezeichnungen, die pro Tag in den letzten 31 Tagen herabgestuft wurden 


```
InformationProtectionEvents 
| where Time > ago(31d) 
| where Activity == "DowngradeLabel"  
| summarize Label_Downgrades_per_Day = count(Activity) by bin(Time, 1d) 
 
```
 
##### <a name="example-3-return-the-number-of-labels-that-were-downgraded-from-confidential-by-user-in-the-last-31-days"></a>Beispiel 3: Zurückgeben der Anzahl der Bezeichnungen, die von einem vertraulichen Benutzer in den letzten 31 Tagen herabgestuft wurden 

```

InformationProtectionEvents 
| where Time > ago(31d) 
| where Activity == "DowngradeLabel"  
| where LabelNameBefore contains "Confidential" and LabelName !contains "Confidential"  
| summarize Label_Downgrades_by_User = count(Activity) by User | sort by Label_Downgrades_by_User desc 

```

In diesem Beispiel werden herabgestufte Bezeichnungen nur gezählt, wenn der Bezeichnungsname vor der Aktion den Namen **Vertraulich** enthielt und den Namen **Vertraulich** nach der Aktion nicht mehr enthielt. 


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Informationen in den Berichten überprüft haben, können Sie bei Verwendung des Azure Information Protection Clients Änderungen an der Beschriftungs Richtlinie vornehmen. 

- **Einheitlicher** Bezeichnungs Client: nehmen Sie Änderungen an der Beschriftungs Richtlinie in Ihrem Bezeichnungs-Admin Center vor, einschließlich der Microsoft 365 Security Center, Microsoft 365 Compliance Center oder der Microsoft 365 Security & Compliance Center. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/sensitivity-labels).

- **Klassischer Client**: nehmen Sie im Azure-Portal Änderungen an der Richtlinie vor. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Wenn Sie ein Microsoft 365-Abonnement haben, können Sie die Nutzung von Bezeichnungen auch im Microsoft 365 Compliance Center und im Microsoft 365 Security Center anzeigen. Weitere Informationen finden Sie unter [Anzeigen der Nutzung der Bezeichnung mit Bezeichnungsanalysen](/microsoft-365/compliance/label-analytics).

AIP-Überwachungs Protokolle werden auch an den Microsoft 365-Aktivitäts-Explorer gesendet, wo Sie mit unterschiedlichen Namen angezeigt werden können. Weitere Informationen finden Sie unter

- [Public Preview: AIP-Überwachungs Protokolle im Aktivitäts-Explorer](https://www.yammer.com/askipteam/#/Threads/show?threadId=1085834054254592)
- [Beginnen Sie mit dem Aktivitäts-Explorer](/microsoft-365/compliance/data-classification-activity-explorer).