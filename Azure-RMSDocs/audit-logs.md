---
title: Von Azure Information Protection-AIP generierte Überwachungs Protokolle
description: Erfahren Sie mehr über die von Azure Information Protection-AIP generierten Überwachungs Protokolle.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/01/2021
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: fc51c360e4cded259b87eee7bedcaf0829e0b717
ms.sourcegitcommit: 7420cf0200c90687996124424a254c289b11a26f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844267"
---
# <a name="azure-information-protection-audit-log-reference-public-preview"></a>Azure Information Protection Überwachungs Protokoll Referenz (öffentliche Vorschau)

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Das Azure Information Protection Audit Log-Feature befindet sich derzeit in der Vorschau Phase. Die [ergänzenden Bestimmungen für Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) enthalten zusätzliche rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden bzw. anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind.

Microsoft Azure Information Protection generiert Überwachungs Protokolle bei den folgenden Aktivitäts Ereignissen:

* [zugreifen](#access-audit-logs)
* [Zugriff verweigert](#access-denied-audit-logs)
* [Schutz ändern](#change-protection-audit-logs)
* [Entdecken](#discover-audit-logs)
* [Bezeichnung für Herabstufung](#downgrade-label-audit-logs)
* [Datei entfernt](#file-removed-audit-logs)
* [Neue Bezeichnung](#new-label-audit-logs)
* [Neuer Schutz](#new-protection-audit-logs)
* [Bezeichnung entfernen](#remove-label-audit-logs)
* [Schutz entfernen](#remove-protection-audit-logs)
* [Bezeichnung "Upgrade"](#upgrade-label-audit-logs)

## <a name="access-audit-logs"></a>Zugreifen auf Überwachungsprotokolle

**Access** Audit-Protokolle werden für die folgenden Aktivitäten generiert:

|Gemeldet von  |Plattform  |Application  |Aktion/Beschreibung  |
|---------|---------|---------|---------|
|Azure Information Protection: nur klassischer Client | Windows        | Office        |Wird zum ersten Mal in jeder Sitzung generiert, dass eine bezeichnete oder geschützte Datei gespeichert wird.<br>Das Protokoll enthält alle Übereinstimmungen von Informationstypen.      |
|Azure Information Protection: nur klassischer Client     |Windows         |Office         |Wird jedes Mal generiert, wenn eine Bezeichnung oder eine geschützte Datei erstellt wird.       |
|Azure Information Protection:<br />-Klassischer Client<br />-Unified-Bezeichnungs Client     | Windows, SharePoint, onedrive        | Office        | Wird jedes Mal generiert, wenn eine bezeichnete oder geschützte Datei geöffnet wird. <br /><br />**Hinweis**: für geschützte Dateien werden Zugriffs Überwachungs Protokolle nur generiert, wenn die Datei geöffnet wird und der Inhalt erfolgreich entschlüsselt und für den Benutzer verfügbar gemacht wird. <br />Bei geschützten e-Mails in Outlook werden Zugriffs Überwachungs Protokolle auch dann generiert, wenn der Benutzer versucht, eine verschlüsselte e-Mail zu öffnen, selbst wenn die Entschlüsselung aufgrund fehlender Berechtigungen blockiert wird.         |
|Microsoft Information Protection (MIP) SDK     | Any        | Drittanbieteranwendungen        | Wird jedes Mal generiert, wenn von einer Drittanbieter Anwendung, die Sie unterstützt, auf eine bezeichnete oder geschützte Datei zugegriffen wird.       |
|RMS-Dienst     | Windows        | Office         |Wird jedes Mal generiert, wenn auf ein beschrifteten oder geschütztes Dokument zugegriffen wird.       |
| | | | |


## <a name="access-denied-audit-logs"></a>Zugriffs Verweigerungs Überwachungs Protokolle

Für die folgenden Aktivitäten werden **Zugriffs Verweigerungs** Überwachungs Protokolle generiert:

|Gemeldet von  |Plattform  |Application  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|RMS-Dienst     | Windows        | Office         |Wird jedes Mal generiert, wenn ein Benutzer versucht, auf ein geschütztes Dokument zuzugreifen, für das Sie keine Berechtigungen haben.
| | | | |

## <a name="change-protection-audit-logs"></a>Überwachungs Protokolle für den Schutz ändern

Überwachungs Protokolle für den **Änderungs Schutz** werden für die folgenden Aktivitäten generiert:

|Gemeldet von  |Plattform  |Application  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|Azure Information Protection:<br />-Klassischer Client<br />-Unified-Bezeichnungs Client     | Windows, SharePoint, onedrive        | Office        | Wird jedes Mal generiert, wenn der Schutz für ein Dokument ohne Bezeichnung manuell geändert wird.         |
|Microsoft Information Protection (MIP) SDK     | Any        | Drittanbieteranwendungen        | Wird jedes Mal generiert, wenn der Schutz für ein Dokument ohne Bezeichnung manuell geändert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt.       |
| | | | |

## <a name="discover-audit-logs"></a>Überwachungs Protokolle ermitteln

Überwachungs Protokolle **ermitteln** werden für die folgenden Aktivitäten generiert:

|Gemeldet von  |Plattform  |Application  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|Azure Information Protection: <br />-Klassischer Scanner <br />-Unified-Beschriftungs Scanner | Windows        | Office        |Wird jedes Mal generiert, wenn eine Datei durch den AIP-Scanner gescannt wird.<br>Das Protokoll enthält die folgenden Details:<br>-Übereinstimmende Informationstypen<br>-Bezeichnungen |
|Microsoft Information Protection (MIP) SDK | Any | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Datei von einer Drittanbieter Anwendung gescannt wird, von der Sie unterstützt wird. <br />Das Protokoll enthält die folgenden Details:<br />-Übereinstimmende Informationstypen<br />-Bezeichnungen|
|Azure Information Protection Unified Bezeichnung-Viewer |Windows |Einheitlicher AIP-Beschriftungs Viewer  | Wird jedes Mal generiert, wenn eine bezeichnete oder geschützte Datei geöffnet wird.|
| | | | |

## <a name="downgrade-label-audit-logs"></a>Überwachungs Protokolle für das Downgrade der Bezeichnung

Überwachungs Protokolle für die **Herabstufung der Bezeichnung** werden für die folgenden Aktivitäten generiert:

| Gemeldet von      | Plattform                       | Application              | Aktion/Beschreibung      |
| ---------------- | ------------------------------ | ------------------------ | --------------- |
|Azure Information Protection:<br />-Klassischer Scanner und Client<br />-Unified Beschriftung Scanner und Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird.|
| Microsoft Defender ATP            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird. |
| Microsoft Information Protection (MIP) SDK          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
| | | | |

## <a name="file-removed-audit-logs"></a>Datei entfernte Überwachungs Protokolle

> [!NOTE]
> Datei entfernte Überwachungs Protokolle werden nur in Azure Information Protection Scanner-Version [2.7.96.0](rms-client/unifiedlabelingclient-version-release-history.md#version-27960) und höher unterstützt.

**Dateien** , die entfernt wurden, werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                              | Plattform | Application                     | Aktion/Beschreibung                                                          |
| ---------------------------------------------------------------------------------------- | -------- | ------------------------------- | ------------------------------------------------------------------------------ |
| Azure Information Protection Scanner, einheitlicher Bezeichnungs Client | Windows  | Office-und unterstützte Dateitypen | Wird jedes Mal generiert, wenn der AIP-Scanner erkennt, dass eine zuvor gescannte Datei entfernt wurde. |
| | | | |

## <a name="new-label-audit-logs"></a>Neue Beschriftungs Überwachungs Protokolle

**Neue Beschriftungs** Überwachungs Protokolle werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:<br />-Klassischer Scanner und Client<br />-Unified Beschriftung Scanner und Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine neue Bezeichnung angewendet wird.                                                                  |
| Microsoft Defender ATP                                                                            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine neue Dokument Bezeichnung angewendet wird.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine neue Dokument Bezeichnung angewendet wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
| | | | |

## <a name="new-protection-audit-logs"></a>Neue Schutz Überwachungs Protokolle

Für die folgenden Aktivitäten werden **neue Schutz** Überwachungs Protokolle generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:<br />-Klassischer Client<br />-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn der Schutz manuell neu hinzugefügt wird, ohne eine Bezeichnung.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn der Schutz manuell neu hinzugefügt wird, ohne eine Bezeichnung.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
| | | | |

## <a name="remove-label-audit-logs"></a>Überwachungs Protokolle für die Bezeichnung entfernen

Überwachungs Protokolle für die **Bezeichnung entfernen** werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:<br />-Klassischer Scanner und Client<br />-Unified Beschriftung Scanner und Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.                                                                  |
| Microsoft Defender ATP                                                                            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
| | | | |

## <a name="remove-protection-audit-logs"></a>Schutz Überwachungs Protokolle entfernen

Zum **Entfernen von Schutz** Überwachungsprotokollen werden die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:<br />-Klassischer Client<br />-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn der Schutz manuell entfernt wird, ohne eine Bezeichnung zu erhalten.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn der Schutz manuell entfernt wird, ohne eine Bezeichnung zu erhalten.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
| | | | |

## <a name="upgrade-label-audit-logs"></a>Überwachungs Protokolle für Bezeichnung aktualisieren

Überwachungs Protokolle für die **upgradebezeichnung** werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:<br />-Klassischer Scanner und Client<br />-Unified Beschriftung Scanner und Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.                                                                   |
| Microsoft Defender ATP                                                                            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.                                                                   |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
| | | | |

## <a name="next-steps"></a>Nächste Schritte

AIP-Überwachungs Protokolle werden auch an den Microsoft 365-Aktivitäts-Explorer gesendet, wo Sie mit unterschiedlichen Namen angezeigt werden können.

Weitere Informationen finden Sie unter

- [Public Preview: AIP-Überwachungs Protokolle im Aktivitäts-Explorer](https://www.yammer.com/askipteam/#/Threads/show?threadId=1085834054254592)
- [Einstieg in den Aktivitäts-Explorer](/microsoft-365/compliance/data-classification-activity-explorer)
- [Zentrale Berichterstellung für Azure Information Protection (öffentliche Vorschau)](reports-aip.md)
