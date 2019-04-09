---
title: 'Der Azure Information Protection-Client für einheitliche Bezeichnungen: Informationen zum Release'
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/02/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: maayan
ms.suite: ems
ms.openlocfilehash: 7eb7ffd98651ed35be7ecd8043e49c1d15a65e8e
ms.sourcegitcommit: 8da0aa8f9bb9f91375580a703682d23a81a441bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58809708"
---
# <a name="azure-information-protection-unified-labeling-client-version-release-information"></a>Azure Information Protection-Client für einheitliche Bezeichnungen: Informationen zum Release

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

> [!NOTE]
> Der Client befindet sich noch in der Vorschauphase. Es können also noch Änderungen vorgenommen werden. Er verwendet einen Speicher für einheitliche Bezeichnungen und lädt Richtlinien für Bezeichnungen aus den folgenden Admin-Centers herunter: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, und das Microsoft 365 Compliance Center. [Weitere Informationen](/Office365/SecurityCompliance/sensitivity-labels)

Sie können die neuste Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57440) herunterladen.

### <a name="release-information"></a>Informationen zum Release

In diesem Artikel erfahren Sie, welche Funktionen für die neuste Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen unterstützt werden.

Dieser Client installiert ein Office-Add-On für Windows-Computer, eine Erweiterung für den Datei-Explorer und ein PowerShell-Modul. Es gelten die gleichen [Voraussetzungen](../requirements.md) wie für den Azure Information Protection-Client, der Richtlinien aus Azure herunterlädt.

Informationen zu Features und Funktionalität im Azure Information Protection-Client finden Sie unter [Vergleich zwischen den Features der Clients](use-client.md#feature-comparisons-for-the-clients).

## <a name="current-preview-version"></a>Aktuelle Vorschauversion

**Veröffentlicht**: 25.2.2019

Die Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows unterstützt die folgenden Features: 

- Upgrade vom Azure Information Protection-Client.

- Manuelle, automatische und empfohlene Klassifizierung: Weitere Informationen zur Konfiguration der automatischen und empfohlenen Klassifizierung für diesen Client finden Sie unter [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf den Inhalt](/Office365/SecurityCompliance/apply_sensitivity_label_automatically).

- Datei-Explorer, Rechtsklickaktionen zum Klassifizieren und Schützen von Dateien, Entfernen des Schutzes und Anwenden von benutzerdefinierten Berechtigungen.

- Ein Viewer für geschützten Text und geschützte Bilddateien, geschützte PDF-Dateien und Dateien die generisch geschützt werden.

- PowerShell-Befehle für Folgendes:
    - [Festlegen oder Entfernen einer Bezeichnung in einem Dokument](/powershell/module/azureinformationprotection/set-aipfilelabel)
    - [Hinzufügen einer Bezeichnung zu einem Dokument nach Untersuchen des Inhalts](/powershell/module/azureinformationprotection/set-aipfileclassification)
    - [Lesen von Informationen zu einer auf ein Dokument angewendeten Bezeichnung](/powershell/module/azureinformationprotection/get-aipfilestatus)
    - [Authentifizieren der Unterstützung unbeaufsichtigter PowerShell-Sitzungen](/powershell/module/azureinformationprotection/set-aipauthentication)

- Unterstützung einer zentralen Berichterstellung mithilfe von [Azure Information Protection-Analysen](../reports-aip.md).

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

### <a name="features-that-do-not-work-in-this-preview-version-or-are-not-available"></a>Features, die in dieser Vorschauversion nicht funktionieren oder nicht verfügbar sind

Dies umfasst Folgendes:

- Die Überprüfung zum Entdecken, Bezeichnen und Schützen von Dateien in lokalen Datenspeichern ist nicht verfügbar.

- Bezeichnungen, die aus dem Azure-Portal migriert und für den HYOK-Schutz konfiguriert wurden, werden nach Veröffentlichung im Client angezeigt, wenden aber keinen Schutz an.

- Die Cmdlets aus dem AzureInformationProtection-Modul sind nicht vollständig vorhanden. Dies gilt auch für Cmdlets, die direkt mit einem Schutzdienst verbunden sind. Beispiel: Unprotect-RMSFile zum Aufheben des Schutzes von Dateien per Massenvorgang.

Ausführliche Informationen finden Sie in den [Vergleichstabellen](use-client.md#feature-comparisons-for-the-clients).

## <a name="instructions"></a>Anweisungen

1. Installieren Sie den Client mithilfe der folgenden Anweisungen: [Leitfaden: Herunterladen und Installieren des Azure Information Protection-Clients (Vorschauversion)](install-unifiedlabelingclient-app.md) 

2. Verwenden Sie den Client genauso wie den Azure Information Protection-Client – mit folgenden Ausnahmen für Office-Apps:
    - Die Schaltfläche auf dem Office-Menüband heißt **Vertraulichkeit**, nicht **Schützen**.
    - Administratoren können die Information Protection-Leiste nicht standardmäßig anzeigen, aber Benutzer können sie anzeigen, indem sie über die Schaltfläche **Vertraulichkeit** die Option **Leiste anzeigen** auswählen. 
    - Benutzerdefinierte Berechtigungen sind nicht verfügbar
    - Aktionen zum Nachverfolgen und Widerrufen sind nicht verfügbar
    
    Für Benutzeranweisungen:
    
    - [Klassifizieren einer Datei oder E-Mail](client-classify.md) 
    
    - [Klassifizieren und Schützen einer Datei oder E-Mail](client-classify-protect.md)

3. Teilen Sie Ihre Erfahrungen: 
    
    - Sie können über die [Yammer-Seite für Azure Information Protection](https://www.yammer.com/AskIPTeam) Feedback geben oder Fragen zum Client in der Vorschauversion stellen.
