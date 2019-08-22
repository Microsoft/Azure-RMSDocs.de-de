---
title: 'Konzepte: Grundlegende Konzepte im MIP SDK – „Profil“ und „Engine“'
description: Dieser Artikel wird Ihnen dabei helfen, die grundlegenden SDK-Konzepte „Profil“ und „Engine“ zu verstehen, die während der Anwendungsinitialisierung erstellt werden.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/29/2019
ms.author: mbaldwin
ms.openlocfilehash: a1112b3c35539654ac71b6c8c686f93e676ac5f3
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69886123"
---
# <a name="microsoft-information-protection-sdk---profile-and-engine-object-concepts"></a>Microsoft Information Protection SDK: Konzepte der Profile- und Engine-Objekte

## <a name="profiles"></a>Profile

Wenn die `MipContext` Klasse zum Speichern von SDK-spezifischen Einstellungen ist, ist das Profil die Stamm Klasse für alle MIP-Bezeichnungen und Schutz spezifischen Vorgänge im MIP SDK. Bevor Sie einen der drei API-Sätze verwenden, muss die Client Anwendung ein Profil erstellen. Zukünftige Vorgänge werden vom Profil oder von anderen Objekten, die dem Profil *hinzugefügt* werden, ausgeführt.

Es gibt drei Arten von Profilen im MIP SDK:

- [`PolicyProfile`](reference/class_mip_policyprofile.md): Die Profilklasse für die MIP-Richtlinien-API.
- [`ProtectionProfile`](reference/class_mip_protectionprofile.md): Die Profilklasse für die MIP-Schutz-API.
- [`FileProfile`](reference/class_mip_fileprofile.md): Die Profilklasse für die MIP-Datei-API.

Die API, die in der verarbeitenden Anwendung verwendet wird, bestimmt, welche Profilklasse verwendet werden soll.

Das Profil selbst bietet die folgenden Funktionen:

- Definiert, ob der Zustand im Arbeitsspeicher geladen oder auf dem Datenträger persistent gespeichert werden soll, und ob er ggf. auf dem Datenträger gespeichert werden soll.
- Verarbeitet die Authentifizierung durch das Akzeptieren eines `mip::AuthDelegate`.
- Definiert den `mip::ConsentDelegate` , der für Zustimmungs Vorgänge verwendet werden soll.
- Definiert die `mip::FileProfile::Observer` -Implementierung, die für asynchrone Rückrufe für Profil Vorgänge verwendet wird.

### <a name="profile-settings"></a>Profileinstellungen

- `MipContext`: Das `MipContext` Objekt, das zum Speichern von Anwendungsinformationen, Zustands Pfad usw. initialisiert wurde.
- `CacheStorageType`: Definiert, wie der Zustand gespeichert wird: Im Arbeitsspeicher, auf dem Datenträger oder auf dem Datenträger gespeichert und verschlüsselt.
- `authDelegate`: Ein frei gegebener Zeiger der `mip::AuthDelegate`-Klasse.
- `consentDelegate`: Ein frei gegebener Zeiger der [`mip::ConsentDelegate`](reference/class_mip_consentdelegate.md)-Klasse.
- `observer`: Ein frei gegebener Zeiger auf die `Observer` Profil Implementierung ( [`PolicyProfile`](reference/class_mip_policyprofile_observer.md)in [`ProtectionProfile`](reference/class_mip_protectionprofile_observer.md), und [`FileProfile`](reference/class_mip_fileprofile_observer.md)).
- `applicationInfo`: Ein [`mip::ApplicationInfo`](reference/mip-enums-and-structs.md#structures) -Objekt. Informationen über die Anwendung, die das SDK nutzt, das Ihren Azure Active Directory Anwendungs Registrierungs-ID und-Namen entspricht.

## <a name="engines"></a>Engines

Die Datei-, Profil-und Schutz-API-Engines stellen eine Schnittstelle für Vorgänge bereit, die von einer bestimmten Identität ausgeführt werden. Eine Engine wird dem Profil Objekt für jeden Benutzer oder Dienst Prinzipal hinzugefügt, der sich bei der Anwendung anmeldet. Es ist möglich, delegierte Vorgänge über `mip::ProtectionSettings` und die Datei oder den Schutz Handler auszuführen. Weitere Informationen finden Sie [im Abschnitt Schutzeinstellungen in den fileHandler-Konzepten](concept-handler-file-cpp.md) .

Es gibt drei Engineklassen im SDK: eine für jede API. Die folgende Liste enthält die Engineklassen und einige der ihnen jeweils zugeordneten Funktionen:

- [`mip::ProtectionEngine`](reference/class_mip_protectionengine.md)
- [`mip::PolicyEngine`](reference/class_mip_policyengine.md)
  - `ListSensitivityLabels()`: Ruft die Liste der Bezeichnungen für die geladene Engine ab.
  - `GetSensitivityLabel()`: Ruft die Bezeichnung aus dem vorhandenen Inhalt ab.
  - `ComputeActions()`: Gibt eine Bezeichnungs-ID und optionale Metadaten an und gibt die Liste der Aktionen zurück, die für ein bestimmtes Element ausgeführt werden sollen.
- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: Ruft die Liste der Bezeichnungen für die geladene Engine ab.
  - `CreateFileHandler()`: Erstellt eine `mip::FileHandler` für eine bestimmte Datei oder einen Stream.

### <a name="engine-states"></a>Enginezustände

Eine Engine kann einen von zwei Zuständen aufweisen:

- `CREATED`: Erstellt gibt an, dass das SDK über genügend lokale Zustandsinformationen verfügt, nachdem die erforderlichen Back-End-Dienste aufgerufen wurden
- `LOADED`: Das SDK hat die erforderlichen Datenstrukturen erstellt, damit die Engine funktionstüchtig ist.

Eine Engine muss sowohl erstellt als auch geladen werden, um Vorgänge ausführen zu können. Die `Profile`-Klasse stellt einige Engineverwaltungsmethoden bereit: `AddEngineAsync`, `RemoveEngineAsync` und `UnloadEngineAsync`.

In der folgenden Tabelle werden die möglichen Engine-Zustände und die möglichen Methoden zum Ändern des Status beschrieben:

|         | NONE              | CREATED           | LOADED         |
|---------|-------------------|-------------------|----------------|
| NONE    |                   |                   | AddEngineAsync |
| CREATED | DeleteEngineAsync |                   | AddEngineAsync |
| LOADED  | DeleteEngineAsync | UnloadEngineAsync |                |

### <a name="engine-id"></a>Engine-ID

Jede Engine besitzt einen eindeutigen Bezeichner (`id`), der in allen Engineverwaltungsvorgängen verwendet wird. Die Anwendung kann eine `id`bereitstellen, oder das SDK kann eines generieren, wenn es nicht von der Anwendung bereitgestellt wird. Alle anderen Engineeigenschaften (z.B. die E-Mail-Adresse in den Identitätsinformationen) sind nicht transparente Nutzlasten für das SDK. Das SDK führt KEINE Logik aus, um die Eindeutigkeit der anderen Eigenschaften zu bewahren oder andere Einschränkungen zu erzwingen.

> [!IMPORTANT]
> Verwenden Sie als bewährte Vorgehensweise eine Engine-ID, die für den Benutzer eindeutig ist, und verwenden Sie diese, wenn der Benutzer einen Vorgang mit dem SDK ausführt. Wenn Sie eine vorhandene Engine-ID nicht bereitstellen, führt dies zu zusätzlichen Dienst Roundtrips zum Abrufen der Richtlinie und zum Abrufen von Lizenzen, die möglicherweise bereits für die vorhandene Engine zwischengespeichert wurden.

### <a name="engine-management-methods"></a>Engineverwaltungsmethoden

Wie bereits erwähnt, gibt es drei Modul Verwaltungsmethoden im SDK: `AddEngineAsync`, `DeleteEngineAsync`und `UnloadEngineAsync`.

#### <a name="addengineasync"></a>AddEngineAsync

Mit dieser Methode wird ein vorhandenes Modul geladen, oder es wird eine vorhandene Engine erstellt, wenn noch keine vorhanden ist.

Wenn die Anwendung keine `id` bereitstellt, generiert `AddEngineAsync` eine neue `id`. Anschließend wird überprüft, ob eine Engine mit dieser `id` bereits im lokalen Zustand vorhanden ist. Wenn dies der Fall ist, wird diese Engine geladen. Wenn die-Engine *nicht* im lokalen Zustand vorhanden ist, wird eine neue Engine durch Aufrufen der erforderlichen APIs und Back-End-Dienste erstellt.

In beiden Fällen wird die Engine geladen und ist einsatzbereit, wenn die Methode erfolgreich ist.

#### <a name="deleteengineasync"></a>DeleteEngineAsync

Löscht die Engine mit der angegebenen `id`. Alle Spuren der-Engine werden aus dem lokalen Zustand entfernt.

#### <a name="unloadengineasync"></a>UnloadEngineAsync

Entlädt die In-Memory-Datenstrukturen für die Engine mit der angegebenen `id`. Der lokale Zustand dieser Engine ist noch intakt und kann mit `AddEngineAsync` erneut geladen werden.

Diese Methode ermöglicht es der Anwendung, die Speicherauslastung zu überstehen, indem Engines entladen werden, die nicht in Kürze verwendet werden sollen.

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie im nächsten Schritt mehr über [Authentifizierungskonzepte](concept-authentication-cpp.md) und [Observer-Objekte](concept-async-observers.md). MIP bietet ein erweiterbares Authentifizierungsmodell, während Observer-Objekte verwendet werden, um Ereignisbenachrichtigungen für asynchrone Ereignisse bereitzustellen. Beides sind grundlegende Konzepte, die für alle MIP-API-Sätze gelten.
- Anschließend arbeiten Sie das Profil- und Enginekonzept für die File-, Policy- und Protection-APIs durch.
  - [Profilkonzepte der File-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der File-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Policy-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Policy-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Protection-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Protection-API](concept-profile-engine-file-engine-cpp.md)  
