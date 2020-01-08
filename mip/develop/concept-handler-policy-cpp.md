---
title: 'Konzepte: Richtlinienhandler im MIP SDK'
description: In diesem Artikel erfahren Sie, wie Richtlinien-API-Handler für Aufrufe erstellt und implementiert werden.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: tommos
ms.openlocfilehash: 583e59832e40f87665232ebf39e1dddb462ba212
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556179"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>Microsoft Information Protection SDK: Konzepte für Richtlinienhandler

In der Richtlinien-API macht `mip::PolicyHandler` Vorgänge verfügbar, die zum Berechnen von Richtlinien Aktionen und zum Übermitteln von Überwachungs Ereignissen verwendet werden.

## <a name="policy-handler-functions"></a>Richtlinienhandlerfunktionen

`mip::PolicyHandler` stellt Methoden zum Lesen, Schreiben und Entfernen von Bezeichnungen und Schutzinformationen bereit. Die vollständige Liste finden Sie in der [API-Referenz](reference/class_mip_PolicyHandler.md).

In diesem Artikel werden die folgenden Methoden behandelt:

- `ComputeActions`
- `NotifyCommittedActions`

## <a name="requirements"></a>Anforderungen

Das Erstellen eines `PolicyHandler`-Elements erfordert:

- Ein `mip::MipContext`-Element.
- Ein `mip::PolicyProfile`-Element.
- Ein `mip::PolicyEngine`-Element, dass `mip::PolicyProfile` hinzugefügt wurde.
- Eine Klasse, die implementiert `mip::PolicyHandler::Observer`

## <a name="create-a-policy-handler"></a>Erstellen eines Richtlinienhandlers

Der erste Schritt zum Abrufen von Richtlinienaktionen ist die Erstellung eines `PolicyHandler`-Objekts. Diese Klasse implementiert die Funktionalität, die erforderlich ist, um die Liste der Aktionen für eine bestimmte Bezeichnung zu erhalten. Außerdem implementiert Sie die-Funktion, um ein Audit-Ereignis auslöst.

Das Erstellen des `PolicyHandler` ist so einfach wie das Aufrufen der `CreatePolicyHandlerAsync`-Funktion von `PolicyEngine` mithilfe des Promise-/Future-Musters.

`CreatePolicyHandlerAsync` akzeptiert einen einzelnen Parameter: **isAuditDiscoveryEnabled**. Legen Sie diesen Wert auf **true** fest, wenn die Anwendung Takt-und Ermittlungs Ereignisse in der Überwachungs Protokollierung überprüfen soll.

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

Nachdem Sie nun die Erstellung eines Richtlinien Handlers kennengelernt haben, haben Sie Folgendes gelernt:

- Erfahren Sie, wie Sie [eine Ausführungs Zustands Klasse erstellen](concept-handler-policy-executionstate-cpp.md), die zum Bestimmen von Compute-Aktionen verwendet wird.
- Laden Sie die [Richtlinien-API-Beispiele von GitHub herunter, und testen Sie die Richtlinien-API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
