---
title: 'Konzepte: Dateihandler im MIP SDK'
description: Dieser Artikel wird Ihnen helfen zu verstehen, wie File-API-Handler erstellt und für den Aufruf von Vorgängen verwendet werden.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 414ad04c062a81d374a9e46d170feabb15e0e6cc
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "69886227"
---
# <a name="microsoft-information-protection-sdk---file-handler-concepts"></a>Microsoft Information Protection SDK: Konzepte für Dateihandler

In der File-API des MIP SDK stellt `mip::FileHandler` alle Vorgänge dar, die zum Lesen und Schreiben von Bezeichnungen oder zum Schützen in einer Reihe von Dateitypen verwendet werden können, für die Unterstützung integriert ist. 

## <a name="supported-file-types"></a>Unterstützte Dateitypen

- Auf OCP basierende Office-Dateiformate (Office 2010 oder höher)
- Ältere Office-Dateiformate (Office 2007)
- PDF
- Generische PFILE-Unterstützung
- Dateien, die Adobe XMP unterstützen

## <a name="file-handler-functions"></a>Dateihandlerfunktionen

`mip::FileHandler` stellt Methoden zum Lesen, Schreiben und Entfernen von Bezeichnungen und Schutzinformationen bereit. Die vollständige Liste finden Sie in der [API-Referenz](reference/class_mip_filehandler.md).

In diesem Artikel werden die folgenden Methoden behandelt:

- `GetLabelAsync()`
- `SetLabel()`
- `DeleteLabel()`
- `CommitAsync()`

## <a name="requirements"></a>Anforderungen

Folgende Voraussetzungen gelten für das Erstellen eines `FileHandler`-Elements für eine bestimmte Datei:

- Ein `FileProfile`-Element.
- Ein `FileEngine`-Element, dass `FileProfile` hinzugefügt wurde
- Eine Klasse, die `mip::FileHandler::Observer` erbt.

## <a name="create-a-file-handler"></a>Erstellen eines Dateihandlers

Der erste Schritt bei der Verwaltung von Dateien in der File-API ist das Erstellen eines `FileHandler`-Objekts. Diese Klasse implementiert die gesamte Funktionalität zum Abrufen, Festlegen, Aktualisieren, Löschen und Committen von Bezeichnungsänderungen an Dateien.

Das Erstellen des `FileHandler` ist so einfach wie das Aufrufen der `CreateFileHandlerAsync`-Funktion von `FileEngine` mithilfe des Promise-/Future-Musters.

`CreateFileHandlerAsync` nimmt drei Parameter an: den Pfad zu der Datei, die gelesen oder geändert werden soll, das `mip::FileHandler::Observer`-Element für asynchrone Ereignisbenachrichtigungen und das Versprechen für den `FileHandler`.

**Hinweis:** Die `mip::FileHandler::Observer`-Klasse muss in einer abgeleiteten Klasse implementiert werden, da `CreateFileHandler` das `Observer`-Objekt erfordert. 

```cpp
auto createFileHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::FileHandler>>>();
auto createFileHandlerFuture = createFileHandlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(filePath, std::make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = createFileHandlerFuture.get();
```

Wenn das `FileHandler`-Objekt erfolgreich erstellt wurde, können Dateivorgänge („Get“/„Set“/„Delete“/„Commit“) ausgeführt werden.

## <a name="read-a-label"></a>Lesen einer Bezeichnung

### <a name="metadata-requirements"></a>Metadatenanforderungen

Es gibt einige Voraussetzungen, um Metadaten erfolgreich aus einer Datei zu lesen und in etwas zu übersetzen, das in Anwendungen verwendet werden kann.

- Die Bezeichnung, die gelesen wird, muss noch im O365-Dienst vorhanden sein. Wenn sie vollständig gelöscht wurde, kann das SDK keine Informationen zu dieser Bezeichnung abrufen und gibt einen Fehler zurück.
- Die Dateimetadaten müssen intakt sein. Zu diesen Metadaten gehören die folgenden Angaben:
  - Attribute1
  - Attribute2

### <a name="getlabelasync"></a>GetLabelAsync()

Nachdem wir den Handler so erstellt haben, dass er auf eine bestimmte Datei zeigt, kehren wir zum Promise-/Future-Muster zurück, um die Bezeichnung asynchron zu lesen. Das Versprechen gilt für ein `mip::ContentLabel`-Objekt, das alle Informationen zur angewendeten Bezeichnung enthält.

Nach der Instanziierung der `promise`- und `future`-Objekte lesen wir die Bezeichnung durch den Aufruf von `handler->GetLabelAsync()` und Bereitstellen von `promise` als einzigem Parameter. Schließlich kann die Bezeichnung in einem `mip::ContentLabel`-Objekt gespeichert werden, das wir aus der `future` abrufen.

```cpp
auto loadPromise = std::make_shared<std::promise<std::shared_ptr<mip::ContentLabel>>>();
auto loadFuture = loadPromise->get_future();
handler->GetLabelAsync(loadPromise);
auto label = loadFuture.get();
```

Bezeichnungsdaten können aus dem `label`-Objekt gelesen und an jede andere Komponente oder Funktionalität in der Anwendung übergeben werden.

***

## <a name="set-a-label"></a>Festlegen einer Bezeichnung

Das Festlegen einer Bezeichnung ist ein zweiteiliger Vorgang. Zuerst, wenn Sie einen Handler erstellt haben, der auf die betreffende Datei verweist, kann die Bezeichnung durch Aufrufen von `FileHandler->SetLabel()` mit einigen Parametern festgelegt werden: `mip::Label`, `mip::LabelingOptions`und `mip::ProtectionOptions`. Zuerst müssen wir die Bezeichnungs-ID in eine Bezeichnung auflösen und dann die Beschriftungs Optionen definieren. 

### <a name="resolve-label-id-to-miplabel"></a>Bezeichnungs-ID in MIP:: Label auflösen

Der erste Parameter der **setlabel** -Funktion ist eine `mip::Label`. Häufig arbeitet die Anwendung mit Bezeichnungs Bezeichnern anstelle von Bezeichnungen. Der Bezeichnungs Bezeichner kann in den `mip::Label` aufgelöst werden, indem **getlabelbyid** für die Datei oder das Richtlinien Modul aufgerufen wird:

```cpp
mip::Label label = mEngine->GetLabelById(labelId);
```

### <a name="labeling-options"></a>Bezeichnungsoptionen

Der zweite Parameter, der zum Festlegen der Bezeichnung erforderlich ist, ist `mip::LabelingOptions`. 

`LabelingOptions` gibt zusätzliche Informationen zur Bezeichnung an, z.B. die `AssignmentMethod` und eine Begründung für eine Aktion.

- `mip::AssignmentMethod` ist einfach ein Enumerator, der drei Werte aufweisen kann: `STANDARD`, `PRIVILEGED` oder `AUTO`. Weitere Informationen finden Sie in der Referenz zu `mip::AssignmentMethod`.
- Eine Begründung ist nur erforderlich, wenn die Dienstrichtlinie dies erfordert *und* wenn die *vorhandene* Vertraulichkeit einer Datei herabgesetzt wird.

Dieser Ausschnitt veranschaulicht das Erstellen des `mip::LabelingOptions` Objekts und das Festlegen der Grundausrichtung und der Nachricht.

```cpp
auto labelingOptions = mip::LabelingOptions(mip::AssignmentMethod::STANDARD);
labelingOptions.SetDowngradeJustification(true, "Because I made an educated decision based upon the contents of this file.");
```

### <a name="protection-settings"></a>Schutzeinstellungen

Einige Anwendungen müssen möglicherweise Vorgänge im Namen einer Delegierten Benutzeridentität ausführen. Die `mip::ProtectionSettings`-Klasse ermöglicht der Anwendung die Definition der Delegierten Identität *pro Handler*. Zuvor wurde die Delegierung von den Engine-Klassen ausgeführt. Dies hat erhebliche Nachteile beim Anwendungs Aufwand und bei der Dienst Roundtrips. Indem die Delegierten Benutzereinstellungen auf `mip::ProtectionSettings` verschoben und dieser Teil der Handlerklasse gemacht werden, entfällt dieser mehr Aufwand. Dies führt zu einer besseren Leistung für Anwendungen, die viele Vorgänge im Namen verschiedener Gruppen von Benutzer Identitäten durchführen. 

Wenn eine Delegierung nicht erforderlich ist, übergeben Sie einfach `mip::ProtectionSettings()` an die Funktion " **setlabel** ". Wenn eine Delegierung erforderlich ist, kann dies erreicht werden, indem ein `mip::ProtectionSettings` Objekt erstellt und die Delegierte e-Mail-Adresse festgelegt wird:

```cpp
mip::ProtectionSettings protectionSettings; 
protectionSettings.SetDelegatedUserEmail("alice@contoso.com");
```

### <a name="set-the-label"></a>Festlegen der Bezeichnung

Nachdem Sie die `mip::Label` aus der ID abgerufen, die Beschriftungs Optionen festgelegt und optional die Schutzeinstellungen festgelegt haben, kann die Bezeichnung jetzt festgelegt werden.

Wenn Sie keine Schutzeinstellungen festgelegt haben, legen Sie die Bezeichnung fest, indem Sie `SetLabel` für den Handler aufrufen:

```cpp
handler->SetLabel(label, labelingOptions, mip::ProtectionSettings());
```

Wenn Sie zum Ausführen eines Delegierten Vorgangs Schutzeinstellungen benötigen, dann gehen Sie wie folgt vor:

```cpp
handler->SetLabel(label, labelingOptions, protectionSettings);
```

Nachdem nun die Bezeichnung für die Datei festgelegt wurde, auf die der Handler verweist, gibt es noch einen weiteren Schritt, um die Änderung zu committen und eine Datei auf den Datenträger zu schreiben oder einen Ausgabedatenstrom zu erstellen.

### <a name="commit-changes"></a>Committen von Änderungen

Der letzte Schritt beim Committen einer Änderung in eine Datei im MIP SDK besteht im eigentlichen **Committen** der Änderung. Dies geschieht mithilfe der `FileHandler->CommitAsync()`-Funktion. 

Um die Commitfunktion zu implementieren, kehren wir zu Promise/Future zurück und erstellen ein Versprechen für ein `bool`-Element. Die `CommitAsync()` Funktion gibt TRUE zurück, wenn der Vorgang erfolgreich war, oder FALSE, wenn er aus irgendeinem Grund fehlgeschlagen ist. 

Nach dem Erstellen von `promise` und `future` wird `CommitAsync()` aufgerufen, und es werden zwei Parameter angegeben: der Pfad der Ausgabedatei (`std::string`) und das Versprechen. Abschließend wird das Ergebnis abgerufen, indem der Wert des `future`-Objekts abgerufen wird.

```cpp
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
auto wasCommitted = commitFuture.get();
```

**Wichtig:** Der `FileHandler` aktualisiert oder überschreibt keine vorhandenen Dateien. Es bleibt dem Entwickler überlassen, **das Ersetzen** der Datei zu implementieren, die mit einer Bezeichnung versehen wurde. 

Wenn Sie eine Bezeichnung in **FileA.docx** schreiben, wird eine Kopie der Datei (**FileB.docx**) mit der angewendeten Bezeichnung erstellt. Code muss geschrieben werden, um **FileA.docx** zu entfernen/umzubenennen und **FileB.docx** umzubenennen.

***

## <a name="delete-a-label"></a>Löschen einer Bezeichnung

```cpp
auto handler = mEngine->CreateFileHandler(filePath, std::make_shared<FileHandlerObserverImpl>());
handler->DeleteLabel(mip::AssignmentMethod::PRIVILEGED, "Label unnecessary.");
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
```
