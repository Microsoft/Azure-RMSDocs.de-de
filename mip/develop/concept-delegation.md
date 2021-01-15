---
title: 'Konzepte: Delegierung'
description: In diesem Artikel erhalten Sie Informationen zu den Konzepten in Bezug auf die Delegierung im MIP SDK.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: tommos
ms.openlocfilehash: 848b0752f6158ade4fd61b562163e2e641454773
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98224946"
---
# <a name="concept---delegation-in-the-mip-sdk"></a>Konzept Delegierung im MIP SDK

Das Microsoft Information Protection SDK bietet zwei Pfade für Dienst basierte Anwendungen, die im Auftrag eines anderen Benutzers agieren. Eine Delegierung ist möglicherweise erforderlich, wenn Dateien im Kontext einer Benutzeridentität, die von der Dienst Identität abweicht, beschriftet, geschützt oder genutzt werden muss. Diese Delegierte Identität kann auf **Engine** -oder **handlerebene** festgelegt werden, und wo Sie festgelegt ist, hängt vom Anwendungsfall ab.

## <a name="engine-settings-based-delegation"></a>Auf Engine-Einstellungen basierende Delegierung

Das MIP-SDK unterstützt die Bereitstellung einer delegierten Benutzer-e-Mail-Adresse im Einstellungs Objekt für alle SDKs. Datei, Schutz und Richtlinie. Dies wird erreicht, indem die- `DelegatedUserEmail` Eigenschaft für das Settings-Objekt festgelegt wird. Das Ergebnis ist, dass die Engine, die mit diesem Einstellungs Objekt initialisiert wird, **alle MIP-Vorgänge** ausführt, als wäre es der Benutzer, der für die Eigenschaft bereitgestellt würde `DelegatedUserEmail` . Die Richtlinie wird für diesen bestimmten Benutzer abgerufen, und alle Schutz Vorgänge werden als dieser Benutzer ausgeführt, einschließlich des Besitzers der geschützten Dateien.

Dieses Muster ist hilfreich, wenn die Dienst basierte Anwendung vollständig als Benutzer ausgeführt werden muss. die Richtlinie muss nur für den angegebenen Benutzer abgerufen werden, und alle Entschlüsselungs Vorgänge müssen im Kontext der Benutzeridentität durchgeführt werden. Beim Erstellen dieser Engine ist es wichtig, dass die Anwendung eine Engine-ID angibt, die für diesen Benutzer eindeutig ist, häufig die e-Mail-Adresse. Dadurch wird sichergestellt, dass die Vorteile der Zwischenspeicherung realisiert werden. Wenn keine eindeutige Engine-ID angegeben wird, kann die Leistung Ihrer Anwendung beeinträchtigt werden.

### <a name="file-sdk"></a>Datei-SDK

Im folgenden Beispiel wird veranschaulicht, wie die Delegierte Identität für eine Datei-SDK-Anwendung in C++ und c# festgelegt wird. Das gleiche Muster kann auch für das Richtlinien-SDK verwendet werden.

In diesem Beispiel wird gezeigt, wie **ein** delegatmodul im Datei-SDK in .NET erstellt wird.

```csharp
// C# Example for creating a delegated file engine
string delegatedUserEmail = "alice@contoso.com";
var engineSettings = new PolicyEngineSettings(delegatedUserEmail, authDelegate, "", "en-US")
{
    // Provide the identity for service discovery.
    Identity = identity,
    // Set the identity for which all MIP operations will be performed.
    DelegatedUserEmail = delegatedUserEmail
};

var engine = Task.Run(async () => await profile.AddEngineAsync(engineSettings)).Result;
```

Dieses Beispiel zeigt, wie Sie in **C++ ein** delegatmodul im Datei-SDK erstellen.

```c++
// C++ Example for creating a delegated file engine
std::string delegatedUserEmail = "alice@contoso.com";
FileEngine::Settings engineSettings(delegatedUserEmail, mAuthDelegate, "", "en-US", false);
// Set the identity for which all MIP operations will be performed. 
engineSettings.SetDelegatedUserEmail(delegatedUserEmail);

auto enginePromise = std::make_shared<std::promise<std::shared_ptr<FileEngine>>>();
auto engineFuture = enginePromise->get_future();

mProfile->AddEngineAsync(engineSettings, enginePromise);
mEngine = engineFuture.get();
```

Das Ergebnis ist, dass alle Datei-Engines im Namen des angegebenen Benutzers erstellt werden.


## <a name="handler-based-delegation"></a>Handlerbasierte Delegierung

In Szenarien, in denen nur Dateien im Kontext einer bestimmten Benutzeridentität **geschützt** werden müssen, `FileHandler` stellt eine Methode zum übergeben der Benutzeridentität über ein-Objekt bereit `ProtectionSettings` . Die Richtlinie und alle Entschlüsselungs Vorgänge werden als authentifizierte **Dienst Identität** ausgeführt. Die Schutz Aktion wird im Namen des angegebenen Benutzers ausgeführt. dieser Benutzer ist der **Besitzer** des MIP-Schutzes für das Dokument.

### <a name="file-sdk"></a>Datei-SDK

Nur der Vorgang, bei dem der Schutz direkt oder über eine Bezeichnung angewendet wird, wird als der Benutzer ausgeführt, der für das Objekt bereitgestellt wird `ProtectionSettings` . Dieses Objekt wird an die `SetLabel()` `SetProtection()` Funktionen oder im Datei-SDK übermittelt.

Dieses Beispiel zeigt, wie Sie einen **delegatschutzvorgang** im Datei-SDK in .net ausführen.

```csharp
string delegatedUserEmail = "bob@contoso.com";
ProtectionSettings protectionSettings = new ProtectionSettings()
{
    // Set the delegated mail address 
    DelegatedUserEmail = delegatedUserEmail
};
handler.SetLabel(engine.GetLabelById(options.LabelId), labelingOptions, protectionSettings);
// Similar pattern for SetProtection()
// handler.SetProtection(protectionDescriptor, protectionSettings);
```

Dieses Beispiel zeigt, wie Sie einen **delegatschutzvorgang** im Datei-SDK in C++ ausführen.

```c++
mip::ProtectionSettings protectionSettings;
// Set the delegated mail address 
protectionSettings.SetDelegatedUserEmail(delegatedUserEmail);
handler->SetLabel(mEngine->GetLabelById(labelId), labelingOptions, protectionSettings);
```

Das Ergebnis ist, dass alle **handlerschreibvorgänge** , bei denen der Schutz angewendet wird, als Delegierter Benutzer ausgeführt werden. 

### <a name="protection-sdk"></a>Schutz-SDK

Das Schutz-SDK funktioniert anders als das Datei-SDK. Es gibt **zwei Arten von Handlern** , die erstellt werden können, eine für die Veröffentlichung und eine für den Verbrauch. Ähnlich wie beim File SDK wird die Delegierte e-Mail-Adresse über das Einstellungs Objekt für jeden Handlertyp festgelegt.

#### <a name="net"></a>.NET

In diesem Beispiel wird das Ausführen der **Delegierten Veröffentlichung** veranschaulicht.

```csharp
string delegatedUserEmail = "bob@contoso.com";
PublishingSettings publishingSettings = new PublishingSettings(protectionDescriptor)
{
    // Set the delegated mail address 
    DelegatedUserEmail = delegatedUserEmail
};          
var protectionHandler = engine.CreateProtectionHandlerForPublishing(publishingSettings);
```

In diesem Beispiel wird die Ausführung eines **Delegierten Konsums** veranschaulicht.

```csharp
string delegatedUserEmail = "bob@contoso.com";
ConsumptionSettings consumptionSettings = new ConsumptionSettings(plInfo)
{                
    ContentName = "A few bytes.",
    // Set the delegated mail address 
    DelegatedUserEmail = delegatedUserEmail
};
var protectionHandler = engine.CreateProtectionHandlerForConsumption(consumptionSettings);
```

#### <a name="c"></a>C++

In diesem Beispiel wird die Ausführung eines **Delegierten Konsums** veranschaulicht.

```c++
string delegatedUserEmail = "bob@contoso.com";
mip::ProtectionHandler::PublishingSettings publishingSettings = mip::ProtectionHandler::PublishingSettings(descriptor);
// Set the delegated mail address 
publishingSettings.SetDelegatedUserEmail(delegatedUserEmail);
mEngine->CreateProtectionHandlerForPublishingAsync(publishingSettings, handlerObserver, handlerPromise);
auto handler = handlerFuture.get(); 
```

In diesem Beispiel wird das Ausführen der **Delegierten Veröffentlichung** veranschaulicht.

```c++
string delegatedUserEmail = "bob@contoso.com";
mip::ProtectionHandler::ConsumptionSettings consumptionSettings = mip::ProtectionHandler::ConsumptionSettings(serializedPublishingLicense);
// Set the delegated mail address 
consumptionSettings.SetDelegatedUserEmail(delegatedUserEmail);
mEngine->CreateProtectionHandlerForConsumptionAsync(consumptionSettings, handlerObserver, handlerPromise);
auto handler = handlerFuture.get(); 
```

## <a name="required-permissions"></a>Erforderliche Berechtigungen

Jedes der oben genannten Szenarien erfordert einen anderen Berechtigungs Satz. 

| Szenario                             | Berechtigung erforderlich                                                             |
| ------------------------------------ | ------------------------------------------------------------------------------- |
| Delegierte Datei-SDK-Engine            | Unifedpolicy. Tenant. Read<br>Content. delegatedreader<br>Content. delegatedwriter |
| Delegiertes Richtlinien-SDK-Modul          | Unifedpolicy. Tenant. Read                                                       |
| Delegierter Datei-SDK-Handler           | Content. delegatedwriter                                                         |
| Schutz-SDK Delegierte Veröffentlichung     | Content. delegatedwriter                                                         |
| Schutz-SDK-Delegierter Verbrauch | Content. delegatedreader                                                         |

Eine vollständige Überprüfung der Berechtigungen und deren Festlegung finden Sie unter [API-Berechtigungen für das Microsoft Information Protection SDK](concept-api-permissions.md) .

## <a name="next-steps"></a>Nächste Schritte

- Überprüfen der [API-Berechtigungen für das Microsoft Information Protection SDK](concept-api-permissions.md)
- Lesen Sie den Verweis <TODO> Dienst Prinzipal Authentifizierung hinzufügen.