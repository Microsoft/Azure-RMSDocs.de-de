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
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
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
* User Principal Name (Benutzerprinzipalname)
* Name des Computers, auf dem die Überwachung generiert wurde
* Prozessname
* Plattform
* Die Anwendungs-ID entspricht der Azure AD-Anwendungs-ID.

Diese Ereignisse sind hilfreich, um Anwendungen in Ihrem Unternehmen zu erkennen, die das Microsoft Information Protection SDK verwenden.

### <a name="discovery-events"></a>Ermittlungsereignisse

Ermittlungsereignisse liefern Informationen über Daten mit Bezeichnungen, die von der Richtlinien-API gelesen oder verwendet werden. Diese Ereignisse sind hilfreich, da sie die Geräte, den Standort und die Benutzer erfassen, die auf Informationen in einer Organisation zugreifen.

Ermittlungs Ereignisse werden in der Richtlinien-API generiert, indem beim Erstellen des `mip::PolicyHandler` Objekts ein Flag festgelegt wird. Im folgenden Beispiel ist der Wert für **isauditdiscoveryaktivierte** auf `true`festgelegt. Wenn `mip::ExecutionState` an `ComputeActions()` oder `GetSensitivityLabel()` übergeben wird (mit vorhandenen Metadateninformationen und Inhalts Bezeichner), werden Ermittlungs Informationen an Azure Information Protection Analytics übermittelt.

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

An die Überwachungspipeline von Azure Information Protection übermittelte Ereignisse werden in Berichten unter https://portal.azure.com angezeigt. Azure Information Protection Analytics befindet sich in der öffentlichen Vorschau, und Features/Funktionen können sich ändern.

## <a name="next-steps"></a>Nächste Schritte

- Ausführliche Informationen zur Überwachungsfunktion in Azure Information Protection finden Sie im [Vorschau Ankündigungs Blog in der Tech Community](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).
- Laden Sie die [Richtlinien-API-Beispiele von GitHub herunter, und testen Sie die Richtlinien-API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)

