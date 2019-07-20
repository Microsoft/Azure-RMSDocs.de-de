---
title: Zentrale Berichterstellung für Azure Information Protection
description: Erfahren Sie, wie Sie mithilfe der zentralen Berichterstellung die Übernahme Ihrer Azure Information Protection-Bezeichnungen nachverfolgen und Dateien mit vertraulichen Daten erkennen.
author: cabailey
ms.author: cabailey
ms.date: 07/04/2019
manager: barbkess
ms.topic: article
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: 120cc1298d48c3dd9952362b8abacbca22ef6acc
ms.sourcegitcommit: eff3bfbf95588e8876d9d6cbb95f80d304142668
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68340738"
---
# <a name="central-reporting-for-azure-information-protection"></a>Zentrale Berichterstellung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Dieses Feature befindet sich in der Vorschau und unterliegt Änderungen.

Verwenden Sie die Azure Information Protection Analysen für die zentrale Berichterstellung, um die Einführung Ihrer Azure Information Protection-Bezeichnungen einfacher zu verfolgen. Zusätzlich:

- Unternehmensweite Überwachung bezeichneter und geschützter Dokumente und E-Mails

- Identifizieren von Dokumenten, die vertrauliche Unternehmensinformationen enthalten

- Überwachen Sie den Benutzerzugriff auf bezeichnete Dokumente und E-Mails, und verfolgen Sie Änderungen an Dokumentklassifizierungen.

- Identifizieren Sie Dokumente, die vertrauliche Informationen enthalten und geschützt werden müssen, da Ihre Organisation andernfalls einem Risiko ausgesetzt ist, und verringern Sie dieses Risiko mithilfe der Empfehlungen.

Die Daten, die Sie sehen, werden von ihren Azure Information Protection Clients und Azure Information Protection Scannern, von Windows-Computern, auf denen [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)](/windows/security/threat-protection/microsoft-defender-atp/overview)ausgeführt wird, und von [ Clients, die eine einheitliche Bezeichnung unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

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
    
    - Welche Bezeichnungsaktionen von einer bestimmten Anwendung wie Datei-Explorer und Rechtsklicken oder dem AzureInformationProtection-PowerShell-Modul ausgeführt wurden
    
    - Drilldown auf gemeldete Dateien, um zusätzliche Informationen in den **Aktivitätsdetails** zu finden

- Im Bericht **Datenermittlung**:

    - Welche Dateien befinden sich auf den überprüften Daten Depots, Windows 10-Computern oder Computern, auf denen die Azure Information Protection Client oder Clients ausgeführt werden, die die [einheitliche Bezeichnung unterstützen](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling)
    
    - Welche Dateien Bezeichnungen aufweisen und geschützt werden sowie den Speicherort der Dateien nach Bezeichnung
    
    - Welche Dateien vertrauliche Daten für bekannte Kategorien enthalten, z.B. Finanzdaten und persönliche Informationen, und den Speicherort von Dateien nach diesen Kategorien

- Aus dem Bericht **Empfehlungen**:
    
    - Identifizieren Sie ungeschützte Dateien, die eine bekannte Art von vertraulichen Informationen enthalten. Mit einer Empfehlung können Sie sofort die entsprechende Bedingung für eine Ihrer Bezeichnungen konfigurieren, um die Bezeichnung automatisch oder nach Empfehlung anzuwenden.
        
        Wenn Sie die Empfehlung befolgen, geschieht Folgendes: Wenn die Dateien das nächste Mal von einem Benutzer geöffnet oder vom Azure Information Protection-Scanner überprüft werden, können die Dateien automatisch klassifiziert und geschützt werden.
    
    - Identifizierten Sie, welche Datenrepositorys über Dateien mit identifizierten vertraulichen Informationen verfügen, aber nicht von Azure Information Protection überprüft werden. Mit einer Empfehlung können Sie den identifizierten Datenspeicher sofort zu einem der Profile Ihres Scanners hinzufügen.
        
        Wenn Sie die Empfehlung befolgen, geschieht Folgendes: Im nächsten Scannerzyklus können die Dateien automatisch klassifiziert und geschützt werden.

Die Berichte verwenden [Azure Monitor](/azure/log-analytics/log-analytics-overview), um die Daten in einem Log Analytics-Arbeitsbereich zu speichern, der Ihrer Organisation gehört. Wenn Sie mit der Abfragesprache vertraut sind, können Sie die Abfragen ändern und neue Berichte und Power BI-Dashboards erstellen. Das folgende Tutorial dient als Einführung in die Abfragesprache: [Erste Schritte mit Abfragen in Log Analytics](/azure/azure-monitor/log-query/get-started-queries).

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

- Für Dokumente: Den Dateipfad und -namen von Dokumenten, die Bezeichnungen aufweisen.

- Für E-Mails: Den Betreff und den Absender von E-Mails mit Bezeichnung 

- Die Typen vertraulicher Informationen ([vordefiniert](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) und benutzerdefiniert), die im Inhalt erkannt wurden.

- Die Azure Information Protection-Clientversion.

- Die Client-Betriebssystemversion.

Diese Informationen werden in einem Azure Log Analytics-Arbeitsbereich gespeichert, der Ihrer Organisation gehört, und kann unabhängig von Azure Information Protection von Benutzern eingesehen werden, die über Zugriffsrechte für diesen Arbeitsbereich verfügen. Details hierzu finden Sie im Abschnitt [Erforderliche Berechtigungen für Azure Information Protection-Analysen](#permissions-required-for-azure-information-protection-analytics). Informationen zum Verwalten des Zugriffs auf Ihren Arbeitsbereich finden Sie in der Azure-Dokumentation im Abschnitt [Verwalten des Zugriffs auf den Log Analytics-Arbeitsbereich mit Azure-Berechtigungen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-to-log-analytics-workspace-using-azure-permissions).

Um zu verhindern, dass Azure Information Protection-Clients diese Daten senden, stellen Sie die [Richtlinieneinstellung](configure-policy-settings.md) von **Überwachungsdaten an Azure Information Protection-Protokollanalyse senden** auf **Aus**:

- Die meisten Benutzer können diese Daten senden, und eine Teilmenge von Benutzern kann keine Überwachungsdaten senden: 
    - Stellen Sie **Überwachungsdaten an Azure Information Protection-Protokollanalyse senden** in einer bereichsbezogenen Richtlinie für die Teilmenge an Benutzern auf **Aus**. Diese Konfiguration ist typisch für Produktionsszenarien.

- So kann nur eine Teilmenge an Benutzern Überwachungsdaten senden: 
    - Stellen Sie **Überwachungsdaten an Azure Information Protection-Protokollanalyse senden** in einer globalen Richtlinie auf **Aus**  und in einer bereichsbezogenen Richtlinie für die Teilmenge an Benutzern auf **Ein**. Diese Konfiguration ist typisch für Testszenarien.

#### <a name="content-matches-for-deeper-analysis"></a>Inhaltsübereinstimmungen für umfassendere Analysen 

Ihr Azure Log Analytics-Arbeitsbereich für Azure Information Protection enthält ein Kontrollkästchen zum Sammeln und Speichern der Daten, die durch die vertraulichen Datentypen oder Ihre individuellen Bedingungen identifiziert werden. Dies kann z. B. gefundene Kreditkartennummern sowie Sozialversicherungsnummern, Kennwortnummern und Kontonummern betreffen. Wenn Sie diese zusätzlichen Daten nicht senden möchten, deaktivieren Sie das Kontrollkästchen. Wenn Sie möchten, dass die meisten Benutzer diese zusätzlichen Daten senden und eine Teilmenge von Benutzern sie nicht senden kann, aktivieren Sie das Kontrollkästchen und konfigurieren Sie eine [erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users) in einer bereichsbezogenen Richtlinie für die Teilmenge von Benutzern.

Nachdem Sie die Inhaltsübereinstimmungen gesammelt haben, werden sie in den Berichten angezeigt, wenn Sie für die Dateien aus den Aktivitätsprotokollen einen Drilldown ausführen, um **Aktivitätsdetails** anzuzeigen. Diese Informationen können auch mit Abfragen eingesehen und abgerufen werden.

## <a name="prerequisites"></a>Vorraussetzungen
Damit Sie Azure Information Protection-Berichte anzeigen und eigene Berichte erstellen können, müssen die folgenden Voraussetzungen erfüllt sein.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Azure-Abonnement, das Log Analytics umfasst und sich auf denselben Mandanten wie Azure Information Protection bezieht|Siehe Seite [Azure Monitor – Preise](https://azure.microsoft.com/pricing/details/log-analytics).<br /><br />Wenn Sie kein Azure-Abonnement haben oder Azure Log Analytics derzeit nicht verwenden, finden Sie auf der Preisseite einen Link für eine kostenlose Testversion.|
|Der Azure Information Protection Client oder der Azure Information Protection Unified-Beschriftungs Client|Wenn Sie noch nicht über einen dieser Clients verfügen, können Sie diese aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen und installieren. <br /><br /> Stellen Sie sicher, dass Sie über die neueste Version verfügen, um [alle Features](#features-that-require-a-minimum-version-of-the-client) für Azure Information Protection Analytics zu unterstützen.|
|Für den Bericht **Ermittlung und Risiko**: <br /><br />-Zum Anzeigen von Daten aus lokalen Daten speichern haben Sie mindestens eine Instanz des Azure Information Protection Scanners bereitgestellt. <br /><br />-Zum Anzeigen von Daten von Windows 10-Computern müssen Sie ein minimaler Build von 1809 sein. Sie verwenden Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP), und Sie haben das Azure Information Protection-Integrations Feature von Microsoft aktiviert. Defender-Security Center|Eine Installationsanleitung für die Überprüfung finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md). <br /><br />Informationen zum Konfigurieren und Verwenden des Azure Information Protection-Integrations Features von Microsoft Defender Security Center finden Sie unter [Übersicht über den Datenschutz in Windows](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview).|
|Für den Bericht **Empfehlungen**: <br /><br />-Wenn Sie ein neues Datenrepository aus dem Azure-Portal als empfohlene Aktion hinzufügen möchten, müssen Sie die neueste Version der allgemeinen Verfügbarkeit des Azure Information Protection Scanners verwenden. |Informationen zum Bereitstellen des Scanners finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).|

### <a name="permissions-required-for-azure-information-protection-analytics"></a>Erforderliche Berechtigungen für Azure Information Protection-Analysen

Speziell für Azure Information Protection-Analysen können Sie nach der Konfiguration des Azure Log Analytics-Arbeitsbereichs die Azure AD-Administratorrolle „Sicherheitsleseberechtigter“ als Alternative zu den anderen Azure AD-Rollen verwenden, die die Verwaltung von Azure Information Protection im Azure-Portal unterstützen.

Da dieses Feature die Azure Monitor-Plattform verwendet, steuert die rollenbasierte Zugriffssteuerung (Role-Based Access Control, RBAC) für Azure auch den Zugriff auf Ihren Arbeitsbereich. Daher benötigen Sie zum Verwalten von Azure Information Protection-Analysen sowohl eine Azure-Rolle als auch eine Azure AD-Administratorrolle. Wenn Sie noch keine Erfahrung mit Azure-Rollen haben, sollten Sie [Unterschiede zwischen Azure RBAC-Rollen und Azure AD-Administratorrollen](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles) lesen.

Details:

1. Um auf das Azure Information Protection-Analyseblatt zuzugreifen, müssen Sie eine der folgenden [Azure AD-Administratorrollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) besitzen:
    
    - Um Ihren Log Analytics-Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
        - **Azure Information Protection-Administrator**
        - **Sicherheitsadministrator**
        - **Complianceadministrator**
        - **Kompatibilitäts Daten Administrator**
        - **Globaler Administrator**
    
    - Nachdem der Arbeitsbereich erstellt wurde, können Sie dann die folgende Rolle mit weniger Berechtigungen verwenden, um die gesammelten Daten anzuzeigen:
    
        - **Sicherheitsleseberechtigter**
    
    > [!NOTE] 
    > Wenn Ihr Mandant zum vereinheitlichten Speicher der vereinheitlichten Bezeichnung migriert wurde, können Sie die Azure Information Protection Administrator-Rolle nicht verwenden. [Weitere Informationen](configure-policy-migrate-labels.md#administrative-roles-that-support-the-unified-labeling-platform)

2. Darüber hinaus benötigen Sie eine der folgenden [Azure Log Analytics-Rollen](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/manage-access#manage-access-to-log-analytics-workspace-using-azure-permissions) oder standardmäßige [Azure-Rollen](https://docs.microsoft.com/azure/role-based-access-control/overview#role-assignments), um auf Ihren Azure Log Analytics-Arbeitsbereich zuzugreifen:
    
    - Um einen Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
        - **Log Analytics-Mitwirkender**
        - **Mitwirkender**
        - **Besitzer**
    
    - Nachdem der Arbeitsbereich erstellt wurde, können Sie dann eine der folgenden Rollen mit weniger Berechtigungen verwenden, um die gesammelten Daten anzuzeigen:
    
        - **Log Analytics-Leser**
        - **Leser**

#### <a name="minimum-roles-to-view-the-reports"></a>Mindestens erforderliche Rolle zum Anzeigen von Berichten

Nachdem Sie Ihren Arbeitsbereich für Azure Information Protection-Analysen erstellt haben, benötigen Sie mindestens die beiden folgenden Rollen zum Anzeigen der Berichte der Azure Information Protection-Analysen:

- Azure AD-Administratorrolle: **Sicherheitsleseberechtigter**
- Azure-Rolle: **Log Analytics-Leser**

Eine typische Rollenzuordnung für viele Organisationen ist jedoch die Azure AD-Rolle des **Sicherheitsleseberechtigten** und die Azure-Rolle des **Leseberechtigten**.

### <a name="features-that-require-a-minimum-version-of-the-client"></a>Funktionen, für die eine Mindestversion des Clients erforderlich ist

Sie können die Versions Verlaufs Informationen für den [Azure Information Protection Unified](./rms-client/unifiedlabelingclient-version-release-history.md) -Bezeichnungs Client und den [Azure Information Protection-Client](./rms-client/client-version-release-history.md) verwenden, um zu bestätigen, ob Ihre Version des Clients alle zentralen Berichterstattungs Features unterstützt. Die Mindestversionen für die Clients:

Für den Azure Information Protection Unified Bezeichnung-Client:

- Unterstützung für Überwachung und Endpunkt Ermittlung: Version 2.0.778.0

Für den Azure Information Protection-Client:

- Unterstützung für die Überwachung: Version 1.41.51.0
- Unterstützung für die Endpunkt Ermittlung: Version 1.48.204.0

### <a name="storage-requirements-and-data-retention"></a>Speicheranforderungen und Daten Aufbewahrung

Die Menge der Daten, die in Ihrem Azure Information Protection Arbeitsbereich erfasst und gespeichert werden, variiert für jeden Mandanten erheblich. Dies hängt von Faktoren ab, wie z. b. wie viele Azure Information Protection Clients und andere unterstützte Endpunkte vorhanden sind, egal ob Sammeln von Endpunkt Ermittlungs Daten, bereitgestellte Scanner und so weiter.

Als Ausgangspunkt kann es jedoch hilfreich sein, die folgenden Schätzwerte zu finden:

- Nur für Überwachungsdaten, die von Azure Information Protection Clients generiert werden: 2 GB pro 10.000 aktiven Benutzern pro Monat.

- Für Überwachungsdaten, die von Azure Information Protection Clients, Scanner und Microsoft Defender ATP generiert werden: 20 GB pro 10.000 aktiven Benutzern pro Monat.

Wenn Sie eine obligatorische Bezeichnung verwenden oder eine Standard Bezeichnung in der globalen Richtlinie konfiguriert haben, sind ihre Tarife wahrscheinlich deutlich höher.

Azure Monitor Protokolle verfügt über die Funktion " **Nutzung und geschätzte Kosten** ", mit deren Hilfe Sie die Menge der gespeicherten Daten schätzen und überprüfen können. Außerdem können Sie die Daten Beibehaltungs Dauer für den Log Analytics Arbeitsbereich steuern. Weitere Informationen finden Sie unter [Verwalten von Nutzung und Kosten mit Azure Monitor Protokollen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-cost-storage).

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Konfigurieren eines Log Analytics-Arbeitsbereichs für Berichte

1. Wenn dies noch nicht erfolgt ist, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal](https://portal.azure.com) mit einem Konto an, das über die [erforderlichen Berechtigungen für die Azure Information Protection-Analyse](#permissions-required-for-azure-information-protection-analytics) verfügt. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
2. Navigieren Sie zu den Menüoptionen **Verwalten**, und wählen Sie **Analyse konfigurieren (Vorschau)** aus.

3. Auf dem Blatt **Azure Information Protection-Protokollanalyse** sehen Sie eine Liste aller Log Analytics-Arbeitsbereiche, die Ihrem Mandanten gehören. Führen Sie eines der folgenden Verfahren aus:
    
    - Erstellen eines neuen Log Analytics-Arbeitsbereichs: Wählen Sie **Neuen Arbeitsbereich erstellen** aus, und geben Sie auf dem Blatt **Log Analytics-Arbeitsbereich** die erforderlichen Informationen ein.
    
    - Verwenden eines vorhandenen Log Analytics-Arbeitsbereichs: Wählen Sie den Arbeitsbereich aus der Liste aus.

Wenn Sie Hilfe beim Erstellen des Log Analytics-Arbeitsbereichs benötigen, lesen Sie sich den Artikel [Erstellen eines Log Analytics-Arbeitsbereichs im Azure-Portal](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace) durch.

Wenn der Arbeitsbereich konfiguriert wurde, können Sie die Berichte anzeigen.

> [!NOTE] 
> Es gibt derzeit ein bekanntes Problem bei der erstmaligen Anzeige von Daten in den Berichten. Wenn dieses Problem bei Ihnen auftritt, stellen Sie in der globalen Richtlinie die [Richtlinieneinstellung](configure-policy-settings.md) von **Überwachungsdaten an Azure Information Protection-Protokollanalysen senden** auf **Aus**, und speichern Sie die Richtlinie. Ändern Sie dann die gleiche Einstellung in **Ein**, und speichern Sie die Richtlinie. Nachdem Clients [ die Änderung heruntergeladen haben](configure-policy.md#making-changes-to-the-policy), kann es bis zu 30 Minuten dauern, bis ihre Überwachungsereignisse in Ihrem Log Analytics-Arbeitsbereich angezeigt werden.

## <a name="how-to-view-the-reports"></a>Anzeigen von Berichten

Suchen Sie auf dem Azure Information Protection-Blatt die Menüoptionen **Dashboards**, und wählen Sie eine der folgenden Optionen aus:

- **Nutzungsbericht (Vorschau)** : Dieser Bericht informiert Sie darüber, wie Ihre Bezeichnungen verwendet werden.

- **Aktivitätsprotokolle (Vorschau)** : Mithilfe dieses Berichts finden Sie Bezeichnungsaktionen von Benutzern sowie auf Geräten und Dateipfaden.
    
    Dieser Bericht enthält eine Option **Spalten**, mit der Sie mehr Aktivitätsinformationen als in der Standardanzeige anzeigen können. Wenn Sie **Aktivitätsdetails** auswählen, werden weitere Details zu einer Datei angezeigt.

- **Datenermittlung (Vorschau)** : Verwenden Sie diesen Bericht, um Informationen über bezeichnete Dateien anzuzeigen, die durch die Überprüfung und von unterstützten Endpunkten gefunden wurden.
    
    Tipp: Aus den gesammelten Informationen ist z. B. ersichtlich, welche Benutzer von Orten, die Sie nicht kennen oder die derzeit nicht überprüft werden, auf Dateien mit vertraulichen Informationen zugreifen:
    
    - Wenn die Zugriffe vor Ort stattfinden, können Sie die Orte der Azure Information Protection-Überprüfung als zusätzliche Datenrepositorys hinzufügen.
    - Wenn die Zugriffe über die Cloud stattfinden, können Sie die Orte über Microsoft Cloud App Security verwalten. 
    
- **Empfehlungen (Vorschau):** Verwenden Sie diesen Bericht, um Dateien zu identifizieren, die vertrauliche Informationen enthalten, und minimieren Sie das Risiko mithilfe der Empfehlungen.
    
    Wenn Sie ein Element auswählen, zeigt die Option **Daten anzeigen** die Überwachungsaktivitäten an, die die Empfehlung ausgelöst haben.


## <a name="how-to-modify-the-reports-and-create-custom-queries"></a>Ändern von Berichten und Erstellen benutzerdefinierter Abfragen

Wählen Sie im Dashboard das Abfragesymbol aus, um das Blatt **Protokollsuche** zu öffnen: 

![Log Analytics-Symbol zum Anpassen von Azure Information Protection-Berichten](./media/log-analytics-icon.png)


Die protokollierten Daten für Azure Information Protection werden in der folgenden Tabelle gespeichert: **InformationProtectionLogs_CL**

Wenn Sie eigene Abfragen erstellen, verwenden Sie benutzerfreundliche Schemanamen, die als **InformationProtectionEvents**-Funktionen implementiert wurden. Diese Funktionen werden von Attributen abgeleitet, die für benutzerdefinierte Abfragen unterstützt werden (einige Attribute sind nur für den internen Gebrauch bestimmt). Die Namen bleiben unverändert, auch wenn sich die zugrunde liegenden Attribute aufgrund von Neuerungen und neuen Funktionen ändern.

### <a name="friendly-schema-reference-for-event-functions"></a>Benutzerfreundliche Schemareferenz für Ereignisfunktionen

In der folgenden Tabelle finden Sie die Anzeigenamen der Ereignisfunktionen, die Sie für benutzerdefinierte Abfragen mit Azure Information Protection-Analysen verwenden können.

|Spaltenname|Beschreibung|
|-----------|-----------|
|Uhrzeit|Ereignis Zeit: UTC im Format yyyy-mm-ddThh: mm: SS|
|Benutzer|Benutzer: UPN oder Domäne \ Benutzer formatieren|
|ItemPath|Vollständiger Element Pfad oder e-Mail-Betreff|
|ItemName|Datei Name oder e-Mail-Betreff |
|Methode|Zugewiesene Methode der Bezeichnung: Manuell, automatisch, empfohlen, Standard oder obligatorisch|
|Aktivität|Überwachungs Aktivität: Downgradelta Abel, upgradelta Abel, removelabel, newlabel, Discover, Access, removecustomprotection, changecustomprotection oder newcustomprotection |
|Bezeichnungsname|Name der Bezeichnung (nicht lokalisiert)|
|LabelNameBefore |Name der Bezeichnung vor der Änderung (nicht lokalisiert) |
|ProtectionType|Schutztyp [JSON] <br />{ <br />"Type": ["Template", "Custom", "DoNotForward"], <br />  "TemplateID": "GUID" <br /> } <br />|
|Schutz vor|Schutztyp vor Änderung [JSON] |
|InformationTypesMatches|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) in Daten gefunden, bei denen ein leeres Array keine Informationstypen gefunden hat, und NULL bedeutet, dass keine Informationen verfügbar sind|
|MachineName |Vollständig verfügbarer voll qualifizierter Name Andernfalls Hostname|
|DeviceRisk|Geräte Risikobewertung aus wdatp, wenn verfügbar|
|Platform|Geräteplattform (Win, OSX, Android, IOS) |
|ApplicationName|Anzeige Name der Anwendung|
|Aipversion|Die Version des Azure Information Protection Clients, der die Überwachungsaktion ausgeführt hat. |
|TenantId|Azure AD-Mandanten-ID |
|AzureApplicationId|Azure AD registrierte Anwendungs-ID (GUID)|
|ProcessName|Prozess, der MIP SDK hostet|
|LabelId|GUID der Bezeichnung oder NULL|
|Isprotehiert|Ob geschützt: Ja/Nein |
|Schutz Besitzer |Rights Management Besitzer im UPN-Format|
|LabelIdBefore|GUID der Bezeichnung oder NULL vor der Änderung|
|InformationTypesAbove55|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 55 oder höher |
|InformationTypesAbove65|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 65 oder höher |
|InformationTypesAbove75|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 75 oder höher |
|InformationTypesAbove85|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 85 oder höher |
|InformationTypesAbove95|JSON-Array von [sensitiveinformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) in Daten mit Vertrauensgrad 95 oder höher|
|DiscoveredInformationTypes |JSON-Array von [sensitiveinformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) , das in Daten und dem zugehörigen Inhalt gefunden wurde (sofern aktiviert). ein leeres Array bedeutet, dass keine Informationstypen gefunden werden, und NULL bedeutet, dass keine Informationen verfügbar sind. |
|Protectedbefore|Gibt an, ob der Inhalt vor der Änderung geschützt wurde: Ja/Nein |
|ProtectionOwnerBefore|Rights Management Besitzer vor der Änderung |
|Userbegrün dung|Begründung beim Herabstufen oder Entfernen der Bezeichnung|
|LastModifiedBy|Benutzer im UPN-Format, von dem die Datei zuletzt geändert wurde. Nur für Office und SharePoint Online verfügbar|
|LastModifiedDate|UTC im Format yyyy-mm-ddThh: mm: SS: Nur für Office & SharePoint Online verfügbar |


#### <a name="examples-using-informationprotectionevents"></a>Beispiele für InformationProtectionEvents

Anhand der folgenden Beispiele erfahren Sie, wie Sie das benutzerfreundliche Schema zur Erstellung benutzerdefinierter Abfragen verwenden können.

##### <a name="example-1-return-all-users-who-sent-audit-data-in-the-last-31-days"></a>Beispiel 1: Es werden alle Benutzer zurückgegeben, die in den letzten 31 Tagen Überwachungsdaten gesendet haben. 

```
InformationProtectionEvents 
| where Time > ago(31d) 
| distinct User 
```

 
##### <a name="example-2-return-the-number-of-labels-that-were-downgraded-per-day-in-the-last-31-days"></a>Beispiel 2: Es wird die Anzahl der Bezeichnungen zurückgegeben, die in den letzten 31 Tagen pro Tag herabgestuft wurden. 


```
InformationProtectionEvents 
| where Time > ago(31d) 
| where Activity == "DowngradeLabel"  
| summarize Label_Downgrades_per_Day = count(Activity) by bin(Time, 1d) 
 
```
 
##### <a name="example-3-return-the-number-of-labels-that-were-downgraded-from-confidential-by-user-in-the-last-31-days"></a>Beispiel 3: Es wird die Anzahl der Bezeichnungen zurückgegeben, die in den letzten 31 Tagen vom Benutzer von „Vertraulich“ herabgestuft wurden. 

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

Wenn Sie ein Microsoft 365-Abonnement haben, können Sie die Nutzung von Bezeichnungen auch im Microsoft 365 Compliance Center und im Microsoft 365 Security Center anzeigen. Weitere Informationen finden Sie unter [Anzeigen der Nutzung der Bezeichnung mit Bezeichnungsanalysen](/Office365/SecurityCompliance/label-analytics).
