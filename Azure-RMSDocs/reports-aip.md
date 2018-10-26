---
title: Zentrale Berichterstellung für Azure Information Protection
description: Erfahren Sie, wie Sie mithilfe der zentralen Berichterstellung die Übernahme Ihrer Azure Information Protection-Bezeichnungen nachverfolgen und Dateien mit vertraulichen Daten erkennen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/15/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: 424be5910d6a4498bc9d2684888cd2bf9af010af
ms.sourcegitcommit: 26e1ccdd0c4339a51ec7812082b399f13ef73b2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "49324885"
---
# <a name="central-reporting-for-azure-information-protection"></a>Zentrale Berichterstellung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Dieses Feature befindet sich in der Vorschau und unterliegt Änderungen. Alle in dieser Vorschauversion gesammelten Daten werden möglicherweise nicht unterstützt, sobald die Funktion allgemein verfügbar ist.


Mit Azure Information Protection-Analysen für die zentrale Berichterstellung können Sie die Übernahme Ihrer Azure Information Protection-Bezeichnungen nachverfolgen sowie den Benutzerzugriff auf Dokumente bzw. E-Mails mit Bezeichnungen und alle Änderungen an ihrer Klassifizierung überwachen. Außerdem haben Sie die Möglichkeit, Dokumente zu identifizieren, die sensible Daten enthalten, die geschützt werden müssen.

Die angezeigten Daten werden von Ihren Azure Information Protection-Clients, der Azure Information Protection-Überprüfung und [Clients, die einheitliche Bezeichnungen unterstützen](configure-policy-migrate-labels.md#clients-that-support-unified-labeling), aggregiert.

Sie können beispielsweise die folgenden Informationen abrufen:

- Im **Nutzungsbericht** (in dem Sie einen Zeitraum auswählen können):
    
    - Welche Bezeichnungen angewendet werden
    
    - Wie viele Dokumente und E-Mails Bezeichnungen aufweisen
    
    - Wie viele Dokumente und E-Mails geschützt werden
    
    - Wie viele Benutzer und Geräte Dokumente bzw. E-Mails mit Bezeichnungen versehen
    
    - Welche Anwendungen zum Bezeichnen verwendet werden

- Im Bericht **Datenermittlung**:

    - Welche Dateien sich in Ihren überprüften Datenrepositorys befinden
    
    - Welche Dateien Bezeichnungen aufweisen und geschützt werden sowie den Speicherort der Dateien nach Bezeichnung
    
    - Welche Dateien vertrauliche Daten für bekannte Kategorien enthalten, z.B. Finanzdaten und persönliche Informationen, und den Speicherort von Dateien nach diesen Kategorien
    
Die Berichte verwenden [Azure Log Analytics](/azure/log-analytics/log-analytics-overview), um die Daten in einem Arbeitsbereich zu speichern, der Ihnen gehört. Wenn Sie mit der Abfragesprache vertraut sind, können Sie die Abfragen ändern und neue Berichte und Power BI-Dashboards erstellen. Das folgende Tutorial dient als Einführung in die Abfragesprache: [Erste Schritte mit dem Log Analytics-Portal](https://docs.loganalytics.io/docs/Learn/Getting-Started/Getting-started-with-the-Analytics-portal). 

Weitere Informationen finden Sie im Blogbeitrag [Datenermittlung, Berichterstattung und Analysen für alle Daten mit Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854) (in englischer Sprache).

### <a name="information-collected-and-sent-to-microsoft"></a>Gesammelte und an Microsoft gesendete Informationen

Um diese Berichte zu erstellen, senden die Endpunkte die folgenden Informationen an Microsoft:

- Die Bezeichnungsaktion. Z.B. das Festlegen oder Ändern einer Bezeichnung, das Hinzufügen oder Entfernen von Schutz, automatische und empfohlene Bezeichnungen.

- Die Mandanten-ID Ihrer Organisation.

- Die Benutzer-ID (E-Mail-Adresse oder UPN).

- Den Dateipfad und -namen von Dokumenten, die Bezeichnungen aufweisen.

- Die Azure Information Protection-Clientversion.

- Die Client-Betriebssystemversion.

Diese Informationen werden in einem Azure Log Analytics-Arbeitsbereich gespeichert, der Ihnen gehört.

## <a name="prerequisites-for-azure-information-protection-analytics"></a>Voraussetzungen für Azure Information Protection-Analysen
Damit Sie Azure Information Protection-Berichte anzeigen und eigene Berichte erstellen können, müssen die folgenden Voraussetzungen erfüllt sein.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Azure-Abonnement, das Log Analytics umfasst|Eine Preisübersicht finden Sie auf der Seite [Azure Log Analytics – Preise](https://azure.microsoft.com/pricing/details/log-analytics).<br /><br />Wenn Sie kein Azure-Abonnement haben oder Azure Log Analytics derzeit nicht verwenden, finden Sie auf der Preisseite einen Link für eine kostenlose Testversion.|
|Die aktuelle Vorschauversion des Azure Information Protection-Clients|Wenn Sie die aktuelle Vorschauversion des Clients noch nicht installiert haben, können Sie sie über das [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen und installieren.|
|Für den Bericht **Ermittlung und Risiko**: <br /><br />– Mindestens eine Azure Information Protection-Überprüfungsinstanz (aktuelle Vorschauversion) wurde bereitgestellt|Eine Installationsanleitung finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md). <br /><br />Wenn Sie ein Upgrade von einer vorherigen Version ausführen, lesen Sie [Upgrade der Azure Information Protection-Überprüfung](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|


## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Konfigurieren eines Log Analytics-Arbeitsbereichs für Berichte

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
2. Navigieren Sie zu den Menüoptionen **Verwalten**, und wählen Sie **Analyse konfigurieren (Vorschau)** aus.

3. Auf dem Blatt **Azure Information Protection-Protokollanalyse** sehen Sie eine Liste aller Log Analytics-Arbeitsbereiche, die Ihrem Mandanten gehören. Führen Sie eines der folgenden Verfahren aus:
    
    - Erstellen eines neuen Log Analytics-Arbeitsbereichs: Wählen Sie **Neuen Arbeitsbereich erstellen** aus, und geben Sie auf dem Blatt **Log Analytics-Arbeitsbereich** die erforderlichen Informationen ein.
    
    - Verwenden eines vorhandenen Log Analytics-Arbeitsbereichs: Wählen Sie den gewünschten Arbeitsbereich aus der Liste aus.

Wenn Sie Hilfe beim Erstellen des Log Analytics-Arbeitsbereichs benötigen, lesen Sie [Erstellen eines Log Analytics-Arbeitsbereichs im Azure-Portal](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace).

Wenn der Arbeitsbereich konfiguriert wurde, können Sie die Berichte anzeigen.

## <a name="how-to-view-the-reports"></a>Anzeigen von Berichten

Suchen Sie auf dem Azure Information Protection-Blatt die Menüoptionen **Dashboards**, und wählen Sie eine der folgenden Optionen aus:

- **Nutzungsbericht (Vorschauversion)**: Dieser Bericht informiert Sie darüber, wie Ihre Bezeichnungen verwendet werden. 

- **Datenermittlung (Vorschauversion)**: Dieser Bericht enthält beim Überprüfen gefundene Informationen zu Dateien.

## <a name="how-to-modify-the-reports"></a>Ändern von Berichten

Wählen Sie im Dashboard das Abfragesymbol aus, um das Blatt **Protokollsuche** zu öffnen: 

![Log Analytics-Symbol zum Anpassen von Azure Information Protection-Berichten](./media/log-analytics-icon.png)


Die protokollierten Daten für Azure Information Protection werden in folgender Tabelle gespeichert: **InformationProtectionLogs_CL**

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Informationen in den Berichten überprüft haben, haben Sie die Möglichkeit, Änderungen an Ihrer Azure Information Protection-Richtlinie vorzunehmen. Eine Anleitung dazu finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).