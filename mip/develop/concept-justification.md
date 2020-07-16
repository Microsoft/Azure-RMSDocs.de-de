---
title: 'Konzept: Aktions Begründung im MIP SDK'
description: In diesem Artikel erfahren Sie, wie Sie eine Bezeichnung herabstufen oder entfernen, für die eine Begründung erforderlich ist.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: conceptual
ms.date: 04/14/2020
ms.author: v-anikep
ms.openlocfilehash: c783722a7cded0242ae12386854b3c8fca325a9e
ms.sourcegitcommit: 36413b0451ae28045193c04cbe2d3fb2270e9773
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405202"
---
# <a name="action-justification-in-mip-sdk"></a>Aktions Begründung im MIP SDK

## <a name="overview"></a>Übersicht

Mit Bezeichnungs Richtlinien im Security and Compliance Center können Administratoren eine **Begründung** beim Entfernen oder herabstufen einer Bezeichnung anfordern. Das Downgrade wird als Anwenden einer Bezeichnung mit einem niedrigeren Empfindlichkeits Wert anstelle der vorhandenen Bezeichnung definiert.

Wie bereits erläutert, bietet die File-API einfach zu verwendende Schnittstellen zum Lesen von Bezeichnungen aus dem Dienst, zum Anwenden von Bezeichnungen auf definierte Dateitypen und zum Lesen von Bezeichnungen aus diesen Dateitypen. Außerdem werden Datei Vorgänge zum Entfernen und Ändern der Bezeichnungen für unterstützte Dateitypen unterstützt. Änderungen an der Datei Bezeichnung werden von der-Funktion unterstützt, die `mip::FileHandler` `SetLabel()` die Möglichkeit bietet, eine neue Bezeichnung für eine ungeschützte oder zuvor geschützte Datei festzulegen, und die `mip::FileHandler` - `DeleteLabel()` Funktion, die die Bezeichnung aus einer zuvor geschützten Datei entfernt.

Für einige der Vertraulichkeits Bezeichnungen sollten Sicherheits Administratoren strengere Richtlinien anwenden, wenn ein Benutzer versucht, die Empfindlichkeit herabzusetzen, indem er eine Bezeichnung löscht oder die Bezeichnung in eine weniger restriktive Bezeichnung ändert. Mithilfe des Kontrollkästchens können Administratoren dies mithilfe der Bezeichnung Richtlinien Konfiguration im [Security and Compliance Center](https://sip.compliance.microsoft.com/) konfigurieren.

![Aktions Begründung erforderlich](./media/justify-action.png)

Wenn die Datei eine vorhandene Bezeichnung aufweist und die Bezeichnungs Richtlinie im Fall einer Herabstufung der Bezeichnung eine Begründung erfordert, lösen die `SetLabel()` / `DeleteLabel()` Funktionen aus `mip::JustificationRequiredError` . Die Anwendung muss diese Ausnahme abfangen und dann eine Anwendungs Schnittstelle für den Benutzer bereitstellen, um Eingaben für den Grund für das Downgrade bereitzustellen. Nachdem die Begründung aufgezeichnet wurde, kann die Anwendung die-Eigenschaft `isDowngradeJustified` von festlegen `mip::LabelingOptions` und die- `Justification` Eigenschaft festlegen.

## <a name="next-steps"></a>Nächste Schritte

- [Schnellstart für die Aktions Begründung prüfen für (C++)](quick-file-justify-actions-cpp.md)
- [Schnellstart für Aktions Ausrichtung überprüfen für (c#)](quick-file-justify-actions-csharp.md)