---
title: 'Konzepte: Richtlinienhandler im MIP SDK'
description: In diesem Artikel erfahren Sie, wie Richtlinien-API-Handler für Aufrufe erstellt und implementiert werden.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: tommos
ms.openlocfilehash: 02198f7762e2952f946757d14c13a41b22d73c7a
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303990"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>Microsoft Information Protection SDK: Konzepte für Richtlinienhandler

In der API-Richtlinie `mip::PolicyHandler` macht Vorgänge verwendet, um Aktionen zu berechnen und senden die Überwachungsereignisse verfügbar.

## <a name="policy-handler-functions"></a>Richtlinienhandlerfunktionen

`mip::PolicyHandler` stellt Methoden zum Lesen, Schreiben und Entfernen von Bezeichnungen und Schutzinformationen bereit. Die vollständige Liste finden Sie in der [API-Referenz](reference/class_mip_PolicyHandler.md).

In diesem Artikel werden die folgenden Methoden behandelt:

- `ComputeActions`
- `NotifyCommittedActions`

## <a name="requirements"></a>Anforderungen

Das Erstellen eines `PolicyHandler`-Elements erfordert:

- Ein `PolicyProfile`-Element.
- Ein `PolicyEngine`-Element, dass `PolicyProfile` hinzugefügt wurde.
- Eine Klasse, die `mip::PolicyHandler::Observer` erbt.

## <a name="create-a-policy-handler"></a>Erstellen eines Richtlinienhandlers

Der erste Schritt zum Abrufen von Richtlinienaktionen ist die Erstellung eines `PolicyHandler`-Objekts. Diese Klasse implementiert die Funktionalität benötigt wird, um die Liste der Aktionen zu erhalten, die eine bestimmte Bezeichnung ausführen muss. Außerdem implementiert die Funktion, um ein Überwachungsereignis ausgelöst.

Das Erstellen des `PolicyHandler` ist so einfach wie das Aufrufen der `CreatePolicyHandlerAsync`-Funktion von `PolicyEngine` mithilfe des Promise-/Future-Musters.

`CreatePolicyHandlerAsync` akzeptiert einen einzelnen Parameter: **isAuditDiscoveryEnabled**. Setzen Sie diesen Wert auf **true**, wenn die Anwendung Taktereignisse im Überwachungsprotokoll anzeigen soll.

> [!NOTE]
> Die `mip::PolicyHandler::Observer`-Klasse muss in einer abgeleiteten Klasse implementiert werden, da `CreatePolicyHandler` das `Observer`-Objekt erfordert. 

```cpp
auto createPolicyHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyHandler>>>();
auto createPolicyHandlerFuture = createPolicyHandlerPromise->get_future();
PolicyEngine->CreatePolicyHandlerAsync(true);
auto handler = createPolicyHandlerFuture.get();
```

Nach erfolgreicher Erstellung des `PolicyHandler`-Objekts können Aktionen berechnet und Überwachungsereignisse übermittelt werden.

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie zur Erstellung eines Handlers für die Richtlinie gelernt habe:

- Erfahren Sie, wie Sie [erstellen Sie eine Ausführung-Status-Klasse](concept-handler-policy-executionstate-cpp.md), die für die Bestimmung von Compute-Aktionen verwendet wird.
- Herunterladen der [API API Management-Richtlinienbeispiele aus GitHub, und versuchen Sie die Richtlinie-API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
