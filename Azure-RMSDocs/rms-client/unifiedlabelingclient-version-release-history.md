---
title: 'Der Azure Information Protection-Client für einheitliche Bezeichnungen: Informationen zum Release'
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/17/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: maayan
ms.suite: ems
ms.openlocfilehash: f05c1e96222eb70a7257123301d14ef7d885564d
ms.sourcegitcommit: 283782ee7e3ec566f479c8914eae7bf84d904392
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382594"
---
# <a name="azure-information-protection-unified-labeling-client-version-release-information"></a>Der Azure Information Protection-Client für einheitliche Bezeichnungen: Informationen zum Release

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

> [!NOTE]
> Der Client befindet sich noch in der Vorschauphase. Es können also noch Änderungen vorgenommen werden. Er verwendet einen Speicher für einheitliche Bezeichnungen und lädt Richtlinien für Bezeichnungen aus dem Office 365 Security & Compliance Center herunter. [Weitere Informationen](/Office365/SecurityCompliance/sensitivity-labels)

Sie können die neuste Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57440) herunterladen.

### <a name="release-information"></a>Informationen zum Release

In diesem Artikel erfahren Sie, welche Funktionen für die neuste Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen unterstützt werden. 

Der Client wird als Add-On für Office installiert. Es gelten die gleichen [Voraussetzungen](../requirements.md) wie für den Azure Information Protection-Client, der die Richtlinie aus Azure herunterlädt.

## <a name="current-preview-version"></a>Aktuelle Vorschauversion

**Veröffentlicht:** 16.10.2018

Die Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows unterstützt die folgenden Features: 

- Upgrade vom Azure Information Protection-Client

- Manuelle Bezeichnung, die die Klassifizierung und den Schutz für Word, Excel, PowerPoint und Outlook anwendet.

- Optische Kennzeichnung (Kopfzeile, Fußzeile und Wasserzeichen)

- Standardbeschriftung 

- Bezeichnungen, die die Option „Nicht weiterleiten“ anwenden

- Aufforderungen zur Eingabe einer Begründung, wenn Benutzer die Vertraulichkeitsstufe herabsetzen

- Die Dialogfelder „Hilfe“ und „Feedback“, die Einstellungen zum Zurücksetzen und Exportprotokolle umfassen

Die folgenden Funktionen können in dieser Vorschauversion nicht verwendet werden:

- Automatische und empfohlene Klassifizierung

- Benutzerdefinierte Berechtigungen

- Ein Viewer für geschützten Text und geschützte Bilddateien, PDF-Dateien und Dateien die allgemein geschützt werden

- Der Datei-Explorer zum Klassifizieren und Schützen von Dateien (über einen Rechtsklick)

- PowerShell-Befehle zum Klassifizieren und Schützen von Dateien über die Befehlszeile

- Der Scanner zum Finden, Bezeichnen und Schützen von Dateien in lokalen Datenspeichern

- Unterstützung für andere Sprachen als Englisch

## <a name="instructions"></a>Anweisungen

1. Installieren Sie den Client, indem Sie die Anweisungen unter [User Guide: Download and install the Azure Information Protection client (Preview) (Benutzerleitfaden: Herunterladen und Installieren des Azure Information Protection-Clients (Vorschau))](install-unifiedlabelingclient-app.md) ausführen. 

2. Verwenden Sie den Client in Office-Apps genauso wie den Azure Information Protection-Client. Die einzige Ausnahme besteht darin, dass das Office-Menüband nicht **Schutz**, sondern **Vertraulichkeit** heißt:
    
    - [Klassifizieren einer Datei oder E-Mail](client-classify.md) 
    
    - [Klassifizieren und Schützen einer Datei oder E-Mail](client-classify-protect.md)

3. Teilen Sie Ihre Erfahrungen: 
    
    - Sie können über die [Yammer-Seite für Azure Information Protection](https://www.yammer.com/AskIPTeam) Feedback geben oder Fragen zum Client in der Vorschauversion stellen.
    
    - Wenn Sie Probleme mit dem Client in der Vorschauversion melden möchten, verwenden Sie die Option **Hilfe und Feedback** über die Schaltfläche **Vertraulichkeit** im Menüband. Exportieren Sie Ihre Protokolle über das Dialogfeld und fügen Sie diese Protokolldateien an die E-Mail an, die über die Option **Problem melden** erstellt wird. 

