---
title: Azure Information Protection von Client Versionsverlauf & Unterstützungs Richtlinie
description: Erfahren Sie, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde, und erhalten Sie Informationen zum Support der Lifecycle-Richtlinie.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 02/12/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v1client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: abb96a7d86bddea671230fbd033d9c940cf982a3
ms.sourcegitcommit: 6db47d691974b5450b80c58a49b2913ec1a99802
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2020
ms.locfileid: "77155924"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Der Azure Information Protection-Client: Verlauf der Releases und Supportrichtlinie


>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*



Sie können das neueste allgemein verfügbare Release und die aktuelle Vorschauversion (sofern verfügbar) im [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. 

Nach einer kurzen Verzögerung von in der Regel einige Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog mit dem Produktnamen **Microsoft Azure Information Protection** > **Microsoft Azure Information Protection Client**und der Klassifizierung der **Updates**enthalten. Diese Aufnahme in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Softwarebereitstellungsmechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [Upgraden und Verwalten des Azure Information Protection-Clients](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

> [!TIP]
> Sie sind daran interessiert, den Azure Information Protection Unified Label-Client zu verwenden, da ihre Bezeichnungen aus Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center veröffentlicht werden? Wenn Sie den Unified-Bezeichnungs Client aus dem Microsoft Download Center herunterladen und anschließend installieren, können Sie das Upgrade Ihres Azure Information Protection-Clients auf den Unified-Bezeichnungs [Client](unifiedlabelingclient-version-release-history.md)durchführen.

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version des Azure Information Protection-Clients mit allgemeiner Verfügbarkeit wird bis zu sechs Monate nach dem Release der nächsten Version mit allgemeiner Verfügbarkeit unterstützt. Mit Ausnahme dieses Abschnitts enthält die Dokumentation keine Informationen zu nicht unterstützten Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

##### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden:

|Clientversion|Datum der Veröffentlichung|
|--------------|-------------|
|1.48.204.0|04/16/2019|
|1.41.51.0|27.11.2018|
|1.37.19.0|17.9.2018|
|1.29.5.0|26.6.2018|
|1.27.48.0|30.5.2018|
|1.26.6.0|04/17/2018|
|1.10.56.0|09/18/2017|
|1.7.210.0|06/06/2017|
|1.4.21.0|03/15/2017|
|1.3.155.2|02/08/2017|
|1.2.4.0.0|10/27/2016|
|1.1.23.0|10/01/2016|

Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

Ab 6/2/2019 ist für den Bezeichnungs Dienst für Azure Information Protection Verbindungen erforderlich, die TLS 1,2 verwenden.

Alle Client Versionen von 1.4.21.0 veröffentlicht 03/15/2017 unterstützen TLS 1,2. Client Versionen **1.3.155.2**, **1.2.4.0**und **1.1.23.0** verwenden nicht TLS 1,2 und können daher die Azure Information Protection Richtlinie nicht mehr herunterladen.

### <a name="release-history"></a>Releaseverlauf

Im Folgenden wird erläutert, was in einem Release des Azure Information Protection-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt.

> [!NOTE]
> Kleinere Korrekturen werden nicht aufgelistet. Wenn also ein Problem mit dem Azure Information Protection-Client auftreten sollte, wird empfohlen, dass Sie zuerst überprüfen, ob dieses Problem mit dem neusten allgemein verfügbaren Release behoben wird. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

## <a name="version-154590"></a>Version 1.54.59.0

**Veröffentlicht**: 12/02/2020

Diese Version enthält nur Korrekturen. 

**Korrekturen**:

- Das Problem ist behoben, wenn die durch iqp geschützten Dateien **Wiederherstellen** und/oder **Speichern** unter-Optionen nach dem Entfernen des Schutzes angezeigt werden. 

- Viele QuickInfo-Texte zu Produkt Features wurden aus Gründen der Übersichtlichkeit verbessert. 

- Probleme im Zusammenhang mit der Client Stabilität beim Arbeiten mit geschützten PDF-Dateien werden gelöst. 

- Schutz Bezeichnungen werden nun erwartungsgemäß entfernt, wenn die Bezeichnung während des e-Mail-Erstellungs Prozesses auf der e-Mail gelöscht wird. 

## <a name="version-154330"></a>Version 1.54.33.0

**Veröffentlicht**: 10/23/2019

Unterstützt durch 08/12/2020

Diese Version umfasst die msipc-Version 1.0.4008.0813 des RMS-Clients.

Diese Version enthält allgemeine Korrekturen für Stabilität und Leistung.

## <a name="version-153100"></a>Version 1.53.10.0

**Veröffentlicht**: 07/15/2019

Unterstützt durch 04/23/2020

Diese Version umfasst die msipc-Version 1.0.3889.0419 des RMS-Clients.

**Neue Funktionen:**

- Neue erweiterte Client Einstellung zum Ausschließen von Outlook-Nachrichten aus der Richtlinien Einstellung **alle Dokumente und e-Mails müssen eine Bezeichnung aufweisen**. [Weitere Informationen](client-admin-guide-customizations.md#exempt-outlook-messages-from-mandatory-labeling)

- Neue erweiterte Client Einstellung zur weiteren Anpassung der Einstellungen, mit denen Popup Meldungen in Outlook implementiert werden, die gesendete e-Mails warnen, rechtfertigen oder blockieren. Mit dieser neuen erweiterten Einstellung können Sie eine andere Aktion für e-Mail-Nachrichten ohne Anlagen festlegen. [Weitere Informationen](client-admin-guide-customizations.md#to-specify-a-different-action-for-email-messages-without-attachments)

**Korrekturen**:

- Wenn Sie den Datei-Explorer verwenden, klicken Sie mit der rechten Maustaste auf die Bezeichnung einer Datei, für die der Schutz unabhängig von einer Bezeichnung angewendet wurde. dieser Schutz wird beibehalten. Ein Benutzer hat z. b. benutzerdefinierte Berechtigungen auf eine Datei angewendet.

- Wenn Sie die Option "nicht weiterleiten" in einem e-Mail-Thread durch eine Bezeichnung ersetzen, die für benutzerdefinierte Berechtigungen konfiguriert ist und nicht weiterleiten, können die ursprünglichen Empfänger die e-Mail-Nachricht weiterhin öffnen.

- Im folgenden Szenario wird ein Benutzer in der QuickInfo-QuickInfo nicht mehr angezeigt, dass die Bezeichnung automatisch von Ihnen festgelegt wurde: ein Benutzer erhält eine geschützte e-Mail mit einem angefügten Dokument, das nicht gekennzeichnet ist, aber automatisch geschützt wird. Wenn der Benutzer aus derselben Organisation wie der Absender das Dokument öffnet, wird die entsprechende Bezeichnung für die Schutzeinstellungen auf das Dokument angewendet.

- Das minimale [Nutzungsrecht](../configure-usage-rights.md#usage-rights-and-descriptions) zum Ausführen des Cmdlets " [Unprotect-rmsfile](/powershell/module/azureinformationprotection/unprotect-rmsfile) " lautet jetzt " **Speichern unter", "Exportieren** (exportieren)" und nicht " **Kopieren** " (extrahieren).

## <a name="next-steps"></a>Nächste Schritte

Nicht sicher, ob dies der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen des zu verwendenden Kunden für Windows-Computer](use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

Weitere Informationen zum Installieren und Verwenden des Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)
