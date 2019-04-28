---
title: 'Konzepte: Beobachter der Datei-API im MIP SDK'
description: Das MIP SDK ist so konzipiert, dass es beinahe vollständig asynchron ist. In diesem Artikel erfahren Sie, wie Beobachter von Datei-APIs implementiert und mit dem Ziel der Asynchronität verwendet werden.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: baa62e34e10de3fb4cacc3eb7cb21c0b3e2ebf75
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60175444"
---
# <a name="microsoft-information-protection-sdk---file-api-observers"></a>Microsoft Information Protection SDK: Beobachter von Datei-APIs

Die Datei-API enthält zwei Observer-Klassen. Die Member der Observer-Klasse befinden sich auf virtueller Ebene und können überschrieben werden, um Ereignisrückrufe zu verarbeiten.

- [`mip::FileProfile::Observer`](reference/class_mip_fileprofile_observer.md)
- [`mip::FileHandler::Observer`](reference/class_mip_filehandler_observer.md)

Wenn ein asynchroner Vorgang abgeschlossen wird, wird die Memberfunktion `OnXxx()` aufgerufen, die dem Ergebnis entspricht. Z.B.: `OnLoadSuccess()`, `OnLoadFailure()` und `OnAddEngineSuccess()` für `mip::FileProfile::Observer`.

Im nachfolgenden Beispiel wird das Promise-Future-Muster dargestellt. Dieses wird ebenfalls von SDK-Beispielen verwendet und kann erweitert werden, sodass das gewünschte Rückrufverhalten implementieren werden kann. 

## <a name="file-profile-observer-implementation"></a>Implementieren des Dateiprofilbeobachters

Im folgenden Beispiel wurde die Klasse `ProfileObserver` erstellt, die von `mip::FileProfile::Observer` abgeleitet wurde. Die Memberfunktionen wurden überschrieben, um das Promise-Future-Muster anzuwenden, das in allen Beispielen verwendet wird.

**Hinweis**: Die folgenden Beispiele werden nur teilweise implementiert und enthalten keine Außerkraftsetzungen für die `mip::FileEngine` Observer-Objekte beziehen.

### <a name="profileobserverh"></a>profile_observer.h

Im Header wird zunächst die `ProfileObserver`-Klasse definiert, die von `mip::FileProfile::Observer` abgeleitet wird, und anschließend werden die einzelnen Memberfunktionen überschrieben.

```cpp
class ProfileObserver final : public mip::FileProfile::Observer {
public:
ProfileObserver() { }
  void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) override;
  void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
  //TODO: Implement mip::FileEngine related observers.
};
```

### <a name="profileobservercpp"></a>profile_observer.cpp

In der eigentlichen Implementierung wird eine Aktion definiert, die für jede Memberfunktion der Observer-Klasse ausgeführt werden soll.

Jeder Member akzeptiert zwei Parameter. Bei dem ersten Parameter handelt es sich um einen gemeinsamen Zeiger auf die Klasse, die in der Funktion verarbeitet wird. `ProfileObserver::OnLoadSuccess` erwartet dabei den Empfang einer `mip::FileProfile`-Klasse. `ProfileObserver::OnAddEngineSuccess` erwartet hingegen den Empfang einer `mip::FileEngine`-Klasse.

Bei dem zweiten Parameter handelt es sich um einen gemeinsamen Zeiger auf den *context*. In diesem Beispiel stellt der Kontext einen Verweis auf ein `std::promise`-Objekt dar, das je nach Verweis als `std::shared_ptr<void>` übergeben wird. Die erste Zeile der Funktion wandelt dies in das `std::promise` um, das dann in einem Objekt mit dem Namen `promise` gespeichert wird.

Letztendlich wird das Future des Promise-Future-Musters bereitgestellt, indem der Wert `promise->set_value()` festgelegt und das `mip::FileProfile`-Objekt übergeben wird.

```cpp
#include "profile_observer.h"
#include <future>

//Called when FileProfile is successfully loaded
void ProfileObserver::OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) {
  //cast context to promise
  auto promise = 
  std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileProfile>>>(context);
  //set promise value to profile
  promise->set_value(profile);
}

//Called when FileProfile fails to load
void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileProfile>>>(context);
  promise->set_exception(error);
}

//TODO: Implement mip::FileEngine related observers.
```

Wenn eine SDK-Klasse instanziiert oder eine Funktion verwendet wird, die asynchrone Vorgänge ausführt, wird die Implementierung der Observer-Klasse entweder an den Einstellungskonstruktor oder an die asynchrone Funktion selbst übergeben. Wenn das `mip::FileProfile::Settings`-Objekt instanziiert wird, übernimmt der Konstruktor `mip::FileProfile::Observer` als einen der Parameter. Im nachfolgenden Beispiel sehen Sie, wie das benutzerdefinierte `ProfileObserver`-Objekt in einem `mip::FileProfile::Settings`-Konstruktor verwendet wird.

## <a name="filehandler-observer-implementation"></a>Implementieren des FileHandler-Beobachters

Ähnlich wie der Profilbeobachter implementiert auch `mip::FileHandler` eine `mip::FileHandler::Observers`-Klasse zum Verarbeiten von asynchronen Ereignisbenachrichtigungen im Rahmen von Dateivorgängen. Die Implementierung ist der oben beschriebenen Implementierung ähnlich. `FileHandlerObserver` wird nachfolgend teilweise definiert. 

### <a name="filehandlerobserverh"></a>file_handler_observer.h

```cpp
#include "mip/file/file_handler.h"

class FileHandlerObserver final : public mip::FileHandler::Observer {
public:
  void OnCreateFileHandlerSuccess(
      const std::shared_ptr<mip::FileHandler>& fileHandler,
      const std::shared_ptr<void>& context) override;

  void OnCreateFileHandlerFailure(
      const std::exception_ptr& error,
      const std::shared_ptr<void>& context) override;

  //TODO: override remaining member functions inherited from mip::FileHandler::Observer
};
```

### <a name="filehandlerobservercpp"></a>file_handler_observer.cpp

In diesem Beispiel werden zwar nur die ersten beiden Funktionen dargestellt, aber die übrigen Funktionen verwenden ein ähnliches Muster, auch für `ProfileObserver`.

```cpp
#include "file_handler_observer.h"

void FileHandlerObserver::OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) {
    auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
    promise->set_value(fileHandler);
}

void FileHandlerObserver::OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
    auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
    promise->set_exception(error);
}

//TODO: override remaining member functions inherited from mip::FileHandler::Observer
```

