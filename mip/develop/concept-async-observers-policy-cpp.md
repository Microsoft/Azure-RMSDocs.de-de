---
title: 'Konzepte: Beobachter der Richtlinien-API im MIP SDK'
description: Das MIP SDK ist so konzipiert, dass es beinahe vollständig asynchron ist. In diesem Artikel erfahren Sie, wie Beobachter von Richtlinien-APIs implementiert und mit dem Ziel der Asynchronität verwendet werden.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: db2926809ccd7d29628a2b729ce59879e6e513fd
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75555890"
---
# <a name="microsoft-information-protection-sdk---policy-api-observers"></a>Microsoft Information Protection SDK: Beobachter von Richtlinien-APIs

Das SDK für die Richtlinien-API enthält eine Observer-Klasse. Die Member der Observer-Klasse befinden sich auf virtueller Ebene und sollten überschrieben werden, um Rückrufe für asynchrone Vorgänge zu verarbeiten.

- [`mip::PolicyProfile::Observer`](reference/class_mip_policyprofile_observer.md)

Wenn ein asynchroner Vorgang abgeschlossen wird, wird die `OnXxx()`-Memberfunktion aufgerufen, die dem Ergebnis entspricht. Z.B.: `OnLoadSuccess()`, `OnLoadFailure()` und `OnAddEngineSuccess()` für `mip::Profile::Observer`.

Im nachfolgenden Beispiel wird das Promise/Future-Muster dargestellt. Dieses wird ebenfalls von SDK-Beispielen verwendet und kann erweitert werden, sodass das gewünschte Rückrufverhalten implementieren werden kann. 

## <a name="profile-observer-implementation"></a>Implementieren des Profilbeobachters

Im folgenden Beispiel wurde eine Klasse (`ProfileObserver`) erstellt, die von `mip::Profile::Observer` abgeleitet ist. Die Memberfunktionen wurden überschrieben, um das Promise-Future-Muster anzuwenden, das in allen Beispielen verwendet wird.

**Hinweis:** Die nachfolgenden Beispiele wurden nur teilweise implementiert und beinhalten keine Überschreibungen der mit `mip::ProfileEngine` in Verbindung stehenden Beobachter.

### <a name="profile_observerh"></a>profile_observer.h

Im Header wird zunächst die `ProfileObserver`-Klasse definiert, die von `mip::Profile::Observer` abgeleitet ist, und anschließend werden die einzelnen Memberfunktionen überschrieben.

```cpp
class ProfileObserver final : public mip::Profile::Observer {
public:
ProfileObserver() { }
  void OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) override;
  void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
  //TODO: Implement remaining members
};
```

### <a name="profile_observercpp"></a>profile_observer.cpp

In der eigentlichen Implementierung wird eine Aktion definiert, die für jede Memberfunktion der Observer-Klasse ausgeführt werden soll.

Jeder Member akzeptiert zwei Parameter. Bei dem ersten Parameter handelt es sich um einen gemeinsamen Zeiger auf die Klasse, die von der Funktion verarbeitet wird. `ProfileObserver::OnLoadSuccess` erwartet dabei den Empfang einer `mip::Profile`-Klasse. `ProfileObserver::OnAddEngineSuccess` erwartet hingegen den Empfang einer `mip::ProfileEngine`-Klasse.

Bei dem zweiten Parameter handelt es sich um einen gemeinsamen Zeiger auf den *Kontext*. In diesem Beispiel stellt der Kontext einen Verweis auf ein `std::promise`-Element dar, das als `shared_ptr<void>` übergeben wird. Die erste Zeile der Funktion wandelt dies in `std::promise` um. Dieses Element wird dann in einem Objekt mit dem Namen `promise` gespeichert.

Letztendlich wird das Future des Promise-Future-Musters bereitgestellt, indem der Wert `promise->set_value()` festgelegt und das `mip::Profile`-Objekt übergeben wird.

```cpp
#include "profile_observer.h"
#include <future>

//Called when Profile is successfully loaded
void ProfileObserver::OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) {
  //cast context to promise
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  //set promise value to profile
  promise->set_value(profile);
}

//Called when Profile fails to load
void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  promise->set_exception(error);
}

//TODO: Implement remaining observer members
```

Wenn ein beliebiger asynchroner Vorgang ausgeführt wird, wird die Observer-Implementierung an den Einstellungskonstruktor oder die asynchrone Funktion selbst übergeben. 

