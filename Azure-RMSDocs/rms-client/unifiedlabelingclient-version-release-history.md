---
title: Azure Information Protection unified - Clientversion Bezeichnung Versionsgeschichte und Supportrichtlinie
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: maayan
ms.suite: ems
ms.openlocfilehash: 1262a2f1a70002686aed0bad47354cdc5ac23bac
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60180884"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection unified - Clientversion Bezeichnung Versionsgeschichte und Supportrichtlinie

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anleitungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


Sie können den einheitlichen Azure Information Protection-Bezeichnung-Client aus der [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede Version der allgemein verfügbar (GA) des Azure Information Protection unified bezeichnungs-Clients wird für bis zu sechs Monate nach der Veröffentlichung von der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

> [!NOTE]
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

### <a name="release-information"></a>Informationen zum Release

Verwenden Sie die folgende Informationen, um anzuzeigen, was für die allgemein verfügbare Version des Azure Information Protection unified bezeichnungs-Clients unterstützt wird.

Dieser Client installiert ein Office-Add-On für Windows-Computer, eine Erweiterung für den Datei-Explorer und ein PowerShell-Modul. Es gelten die gleichen [Voraussetzungen](../requirements.md) wie für den Azure Information Protection-Client, der Richtlinien aus Azure herunterlädt.

Informationen zu Features und Funktionalität im Azure Information Protection-Client finden Sie unter [Vergleich zwischen den Features der Clients](use-client.md#compare-the-clients).

## <a name="version-20778"></a>Version 2.0.778

**Veröffentlicht**: 04/16/2019

Diese erste allgemein verfügbare Version des Azure Information Protection unified bezeichnungs-Clients für Windows unterstützt die folgenden Features: 

- Upgrade vom Azure Information Protection-Client.

- Manuelle, automatische und empfohlene Klassifizierung: Weitere Informationen zur Konfiguration der automatischen und empfohlenen Klassifizierung für diesen Client finden Sie unter [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf den Inhalt](/Office365/SecurityCompliance/apply_sensitivity_label_automatically).

- Datei-Explorer, Rechtsklickaktionen zum Klassifizieren und Schützen von Dateien, Entfernen des Schutzes und Anwenden von benutzerdefinierten Berechtigungen.

- Ein Viewer für geschützten Text und geschützte Bilddateien, geschützte PDF-Dateien und Dateien die generisch geschützt werden.

- PowerShell-Befehle für Folgendes:
    - [Festlegen oder Entfernen einer Bezeichnung in einem Dokument](/powershell/module/azureinformationprotection/set-aipfilelabel)
    - [Hinzufügen einer Bezeichnung zu einem Dokument nach Untersuchen des Inhalts](/powershell/module/azureinformationprotection/set-aipfileclassification)
    - [Lesen von Informationen zu einer auf ein Dokument angewendeten Bezeichnung](/powershell/module/azureinformationprotection/get-aipfilestatus)
    - [Authentifizieren der Unterstützung unbeaufsichtigter PowerShell-Sitzungen](/powershell/module/azureinformationprotection/set-aipauthentication)

- Überwachung von Daten und der Endpunkt-Discovery-Unterstützung für die zentrale Berichterstattung mithilfe [Analytics für Azure Information Protection](../reports-aip.md).

- Folgende Einstellungen für Bezeichnungen und Richtlinien:
    - Optische Kennzeichnung (Kopfzeile, Fußzeile und Wasserzeichen)
    - Standardbeschriftung
    - Bezeichnungen, die „Nicht weiterleiten“ anwenden und nur in Outlook angezeigt werden
    - Aufforderung zur Angabe einer Begründung, wenn ein Benutzer eine Klassifizierungsstufe senkt oder eine Bezeichnung entfernt
    - Farben für die Bezeichnungen

- Aktualisieren der Richtlinie über die Admin Center:
    - Bei jedem Start einer Office-App und alle vier Stunden
    - Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen
    - Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz

- Die Dialogfelder „Hilfe“ und „Feedback“, die Einstellungen zum Zurücksetzen und Exportprotokolle umfassen.


## <a name="next-steps"></a>Nächste Schritte

Ausführliche Informationen finden Sie in den [Vergleichstabellen](use-client.md#compare-the-clients).

Weitere Informationen zum Installieren und verwenden dieses Clients: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection – einheitliche bezeichnungs Client – Administratorhandbuch](clientv2-admin-guide.md)

