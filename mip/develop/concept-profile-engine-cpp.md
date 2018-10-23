---
title: 'Konzepte: Grundlegende Konzepte im MIP SDK – „Profil“ und „Engine“'
description: Dieser Artikel wird Ihnen dabei helfen, die grundlegenden SDK-Konzepte „Profil“ und „Engine“ zu verstehen, die während der Anwendungsinitialisierung erstellt werden.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6f11944e7cceed39423af2a8104ce044d1f6eec6
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453417"
---
# <a name="microsoft-information-protection-sdk---profile-and-engine-object-concepts"></a>Microsoft Information Protection SDK: Konzepte der Profile- und Engine-Objekte

## <a name="profiles"></a>Profile

Das Profil ist die Stammklasse für alle Vorgänge im MIP SDK. Bevor Sie eine der drei APIs verwenden können, muss von der Clientanwendung ein Profil erstellt werden. Alle zukünftigen Vorgänge werden vom Profil oder von anderen Objekten, die dem Profil *hinzugefügt* wurden, ausgeführt.

Es gibt drei Arten von Profilen im MIP SDK:

- [`PolicyProfile`](reference/class_mip_policyprofile.md): Die Profilklasse für die MIP-Policy-API.
- [`ProtectionProfile`](reference/class_mip_protectionprofile.md): Die Profilklasse für die MIP-Protection-API.
- [`FileProfile`](reference/class_mip_fileprofile.md): Die Profilklasse für die MIP-File-API.

Die in der verarbeitenden Anwendung verwendete API bestimmt, welche Profilklasse verwendet werden soll.

Das Profil selbst bietet die folgenden Funktionen:

- Definiert den Speicherort für den SDK-Zustand. Zustandsdaten umfassen Benutzerdetails, heruntergeladene Benutzerrichtlinien, Protokolle und Telemetriedaten.
- Definiert, ob der Zustand in den Arbeitsspeicher geladen oder auf dem Datenträger persistent gespeichert werden soll.
- Verarbeitet die Authentifizierung durch das Akzeptieren eines `mip::AuthDelegate`.
- Legt die Anwendungs-ID und den Anzeigenamen der App fest, die das SDK verarbeitet.

### <a name="profile-settings"></a>Profileinstellungen

- `Path`: der Dateipfad, unter dem Protokollierung, Telemetriedaten und andere persistente Zustände gespeichert werden.
- `useInMemoryStorage`: Ein boolescher Wert, der definiert, ob der Zustand im Arbeitsspeicher oder auf dem Datenträger gespeichert werden soll.
- `authDelegate`: Ein gemeinsamer Zeiger der Klasse `mip::AuthDelegate`. 
- `consentDelegate`: Ein gemeinsamer Zeiger der Klasse `mip::ConsentDelegate`. 
- `observer`: Ein gemeinsamer Zeiger auf die `Observer`-Implementierung des Profils (in `PolicyProfile`, `ProtectionProfile` und `EngineProfile`).
- `applicationInfo`: Ein `mip::ApplicationInfo`-Objekt. Informationen zu der Anwendung, die das SDK nutzt.

## <a name="engines"></a>Engines

Engines stellen in den File, Profile- und Protection-APIs eine Schnittstelle für Vorgänge bereit, die im Auftrag einer bestimmten Identität ausgeführt werden. Eine Engine wird dem Profile-Objekt für jeden Benutzer hinzugefügt, der sich bei der Anwendung anmeldet. Alle von der Engine ausgeführten Vorgänge erfolgen im Kontext dieser Identität.

Es gibt drei Engineklassen im SDK: eine für jede API. Die folgende Liste enthält die Engineklassen und einige der ihnen jeweils zugeordneten Funktionen:

- [`mip::ProtectionEngine`]
- [`mip::PolicyEngine`](reference/class_mip_policyengine.md)
  - `ListSensitivityLabels()`: Ruft die Liste der Bezeichnungen für die geladene Engine ab.
  - `GetSensitivityLabel()`: Ruft die Bezeichnung aus vorhandenem Inhalt ab.
  - `ComputeActions()`: Gibt die Liste der Aktionen zurück, die für ein bestimmtes Element ausgeführt werden sollen, wenn eine Bezeichnungs-ID und optional Metadaten angegeben werden.
- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: Ruft die Liste der Bezeichnungen für die geladene Engine ab.
  - `CreateFileHandler()`: Erstellt einen `mip::FileHandler` für eine bestimmte Datei oder einen Datenstrom.

### <a name="engine-states"></a>Enginezustände

Eine Engine kann einen von zwei Zuständen aufweisen:

- `CREATED`: „Erstellt“ gibt an, dass das SDK über ausreichende lokale Zustandsinformationen nach dem Aufrufen der erforderlichen Back-End-Dienste verfügt.
- `LOADED`: Das SDK hat die erforderlichen Datenstrukturen erstellt, damit die Engine betriebsbereit ist.

Eine Engine muss sowohl erstellt als auch geladen werden, um Vorgänge ausführen zu können. Die `Profile`-Klasse stellt einige Engineverwaltungsmethoden bereit: `AddEngineAsync`, `RemoveEngineAsync` und `UnloadEngineAsync`.

Die folgende Tabelle beschreibt die möglichen Enginezustände und gibt an, welche Methode den jeweiligen Zustand ändern kann.

|         | NONE              | CREATED           | LOADED         |
|---------|-------------------|-------------------|----------------|
| NONE    |                   |                   | AddEngineAsync |
| CREATED | DeleteEngineAsync |                   | AddEngineAsync |
| LOADED  | DeleteEngineAsync | UnloadEngineAsync |                |

### <a name="engine-id"></a>Engine-ID

Jede Engine besitzt einen eindeutigen Bezeichner (`id`), der in allen Engineverwaltungsvorgängen verwendet wird. Die Anwendung kann eine `id` bereitstellen, oder das SDK generiert einen neuen eindeutigen Bezeichner, wenn dieser nicht von der Anwendung bereitgestellt wird. Alle anderen Engineeigenschaften (z.B. die E-Mail-Adresse in den Identitätsinformationen) sind nicht transparente Nutzlasten für das SDK. Das SDK führt KEINE Logik aus, um die Eindeutigkeit der anderen Eigenschaften zu bewahren oder andere Einschränkungen zu erzwingen.

### <a name="engine-management-methods"></a>Engineverwaltungsmethoden

Wie bereits erwähnt, gibt es im SDK drei Engineverwaltungsmethoden: `AddEngineAsync`, `DeleteEngineAsync` und `UnloadEngineAsync`.

#### <a name="addengineasync"></a>AddEngineAsync

Diese Methode lädt eine vorhandene Engine oder erstellt eine neue, wenn noch keine Engine im lokalen Zustand vorhanden ist.

Wenn die Anwendung keine `id` bereitstellt, generiert `AddEngineAsync` eine neue `id`. Anschließend wird überprüft, ob eine Engine mit dieser `id` bereits im lokalen Zustand vorhanden ist. Wenn dies der Fall ist, wird diese Engine geladen. Wenn die-Engine *nicht* im lokalen Zustand vorhanden ist, wird eine neue Engine durch Aufrufen der erforderlichen APIs und Back-End-Dienste erstellt.

In beiden Fällen wird die Engine geladen und ist einsatzbereit, wenn die Methode erfolgreich ist.

#### <a name="deleteengineasync"></a>DeleteEngineAsync

Löscht die Engine mit der angegebenen `id`. Alle Spuren der-Engine werden aus dem lokalen Zustand entfernt.

#### <a name="unloadengineasync"></a>UnloadEngineAsync

Entlädt die In-Memory-Datenstrukturen für die Engine mit der angegebenen `id`. Der lokale Zustand dieser Engine ist noch intakt und kann mit `AddEngineAsync` erneut geladen werden.

Diese Methode ermöglicht es der Anwendung, die Speichernutzung zu beurteilen, indem Engines entladen werden, von denen nicht erwartet wird, dass sie in Kürze verwendet werden.

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie im nächsten Schritt mehr über [Authentifizierungskonzepte](concept-authentication-cpp.md) und [Observer-Objekte](concept-async-observers.md). MIP bietet ein erweiterbares Authentifizierungsmodell, während Observer-Objekte verwendet werden, um Ereignisbenachrichtigungen für asynchrone Ereignisse bereitzustellen. Beides sind grundlegende Konzepte, die für alle MIP-API-Sätze gelten.
- Anschließend arbeiten Sie das Profil- und Enginekonzept für die File-, Policy- und Protection-APIs durch.
  - [Profilkonzepte der File-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der File-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Policy-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Policy-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Protection-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Protection-API](concept-profile-engine-file-engine-cpp.md)  
