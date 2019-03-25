---
title: Zentrale Berichterstellung für Azure Information Protection
description: Erfahren Sie, wie Sie mithilfe der zentralen Berichterstellung die Übernahme Ihrer Azure Information Protection-Bezeichnungen nachverfolgen und Dateien mit vertraulichen Daten erkennen.
author: cabailey
ms.author: cabailey
ms.date: 03/22/2019
manager: barbkess
ms.topic: article
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: c7f862a7a16579b6d414c79015c42664e4066c29
ms.sourcegitcommit: cf06c3854e6ee8645c3b71a0257bdb6a1b569843
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58343042"
---
# <a name="central-reporting-for-azure-information-protection"></a>Zentrale Berichterstellung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Dieses Feature befindet sich in der Vorschau und unterliegt Änderungen.

Verwenden Sie die Azure Information Protection Analysen für die zentrale Berichterstellung, um die Einführung Ihrer Azure Information Protection-Bezeichnungen zu verfolgen. Zusätzlich:

- Überwachen Sie den Benutzerzugriff auf bezeichnete Dokumente und E-Mails sowie alle Änderungen an deren Klassifizierung. 

- Identifizieren Sie Dokumente, die vertrauliche Informationen enthalten und geschützt werden müssen, da Ihre Organisation andernfalls einem Risiko ausgesetzt ist, und verringern Sie dieses Risiko mithilfe der Empfehlungen.

Derzeit werden die angezeigten Daten von Ihren Azure Information Protection- Clients und Azure Information Protection-Überprüfungen sowie von Windows-Computern mit [Windows Defender Advanced Threat Protection (Windows Defender ATP)](/windows/security/threat-protection/windows-defender-atp/overview) zusammengefasst.

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

- Im Bericht **Datenermittlung**:

    - Welche Dateien sich in Ihren überprüften Datenrepositorys oder auf Windows 10-Computern befinden
    
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

- [Discover and protect sensitive data through Azure Information Protection and Windows Defender ATP (Ermitteln und Schützen vertraulicher Daten mit Azure Information Protection und Windows Defender ATP)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discover-and-protect-sensitive-data-through-Azure-Information/ba-p/297292)

### <a name="information-collected-and-sent-to-microsoft"></a>Gesammelte und an Microsoft gesendete Informationen

Um diese Berichte zu erstellen, senden die Endpunkte die folgenden Informationen an Microsoft:

- Die Bezeichnungsaktion. Z.B. das Festlegen oder Ändern einer Bezeichnung, das Hinzufügen oder Entfernen von Schutz, automatische und empfohlene Bezeichnungen.

- Den Bezeichnungsnamen vor und nach der Bezeichnungsaktion

- Die Mandanten-ID Ihrer Organisation.

- Die Benutzer-ID (E-Mail-Adresse oder UPN).

- Den Namen des Benutzergeräts

- Für Dokumente: Den Dateipfad und -namen von Dokumenten, die Bezeichnungen aufweisen.

- Für E-Mails: Den Betreff, den Absender und die Empfänger für E-Mails mit Bezeichnung 

- Die Typen vertraulicher Informationen ([vordefiniert](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) und benutzerdefiniert), die im Inhalt erkannt wurden.

- Die Azure Information Protection-Clientversion.

- Die Client-Betriebssystemversion.

Diese Informationen werden in einem Azure Log Analytics-Arbeitsbereich gespeichert, der Ihrer Organisation gehört, und kann unabhängig von Azure Information Protection von Benutzern eingesehen werden, die über Zugriffsrechte für diesen Arbeitsbereich verfügen. Details hierzu finden Sie im Abschnitt [Erforderliche Berechtigungen für Azure Information Protection-Analysen](#permissions-required-for-azure-information-protection-analytics). Informationen zum Verwalten des Zugriffs auf Ihren Arbeitsbereich finden Sie in der Azure-Dokumentation im Abschnitt [Verwalten des Zugriffs auf den Log Analytics-Arbeitsbereich mit Azure-Berechtigungen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-to-log-analytics-workspace-using-azure-permissions).

> [!NOTE]
> Ihr Log Analytics-Arbeitsbereich für Azure Information Protection umfasst ein Kontrollkästchen für übereinstimmende Dokumentinhalte. Wenn Sie dieses Kontrollkästchen aktivieren, werden auch die tatsächlichen Daten erfasst, die von den Typen von vertraulichen Informationen oder Ihren benutzerdefinierten Bedingungen ermittelt wurden. Dies kann z. B. gefundene Kreditkartennummern sowie Sozialversicherungsnummern, Kennwortnummern und Kontonummern betreffen. Wenn diese Daten nicht erfasst werden sollen, deaktivieren Sie das Kontrollkästchen.
>
> Derzeit werden die Informationen nicht in den Berichten, sondern nur über Abfragen angezeigt.

## <a name="prerequisites-for-azure-information-protection-analytics"></a>Voraussetzungen für Azure Information Protection-Analysen
Damit Sie Azure Information Protection-Berichte anzeigen und eigene Berichte erstellen können, müssen die folgenden Voraussetzungen erfüllt sein.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Azure-Abonnement, das Log Analytics umfasst|Siehe Seite [Azure Monitor – Preise](https://azure.microsoft.com/pricing/details/log-analytics).<br /><br />Wenn Sie kein Azure-Abonnement haben oder Azure Log Analytics derzeit nicht verwenden, finden Sie auf der Preisseite einen Link für eine kostenlose Testversion.|
|Azure Information Protection-Client (aktuelle allgemein verfügbare Version oder Vorschauversion) oder Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen|Wenn Sie noch keine dieser Versionen des Clients nicht installiert haben, können Sie sie über das Microsoft Download Center herunterladen und installieren:<br /> - [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) <br /> - [Azure Information Protection-Client für einheitliche Bezeichnungen](https://www.microsoft.com/en-us/download/details.aspx?id=57440)|
|Für den Bericht **Ermittlung und Risiko**: <br /><br />– Sie müssen mindestens eine Azure Information Protection-Scannerinstanz (aktuelle allgemein verfügbare Version oder Vorschauversion) bereitstellen, um Daten aus lokalen Datenspeichern anzuzeigen <br /><br />– Um Daten von Windows 10-Computern anzuzeigen, müssen diese mindestens Build 1809 haben, Sie müssen Windows Defender Advanced Threat Protection (Windows Defender ATP) verwenden, und es muss das Integrationsfeature Azure Information Protection im Windows Defender Security Center aktiviert sein.|Eine Installationsanleitung für die Überprüfung finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md). <br /><br />Informationen zur Konfiguration und Verwendung des Integrationsfeatures von Azure Information Protection aus dem Windows Defender Security Center finden Sie unter [Informationsschutz in der Windows-Übersicht](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview).|
|Für den Bericht **Empfehlungen**: <br /><br />– Sie müssen die aktuelle Vorschauversion des Azure Information Protection-Scanners verwenden, um ein neues Datenrepository aus dem Azure-Portal als empfohlene Aktion hinzuzufügen |Informationen zur Bereitstellung der Vorschauversion des Scanners finden Sie unter [Bereitstellen der Vorschauversion des Azure Information Protection-Scanners zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner-preview.md).|

### <a name="permissions-required-for-azure-information-protection-analytics"></a>Erforderliche Berechtigungen für Azure Information Protection-Analysen

Speziell für Azure Information Protection-Analysen können Sie nach der Konfiguration des Azure Log Analytics-Arbeitsbereichs die Azure AD-Administratorrolle „Sicherheitsleseberechtigter“ als Alternative zu den anderen Azure AD-Rollen verwenden, die die Verwaltung von Azure Information Protection im Azure-Portal unterstützen.

Da dieses Feature die Azure Monitor-Plattform verwendet, steuert die rollenbasierte Zugriffssteuerung (Role-Based Access Control, RBAC) für Azure auch den Zugriff auf Ihren Arbeitsbereich. Daher benötigen Sie zum Verwalten von Azure Information Protection-Analysen sowohl eine Azure-Rolle als auch eine Azure AD-Administratorrolle. Wenn Sie noch keine Erfahrung mit Azure-Rollen haben, sollten Sie [Unterschiede zwischen Azure RBAC-Rollen und Azure AD-Administratorrollen](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles) lesen.

Details:

1. Um auf das Azure Information Protection-Analyseblatt im Azure-Portal zuzugreifen, müssen Sie eine der folgenden [Azure AD-Administratorrollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) besitzen:
    
    - Um Ihren Log Analytics-Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
        - **Information Protection-Administrator**
        - **Sicherheitsadministrator**
        - **Globaler Administrator**
    
    - Um die Daten nach dem Erstellen des Log Analytics-Arbeitsbereichs anzuzeigen, benötigen Sie eine der folgenden Rollen:
    
        - **Sicherheitsleseberechtigter**
        - **Information Protection-Administrator**
        - **Sicherheitsadministrator**
        - **Globaler Administrator**
    
    > [!NOTE] 
    > Wenn Ihr Mandant zum einheitlichen Bezeichnungsspeicher migriert wurde, muss Ihr Konto ein globaler Administrator oder eine der aufgelisteten Rollen zuzüglich Zugriffsberechtigungen für das Office 365 Security & Compliance Center sein. [Weitere Informationen](configure-policy-migrate-labels.md#important-information-about-administrative-roles)

2. Um auf Ihren Azure Log Analytics-Arbeitsbereich zuzugreifen, benötigen Sie eine der folgenden [Azure Log Analytics-Rollen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-to-log-analytics-workspace-using-azure-permissions) oder standardmäßigen [Azure-Rollen](https://docs.microsoft.com/azure/role-based-access-control/overview#role-assignments):
    
    - Um einen Log Analytics-Arbeitsbereich oder benutzerdefinierte Abfragen zu erstellen, benötigen Sie eine der folgenden Rollen:
    
        - **Log Analytics-Mitwirkender**
        - Azure-Rolle: **Besitzer** oder **Mitwirkender**
    
    - Um die Daten in einem Log Analytics-Arbeitsbereich anzuzeigen, nachdem dieser erstellt wurde, benötigen Sie eine der folgenden Rollen:
    
        - **Log Analytics-Leser**
        - Azure-Rolle: **Leser**

#### <a name="minimum-roles-to-view-the-reports"></a>Mindestens erforderliche Rolle zum Anzeigen von Berichten

Nachdem Sie Ihren Arbeitsbereich für Azure Information Protection-Analysen erstellt haben, benötigen Sie mindestens die beiden folgenden Rollen zum Anzeigen der Berichte:

- Azure AD-Administratorrolle: **Sicherheitsleseberechtigter**
- Azure-Rolle: **Log Analytics-Leser**

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Konfigurieren eines Log Analytics-Arbeitsbereichs für Berichte

1. Wenn dies noch nicht erfolgt ist, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal](https://portal.azure.com) mit einem Konto an, das über die [erforderlichen Berechtigungen für die Azure Information Protection-Analyse](#permissions-required-for-azure-information-protection-analytics) verfügt. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
2. Navigieren Sie zu den Menüoptionen **Verwalten**, und wählen Sie **Analyse konfigurieren (Vorschau)** aus.

3. Auf dem Blatt **Azure Information Protection-Protokollanalyse** sehen Sie eine Liste aller Log Analytics-Arbeitsbereiche, die Ihrem Mandanten gehören. Führen Sie eines der folgenden Verfahren aus:
    
    - Erstellen eines neuen Log Analytics-Arbeitsbereichs: Wählen Sie **Neuen Arbeitsbereich erstellen** aus, und geben Sie auf dem Blatt **Log Analytics-Arbeitsbereich** die erforderlichen Informationen ein.
    
    - Verwenden eines vorhandenen Log Analytics-Arbeitsbereichs: Wählen Sie den Arbeitsbereich aus der Liste aus.

Wenn Sie Hilfe beim Erstellen des Log Analytics-Arbeitsbereichs benötigen, lesen Sie sich den Artikel [Erstellen eines Log Analytics-Arbeitsbereichs im Azure-Portal](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace) durch.

Wenn der Arbeitsbereich konfiguriert wurde, können Sie die Berichte anzeigen.

## <a name="how-to-view-the-reports"></a>Anzeigen von Berichten

Suchen Sie auf dem Azure Information Protection-Blatt die Menüoptionen **Dashboards**, und wählen Sie eine der folgenden Optionen aus:

- **Nutzungsbericht (Vorschau)**: Dieser Bericht informiert Sie darüber, wie Ihre Bezeichnungen verwendet werden. 

- **Aktivitätsprotokolle (Vorschau)**: Mithilfe dieses Berichts finden Sie Bezeichnungsaktionen von Benutzern sowie auf Geräten und Dateipfaden.
    
    Dieser Bericht enthält eine Option **Spalten**, mit der Sie mehr Aktivitätsinformationen als in der Standardanzeige anzeigen können.

- **Datenermittlung (Vorschau)**: Dieser Bericht enthält beim Überprüfen oder von Windows Defender ATP gefundene Informationen zu Dateien.

- **Empfehlungen (Vorschau):** Verwenden Sie diesen Bericht, um Dateien zu identifizieren, die vertrauliche Informationen enthalten, und minimieren Sie das Risiko mithilfe der Empfehlungen.
    
    Dieser Bericht wird derzeit für Mandanten eingeführt – wenn er nicht angezeigt wird, versuchen Sie es in wenigen Tagen erneut.
    
    Wenn Sie ein Element auswählen, zeigt die Option **Daten anzeigen** die Überwachungsaktivitäten an, die die Empfehlung ausgelöst haben.

> [!NOTE]
> Es gibt derzeit ein bekanntes Problem beim Anzeigen von Fragezeichen (**?**) in Pfaden und Dateinamen anstelle von Zeichen, bei denen es sich nicht um ASCII-Zeichen handelt, wenn das Gebietsschema des Ausgangsbetriebssystems Englisch ist.

## <a name="how-to-modify-the-reports"></a>Ändern von Berichten

Wählen Sie im Dashboard das Abfragesymbol aus, um das Blatt **Protokollsuche** zu öffnen: 

![Log Analytics-Symbol zum Anpassen von Azure Information Protection-Berichten](./media/log-analytics-icon.png)


Die protokollierten Daten für Azure Information Protection werden in der folgenden Tabelle gespeichert: **InformationProtectionLogs_CL**

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Informationen in den Berichten überprüft haben, haben Sie die Möglichkeit, Änderungen an Ihrer Azure Information Protection-Richtlinie vorzunehmen. Eine Anleitung dazu finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).
