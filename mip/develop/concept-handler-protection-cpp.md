---
title: Konzepte – ProtectionHandler im Microsoft Information Protection SDK
description: Dieser Artikel erläutert, wie Schutz-API-Handler erstellt und für Aufrufe verwendet werden.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 892e492351d3779667629ff4522891bb527fd782
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556162"
---
# <a name="microsoft-information-protection-sdk---protection-handler-concepts"></a>Microsoft Information Protection SDK – ProtectionHandler-Konzepte

Die Schutz-API des Microsoft Information Protection SDKs (MSIP SDK) macht `mip::ProtectionHandler` die Funktionen zum Verschlüsseln und Entschlüsseln geschützter Streams und Puffer verfügbar, führt Zugriffsprüfungen aus, ruft die Veröffentlichungslizenz und Attribute aus geschützten Informationen ab.

## <a name="requirements"></a>Anforderungen

Folgende Voraussetzungen gelten für das Erstellen eines `ProtectionHandler`-Elements für eine bestimmte Datei:

- Ein `mip::MipContext`-Element.
- Ein `mip::ProtectionProfile`-Element.
- Ein `mip::ProtectionEngine`-Element, dass `ProtectionProfile` hinzugefügt wurde.
- Eine Klasse, die `mip::ProtectionHandler::Observer`erbt.
- Ein `mip::ProtectionDescriptor`-Element oder eine Veröffentlichungslizenz

## <a name="create-a-protection-handler"></a>Erstellen eines ProtectionHandler-Elements

`mip::ProtectionHandler`-Objekte werden erstellt, indem entweder ein `ProtectionDescriptor`-Element oder eine serialisierte Veröffentlichungslizenz für eine von zwei `ProtectionEngine`-Funktionen bereitgestellt wird. „ProtectionDescriptor“ muss zum Schutz von Klartextinformationen generiert werden, die noch über keine Veröffentlichungslizenz verfügen. Die **Veröffentlichungslizenz** wird verwendet, wenn bereits geschützte Inhalte entschlüsselt oder Inhalte geschützt werden, deren Lizenz bereits erstellt wurde. Geschützte Inhalte können nicht ohne die entsprechende Veröffentlichungslizenz entschlüsselt werden.

`mip::ProtectionEngine` stellt zwei Funktionen zum Erstellen eines `ProtectionHandler`-Elements bereit. Die Parameter sind identisch, mit Ausnahme des Handlers bzw. der Veröffentlichungslizenz als erster Parameter.

- `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync`
  - Erfordert ein `ProtectionDescriptor`-Element als ersten Parameter
- `mip::ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync`
  - Erfordert eine serialisierte Veröffentlichungslizenz, die in `std::vector<unint8_t>` als erster Parameter gespeichert ist

### <a name="create-from-descriptor"></a>Erstellen über den Deskriptor

Wenn Sie noch nicht geschützte Inhalte schützen oder einen neuen Schutz auf Inhalte anwenden (setzt vorheriges Entschlüsseln voraus), muss ein `mip::ProtectionDescriptor`-Element erstellt werden. Nach dem Erstellen wird das Element an `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync()` übergeben, und das Ergebnis wird über `mip::ProtectionHandler::Observer` zurückgegeben.

```cpp
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();
auto observer = std::make_shared<ProtectionHandlerObserverImpl>();

//Refer to ProtectionDescriptor docs for details on creating the descriptor
auto descriptor = CreateProtectionDescriptor(); //Stub function

mEngine->CreateProtectionHandlerFromDescriptorAsync(
    descriptor,
    mip::ProtectionHandlerCreationOptions::None,
    observer,
    handlerPromise);

auto handler = handlerFuture.get();
```

Wenn das `ProtectionHandler`-Objekt erfolgreich erstellt wurde, können Dateivorgänge („Get“/„Set“/„Delete“/„Commit“) ausgeführt werden.

### <a name="create-from-publishing-license"></a>Erstellen über die Veröffentlichungslizenz

In diesem Beispiel wird davon ausgegangen, dass die Veröffentlichungslizenz bereits aus einer Quelle gelesen und in `std::vector<uint8_t> serializedPublishingLicense` gespeichert wurde.

```cpp

//TODO: Implement GetPublishingLicense()
//Snip implies that function reads PL from source file, database, stream, etc.
std::vector<uint8_t> serializedPublishingLicense = GetPublishingLicense(filePath);

auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();

shared_ptr<ProtectionHandlerObserverImpl> handleObserver =
    std::make_shared<ProtectionHandlerObserverImpl>();

mEngine->CreateProtectionHandlerFromPublishingLicenseAsync(
    serializedPublishingLicense,
    mip::ProtectionHandlerCreationOptions::None,
    handleObserver,
    handlerPromise);

auto handler = handlerFuture.get();
```

