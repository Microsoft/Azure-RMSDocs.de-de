---
title: Azure Information Protection klassischer Client Versionsverlauf & Unterstützungs Richtlinie
description: Sehen Sie sich an, was in einer Version des klassischen Azure Information Protection-Clients neu ist oder geändert wurde, und verstehen Sie die Lebenszyklus Richtlinie für Support.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/11/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ROBOTS: NOINDEX
ms.subservice: v1client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 9e03169c4c30bbad4ff9ed9ccaf06b6992994785
ms.sourcegitcommit: 99f1a1ab40eea7802e6c4f98724958409ee779ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2021
ms.locfileid: "103558109"
---
# <a name="azure-information-protection-classic-client-version-release-history-and-support-policy"></a>Azure Information Protection klassischer Client: Versions Veröffentlichungs Verlauf und Unterstützungs Richtlinie


>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified-Bezeichnungs Client finden Sie unter [Unified Bezeichnung Client Version History](unifiedlabelingclient-version-release-history.md). *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

**Zum Bereitstellen des klassischen AIP-Clients** öffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.

Weitere Informationen finden Sie unter [Upgraden und Verwalten des Azure Information Protection-Clients](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version des Azure Information Protection-Clients mit allgemeiner Verfügbarkeit wird bis zu sechs Monate nach dem Release der nächsten Version mit allgemeiner Verfügbarkeit unterstützt. Mit Ausnahme dieses Abschnitts enthält die Dokumentation keine Informationen zu nicht unterstützten Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

##### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden:

|Clientversion|Datum der Veröffentlichung|
|--------------|-------------|
|1.54.33.0 | 23.10.2019|
|1.53.10|07/15/2019|
|1.48.204.0|04/16/2019|
|1.41.51.0|27.11.2018|
|1.37.19.0|17.9.2018|
|1.29.5.0|26.6.2018|
|1.27.48.0|30.5.2018|
|1.26.6.0|04/17/2018|
|1.10.56.0|09/18/2017|
|1.7.210.0|06/06/2017|
|1.4.21.0|15.03.2017|
|1.3.155.2|02/08/2017|
|1.2.4.0.0|27.10.2016|
|1.1.23.0|10/01/2016|

Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

Ab 6/2/2019 ist für den Bezeichnungs Dienst für Azure Information Protection Verbindungen erforderlich, die TLS 1,2 verwenden.

Alle Client Versionen von 1.4.21.0 veröffentlicht 03/15/2017 unterstützen TLS 1,2. Client Versionen **1.3.155.2**, **1.2.4.0** und **1.1.23.0** verwenden nicht TLS 1,2 und können daher die Azure Information Protection Richtlinie nicht mehr herunterladen.

### <a name="release-history"></a>Releaseverlauf

Verwenden Sie die folgenden Informationen, um zu erfahren, was für eine unterstützte Version des Azure Information Protection klassischen Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt.

Beachten Sie, Azure Information Protection Features derzeit in der Vorschau Phase sind. Die [ergänzenden Bestimmungen für Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) enthalten zusätzliche rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden bzw. anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

> [!NOTE]
>  Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.
>
## <a name="version-156250"></a>Version 1.56.25.0

**Veröffentlicht**: 11/05/2020

**Unterstützt durch**: 03/31/2021

Kleinere Fehlerbehebungen im Zusammenhang mit Outlook-Unterstützung

## <a name="version-154590"></a>Version 1.54.59.0

**Veröffentlicht**: 02/12/2020

**Unterstützt durch**: 03/31/2021

Diese Version enthält nur Korrekturen.

**Fixes**:

- Das Problem ist behoben, wenn die durch iqp geschützten Dateien **Wiederherstellen** und/oder **Speichern** unter-Optionen nach dem Entfernen des Schutzes angezeigt werden. 

- Viele QuickInfo-Texte zu Produkt Features wurden aus Gründen der Übersichtlichkeit verbessert. 

- Probleme im Zusammenhang mit der Client Stabilität beim Arbeiten mit geschützten PDF-Dateien werden gelöst. 

- Schutz Bezeichnungen werden nun erwartungsgemäß entfernt, wenn die Bezeichnung während des e-Mail-Erstellungs Prozesses auf der e-Mail gelöscht wird. 

## <a name="next-steps"></a>Nächste Schritte

Nicht sicher, ob dies der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen der Windows-Bezeichnung](use-client.md#choose-your-windows-labeling-solution).

Weitere Informationen zum Installieren und Verwenden des Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)
