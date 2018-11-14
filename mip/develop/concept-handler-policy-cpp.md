---
title: 'Konzepte: Richtlinienhandler im MIP SDK'
description: In diesem Artikel erfahren Sie, wie Richtlinien-API-Handler für Aufrufe erstellt und implementiert werden.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: c1e150de6096e070f46232e77a4749081fe0bb9f
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297819"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>Microsoft Information Protection SDK: Konzepte für Richtlinienhandler

In der Richtlinien-API macht `mip::PolicyHandler` die verschiedenen Vorgänge verfügbar, die zum Berechnen von Richtlinienaktionen und Übermitteln von Überwachungsereignissen verwendet werden können.

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

Der erste Schritt zum Abrufen von Richtlinienaktionen ist die Erstellung eines `PolicyHandler`-Objekts. Diese Klasse implementiert die erforderliche Funktionalität, um die Liste der Aktionen für eine bestimmte Bezeichnung und die Funktion zum Auslösen eines Überwachungsereignisses zu erhalten.

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

# <a name="compute-an-action"></a>Berechnen einer Aktion

Wie zuvor erläutert, hat die Richtlinien-API folgende Hauptfunktionen:

- Auflisten der verfügbaren Bezeichnungen
- Zurückgeben der spezifischen auszuführenden Aktionen, basierend auf dem aktuellen und gewünschten Status 

Der letzte Schritt in diesem Prozess besteht darin, für die Funktion `ComputeActions()` eine Bezeichnungs-ID und optional Metadaten zur vorhandenen Bezeichnung anzugeben.

Einen Beispielcode zu diesem Artikel finden Sie auf GitHub.

* [mipsdk-policyapi-cpp-sample-basic](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic)

## <a name="compute-an-action-for-a-new-label"></a>Berechnen einer Aktion für eine neue Bezeichnung

Mithilfe von `ExecutionStateImpl` (definiert im Abschnitt [ExecutionState](concept-auditing-policy-executionstate-cpp.md)) kann `mip::Actions` für eine neue Bezeichnung berechnet werden.

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c"; 
sample::policy::ExecutionStateOptions options;

// Set desired newLabelId in ExecutionStateOptions.
options.newLabelId = newLabelId;

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions.
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

Wird nur das als Teil des `actions`-Elements zurückgegebene `mip::MetadataActions`-Element geschrieben, wird Folgendes angezeigt:

```cpp
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled : true
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate : 2018-10-23T20:39:06-0800
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method : Standard
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name : Contoso FTEs (C)
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId : 2266fbe8-a0d9-44e8-bad8-00008f2a0915
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits : 3
```

Durch `PolicyHandler` werden die Aktionen berechnet und `std::vector` mit dem Wert `mip::Action` zurückgegeben. Der Anwendungsentwickler selbst muss diese Metadaten auf die Datei oder die Daten anwenden.

> [!NOTE]
> Das obige Beispiel zeigt nur die `mip::MetadataAction`-Ausgabe. Ein Beispiel für die Anzeige zusätzlicher Aktionstypen finden Sie in den Beispielbundles im [Download der Richtlinien-API](https://aka.ms/mipsdkbins).

## <a name="compute-actions-with-an-existing-label"></a>Berechnen von Aktionen mit einer vorhandenen Bezeichnung

Bei Verwendung der Richtlinien-API muss die Anwendung die Metadaten aus dem Inhalt lesen. Diese Metadaten werden der API als Teil des `mip::ExecutionState`-Elements zur Verfügung gestellt. Mit `ComputeActions()` können komplexere Vorgänge ausgeführt werden, als eine neue Bezeichnung auf ein noch nicht gekennzeichnetes Dokument anzuwenden. Das folgende Beispiel zeigt die Herabstufung einer Bezeichnung von einer vertraulicheren Bezeichnung auf eine weniger vertrauliche Bezeichnung, wenn bereits ein Bezeichnung vorhanden ist. Dieser Prozess wird simuliert, indem eine durch Trennzeichen getrennte Zeichenfolge von Metadaten gelesen und über `mip::ExecutionState` an die API übergeben wird.

> [!NOTE]
> Im Beispielcode wird eine Hilfsfunktion namens `SplitString()` verwendet. Ein Beispiel finden Sie [hier](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-advanced/blob/master/mipsdk-policyapi-cpp-sample-advanced/utils.cpp).

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c";

// Comma and Pipe Delimited Metadata.
string metadata = "MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled|true,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate|2018-10-23T21:53:31-0800,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method|Standard,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name|Contoso FTEs (C),MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId|94f6984e-8d31-4794-bdeb-3ac89ad2b660,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId|b56491d9-155f-40ff-866f-0000acd85c31,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits|7";

// Create ExecutionStateOptions and set newLabelId.
sample::policy::ExecutionStateOptions options;
options.newLabelId = newLabelId;

// Split metadata string by commas, store in vector.
vector<string> metadataPairs = sample::utils::SplitString(metadata, ','); 

// Iterate through each string, splitting by the pipe.
// Add each key/value pair to ExecutionStateOptions metadata.
for (const string& metadataPair : metadataPairs) {
    vector<string> keyValue = sample::utils::SplitString(metadataPair, '|');
    options.metadata[keyValue[0]] = keyValue[1];
}

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

Das obige Beispiel kann zu mehreren Aktionen führen. Diese Aktionen hängen von den als Eingabe bereitgestellten Bezeichnungen und der Bezeichnungskonfiguration ab. Das Ergebnis ist mindestens ein einzelnes `mip::MetadataAction`-Element, das die zu entfernenden Daten über `GetMetadataToRemove()` und die hinzuzufügenden Daten über `GetMetadataToAdd()` enthält.

```
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Enabled : true
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SetDate : 2018-10-23T23:59:41-0800
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Method : Standard
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Name : General
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ActionId : 447a996b-28ea-482c-b0b5-000075bd4bb3
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ContentBits : 7
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId
```

## <a name="next-steps"></a>Nächste Schritte

* Laden Sie als Nächstes die [Beispiele zur Richtlinien-API von GitHub herunter, und testen Sie die Richtlinien-API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi).
* Erfahren Sie, wie Sie [Überwachungsereignisse an die Azure Information Protection-Analyse übergeben](concept-auditing-policy-cpp.md).