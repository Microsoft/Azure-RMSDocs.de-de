---
title: 'Konzepte: Überwachung mit der Richtlinien-API für das Microsoft Information Protection SDK'
description: In diesem Artikel erfahren Sie, wie Sie das Microsoft Information Protection SDK verwenden können, um Richtlinien-API-Überwachungsereignisse an die Azure Information Protection-Analyse zu übermitteln.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 11/07/2018
ms.author: tommos
ms.openlocfilehash: 729570c902ad3175b65ddd8167005c0cb4e4078c
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60175223"
---
# <a name="auditing-in-the-mip-sdk"></a>Überwachung im MIP SDK

Über das Administrationsportal von Azure Information Protection können Sie auf Administratorberichte zugreifen. Diese Berichte bieten einen Überblick über die Bezeichnungen, die Benutzer manuell oder automatisch in allen Anwendungen anwenden, in denen das MIP SDK integriert ist. Entwicklungspartner, die das SDK nutzen, können diese Funktionalität ganz einfach aktivieren, um Informationen aus ihren Anwendungen in Kundenberichten anzuzeigen.

## <a name="event-types"></a>Ereignistypen

Es gibt drei Typen von Ereignissen, die über das SDK an die Azure Informationen Protection-Analyse übermittelt werden können. **Taktereignisse**, **Ermittlungsereignisse** und **Änderungsereignisse**

### <a name="heartbeat-events"></a>Taktereignisse

Taktereignisse werden für jede Anwendung, in der die Richtlinien-API integriert ist, automatisch generiert. Taktereignisse enthalten Folgendes:

* TenantId
* Erstellungszeit
* Benutzerprinzipalname
* Name des Computers, auf dem die Überwachung generiert wurde
* Prozessname
* Platform
* Die Anwendungs-ID entspricht der Azure AD-Anwendungs-ID.

Diese Ereignisse sind hilfreich, um Anwendungen in Ihrem Unternehmen zu erkennen, die das Microsoft Information Protection SDK verwenden.

### <a name="discovery-events"></a>Ermittlungsereignisse

Ermittlungsereignisse liefern Informationen über Daten mit Bezeichnungen, die von der Richtlinien-API gelesen oder verwendet werden. Diese Ereignisse sind hilfreich, da sie die Geräte, den Standort und die Benutzer erfassen, die auf Informationen in einer Organisation zugreifen.

Discovery-Ereignisse werden in der API-Richtlinie generiert, durch ein Flag festlegen, beim Erstellen der `mip::PolicyHandler` Objekt. Im folgenden Beispiel wird der Wert für **IsAuditDiscoveryEnabled** nastaven NA hodnotu `true`. Wenn `mip::ExecutionState` übergeben wird, um `ComputeActions()` oder `GetSensitivityLabel()` (mit vorhandenen Informationen und Inhalte Metadatenbezeichner), wird Azure Informationen Protection Analytics Ermittlungsinformationen gesendet werden.

Die Ermittlungsüberwachung erfolgt, sobald die Anwendung `ComputeActions()` oder `GetSensitivityLabel()` aufruft und `mip::ExecutionState` bereitstellt. Dieses Ereignis wird nur einmal pro Handler generiert.

Weitere Einzelheiten zum Ausführungsstatus finden Sie in der Dokumentation unter den Konzepten zu `mip::ExecutionState`.

```cpp
// Create PolicyHandler, passing in true for isAuditDiscoveryEnabled
auto handler = mEngine->CreatePolicyHandler(true);

// Returns vector of mip::Action and generates discovery event.
auto actions = handler->ComputeActions(*state);

//Or, get the label for a given state
auto label = handler->GetSensitivityLabel(*state);
```

In der Praxis sollte **isAuditDiscoveryEnabled** während der `mip::PolicyHandler`-Konstruktion `true` sein, damit Dateizugriffsinformationen an die Azure Information Protection-Analyse weitergeleitet werden können.

## <a name="change-event"></a>Änderungsereignis

Änderungsereignisse liefern Informationen über die Datei, die Bezeichnung, die angewendet oder geändert wurde, und alle vom Benutzer angegebenen Begründungen. Änderungsereignisse werden durch den Aufruf von `NotifyCommittedActions()` auf der `mip::PolicyHandler`-Instanz generiert. Der Aufruf erfolgt nach dem erfolgreichen Commit einer Änderung in eine Datei, wobei das `mip::ExecutionState`-Element übergeben wurde, das zur Berechnung der Aktionen verwendet wurde.

> Wenn die Anwendung diese Funktion nicht aufruft, werden auch keine Ereignisse an die Azure Information Protection-Analyse übergeben.

```cpp
handler->NotifyCommittedActions(*state);
```

## <a name="audit-dashboard"></a>Überwachungsdashboard

An die Überwachungspipeline von Azure Information Protection übermittelte Ereignisse werden in Berichten unter https://portal.azure.com angezeigt. Azure Informationen Protection Analytics ist in der öffentlichen Vorschau und Features und Funktionen kann sich ändern.

## <a name="next-steps"></a>Nächste Schritte

- Ausführliche Informationen zu den überwachungsmöglichkeiten in Azure Information Protection, finden Sie unter der [Vorschau ankündigungs-Blog auf Tech Community](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).
- Herunterladen der [API API Management-Richtlinienbeispiele aus GitHub, und versuchen Sie die Richtlinie-API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)

