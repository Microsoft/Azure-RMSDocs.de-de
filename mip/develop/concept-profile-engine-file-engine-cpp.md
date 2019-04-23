---
title: 'Konzepte: Das Engine-Objekt der File-API'
description: In diesem Artikel werden die Konzepte des Engine-Objekts der File-API erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: fcdcb5c11646fd7d32284b6df31cda33abbfde4a
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60175512"
---
# <a name="microsoft-information-protection-sdk---file-api-engine-concepts"></a>Microsoft Information Protection SDK: Konzepte für das Engine-Objekt der File-API

Die `mip::FileEngine` in der File-API des MIP SDK stellt eine Schnittstelle für alle Vorgänge bereit, die im Auftrag einer bestimmten Identität ausgeführt werden. Für jeden Benutzer, der sich bei der Anwendung anmeldet, wird eine Engine hinzugefügt, und alle Vorgänge, die die Engine ausführt, werden im Kontext dieser Identität ausgeführt.

Die `FileEngine` hat zwei primäre Aufgaben: Auflisten von Bezeichnungen für einen authentifizierten Benutzer aus, und erstellen Datei-Ereignishandler, um die Dateivorgänge im Auftrag des Benutzers ausführen. 

- [`mip::FileEngine`](reference/class_mip_fileengine.md)
- `ListSensitivityLabels()`: Ruft die Liste der Bezeichnungen für das geladene Modul ab.
- `CreateFileHandler()`: Erstellt eine `mip::FileHandler` für eine bestimmte Datei oder einen Stream.

## <a name="add-a-file-engine"></a>Hinzufügen einer Dateiengine

Wie unter [Profile- und Engine-Objekte](concept-profile-engine-cpp.md) beschrieben wurde, kann ein Modul zwei Zustände aufweisen: `CREATED` oder `LOADED`. Wenn es nicht einen dieser beiden Zustände aufweist, ist es nicht vorhanden. Um einen Zustand zu erstellen und zu laden, ist nur ein einziger Aufruf von `FileProfile::LoadAsync` erforderlich. Wenn die Engine im zwischengespeicherten Zustand bereits vorhanden ist, geht sie in den Zustand `LOADED` über. Wenn sie nicht vorhanden ist, wird sie `CREATED` und `LOADED`. `CREATED` bedeutet, dass die Anwendung über alle Informationen aus dem Dienst verfügt, die zum Laden der Engine benötigt werden. `LOADED` bedeutet, dass alle für die Nutzung der Engine notwendigen Datenstrukturen im Speicher erstellt wurden.

### <a name="create-file-engine-settings"></a>Erstellen der Dateiengineeinstellungen

Ähnlich wie bei einem Profil erfordert auch die Engine ein Einstellungsobjekt (`mip::FileEngine::Settings`). In diesem Objekt werden der eindeutige Bezeichner der Engine, anpassbare Clientdaten, die zum Debuggen oder für die Telemetrie verwendet werden können, und optional auch das Gebietsschema gespeichert.

Im folgenden Beispiel wird ein `FileEngine::Settings`-Objekt mit dem Namen *engineSettings* erstellt. 

```cpp
FileEngine::Settings engineSettings("UniqueID", "");
```

Als bewährte Methode sollte der erste Parameter (`id`) erlauben, dass ganz einfach eine Verbindung zwischen der Engine und dem zugewiesenen Benutzer hergestellt werden kann. Eine Angabe wie etwa die E-Mail-Adresse, der UPN oder eine AAD-Objekt-GUID würde sicherstellen, dass die ID sowohl eindeutig ist als auch aus dem lokalen Zustand geladen werden kann, ohne den Dienst aufzurufen.

### <a name="add-the-file-engine"></a>Hinzufügen der Dateiengine

Damit Sie die Engine hinzufügen können, müssen Sie erneut das Promise-/Future-Muster berücksichtigen, das zum Laden des Profils verwendet wurde. Anstatt das Versprechen für `mip::FileProfile` zu erstellen, wird es mit `mip::FileEngine` erstellt.

```cpp
  //auto profile will be std::shared_ptr<mip::FileProfile>
  auto profile = profileFuture.get();

  //Create the FileEngine::Settings object
  FileEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::FileEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::FileEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::FileEngine>
  auto engine = engineFuture.get();
```

Das Endergebnis des obigen Codes ist, dass die Engine für den authentifizierten Benutzer dem Profil hinzugefügt wird.

## <a name="list-sensitivity-labels"></a>Auflisten der Vertraulichkeitsbezeichnungen

Unter Verwendung der hinzugefügten Engine ist es jetzt möglich, sämtliche Vertraulichkeitsbezeichnungen aufzulisten, die dem authentifizierten Benutzer zur Verfügung stehen, indem `engine->ListSensitivityLabels()` aufgerufen wird.

`ListSensitivityLabels()` ruft die Liste mit Bezeichnungen und Attributen dieser Bezeichnungen für einen bestimmten Benutzer aus dem Dienst ab. Das Ergebnis wird in einem Vektor von `std::shared_ptr<mip::Label>` gespeichert.

Weitere Informationen zu `mip::Label` finden Sie [hier]().

### <a name="listsensitivitylabels"></a>ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

Oder in vereinfachter Form:

```cpp
auto labels = engine->ListSensitivityLabels();
```

### <a name="print-the-labels-and-ids"></a>Ausgeben der Bezeichnungen und IDs

Die Ausgabe der Namen stellt eine einfache Möglichkeit dar, um zu zeigen, dass dem Dienst erfolgreich eine Richtlinie entnommen wurde und die Bezeichnungen abgerufen werden konnten. Um die Bezeichnung anzuwenden, ist die Bezeichnungs-ID erforderlich. Der folgende Code durchläuft alle Bezeichnungen und zeigt die Angaben `name` und `id` für jede übergeordnete und untergeordnete Bezeichnung an.

```cpp
//Iterate through all labels in the vector
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

## <a name="next-steps"></a>Nächste Schritte

Da das Profil nun geladen und die Engine hinzugefügt wurde und wir über Bezeichnungen verfügen, können wir einen Handler hinzufügen, um mit dem Lesen, Schreiben oder Entfernen von Bezeichnungen aus Dateien zu beginnen. Siehe [Dateihandler im MIP SDK](concept-handler-file-cpp.md).

