---
title: Übersicht über die Azure Information Protection-Richtlinie
description: Grundlegendes zu Bezeichnungen und Einstellungen in einer Azure Information Protection-Richtlinie
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e66a2c117523eb01089881b8210f12ed2f657ed4
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304892"
---
# <a name="overview-of-the-azure-information-protection-policy"></a>Übersicht über die Azure Information Protection-Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Eine Azure Information Protection-Richtlinie enthält die folgenden Elemente, die Sie konfigurieren können:
    
- Die Bezeichnungen, die enthalten sein sollen, mit deren Hilfe Administratoren und Benutzer Dokumente und E-Mails klassifizieren (und optional schützen) können.

- Einen Titel und eine QuickInfo für die Information Protection-Leiste, die in den Office-Anwendungen von Benutzern angezeigt wird.

- Die Option zum Festlegen einer Standardbezeichnung als Ausgangspunkt für die Klassifizierung von Dokumenten und E-Mails.

- Die Option zum Erzwingen einer Klassifizierung, wenn Benutzer Dokumente speichern und E-Mails senden.

- Die Option, um Benutzer zur Angabe einer Begründung aufzufordern, wenn sie eine Bezeichnung mit einer niedrigeren Vertraulichkeitsstufe wählen.

- Die Möglichkeit zum automatischen Bezeichnen einer E-Mail-Nachricht nach deren Anlagen.

- Die Option, um zu steuern, ob die Information Protection-Leiste in Office-Anwendungen angezeigt wird.

- Die Option, um zu steuern, ob die Schaltfläche „Nicht weiterleiten“ in Outlook angezeigt werden soll.

- Die Option, mit der Benutzer ihre eigenen Berechtigungen für Dokumente angeben können.

- Die Möglichkeit zum Bereitstellen eines benutzerdefinierten Hilfelinks für Benutzer.

Azure Information Protection enthält eine [Standardrichtlinie](configure-policy-default.md) mit fünf Hauptbezeichnungen. Zwei dieser Bezeichnungen enthalten untergeordnete Bezeichnungen für Unterkategorien, falls diese benötigt werden. Wenn für eine Bezeichnung untergeordnete Bezeichnungen konfiguriert werden, können Benutzer den Hauptbezeichner nicht auswählen und müssen stattdessen eine der untergeordneten Bezeichnungen auswählen.

Die Azure Information Protection-Bezeichnungen können mit dem vollständigen Bereich von Daten verwendet werden, die ein Unternehmen in der Regel erstellt und speichert – von der niedrigsten Klassifizierung für persönliche Daten bis zur höchsten Klassifizierung für streng vertrauliche Daten. 

Sie können die Standardbezeichnungen unverändert verwenden, diese Bezeichnungen anpassen oder löschen und neue Bezeichnungen erstellen. Die vollständige Anleitung dazu finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).


## <a name="next-steps"></a>Nächste Schritte

Beispiele zum Anpassen der Azure Information Protection-Richtlinie und das resultierende Verhalten für Benutzer finden Sie in den folgenden Tutorials:

- [Tutorial: Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md)

- [Tutorial: Konfigurieren von Azure Information Protection-Richtlinieneinstellungen, die nahtlos funktionieren](infoprotect-settings-tutorial.md)
