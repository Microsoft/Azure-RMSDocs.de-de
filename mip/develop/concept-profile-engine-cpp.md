---
title: 'Konzepte: Grundlegende Konzepte im MIP SDK – „Profil“ und „Engine“'
description: Dieser Artikel wird Ihnen dabei helfen, die grundlegenden SDK-Konzepte „Profil“ und „Engine“ zu verstehen, die während der Anwendungsinitialisierung erstellt werden.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 66c8f462aa45c964e471a8ca056c102fec3ffbcc
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252927"
---
# <a name="microsoft-information-protection-sdk---profile-and-engine-object-concepts"></a>Microsoft Information Protection SDK: Konzepte der Profile- und Engine-Objekte

## <a name="profiles"></a>Profile

Das Profil ist die Stammklasse für alle Vorgänge im MIP SDK. Vor der Verwendung der drei-APIs, muss die Client-Anwendung ein Profil erstellen. Zukünftige Vorgänge werden ausgeführt, indem Sie das Profil oder andere Objekte *hinzugefügt* für das Profil.

Es gibt drei Arten von Profilen im MIP SDK:

- [`PolicyProfile`](reference/class_mip_policyprofile.md): Die Profilklasse für die MIP-Policy-API.
- [`ProtectionProfile`](reference/class_mip_protectionprofile.md): Die Profilklasse für die MIP-Datenschutz-API.
- [`FileProfile`](reference/class_mip_fileprofile.md): Die Profilklasse für die MIP-Datei-API.

In der verarbeitenden Anwendung verwendete API bestimmt, welche Profilklasse verwendet werden soll.

Das Profil selbst bietet die folgenden Funktionen:

- Definiert den Speicherort für den SDK-Zustand. Zustandsdaten umfassen Benutzerdetails, heruntergeladene Benutzerrichtlinien, Protokolle und Telemetriedaten.
- Definiert, ob der Zustand in den Arbeitsspeicher geladen oder auf dem Datenträger persistent gespeichert werden soll.
- Verarbeitet die Authentifizierung durch das Akzeptieren eines `mip::AuthDelegate`.
- Legt die Anwendungs-ID und den Anzeigenamen der App fest, die das SDK verarbeitet.

### <a name="profile-settings"></a>Profileinstellungen

- `Path`: Pfad der Datei unter die Protokollierung, Telemetrie und andere persistente Zustand gespeichert ist.
- `useInMemoryStorage`: Ein boolescher Wert, der definiert, ob der Zustand im Arbeitsspeicher gespeichert werden sollen oder auf dem Datenträger.
- `authDelegate`: Ein freigegebener Zeiger Klasse `mip::AuthDelegate`. 
- `consentDelegate`: Ein freigegebener Zeiger Klasse [ `mip::ConsentDelegate` ](reference/class_mip_consentdelegate.md). 
- `observer`: Ein freigegebener Zeiger auf das Profil `Observer` Implementierung (im [ `PolicyProfile` ](reference/class_mip_policyprofile_observer.md), [ `ProtectionProfile` ](reference/class_mip_protectionprofile_observer.md), und [ `FileProfile` ](reference/class_mip_fileprofile_observer.md)).
- `applicationInfo`: Ein [ `mip::ApplicationInfo` ](reference/mip-enums-and-structs.md#structures) Objekt. Informationen zur Anwendung, die das SDK-Nutzung Ihrer Azure Active Directory-Anwendung-Registrierungs-ID und Namen übereinstimmt.

## <a name="engines"></a>Engines

Die Datei, Profil- und Datenschutz-API-Engines bieten eine Schnittstelle für Vorgänge, die im Auftrag von einer bestimmten Identität ausgeführt. Auf das Profil-Objekt, für jeden Benutzer, die bei der Anwendung anmeldet, wird ein Modul hinzugefügt. Alle Vorgänge, die von der Engine sind im Kontext dieser Identität.

Es gibt drei Engineklassen im SDK: eine für jede API. Die folgende Liste enthält die Engineklassen und einige der ihnen jeweils zugeordneten Funktionen:

- [`mip::ProtectionEngine`](reference/class_mip_protectionengine.md)
- [`mip::PolicyEngine`](reference/class_mip_policyengine.md)
  - `ListSensitivityLabels()`: Ruft die Liste der Bezeichnungen für das geladene Modul ab.
  - `GetSensitivityLabel()`: Ruft die Bezeichnung aus dem vorhandenen Inhalt ab.
  - `ComputeActions()`: Bereitgestellt mit bezeichnungs-ID und optional gibt Metadaten, die Liste der Aktionen, die für ein bestimmtes Element erfolgen soll.
- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: Ruft die Liste der Bezeichnungen für das geladene Modul ab.
  - `CreateFileHandler()`: Erstellt eine `mip::FileHandler` für eine bestimmte Datei oder einen Stream.

### <a name="engine-states"></a>Enginezustände

Eine Engine kann einen von zwei Zuständen aufweisen:

- `CREATED`: Erstellt gibt an, dass das SDK ausreichend lokalen Statusinformationen, die nach dem Aufrufen der erforderlichen Back-End-Dienste.
- `LOADED`: Das SDK verfügt über die erforderlichen Datenstrukturen für die Engine funktionstüchtig ist erstellt haben.

Eine Engine muss sowohl erstellt als auch geladen werden, um Vorgänge ausführen zu können. Die `Profile`-Klasse stellt einige Engineverwaltungsmethoden bereit: `AddEngineAsync`, `RemoveEngineAsync` und `UnloadEngineAsync`.

Die folgende Tabelle beschreibt die möglichen-Engine-Status, und welche Methoden können diesen Status ändern:

|         | KEINE              | ERSTELLT           | LOADED         |
|---------|-------------------|-------------------|----------------|
| KEINE    |                   |                   | AddEngineAsync |
| ERSTELLT | DeleteEngineAsync |                   | AddEngineAsync |
| LOADED  | DeleteEngineAsync | UnloadEngineAsync |                |

### <a name="engine-id"></a>Engine-ID

Jede Engine besitzt einen eindeutigen Bezeichner (`id`), der in allen Engineverwaltungsvorgängen verwendet wird. Die Anwendung bereitstellen, kann ein `id`, oder das SDK generiert, wenn es nicht von der Anwendung bereitgestellt wird. Alle anderen Engineeigenschaften (z.B. die E-Mail-Adresse in den Identitätsinformationen) sind nicht transparente Nutzlasten für das SDK. Das SDK führt KEINE Logik aus, um die Eindeutigkeit der anderen Eigenschaften zu bewahren oder andere Einschränkungen zu erzwingen.

### <a name="engine-management-methods"></a>Engineverwaltungsmethoden

Wie bereits erwähnt, stehen Sie Ihnen drei Methoden der Engine-Verwaltung im SDK: `AddEngineAsync`, `DeleteEngineAsync`, und `UnloadEngineAsync`.

#### <a name="addengineasync"></a>AddEngineAsync

Diese Methode eine vorhandene Engine lädt oder erstellt eine Falls nicht bereits im lokalen Zustand vorhanden.

Wenn die Anwendung keine `id` bereitstellt, generiert `AddEngineAsync` eine neue `id`. Anschließend wird überprüft, ob eine Engine mit dieser `id` bereits im lokalen Zustand vorhanden ist. Wenn dies der Fall ist, wird diese Engine geladen. Wenn die-Engine *nicht* im lokalen Zustand vorhanden ist, wird eine neue Engine durch Aufrufen der erforderlichen APIs und Back-End-Dienste erstellt.

In beiden Fällen wird die Engine geladen und ist einsatzbereit, wenn die Methode erfolgreich ist.

#### <a name="deleteengineasync"></a>DeleteEngineAsync

Löscht die Engine mit der angegebenen `id`. Alle Spuren der-Engine werden aus dem lokalen Zustand entfernt.

#### <a name="unloadengineasync"></a>UnloadEngineAsync

Entlädt die In-Memory-Datenstrukturen für die Engine mit der angegebenen `id`. Der lokale Zustand dieser Engine ist noch intakt und kann mit `AddEngineAsync` erneut geladen werden.

Diese Methode kann es sich um die Anwendung zur speicherauslastung, indem entladen Engines umsichtiger sein, die erwartungsgemäß nicht in Kürze verwendet werden.

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie im nächsten Schritt mehr über [Authentifizierungskonzepte](concept-authentication-cpp.md) und [Observer-Objekte](concept-async-observers.md). MIP bietet ein erweiterbares Authentifizierungsmodell, während Observer-Objekte verwendet werden, um Ereignisbenachrichtigungen für asynchrone Ereignisse bereitzustellen. Beides sind grundlegende Konzepte, die für alle MIP-API-Sätze gelten.
- Anschließend arbeiten Sie das Profil- und Enginekonzept für die File-, Policy- und Protection-APIs durch.
  - [Profilkonzepte der File-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der File-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Policy-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Policy-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Protection-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Protection-API](concept-profile-engine-file-engine-cpp.md)  
