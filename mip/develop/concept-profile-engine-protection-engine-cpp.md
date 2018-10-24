---
title: 'Konzepte: das Engine-Objekt der Schutz-API'
description: In diesem Artikel werden die Konzepte des Engine-Objekts für den Schutz erläutert, das während der Anwendungsinitialisierung erstellt wird.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: da0c50de6a818fcd8beda0483696ba433ce22149
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453315"
---
# <a name="microsoft-information-protection-sdk---protection-api-engine-concepts"></a>Microsoft Information Protection SDK: Engine-Konzepte für die Schutz-API

## <a name="implementation-add-a-protection-engine"></a>Implementierung: Hinzufügen einer Schutz-Engine

In der Datei-API stellt die Klasse `mip::ProtectionProfile` die Stammklasse für sämtliche SDK-Vorgänge dar. Da Sie bereits das Profil erstellt haben, können Sie nun eine Engine zu diesem hinzufügen.

Im nachfolgenden Beispiel wird die Verwendung einer einzelnen Engine für einen einzelnen authentifizierten Benutzer veranschaulicht.

### <a name="implementation-create-protection-engine-settings"></a>Implementierung: Erstellen von Einstellungen für die Schutz-Engine

Ähnlich wie bei einem Profil erfordert auch die Engine ein Einstellungsobjekt (`mip::ProtectionEngine::Settings`). In diesem Objekt werden der eindeutige Bezeichner der Engine, anpassbare Clientdaten, die zum Debuggen oder für die Telemetrie verwendet werden können, und optional auch das Gebietsschema gespeichert.

Im folgenden Beispiel wird ein `ProtectionEngine::Settings`-Objekt mit dem Namen *engineSettings* erstellt. 

```cpp
ProtectionEngine::Settings engineSettings("UniqueID", "");
```

**Hinweis:** Wenn Sie auf diese Methode zurückgreifen, um ein Objekt für die Schutzeinstellungen zu erstellen, müssen Sie manuell CloudEndpointBaseUrl auf https://api.aadrm.com festlegen.

Als bewährte Methode sollte der erste Parameter (**id**) erlauben, dass ganz einfach eine Verbindung zwischen der Engine und dem zugewiesenen Benutzer hergestellt werden kann, **oder** es sollte sich um ein `mip::Identity`-Objekt handeln. Gehen Sie wie folgt vor, um die Einstellungen mit `mip::Identity` zu initialisieren:

```cpp
ProtectionEngine::Settings engineSettings(mip::Identity("Bob@Contoso.com", "");
```

Allerdings wird in der Regel eine Variable an die Identität übergeben und keine Hartcodierung vorgenommen.

### <a name="implementation-add-the-protection-engine"></a>Implementierung: Hinzufügen der Schutz-Engine

Damit Sie die Engine hinzufügen können, müssen Sie erneut das Promise-Future-Muster berücksichtigen, das zum Laden des Profils verwendet wurde. In diesem Beispiel wird nicht das Promise für `mip::ProtectionProfile` erstellt, sondern `mip::ProtectionEngine` verwendet.

```cpp

  //auto profile will be std::shared_ptr<mip::ProtectionProfile>
  auto profile = profileFuture.get();

  //Create the ProtectionEngine::Settings object
  ProtectionEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::ProtectionEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::ProtectionEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::ProtectionEngine>
  auto engine = engineFuture.get();
```

Mithilfe des obenstehenden Codes wurde erfolgreich eine Engine für den authentifizierten Benutzer zum Profil hinzugefügt.

## <a name="implementation-list-templates"></a>Implementierung: Auflisten von Vorlagen

Unter Verwendung der hinzugefügten Engine ist es jetzt möglich, sämtliche Vertraulichkeitsvorlagen aufzulisten, die dem authentifizierten Benutzer zur Verfügung stehen, indem `engine->GetTemplatesAsync()` aufgerufen wird. 

`GetTemplatesAsync()` ruft die Liste mit Vorlagenbezeichnern ab. Das Ergebnis wird in einem Vektor von `std::shared_ptr<std::string>` gespeichert.

### <a name="implementation-listsensitivitytemplates"></a>Implementierung: ListSensitivityTemplates()

```cpp
auto loadPromise = std::make_shared<std::promise<shared_ptr<vector<string>>>>();
std::future<std::shared_ptr<std::vector<std::string>>> loadFuture = loadPromise->get_future();
mEngine->GetTemplatesAsync(engineObserver, loadPromise);
auto templates = loadFuture.get();
```

### <a name="implementation-print-the-template-ids"></a>Implementierung: Ausgeben der Vorlagen-IDs

```cpp
//Iterate through all template IDs in the vector
for (const auto& temp : *templates) {
  cout << "Template:" << "\n\tId: " << temp << endl;
}
```

Die Ausgabe der Namen stellt eine einfache Möglichkeit dar, um zu zeigen, dass dem Dienst erfolgreich eine Richtlinie entnommen wurde und die Vorlagen abgerufen werden konnten. Der Vorlagenbezeichner wird zum Anwenden der Vorlage benötigt.

Sie können Bezeichnungen nur über die Richtlinien-API Vorlagen zuordnen, indem Sie das Ergebnis von `ComputeActions()` untersuchen.

## <a name="next-steps"></a>Nächste Schritte

Da das Profil nun geladen und die Engine hinzugefügt wurde und Sie über Bezeichnungen verfügen, können Sie jetzt einen Handler hinzufügen, um mit dem Lesen, Schreiben oder Entfernen von Vorlagen aus Dateien zu beginnen. Weitere Informationen finden Sie unter [Protection handler concepts (Konzepte des Schutzhandlers)](concept-handler-protection-cpp.md).