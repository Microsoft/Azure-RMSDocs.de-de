---
title: Von Azure Information Protection-AIP generierte Überwachungs Protokolle
description: Erfahren Sie mehr über die von Azure Information Protection-AIP generierten Überwachungs Protokolle.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/09/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e48c3a32527ea214d952725a4935c566a60d208f
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97383940"
---
# <a name="azure-information-protection-audit-log-reference-public-preview"></a>Azure Information Protection Überwachungs Protokoll Referenz (öffentliche Vorschau)

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Das Azure Information Protection Audit Log-Feature befindet sich derzeit in der Vorschau Phase. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

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

> [!NOTE]
> Der [AIP-Viewer](rms-client/clientv2-view-use-files.md) sendet keine Überwachungs Protokolle. 
>
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
| | | | |

## <a name="downgrade-label-audit-logs"></a>Überwachungs Protokolle für das Downgrade der Bezeichnung

Überwachungs Protokolle für die **Herabstufung der Bezeichnung** werden für die folgenden Aktivitäten generiert:

| Gemeldet von      | Plattform                       | Application              | Aktion/Beschreibung      |
| ---------------- | ------------------------------ | ------------------------ | --------------- |
|Azure Information Protection:<br />-Klassischer Scanner und Client<br />-Unified Beschriftung Scanner und Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird.|
| Microsoft Defender ATP            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird. |
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
| Microsoft Defender ATP                                                                            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine neue Dokument Bezeichnung angewendet wird.                                                                  |
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
| Microsoft Defender ATP                                                                            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.                                                                  |
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
| Microsoft Defender ATP                                                                            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.                                                                   |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
| | | | |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Überwachungs Protokollierung finden Sie unter [Zentrale Berichterstellung für Azure Information Protection (öffentliche Vorschau)](reports-aip.md).
