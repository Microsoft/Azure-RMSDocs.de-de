---
title: Von Azure Information Protection-AIP generierte Überwachungs Protokolle
description: Erfahren Sie mehr über die von Azure Information Protection-AIP generierten Überwachungs Protokolle.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 06/08/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 682b7e7c51c270257046e3817399d3eeedb23c93
ms.sourcegitcommit: f32928f7dcc03111fc72d958cda9933d15065a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2020
ms.locfileid: "84666063"
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

|Gemeldet von  |Plattform  |Anwendung  |Aktion/Beschreibung  |
|---------|---------|---------|---------|
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     | Windows        | Office        |Wird zum ersten Mal in jeder Sitzung generiert, dass eine bezeichnete oder geschützte Datei gespeichert wird.<br>Das Protokoll enthält alle Übereinstimmungen von Informationstypen.  <!-- plan to be removed -->    |
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     |Windows         |Office         |Wird jedes Mal generiert, wenn eine Bezeichnung oder eine geschützte Datei erstellt wird.<!-- plan to be removed -->       |
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     | Windows, SharePoint, onedrive        | Office        | Wird jedes Mal generiert, wenn eine bezeichnete oder geschützte Datei geöffnet wird. </br></br>**Hinweis:** Bei geschützten Dateien werden Zugriffs Überwachungs Protokolle nur generiert, wenn die Datei geöffnet wird und der Inhalt erfolgreich entschlüsselt und für den Benutzer verfügbar gemacht wird. </br>Bei geschützten e-Mails in Outlook werden Zugriffs Überwachungs Protokolle auch dann generiert, wenn der Benutzer versucht, eine verschlüsselte e-Mail zu öffnen, selbst wenn die Entschlüsselung aufgrund fehlender Berechtigungen blockiert wird. <!--limitations-->         |
|Microsoft Information Protection (MIP) SDK     | Any        | Drittanbieteranwendungen        | Wird jedes Mal generiert, wenn von einer Drittanbieter Anwendung, die Sie unterstützt, auf eine bezeichnete oder geschützte Datei zugegriffen wird.       |
|RMS-Dienst     | Windows        | Office         |Wird jedes Mal generiert, wenn auf ein beschrifteten oder geschütztes Dokument zugegriffen wird.<!-- plan to be removed -->       |


## <a name="access-denied-audit-logs"></a>Zugriffs Verweigerungs Überwachungs Protokolle

Für die folgenden Aktivitäten werden **Zugriffs Verweigerungs** Überwachungs Protokolle generiert:

|Gemeldet von  |Plattform  |Anwendung  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|RMS-Dienst     | Windows        | Office         |Wird jedes Mal generiert, wenn ein Benutzer versucht, auf ein geschütztes Dokument zuzugreifen, für das Sie keine Berechtigungen haben.

## <a name="change-protection-audit-logs"></a>Überwachungs Protokolle für den Schutz ändern

Überwachungs Protokolle für den **Änderungs Schutz** werden für die folgenden Aktivitäten generiert:

|Gemeldet von  |Plattform  |Anwendung  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client     | Windows, SharePoint, onedrive        | Office        | Wird jedes Mal generiert, wenn der Schutz für ein Dokument ohne Bezeichnung manuell geändert wird.         |
|Microsoft Information Protection (MIP) SDK     | Any        | Drittanbieteranwendungen        | Wird jedes Mal generiert, wenn der Schutz für ein Dokument ohne Bezeichnung manuell geändert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt.       |

## <a name="discover-audit-logs"></a>Überwachungs Protokolle ermitteln

Überwachungs Protokolle **ermitteln** werden für die folgenden Aktivitäten generiert:

|Gemeldet von  |Plattform  |Anwendung  |Aktion/Beschreibung   |
|---------|---------|---------|---------|
|Azure Information Protection:</br>-Klassischer Scanner </br>-Unified-Beschriftungs Scanner     | Windows        | Office        |Wird jedes Mal generiert, wenn eine Datei durch den AIP-Scanner gescannt wird.<br>Das Protokoll enthält die folgenden Details:<br>-Übereinstimmende Informationstypen<br>-Bezeichnungen |
|Microsoft Information Protection (MIP) SDK | Any | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Datei von einer Drittanbieter Anwendung gescannt wird, von der Sie unterstützt wird. </br>Das Protokoll enthält die folgenden Details:</br>-Übereinstimmende Informationstypen</br>-Bezeichnungen|

## <a name="downgrade-label-audit-logs"></a>Überwachungs Protokolle für das Downgrade der Bezeichnung

Überwachungs Protokolle für die **Herabstufung der Bezeichnung** werden für die folgenden Aktivitäten generiert:

| Gemeldet von      | Plattform                       | Anwendung              | Aktion/Beschreibung      |
| ---------------- | ------------------------------ | ------------------------ | --------------- |
|Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird.|
| Microsoft Defender ATP            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird. |
| Microsoft Information Protection (MIP) SDK          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer weniger sensiblen Bezeichnung aktualisiert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="file-removed-audit-logs"></a>Datei entfernte Überwachungs Protokolle

> [!NOTE]
> Datei entfernte Überwachungs Protokolle werden nur in Azure Information Protection Scanner-Version [2.7.95.0](rms-client/unifiedlabelingclient-version-release-history.md#version-27950-public-preview) und höher unterstützt.

**Dateien** , die entfernt wurden, werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                              | Plattform | Anwendung                     | Aktion/Beschreibung                                                          |
| ---------------------------------------------------------------------------------------- | -------- | ------------------------------- | ------------------------------------------------------------------------------ |
| Azure Information Protection Scanner, einheitlicher Bezeichnungs Client | Windows  | Office-und unterstützte Dateitypen | Wird jedes Mal generiert, wenn der AIP-Scanner erkennt, dass eine zuvor gescannte Datei entfernt wurde. |

## <a name="new-label-audit-logs"></a>Neue Beschriftungs Überwachungs Protokolle

**Neue Beschriftungs** Überwachungs Protokolle werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Anwendung              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine neue Bezeichnung angewendet wird.                                                                  |
| Microsoft Defender ATP                                                                            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine neue Dokument Bezeichnung angewendet wird.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine neue Dokument Bezeichnung angewendet wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="new-protection-audit-logs"></a>Neue Schutz Überwachungs Protokolle

Für die folgenden Aktivitäten werden **neue Schutz** Überwachungs Protokolle generiert:

| Gemeldet von                                                                      | Plattform                       | Anwendung              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn der Schutz manuell neu hinzugefügt wird, ohne eine Bezeichnung.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn der Schutz manuell neu hinzugefügt wird, ohne eine Bezeichnung.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="remove-label-audit-logs"></a>Überwachungs Protokolle für die Bezeichnung entfernen

Überwachungs Protokolle für die **Bezeichnung entfernen** werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Anwendung              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.                                                                  |
| Microsoft Defender ATP                                                                            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Bezeichnung entfernt wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="remove-protection-audit-logs"></a>Schutz Überwachungs Protokolle entfernen

Zum **Entfernen von Schutz** Überwachungsprotokollen werden die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Anwendung              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn der Schutz manuell entfernt wird, ohne eine Bezeichnung zu erhalten.                                                                  |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn der Schutz manuell entfernt wird, ohne eine Bezeichnung zu erhalten.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |

## <a name="upgrade-label-audit-logs"></a>Überwachungs Protokolle für Bezeichnung aktualisieren

Überwachungs Protokolle für die **upgradebezeichnung** werden für die folgenden Aktivitäten generiert:

| Gemeldet von                                                                      | Plattform                       | Anwendung              | Aktion/Beschreibung                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Azure Information Protection:</br>-Klassischer Client</br>-Unified-Bezeichnungs Client | Windows, SharePoint, ein Laufwerk | Office                   | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.                                                                   |
| Microsoft Defender ATP                                                                            | Windows                        | OS                       | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.                                                                   |
| Microsoft Information Protection (MIP) SDK                                                                          | Any                            | Drittanbieteranwendungen | Wird jedes Mal generiert, wenn eine Dokument Bezeichnung mit einer sensitiven Bezeichnung aktualisiert wird.<br>Wird nur generiert, wenn von der Drittanbieter Anwendung unterstützt. |