---
title: 'Konzept: Aktions Begründung im MIP SDK (C++)'
description: In diesem Artikel erfahren Sie, wie Sie eine Bezeichnung Herabstufen oder entfernen, die eine Begründung erfordert.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: conceptual
ms.date: 04/14/2020
ms.author: v-anikep
ms.openlocfilehash: 1b0926114dd4d494593bd0d2340fee35edfe5fe6
ms.sourcegitcommit: a1feede30ac1f54e900e52eb45b3e6634e0f13f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84548240"
---
# <a name="action-justification-in-mip-sdk-c"></a>Aktions Begründung im MIP SDK (C++)

## <a name="overview"></a>Übersicht

Mit Bezeichnungs Richtlinien im Security and Compliance Center können Administratoren eine **Begründung** beim Entfernen oder herabstufen einer Bezeichnung anfordern. Das Downgrade wird als Anwenden einer Bezeichnung mit einem niedrigeren Empfindlichkeits Wert anstelle der vorhandenen Bezeichnung definiert.

Wie bereits erläutert, bietet die File-API einfach zu verwendende Schnittstellen zum Lesen von Bezeichnungen aus dem Dienst, zum Anwenden von Bezeichnungen auf definierte Dateitypen und zum Lesen von Bezeichnungen aus diesen Dateitypen. Außerdem werden Datei Vorgänge zum Entfernen von Bezeichnungen aus und zum Ändern der Bezeichnungen in unterstützten Dateitypen unterstützt. Änderungen an der Datei Bezeichnung werden von der-Funktion unterstützt, die `mip::FileHandler` `SetLabel()` die Möglichkeit bietet, eine neue Bezeichnung für eine ungeschützte oder zuvor geschützte Datei festzulegen, und die `mip::FileHandler` - `DeleteLabel()` Funktion, die die Bezeichnung aus einer zuvor geschützten Datei entfernt.

Für einige der Vertraulichkeits Bezeichnungen sollten Sicherheits Administratoren strengere Richtlinien anwenden, wenn ein Benutzer versucht, die Empfindlichkeit herabzusetzen, indem er eine Bezeichnung löscht oder die Bezeichnung in eine weniger restriktive Bezeichnung ändert. Mithilfe des Kontrollkästchens können Administratoren dies mithilfe der Bezeichnung Richtlinien Konfiguration im [Security and Compliance Center](https://sip.compliance.microsoft.com/) konfigurieren.

![Aktions Begründung erforderlich](./media/justify-action.png)

Wenn die Datei eine vorhandene Bezeichnung aufweist und die Bezeichnungs Richtlinie im Falle einer Herabstufung der Vertraulichkeits Stufe eine Begründung erfordert, lösen die `SetLabel()` / `DeleteLabel()` Funktionen aus `mip::JustificationRequiredError` . In einem solchen Szenario bietet die API die Möglichkeit, die Benutzer Begründung aufzuzeichnen. SDK-Consumer sollten eine Anwendungs Schnittstelle für den Benutzer bereitstellen, um Eingaben für den Grund für das Downgrade bereitzustellen. Nachdem die Begründung aufgezeichnet wurde, kann die Anwendung die-Eigenschaft `isDowngradeJustified` von festlegen `mip::LabelingOptions` und die- `Justification` Eigenschaft festlegen.

## <a name="next-steps"></a>Nächste Schritte

- [Schnellstart für die Aktions Begründung prüfen für (C++)](quick-file-justify-actions-cpp.md)
- [Schnellstart für Aktions Ausrichtung überprüfen für (c#)](quick-file-justify-actions-csharp.md)