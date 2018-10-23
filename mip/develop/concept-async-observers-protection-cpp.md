---
title: 'Konzepte: Observer-Objekte der Protection-API im MIP SDK'
description: Das MIP SDK ist so konzipiert, dass es beinahe vollständig asynchron ist. In diesem Artikel erfahren Sie, wie Observer-Objekte der Protection-API implementiert und mit dem Ziel der Asynchronität verwendet werden.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: d7077678ba336b031f7a8f812a3c4e90d8c5b05a
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251708"
---
# <a name="microsoft-information-protection-sdk---protection-api-observers"></a>Microsoft Information Protection SDK: Observer-Objekte der Protection-API

Die Protection-API enthält drei Observer-Klassen. Die Member der Observer-Klasse befinden sich auf virtueller Ebene und können überschrieben werden, um Rückrufe für asynchrone Vorgänge zu verarbeiten.

- [Protection-Profil: `mip::ProtectionProfile::Observer`](reference/class_mip_ProtectionProfile_observer.md)
- [Protection-Engine: `mip::ProtectionEngine::Observer`](reference/class_mip_ProtectionEngine_observer.md)
- [Protection-Handler: `mip::ProtectionHandler::Observer`](reference/class_mip_Protectionhandler_observer.md)

Wenn ein asynchroner Vorgang abgeschlossen wird, wird die `OnXxx()`-Memberfunktion aufgerufen, die dem Ergebnis entspricht. Beispiele sind `OnLoadSuccess()`, `OnLoadFailure()` und `OnAddEngineSuccess()` für `mip::ProtectionProfile::Observer`.

Im nachfolgenden Beispiel wird das Promise/Future-Muster dargestellt. Dieses wird ebenfalls von SDK-Beispielen verwendet und kann erweitert werden, sodass das gewünschte Rückrufverhalten implementieren werden kann. 

## <a name="protection-protection-observer-implementation"></a>Protection: Implementierung des Observer-Objekts der Protection-API

Im folgenden Beispiel wurde eine Klasse (`ProtectionProfileObserverImpl`) erstellt, die von `mip::ProtectionProfile::Observer` abgeleitet ist. Die Memberfunktionen wurden überschrieben, um das Promise-/Future-Muster zu verwenden, das in allen Beispielen verwendet wird.

### <a name="protectionprofileobserverimpl-class-declaration"></a>ProtectionProfileObserverImpl-Klassendeklaration

Im Header wird zunächst die `ProtectionProfileObserverImpl`-Klasse definiert, die von `mip::ProtectionProfile::Observer` abgeleitet ist, und anschließend werden die einzelnen Memberfunktionen überschrieben.

```cpp
//ProtectionProfileObserverImpl.h
class ProtectionProfileObserverImpl final : public mip::ProtectionProfile::Observer {
public:
  ProtectionProfileObserverImpl() { }
  void OnLoadSuccess(const shared_ptr<mip::ProtectionProfile>& profile, const shared_ptr<void>& context) override;
  void OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) override;
  void OnAddEngineSuccess(const shared_ptr<mip::ProtectionEngine>& engine, const shared_ptr<void>& context) override;
  void OnAddEngineError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionprofileobserverimpl-implementation"></a>ProtectionProfileObserverImpl-Implementierung

In der eigentlichen Implementierung wird einfach eine Aktion definiert, die für jede Memberfunktion der Observer-Klasse ausgeführt werden soll.

Jeder Member akzeptiert zwei Parameter. Bei dem ersten Parameter handelt es sich um einen gemeinsamen Zeiger auf die Klasse, die in der Funktion verarbeitet wird. `ProtectionObserver::OnLoadSuccess` erwartet dabei den Empfang einer `mip::ProtectionProtection`-Klasse, `ProtectionObserver::OnAddEngineSuccess` erwartet `mip::ProtectionEngine`.

Bei dem zweiten Parameter handelt es sich um einen gemeinsamen Zeiger auf den *Kontext*. In diesem Beispiel stellt der Kontext einen Verweis auf ein `std::promise`-Element dar, das als `shared_ptr<void>` übergeben wird. Die erste Zeile der Funktion wandelt dies in `std::promise` um, Dieses Element wird dann in einem Objekt mit dem Namen `promise` gespeichert.

Schließlich wird der Future-Aspekt des Future/Promise-Musters bereitgestellt, indem der Wert `promise->set_value()` festgelegt und das `mip::ProtectionProtection`-Objekt übergeben wird.

```cpp
//protection_observers.cpp

void ProtectionProfileObserverImpl::OnLoadSuccess(
  const shared_ptr<mip::ProtectionProfile>& profile,
  const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_value(profile);
};

void ProtectionProfileObserverImpl::OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_exception(error);
};

void ProtectionProfileObserverImpl::OnAddEngineSuccess(
  const shared_ptr<mip::ProtectionEngine>& engine,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_value(engine);
};

void ProtectionProfileObserverImpl::OnAddEngineError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_exception(error);
};
```

Wenn eine SDK-Klasse instanziiert oder eine Funktion verwendet wird, die asynchrone Vorgänge ausführt, wird die Implementierung der Observer-Klasse entweder an den Einstellungskonstruktor oder an die asynchrone Funktion selbst übergeben. Wenn das `mip::ProtectionProfile::Settings`-Objekt instanziiert wird, nimmt der Konstruktor `mip::ProtectionProfile::Observer` als einen der Parameter an. Im nachfolgenden Beispiel sehen Sie, wie das benutzerdefinierte `ProtectionProfileObserverImpl`-Objekt in einem `mip::ProtectionProfile::Settings`-Konstruktor verwendet wird.

## <a name="protectionhandler-observer-implementation"></a>Implementierung des ProtectionHandler-Beobachters

Ähnlich wie der Protection-Beobachter implementiert auch `mip::ProtectionHandler` eine `mip::ProtectionHandler::Observer`-Klasse zum Verarbeiten von asynchronen Ereignisbenachrichtigungen im Rahmen von Schutzvorgängen. Die Implementierung ist der oben beschriebenen Implementierung ähnlich. `ProtectionHandlerObserverImpl` wird nachfolgend teilweise definiert. Die vollständige Implementierung finden Sie in unserem [GitHub-Beispielrepository](https://azure.microsoft.com/resources/samples/?sort=0&term=mip+sdk).

### <a name="protectionhandlerobserverimpl-class-declaration"></a>ProtectionHandlerObserverImpl-Klassendeklaration

```cpp
//protection_observers.h

class ProtectionHandlerObserverImpl final : public mip::ProtectionHandler::Observer {
public:
  ProtectionHandlerObserverImpl() { }
  void OnCreateProtectionHandlerSuccess(const shared_ptr<mip::ProtectionHandler>& protectionHandler, const shared_ptr<void>& context) override;
  void OnCreateProtectionHandlerError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionhandlerobserverimpl-partial-implementation"></a>ProtectionHandlerObserverImpl-Teilimplementierung

In diesem Beispiel werden zwar nur die ersten beiden Funktionen dargestellt, aber die übrigen Funktionen verwenden ein ähnliches Muster, auch für `ProtectionObserver`.

```cpp
//protection_observers.cpp

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerSuccess(
  const shared_ptr<mip::ProtectionHandler>& protectionHandler,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_value(protectionHandler);
};

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_exception(error);
};
```

