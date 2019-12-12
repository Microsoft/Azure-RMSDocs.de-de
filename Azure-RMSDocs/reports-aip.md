---
title: Zentrale Berichterstellung für Azure Information Protection
description: Erfahren Sie, wie Sie mithilfe der zentralen Berichterstellung die Übernahme Ihrer Azure Information Protection-Bezeichnungen nachverfolgen und Dateien mit vertraulichen Daten erkennen.
author: cabailey
ms.author: cabailey
ms.date: 11/27/2019
manager: rkarlin
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.subservice: analytics
ms.reviewer: lilukov
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: fb4167ecc6f4dca175fe478d085a228a044416a9
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74564544"
---
# <a name="central-reporting-for-azure-information-protection"></a>Zentrale Berichterstellung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Dieses Feature befindet sich in der Vorschau und unterliegt Änderungen.

Verwenden Sie Azure Information Protection Analytics für die Zentrale Berichterstellung, damit Sie die Übernahme ihrer Bezeichnungen nachverfolgen können, mit denen die Daten Ihrer Organisation klassifiziert und geschützt werden. Beachten Sie auch Folgendes:

- Unternehmensweite Überwachung bezeichneter und geschützter Dokumente und E-Mails

- Identifizieren von Dokumenten, die vertrauliche Unternehmensinformationen enthalten

- Überwachen Sie den Benutzerzugriff auf bezeichnete Dokumente und E-Mails, und verfolgen Sie Änderungen an Dokumentklassifizierungen.

- Identifizieren Sie Dokumente, die vertrauliche Informationen enthalten und geschützt werden müssen, da Ihre Organisation andernfalls einem Risiko ausgesetzt ist, und verringern Sie dieses Risiko mithilfe der Empfehlungen.

- Identifizieren Sie, ob interne oder externe Benutzer von Windows-Computern auf geschützte Dokumente zugreifen und ob der Zugriff gewährt oder verweigert wurde.

Die Daten, die Sie sehen, werden von ihren Azure Information Protection-Clients und-Scannern, von Microsoft Cloud App Security, von Windows 10-Computern mit Microsoft Defender Advanced Threat Protection und von [Schutz Verwendungs Protokollen](log-analyze-usage.md)aggregiert.

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
    
    - Welche Bezeichnungs Aktionen wurden von einer bestimmten Anwendung ausgeführt, z. b. im Datei-Explorer und mit der rechten Maustaste, PowerShell, der Scanner oder Microsoft Cloud App Security
    
    - Auf welche geschützten Dokumente von Benutzern erfolgreich zugegriffen wurde oder ob Ihnen der Zugriff verweigert wurde, auch wenn diese Benutzer nicht den Azure Information Protection-Client installiert haben oder sich außerhalb Ihrer Organisation befinden.

    - Drilldown auf gemeldete Dateien, um zusätzliche Informationen in den **Aktivitätsdetails** zu finden

- Im Bericht **Datenermittlung**:

    - Welche Dateien befinden sich auf den überprüften Daten Depots, Windows 10-Computern oder Computern, auf denen die Azure Information Protection Clients ausgeführt werden
    
    - Welche Dateien Bezeichnungen aufweisen und geschützt werden sowie den Speicherort der Dateien nach Bezeichnung
    
    - Welche Dateien vertrauliche Daten für bekannte Kategorien enthalten, z.B. Finanzdaten und persönliche Informationen, und den Speicherort von Dateien nach diesen Kategorien

- Aus dem Bericht **Empfehlungen**:
    
    - Identifizieren Sie ungeschützte Dateien, die eine bekannte Art von vertraulichen Informationen enthalten. Mit einer Empfehlung können Sie sofort die entsprechende Bedingung für eine Ihrer Bezeichnungen konfigurieren, um die Bezeichnung automatisch oder nach Empfehlung anzuwenden.
        
        Wenn Sie der Empfehlung folgen: Wenn die Dateien das nächste Mal von einem Benutzer geöffnet oder vom Azure Information Protection Scanner gescannt werden, können die Dateien automatisch klassifiziert und geschützt werden.
    
    - Identifizierten Sie, welche Datenrepositorys über Dateien mit identifizierten vertraulichen Informationen verfügen, aber nicht von Azure Information Protection überprüft werden. Mit einer Empfehlung können Sie den identifizierten Datenspeicher sofort zu einem der Profile Ihres Scanners hinzufügen.
        
        Wenn Sie der Empfehlung folgen: beim nächsten Scanner können die Dateien automatisch klassifiziert und geschützt werden.

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

- Für Dokumente: Den Dateipfad und -namen von Dokumenten, die Bezeichnungen aufweisen

- Für e-Mails: der e-Mail-Betreff und der e-Mail-Absender für e-Mails mit der Bezeichnung. 

- Die Typen vertraulicher Informationen ([vordefiniert](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) und benutzerdefiniert), die im Inhalt erkannt wurden.

- Die Azure Information Protection-Clientversion.

- Die Client-Betriebssystemversion.

Diese Informationen werden in einem Azure Log Analytics-Arbeitsbereich gespeichert, der Ihrer Organisation gehört, und kann unabhängig von Azure Information Protection von Benutzern eingesehen werden, die über Zugriffsrechte für diesen Arbeitsbereich verfügen. Details hierzu finden Sie im Abschnitt [Erforderliche Berechtigungen für Azure Information Protection-Analysen](#permissions-required-for-azure-information-protection-analytics). Informationen zum Verwalten des Zugriffs auf Ihren Arbeitsbereich finden Sie in der Azure-Dokumentation im Abschnitt [Verwalten des Zugriffs auf den Log Analytics-Arbeitsbereich mit Azure-Berechtigungen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-using-azure-permissions).

Um zu verhindern, dass Azure Information Protection von Clients (klassisch) diese Daten senden, legen Sie die [Richtlinien Einstellung](configure-policy-settings.md) Überwachungs **Daten senden auf Azure Information Protection Analytics** auf **aus**fest:

- Die meisten Benutzer können diese Daten senden, und eine Teilmenge von Benutzern kann keine Überwachungsdaten senden: 
    - Legen Sie in einer Bereichs bezogenen Richtlinie für die Teilmenge der Benutzer das Senden von Überwachungs **Daten an Azure Information Protection Analytics** auf **Off** fest. Diese Konfiguration ist typisch für Produktionsszenarien.

- So kann nur eine Teilmenge an Benutzern Überwachungsdaten senden: 
    - Legen Sie in der globalen Richt **Linie und in** einer Bereichs bezogenen Richtlinie für die Teilmenge der Benutzer das Senden von Überwachungs **Daten an Azure Information Protection Analytics** auf **Off** fest. Diese Konfiguration ist typisch für Testszenarien.

Um zu verhindern, dass Azure Information Protection Unified Clients diese Daten senden, konfigurieren Sie eine [Erweiterte Einstellung](./rms-client/clientv2-admin-guide-customizations.md#disable-sending-audit-data-to-azure-information-protection-analytics)für die Bezeichnung "Bezeichnung".

#### <a name="content-matches-for-deeper-analysis"></a>Inhaltsübereinstimmungen für umfassendere Analysen

Mit Azure Information Protection können Sie die eigentlichen Daten erfassen und speichern, die als sensible Informationstypen (vordefiniert oder Benutzer definiert) identifiziert werden. Dies kann z. B. gefundene Kreditkartennummern sowie Sozialversicherungsnummern, Kennwortnummern und Kontonummern betreffen. Die Inhalts Übereinstimmungen werden angezeigt, wenn Sie einen Eintrag aus den **Aktivitäts Protokollen**auswählen und die **Aktivitäts Details**anzeigen. 

Standardmäßig werden von Azure Information Protection Clients keine Inhalts Übereinstimmungen gesendet. So ändern Sie dieses Verhalten, damit Inhalts Übereinstimmungen gesendet werden:

- Wählen Sie für den klassischen Client ein Kontrollkästchen als Teil der [Konfiguration](#configure-a-log-analytics-workspace-for-the-reports) für Azure Information Protection Analytics aus. Das Kontrollkästchen heißt **tiefere Analysen in Ihre sensiblen Daten**.
    
    Wenn Sie möchten, dass die meisten Benutzer, die diesen Client verwenden, Inhalts Übereinstimmungen senden, aber eine Teilmenge der Benutzer keine Inhalts Übereinstimmungen senden kann, aktivieren Sie das Kontrollkästchen, und konfigurieren Sie dann eine [Erweiterte Client Einstellung](./rms-client/client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users) in einer Bereichs bezogenen Richtlinie für die Teilmenge der Benutzer

- Konfigurieren Sie für den Unified Label-Client eine [Erweiterte Einstellung](./rms-client/clientv2-admin-guide-customizations.md#send-information-type-matches-to-azure-information-protection-analytics) in einer Bezeichnungs Richtlinie.

## <a name="prerequisites"></a>Voraussetzungen
Damit Sie Azure Information Protection-Berichte anzeigen und eigene Berichte erstellen können, müssen die folgenden Voraussetzungen erfüllt sein.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Azure-Abonnement, das Log Analytics umfasst und sich auf denselben Mandanten wie Azure Information Protection bezieht|Siehe Seite [Azure Monitor – Preise](https://azure.microsoft.com/pricing/details/log-analytics).<br /><br />Wenn Sie kein Azure-Abonnement haben oder Azure Log Analytics derzeit nicht verwenden, finden Sie auf der Preisseite einen Link für eine kostenlose Testversion.|
|Informationen zur Berichterstellung bei der Bezeichnung von Clients: <br /><br />-Azure Information Protection Clients|Sowohl der Unified-Bezeichnungs Client als auch der klassische Client werden unterstützt. <br /><br />Wenn Sie nicht bereits installiert sind, können Sie diese Clients aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen und installieren.|
|Informationen zur Berichterstellung aus cloudbasierten Daten speichern: <br /><br />-Microsoft Cloud App Security |Um Informationen aus Microsoft Cloud App Security anzuzeigen, konfigurieren Sie [Azure Information Protection-Integration](https://docs.microsoft.com/cloud-app-security/azip-integration).|
|Informationen zu Berichten aus lokalen Daten speichern: <br /><br />-Azure Information Protection Scanner |Eine Installationsanleitung für die Überprüfung finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md). |
|Informationen zur Berichterstellung von Windows 10-Computern:  <br /><br />-Minimaler Build von 1809 mit Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)|Sie müssen das Azure Information Protection-Integrations Feature von Microsoft Defender Security Center aktivieren. Weitere Informationen finden Sie unter [Übersicht über den Datenschutz in Windows](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview).|

### <a name="permissions-required-for-azure-information-protection-analytics"></a>Erforderliche Berechtigungen für Azure Information Protection-Analysen

Speziell für Azure Information Protection-Analysen können Sie nach der Konfiguration des Azure Log Analytics-Arbeitsbereichs die Azure AD-Administratorrolle „Sicherheitsleseberechtigter“ als Alternative zu den anderen Azure AD-Rollen verwenden, die die Verwaltung von Azure Information Protection im Azure-Portal unterstützen. Diese zusätzliche Rolle wird nur unterstützt, wenn Ihr Mandant nicht auf der [Unified-Bezeichnung-Plattform](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)ist.

Da Azure Information Protection Analytics die Azure-Überwachung verwendet, steuert die rollenbasierte Zugriffs Steuerung (RBAC) für Azure auch den Zugriff auf Ihren Arbeitsbereich. Daher benötigen Sie zum Verwalten von Azure Information Protection-Analysen sowohl eine Azure-Rolle als auch eine Azure AD-Administratorrolle. Wenn Sie noch keine Erfahrung mit Azure-Rollen haben, sollten Sie [Unterschiede zwischen Azure RBAC-Rollen und Azure AD-Administratorrollen](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles) lesen.

Details:

1. Eine der folgenden [Azure AD Administrator Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) für den Zugriff auf den Bereich "Azure Information Protection Analyse":
    
    - Um Ihren Log Analytics-Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
        - **Azure Information Protection-Administrator**
        - **Sicherheitsadministrator**
        - **Complianceadministrator**
        - **Kompatibilitäts Daten Administrator**
        - **Globaler Administrator**
    
    - Nachdem der Arbeitsbereich erstellt wurde, können Sie die folgenden Rollen mit weniger Berechtigungen verwenden, um die gesammelten Daten anzuzeigen:
    
        - **Sicherheitsleseberechtigter**
        - **Globaler Reader**

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

- Azure AD Administrator Rolle: **Sicherheits Leser**
- Azure-Rolle: **Log Analytics Reader**

Eine typische Rollenzuordnung für viele Organisationen ist jedoch die Azure AD-Rolle des **Sicherheitsleseberechtigten** und die Azure-Rolle des **Leseberechtigten**.

### <a name="storage-requirements-and-data-retention"></a>Speicheranforderungen und Daten Aufbewahrung

Die Menge der Daten, die in Ihrem Azure Information Protection Arbeitsbereich erfasst und gespeichert werden, variiert für jeden Mandanten erheblich. Dies hängt von Faktoren ab, wie z. b. wie viele Azure Information Protection Clients und andere unterstützte Endpunkte vorhanden sind, egal ob Sammeln von Endpunkt Ermittlungs Daten, Sie haben Scanner bereitgestellt, die Anzahl der geschützten Dokumente, auf die zugegriffen wird usw.

Als Ausgangspunkt kann es jedoch hilfreich sein, die folgenden Schätzwerte zu finden:

- Nur für Überwachungsdaten, die von Azure Information Protection Clients generiert werden: 2 GB pro 10.000 aktive Benutzer pro Monat.

- Für Überwachungsdaten, die von Azure Information Protection Clients, Scannern und Microsoft Defender ATP generiert werden: 20 GB pro 10.000 aktive Benutzer pro Monat.

Wenn Sie eine obligatorische Bezeichnung verwenden oder für die meisten Benutzer eine Standard Bezeichnung konfiguriert haben, sind ihre Tarife wahrscheinlich deutlich höher.

Azure Monitor Protokolle verfügt über die Funktion " **Nutzung und geschätzte Kosten** ", mit deren Hilfe Sie die Menge der gespeicherten Daten schätzen und überprüfen können. Außerdem können Sie die Daten Beibehaltungs Dauer für den Log Analytics Arbeitsbereich steuern. Weitere Informationen finden Sie unter [Verwalten von Nutzung und Kosten mit Azure Monitor Protokollen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-cost-storage).

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Konfigurieren eines Log Analytics-Arbeitsbereichs für Berichte

1. Wenn dies noch nicht erfolgt ist, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal](https://portal.azure.com) mit einem Konto an, das über die [erforderlichen Berechtigungen für die Azure Information Protection-Analyse](#permissions-required-for-azure-information-protection-analytics) verfügt. Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.
    
2. Navigieren Sie zu den Menüoptionen **Verwalten**, und wählen Sie **Analyse konfigurieren (Vorschau)** aus.

3. Im Bereich **Azure Information Protection Log Analytics** wird eine Liste aller Log Analytics Arbeitsbereiche angezeigt, die sich im Besitz Ihres Mandanten befinden. Nehmen Sie eine der folgenden Aktionen vor:
    
    - So erstellen Sie einen neuen Log Analytics Arbeitsbereich: Wählen Sie **neuen Arbeitsbereich erstellen**aus, und geben Sie im **Bereich Log Analytics-Arbeitsbereich** die angeforderten Informationen an.
    
    - Verwenden eines vorhandenen Log Analytics-Arbeitsbereichs: Wählen Sie den gewünschten Arbeitsbereich aus der Liste aus.
    
    Wenn Sie Hilfe beim Erstellen des Log Analytics-Arbeitsbereichs benötigen, lesen Sie sich den Artikel [Erstellen eines Log Analytics-Arbeitsbereichs im Azure-Portal](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace) durch.

4. Wenn Sie über Azure Information Protection Clients (klassisch) verfügen, aktivieren Sie das Kontrollkästchen **tiefere Analysen in Ihre sensiblen Daten aktivieren** , wenn Sie die eigentlichen Daten speichern möchten, die als sensible Informationen identifiziert werden. Weitere Informationen zu dieser Einstellung finden Sie im Abschnitt [Inhalts Übereinstimmungen für eine tiefere Analyse](#content-matches-for-deeper-analysis) auf dieser Seite.

5. Wählen Sie **OK** aus.

Sie sind jetzt bereit, die Berichte anzuzeigen.

## <a name="how-to-view-the-reports"></a>Anzeigen von Berichten

Suchen Sie im Bereich Azure Information Protection die Menü Optionen **Dashboards** , und wählen Sie eine der folgenden Optionen aus:

- **Nutzungsbericht (Vorschauversion)** : Dieser Bericht informiert Sie darüber, wie Ihre Bezeichnungen verwendet werden.

- **Aktivitätsprotokolle (Vorschau)** : Mithilfe dieses Berichts finden Sie Bezeichnungsaktionen von Benutzern sowie auf Geräten und Dateipfaden. Außerdem können Sie für geschützte Dokumente für Benutzer sowohl innerhalb als auch außerhalb Ihrer Organisation Zugriffsversuche (erfolgreich oder verweigert) erkennen, auch wenn Sie den Azure Information Protection-Client nicht installiert haben.
    
    Dieser Bericht enthält eine Option **Spalten**, mit der Sie mehr Aktivitätsinformationen als in der Standardanzeige anzeigen können. Wenn Sie **Aktivitätsdetails** auswählen, werden weitere Details zu einer Datei angezeigt.

- **Daten Ermittlung (Vorschau)** : Verwenden Sie diesen Bericht, um Informationen zu den von den Scannern gefundenen Dateien und unterstützten Endpunkten anzuzeigen.
    
    Tipp: aus den gesammelten Informationen können Benutzer auf Dateien zugreifen, die vertrauliche Informationen von einem Speicherort enthalten, von dem Sie nicht wissen, was Sie gerade nicht kennen oder überprüfen:
    
    - Wenn die Zugriffe vor Ort stattfinden, können Sie die Orte der Azure Information Protection-Überprüfung als zusätzliche Datenrepositorys hinzufügen.
    - Wenn die Zugriffe über die Cloud stattfinden, können Sie die Orte über Microsoft Cloud App Security verwalten. 
    
- **Empfehlungen (Vorschau)** : Verwenden Sie diesen Bericht zum Identifizieren von Dateien, die vertrauliche Informationen enthalten, und mindern Sie das Risiko, indem Sie die Empfehlungen befolgen.
    
    Wenn Sie ein Element auswählen, zeigt die Option **Daten anzeigen** die Überwachungsaktivitäten an, die die Empfehlung ausgelöst haben.


## <a name="how-to-modify-the-reports-and-create-custom-queries"></a>Ändern von Berichten und Erstellen benutzerdefinierter Abfragen

Wählen Sie im Dashboard das Abfrage Symbol aus, um einen Bereich für die **Protokoll Suche** zu öffnen: 

![Log Analytics-Symbol zum Anpassen von Azure Information Protection-Berichten](./media/log-analytics-icon.png)


Die protokollierten Daten für Azure Information Protection werden in folgender Tabelle gespeichert: **InformationProtectionLogs_CL**

Wenn Sie eigene Abfragen erstellen, verwenden Sie benutzerfreundliche Schemanamen, die als **InformationProtectionEvents**-Funktionen implementiert wurden. Diese Funktionen werden von Attributen abgeleitet, die für benutzerdefinierte Abfragen unterstützt werden (einige Attribute sind nur für den internen Gebrauch bestimmt). Die Namen bleiben unverändert, auch wenn sich die zugrunde liegenden Attribute aufgrund von Neuerungen und neuen Funktionen ändern.

### <a name="friendly-schema-reference-for-event-functions"></a>Benutzerfreundliche Schemareferenz für Ereignisfunktionen

In der folgenden Tabelle finden Sie die Anzeigenamen der Ereignisfunktionen, die Sie für benutzerdefinierte Abfragen mit Azure Information Protection-Analysen verwenden können.

|Spaltenname|Description|
|-----------|-----------|
|Zeit|Ereignis Zeit: UTC im Format yyyy-mm-ddThh: mm: SS|
|Benutzer|Benutzer: UPN oder Domäne \ Benutzer formatieren|
|ItemPath|Vollständiger Element Pfad oder e-Mail-Betreff|
|Artikelname|Datei Name oder e-Mail-Betreff |
|Methode|Zugewiesene Methode für Bezeichnung: manuell, automatisch, empfohlen, Standard oder obligatorisch|
|Aktivität|Audit Activity: downgradelta Abel, upgradelta Abel, removelabel, newlabel, Discover, Access, removecustomprotection, changecustomprotection oder newcustomprotection |
|Bezeichnungsname|Name der Bezeichnung (nicht lokalisiert)|
|LabelNameBefore |Name der Bezeichnung vor der Änderung (nicht lokalisiert) |
|ProtectionType|Schutztyp [JSON] <br />{ <br />"Type": ["Template", "Custom", "DoNotForward"], <br />  "TemplateID": "GUID" <br /> } <br />|
|Schutz vor|Schutztyp vor Änderung [JSON] |
|MachineName |Vollständig verfügbarer voll qualifizierter Name Andernfalls Hostname|
|DeviceRisk|Geräte Risikobewertung aus wdatp, wenn verfügbar|
|Plattform|Geräteplattform (Win, OSX, Android, IOS) |
|ApplicationName|Anzeige Name der Anwendung|
|Aipversion|Die Version des Azure Information Protection Clients, der die Überwachungsaktion ausgeführt hat. |
|TenantId|Azure AD-Mandanten-ID |
|AzureApplicationId|Azure AD registrierte Anwendungs-ID (GUID)|
|ProcessName|Prozess, der MIP SDK hostet|
|LabelId|GUID der Bezeichnung oder NULL|
|Isprotehiert|Ob geschützt: Ja/Nein |
|Schutz Besitzer |Rights Management Besitzer im UPN-Format|
|LabelIdBefore|GUID der Bezeichnung oder NULL vor der Änderung|
|InformationTypesAbove55|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 55 oder höher |
|InformationTypesAbove65|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 65 oder höher |
|InformationTypesAbove75|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 75 oder höher |
|InformationTypesAbove85|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 85 oder höher |
|InformationTypesAbove95|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 95 oder höher|
|DiscoveredInformationTypes |JSON-Array von [sensitiveinformation](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for) , das in Daten und dem zugehörigen Inhalt gefunden wurde (sofern aktiviert). ein leeres Array bedeutet, dass keine Informationstypen gefunden werden, und NULL bedeutet, dass keine Informationen verfügbar sind. |
|Protectedbefore|Ob der Inhalt vor der Änderung geschützt wurde: Ja/Nein |
|ProtectionOwnerBefore|Rights Management Besitzer vor der Änderung |
|Userbegrün dung|Begründung beim Herabstufen oder Entfernen der Bezeichnung|
|LastModifiedBy|Benutzer im UPN-Format, von dem die Datei zuletzt geändert wurde. Nur für Office und SharePoint Online verfügbar|
|LastModifiedDate|UTC im Format yyyy-mm-ddThh: mm: SS: verfügbar für Office & nur SharePoint Online |


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
Nachdem Sie die Informationen in den Berichten überprüft haben, können Sie bei Verwendung des Azure Information Protection Clients Änderungen an ihrer Azure Information Protection Richtlinie vornehmen. Eine Anleitung dazu finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Wenn Sie ein Microsoft 365-Abonnement haben, können Sie die Nutzung von Bezeichnungen auch im Microsoft 365 Compliance Center und im Microsoft 365 Security Center anzeigen. Weitere Informationen finden Sie unter [Anzeigen der Nutzung der Bezeichnung mit Bezeichnungsanalysen](/microsoft-365/compliance/label-analytics).
