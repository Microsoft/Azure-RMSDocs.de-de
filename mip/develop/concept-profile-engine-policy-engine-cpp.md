---
title: 'Konzepte: das Engine-Objekt der Richtlinien-API'
description: In diesem Artikel werden die Konzepte des Engine-Objekts der Richtlinie erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 934fe6e054a6fe2b7f92b869e05d27a834d51366
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75555261"
---
# <a name="microsoft-information-protection-sdk---policy-api-engine-concepts"></a>Microsoft Information Protection SDK: Engine-Konzepte für die Richtlinien-API

`mip::PolicyEngine` implementiert alle Vorgänge, die die Richtlinien-API ausführen kann, mit Ausnahme des Ladens des Profils.

## <a name="implementation-add-a-policy-engine"></a>Implementierung: Hinzufügen einer Richtlinien-Engine

### <a name="implementation-create-policy-engine-settings"></a>Implementierung: Erstellen von Einstellungen für die Richtlinien-Engine

Ähnlich wie bei einem Profil erfordert auch die Engine ein Einstellungsobjekt (`mip::PolicyEngine::Settings`). In diesem Objekt werden der eindeutige Bezeichner der Engine, anpassbare Clientdaten, die zum Debuggen oder für die Telemetrie verwendet werden können, und optional auch das Gebietsschema gespeichert.

Hier erstellen wir ein `FileEngine::Settings` Objekt namens *EngineSettings* mit der Identität des Anwendungs Benutzers:

```cpp
PolicyEngine::Settings engineSettings(
  mip::Identity(mUsername), // mip::Identity.
  "",                       // Client data. Customizable by developer, stored with engine.
  "en-US",                  // Locale.
  false);                   // Load sensitive information types for driving classification.
```

Außerdem ist die Angabe einer benutzerdefinierten Engine-ID gültig:

```cpp
PolicyEngine::Settings engineSettings(
  "myEngineId", // string
  "",           // Client data in string format. Customizable by developer, stored with engine.
  "en-US",      // Locale. Default is en-US
  false);       // Load sensitive information types for driving classification. Default is false.
```

Als bewährte Methode sollte der erste Parameter (**id**) erlauben, dass ganz einfach eine Verbindung zwischen der Engine und dem zugewiesenen Benutzer (am besten dem Benutzerprinzipalnamen) hergestellt werden kann.

### <a name="implementation-add-the-policy-engine"></a>Implementierung: Hinzufügen der Richtlinien-Engine

Damit Sie die Engine hinzufügen können, müssen Sie erneut das Promise-Future-Muster berücksichtigen, das zum Laden des Profils verwendet wurde. In diesem Beispiel wird nicht das Promise für `mip::Profile` erstellt, sondern `mip::PolicyEngine` verwendet.

```cpp

  //auto profile will be std::shared_ptr<mip::Profile>
  auto profile = profileFuture.get();

  //Create the PolicyEngine::Settings object
  PolicyEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::PolicyEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::PolicyEngine>
  auto engine = engineFuture.get();
```

Mithilfe des obenstehenden Codes wurde erfolgreich eine Engine für den authentifizierten Benutzer zum Profil hinzugefügt.

## <a name="implementation-list-sensitivity-labels"></a>Implementierung: Auflisten von Vertraulichkeitsbezeichnungen

Unter Verwendung der hinzugefügten Engine ist es jetzt möglich, sämtliche Vertraulichkeitsbezeichnungen aufzulisten, die dem authentifizierten Benutzer zur Verfügung stehen, indem `engine->ListSensitivityLabels()` aufgerufen wird.

`ListSensitivityLabels()` ruft die Liste mit Bezeichnungen und Attributen dieser Bezeichnungen für einen bestimmten Benutzer aus dem Dienst ab. Das Ergebnis wird in einem Vektor von `std::shared_ptr<mip::Label>` gespeichert.

### <a name="implementation-listsensitivitylabels"></a>Implementierung: ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

### <a name="implementation-print-the-labels"></a>Implementierung: Ausgeben der Bezeichnungen

```cpp
//Iterate through all labels in the vector
for (const auto& label : labels) {
  //print the label name
  cout << label->GetName() << endl;
  //Iterate through all child labels
  for (const auto& child : label->GetChildren()) {
    //Print the label with some formatting
    cout << "->  " << child->GetName() << endl;
  }
}
```

Die Ausgabe der Namen stellt eine einfache Möglichkeit dar, um zu zeigen, dass dem Dienst eine Richtlinie entnommen wurde und die Bezeichnungen abgerufen werden konnten. Sie benötigen einen Bezeichner, um eine Bezeichnung anzuwenden. Wenn Sie den obenstehenden Codeausschnitt bearbeiten, um die Bezeichnungs-ID zurückzugeben, entsteht folgendes Ergebnis:

```cpp
for (const auto& label : labels) {
  //Print label name and GUID
  cout << label->GetName() << " : " << label->GetId() << endl;

  //Print child label name and GUID
  for (const auto& child : label->GetChildren()) {
    cout << "->  " << child->GetName() <<  " : " << child->GetId() << endl;
  }
}
```

Die Sammlung von `mip::Label`, die von `GetSensitivityLabels()` zurückgegeben wird, kann verwendet werden, um zuerst alle verfügbaren Bezeichnungen an den Benutzer zurückzugeben und anschließend ggf. die ID zu verwenden, wenn Bezeichnungen auf eine Datei angewendet werden sollen.
