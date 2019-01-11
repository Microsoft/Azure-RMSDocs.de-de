---
title: 'Konzepte: Implementierung von ExecutionState im Microsoft Information Protection SDK'
description: In diesem Artikel erfahren Sie, wie Sie ExecutionState im Microsoft Information Protection SDK verwenden, um Aktionen zu berechnen und Details für das Überwachungsprotokoll bereitzustellen.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: 71cc6f08e130fe4a97604924643d13fd341a5625
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304162"
---
# <a name="implement-executionstate"></a>Implementieren von ExecutionState

Die Übergabe von Informationen an das MIP SDK zum Berechnen einer Aktion, die basierend auf dem aktuellen oder gewünschten Status ausgeführt werden soll, wird über die `mip::ExecutionState`-Klasse implementiert. Wie andere Klassen im SDK ist `ExecutionState` eine abstrakte Klasse und muss durch den Entwickler implementiert werden.

> Ein vollständiges Beispiel für eine `ExecutionState`-Implementierung finden Sie im folgenden Beispielcode:
>
> * [execution_state_impl.h](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h)
> * [execution_state_impl.cpp](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.cpp)

## <a name="mipexecutionstate-members"></a>mip::ExecutionState-Member

`ExecutionState` macht die folgenden virtuellen Member verfügbar. Jedes stellt einen Kontext für die Richtlinien-Engine bereit, um Informationen darüber zurückzugeben, welche Aktionen von der Anwendung ausgeführt werden sollten. Darüber hinaus können diese Informationen verwendet werden, um Überwachungsinformationen für die Berichterstellungsfunktion von Azure Information Protection Reporting bereitzustellen.


| Mitglied                                                                           | Gibt zurück                                                                                                              |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `std::string GetNewLabelId()`                                                      | Gibt die Bezeichnungs-ID zurück, die auf das Objekt angewendet werden soll.                                                                    |
| `mip::ContentState GetContentState()`                                              | Gibt das „mip::ContentState“-Element des Objekts zurück.                                                                         |
| `std::pair<bool, std::string> IsDowngradeJustified()`                              | Gibt ein „std::pair“-Element zurück, das ausdrückt, ob ein Herabstufen gerechtfertigt ist, und das die Begründung enthält.                                 |
| `std::string GetContentIdentifier()`                                               | Gibt den Inhaltsbezeichner zurück. Sollte ein lesbarer Bezeichner sein, der den Speicherort des Objekts angibt.   |
| `mip::ActionSource GetNewLabelActionSource()`                                      | Gibt das „mip::ActionSource“-Element der Bezeichnung zurück.                                                                          |
| `mip::AssignmentMethod GetNewLabelAssignmentMethod()`                              | Gibt das „mip::AssignmentMethod“-Element der Bezeichnung zurück.                                                                        |
| `std::vector<std::pair<std::string, std::string>> GetNewLabelExtendedProperties()` | Gibt ein „std::vector“-Element von „std::pairs“ von Zeichenfolgen zurück, die benutzerdefinierte Metadaten enthalten, die auf das Dokument angewendet werden. |
| `std::vector<std::pair<std::string, std::string>> GetContentMetadata()`            | Gibt ein „std::vector“-Element von „std::pairs“ einer Zeichenfolge zurück, die die aktuellen Inhaltsmetadaten enthält.                               |
| `std::shared_ptr<mip::ProtectionDescriptor> GetProtectionDescriptor()`           | Gibt einen Zeiger auf ein „mip::ProtectionDescriptor“-Element zurück.                                                                     |
| `mip::ContentFormat GetContentFormat()`                                            | Gibt ein „mip::ContentFormat“-Element zurück.                                                                                           |
| `mip::ActionType GetSupportedActions()`                                           | Gibt ein „mip::ActionTypes“-Element für die Bezeichnung zurück.                                                                              |

Jedes muss in einer Implementierung von einer aus `mip::ExecutionState` abgeleiteten Klasse außer Kraft gesetzt werden. In der Beispielanwendung unter dem oben angegebenen Link erfolgt dieser Prozess durch die Implementierung einer Struktur namens `ExecutionStateOptions` und deren Übergabe an den Konstruktor der abgeleiteten Klasse.

Im [Beispiel](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h) ist eine Struktur namens `ExecutionStateOptions` wie folgt definiert:

```cpp
struct ExecutionStateOptions {
    std::unordered_map<std::string, std::string> metadata;
    std::string newLabelId;
    std::string contentIdentifier;
    mip::ActionSource actionSource = mip::ActionSource::MANUAL;
    mip::ContentState contentState = mip::ContentState::REST;
    mip::AssignmentMethod assignmentMethod = mip::AssignmentMethod::STANDARD;
    bool isDowngradeJustified = false;
    std::string downgradeJustification;
    std::string templateId;
    mip::ContentFormat contentFormat = mip::ContentFormat::DEFAULT;
};
```

Jede Eigenschaft wird durch die Anwendung festgelegt. Dann wird `ExecutionStateOptions` an den Konstruktor der aus `mip::ExecutionState` abgeleiteten Klasse übergeben. Anhand dieser Informationen wird bestimmt, welche Aktionen ausgeführt werden sollen. In der `mip::ExecutionState`-Klasse enthaltene Daten werden ebenfalls in der Azure Informationen Protection-Analyse angezeigt.

### <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie, wie ein, um zu bestimmen, [compute-Aktionen für eine neue oder vorhandene Bezeichnung](concept-handler-policy-computeactions-cpp.md)basierend auf den aktuellen und dem gewünschten Zustand.
- Herunterladen der [API API Management-Richtlinienbeispiele aus GitHub, und versuchen Sie die Richtlinie-API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)