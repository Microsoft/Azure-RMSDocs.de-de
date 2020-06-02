---
title: Von Azure Information Protection-AIP generierte Überwachungs Protokolle
description: Erfahren Sie mehr über die von Azure Information Protection-AIP generierten Überwachungs Protokolle.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 06/01/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: b851372494a3215a1db3f118809ec2bdf438affd
ms.sourcegitcommit: fa16364879823b86b4e56ac18a1fc8de5a5dae57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2020
ms.locfileid: "84250433"
---
# <a name="azure-information-protection-audit-log-reference-public-preview"></a>Azure Information Protection Überwachungs Protokoll Referenz (öffentliche Vorschau)

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Microsoft Azure Information Protection generiert Überwachungs Protokolle bei den folgenden Aktivitäts Ereignissen:
* [zugreifen](#access-audit-logs)
* [Zugriff verweigert](#access-denied-audit-logs)
* [Schutz ändern](#change-protection-audit-logs)
* [Suchen](#discover-audit-logs)
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
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     | Windows        | Office        |Wird zum ersten Mal in jeder Sitzung generiert, dass eine bezeichnete oder geschützte Datei gespeichert wird.<br>Protokolldateien enthalten alle Übereinstimmungen von Informationstypen.  <!-- plan to be removed -->    |
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     |Windows         |Office         |Wird jedes Mal generiert, wenn eine Bezeichnung oder eine geschützte Datei erstellt wird.<!-- plan to be removed -->       |
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     | Windows, SharePoint, onedrive        | Office        | Wird jedes Mal generiert, wenn eine bezeichnete oder geschützte Datei geöffnet wird.         |
|Microsoft Information Protection (MIP) SDK     | Any        | Drittanbieteranwendungen        | Wird jedes Mal generiert, wenn von einer Drittanbieter Anwendung, die Sie unterstützt, auf eine bezeichnete oder geschützte Datei zugegriffen wird.       |
|RMS-Dienst     | Windows        | Office         |Wird jedes Mal generiert, wenn auf ein beschrifteten oder geschütztes Dokument zugegriffen wird.<!-- plan to be removed -->       |

## <a name="access-denied-audit-logs"></a>Zugriffs Verweigerungs Überwachungs Protokolle
Für die folgenden Aktivitäten werden **Zugriffs Verweigerungs** Überwachungs Protokolle generiert:

|Gemeldet von  |Plattform  |Application  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|RMS-Dienst     | Windows        | Office         |Wird jedes Mal generiert, wenn der Benutzer versucht, ein geschütztes Dokument zu erhalten, für das Sie keinen Zugriff haben.|

## <a name="change-protection-audit-logs"></a>Überwachungs Protokolle für den Schutz ändern
Überwachungs Protokolle für den **Änderungs Schutz** werden für die folgenden Aktivitäten generiert:

|Gemeldet von  |Plattform  |Application  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     | Windows, SharePoint, onedrive        | Office        | Wird jedes Mal generiert, wenn der Schutz manuell geändert wird, ohne eine Bezeichnung zu erhalten.  |
|Microsoft Information Protection (MIP) SDK     | Any        | Drittanbieteranwendungen        | Wird jedes Mal generiert, wenn der Schutz manuell geändert wird, ohne eine Bezeichnung zu erhalten.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="discover-audit-logs"></a>Überwachungs Protokolle ermitteln
Überwachungs Protokolle **ermitteln** werden für die folgenden Aktivitäten generiert:

|Gemeldet von  |Plattform  |Application  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|Azure Information Protection:</br>-Klassischer Scanner </br>-Unified-Beschriftungs Scanner     | Windows        | Office        |Wird jedes Mal generiert, wenn eine Datei durch den AIP-Scanner gescannt wird.<br>Protokolldateien enthalten die folgenden Details:<br>-Übereinstimmende Informationstypen<br>-Bezeichnungen |
|Microsoft Information Protection (MIP) SDK | Any | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Datei von einer Drittanbieter Anwendung gescannt wird, von der Sie unterstützt wird. </br>Protokolldateien enthalten die folgenden Details:</br>-Übereinstimmende Informationstypen</br>-Bezeichnungen|

## <a name="downgrade-label-audit-logs"></a>Überwachungs Protokolle für das Downgrade der Bezeichnung
Überwachungs Protokolle für die **Herabstufung der Bezeichnung** werden für die folgenden Aktivitäten generiert:

| Gemeldet von      | Plattform                       | Application              | Aktion/Beschreibung      |
| ---------------- | ------------------------------ | ------------------------ | --------------- |
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird.|
| Microsoft Defender ATP            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird. |
| Microsoft Information Protection (MIP) SDK          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="file-removed-audit-logs"></a>Datei entfernte Überwachungs Protokolle

> [!NOTE]
> Datei entfernte Überwachungs Protokolle werden nur in Azure Information Protection Scanner-Version [2.7.95.0](rms-client/unifiedlabelingclient-version-release-history.md#version-27950-public-preview) und höher unterstützt.

**Dateien** , die entfernt wurden, werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                              | Plattform | Application                     | Aktion/Beschreibung                                                          |
| ---------------------------------------------------------------------------------------- | -------- | ------------------------------- | ------------------------------------------------------------------------------ |
| Azure Information Protection Scanner, einheitlicher Bezeichnungs Client | Windows  | Office-und unterstützte Dateitypen | Wird jedes Mal generiert, wenn der Scanner erkennt, dass eine zuvor überprüfte Datei entfernt wurde. |


## <a name="new-label-audit-logs"></a>Neue Beschriftungs Überwachungs Protokolle
**Neue Beschriftungs** Überwachungs Protokolle werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine neue Bezeichnung angewendet wird.                                                                  |
| Microsoft Defender ATP                                                                            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine neue Dokument Bezeichnung angewendet wird.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine neue Dokument Bezeichnung angewendet wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="new-protection-audit-logs"></a>Neue Schutz Überwachungs Protokolle
Für die folgenden Aktivitäten werden **neue Schutz** Überwachungs Protokolle generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn der Schutz manuell neu hinzugefügt wird, ohne eine Bezeichnung.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn der Schutz manuell neu hinzugefügt wird, ohne eine Bezeichnung.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="remove-label-audit-logs"></a>Überwachungs Protokolle für die Bezeichnung entfernen
Überwachungs Protokolle für die **Bezeichnung entfernen** werden für die folgenden Aktivitäten generiert:


| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.                                                                  |
| Microsoft Defender ATP                                                                            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="remove-protection-audit-logs"></a>Schutz Überwachungs Protokolle entfernen
Zum **Entfernen von Schutz** Überwachungsprotokollen werden die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn der Schutz manuell entfernt wird, ohne eine Bezeichnung zu erhalten.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn der Schutz manuell entfernt wird, ohne eine Bezeichnung zu erhalten.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="upgrade-label-audit-logs"></a>Überwachungs Protokolle für Bezeichnung aktualisieren
Überwachungs Protokolle für die **upgradebezeichnung** werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Application              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.                                                                   |
| Microsoft Defender ATP                                                                            | Windows                        | Betriebssystem                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.                                                                   |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |
