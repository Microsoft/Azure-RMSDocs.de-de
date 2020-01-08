---
title: 'Konzepte: Beobachter im MIP SDK'
description: Das MIP SDK ist so konzipiert, dass es beinahe vollständig asynchron ist. In diesem Artikel erfahren Sie, wie Beobachter implementiert und mit dem Ziel der Asynchronität verwendet werden.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: bd709b75c5b98c4241bc80f4a8542de30f48ff66
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75555873"
---
# <a name="microsoft-information-protection-sdk---observer-concepts"></a>Microsoft Information Protection SDK: Beobachterkonzepte

Das MIP SDK ist so konzipiert, dass es beinahe vollständig asynchron ist. Beispielsweise wird jeder Vorgang, der ein E/A-Netzwerk oder eine E/A-Datei zur Folge hat, asynchron ausgeführt. Das SDK verwendet das [Beobachtermuster](https://wikipedia.org/wiki/Observer_pattern), um die Ereignisbenachrichtigungen für die asynchronen Ereignisse zu verarbeiten. 

## <a name="implementation-overview"></a>Implementierungsübersicht

Wenn ein Objekt erstellt wird, das einen asynchronen Vorgang ausführen soll, muss eine `Observer`-Klasse implementiert werden. Beobachter empfangen die Benachrichtigungsereignisse, die im Zusammenhang mit den verschiedenen asynchronen Vorgängen im MIP SDK stehen, und stellen das Ergebnis für den Aufrufer bereit.

Die Funktionen in den einzelnen `Observer`-Klassen sind virtuell und werden für das bevorzugte asynchrone Muster überschrieben. Das SDK implementiert das Beobachtermuster für die Ereignisbenachrichtigung über `std::promise` und `std::future`.

Klassenspezifische Beobachter enthalten verschiedene Success- und Error/Failure-Funktionen für das Ergebnis von asynchronen Vorgängen. *Success*-Funktionen geben das dem Vorgang zugeordnete Objekt zurück. *Error*/*Failure*-Funktionen geben eine Ausnahme zurück, die Details dazu enthält, warum der Vorgang fehlgeschlagen ist.

Beispielsweise unterstützt das `FileProfile` die folgenden Vorgänge: 

- Es kann über `FileProfile::AddEngineAsync` eine neue Engine zu dem Profil hinzufügen. 
- Es kann über `FileProfile::UnloadEngineAsync` eine neue Engine aus dem Profil entladen.

Da zwei `Observer` Funktionen pro asynchronem Vorgang implementiert werden, kann davon ausgegangen werden, dass **vier** `Observer` Methoden mit `FileProfile`verknüpft sind: 

- `FileProfileObserver::OnAddEngineSuccess()`
- `FileProfileObserver::OnAddEngineError()`
- `FileProfileObserver::OnUnloadEngineSuccess`
- `FileProfileObserver::OnUnloadEngineError()`. 

## <a name="mip-sdk-observer-classes"></a>Observer-Klassen für das MIP SDK

Die Datei-API für das MIP SDK enthält zwei Beobachter:

* `mip::FileProfile::Observer`
* `mip::FileHandler::Observer`

Die Richtlinien-API für das MIP SDK verfügt nur über einen Beobachter:

* `mip::Profile::Observer`

Die Schutz-API für das MIP SDK verfügt über drei Beobachter:

* `mip::ProtectionProfile::Observer`
* `mip::ProtectionEngine::Observer`
* `mip::ProtectionHandler::Observer`

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Implementierung von Beobachtern und deren Verwendungsweise durch die verschiedenen APIs:

* [File API Observers (C++) (Beobachter der Datei-API (C++))](concept-async-observers-file-cpp.md)
* [Policy API Observers (C++) (Beobachter der Richtlinien-API (C++))](concept-async-observers-policy-cpp.md)
* [Protection API Observers (C++) (Beobachter der Schutz-API (C++))](concept-async-observers-protection-cpp.md)
