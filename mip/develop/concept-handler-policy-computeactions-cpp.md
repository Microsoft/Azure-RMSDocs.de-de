---
title: 'Konzepte: Verwendung des Microsoft Information Protection SDK zum Generieren von Überwachungsereignissen'
description: In diesem Artikel erfahren Sie, wie Sie das Microsoft Information Protection SDK zum Berechnen von verwenden.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: tommos
ms.openlocfilehash: 8ade287531ee9f1c18678d42ef5e51a4c70ee13f
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69886199"
---
# <a name="compute-an-action"></a>Berechnen einer Aktion

Wie zuvor erläutert, hat die Richtlinien-API folgende Hauptfunktionen:

- Auflisten der verfügbaren Bezeichnungen
- gibt eine Reihe von Aktionen zurück, die durchgeführt werden sollen, basierend auf dem aktuellen und dem gewünschten Zustand.

Der letzte Schritt in diesem Prozess besteht darin, für die Funktion `ComputeActions()` eine Bezeichnungs-ID und optional Metadaten zur vorhandenen Bezeichnung anzugeben.

Einen Beispielcode zu diesem Artikel finden Sie auf GitHub.

- [mipsdk-policyapi-cpp-sample-basic](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic)

## <a name="compute-an-action-for-a-new-label"></a>Berechnen einer Aktion für eine neue Bezeichnung

Das Berechnen `mip::Actions` der für eine neue Bezeichnung kann mithilfe der `ExecutionStateImpl` in [executionstate](concept-handler-policy-executionstate-cpp.md)definierten erreicht werden.

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c"; 
sample::policy::ExecutionStateOptions options;

// Resolve desired label id to mip::Label and set in ExecutionStateOptions.
options.newLabel = mEngine->GetLabelById(newLabelId);

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

Wenn Sie die Richtlinien-API verwenden, liegt es an der Anwendung, Metadaten aus dem Inhalt zu lesen. Diese Metadaten werden der API als Teil des `mip::ExecutionState`-Elements zur Verfügung gestellt. Mit `ComputeActions()` können komplexere Vorgänge ausgeführt werden, als eine neue Bezeichnung auf ein noch nicht gekennzeichnetes Dokument anzuwenden. Das folgende Beispiel veranschaulicht das Herabstufen einer Bezeichnung von einer sensitiven Bezeichnung in eine weniger sensible Bezeichnung. Dieser Prozess wird simuliert, indem eine durch Trennzeichen getrennte Zeichenfolge von Metadaten gelesen und die API über `mip::ExecutionState`bereitgestellt wird.

> [!NOTE]
> Im Beispielcode wird eine Hilfsfunktion namens `SplitString()` verwendet. Ein Beispiel finden Sie [hier](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/utils.cpp).

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c";

// Comma and Pipe Delimited Metadata.
string metadata = "MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled|true,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate|2018-10-23T21:53:31-0800,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method|Standard,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name|Contoso FTEs (C),MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId|94f6984e-8d31-4794-bdeb-3ac89ad2b660,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId|b56491d9-155f-40ff-866f-0000acd85c31,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits|7";

// Create ExecutionStateOptions and resolve newLabelId to mip::Label
sample::policy::ExecutionStateOptions options;
options.newLabel = mEngine->GetLabelById(newLabelId);

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

- Erfahren Sie, wie Überwachungs [Ereignisse an Azure Information Protection Analytics übergeben](concept-handler-policy-auditing-cpp.md) werden.
- Laden Sie die [Richtlinien-API-Beispiele von GitHub herunter, und testen Sie die Richtlinien-API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
