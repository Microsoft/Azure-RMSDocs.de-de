---
title: 'Konzepte: Cache Speicher'
description: Dieser Artikel hilft Ihnen dabei, die Konzepte im Zusammenhang mit dem Cache Speicher im MIP SDK nachzuvollziehen.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: tommos
ms.openlocfilehash: 6e9e726c133f5796a2406a1cacb746fc561a6457
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "95567922"
---
# <a name="microsoft-information-protection-sdk---cache-storage"></a>Microsoft Information Protection SDK-Cache Speicher

Das MIP SDK implementiert eine SQLite3-Datenbank für die Wartung des SDK-Cache Speichers. Vor Version 1,3 des Microsoft Information Protection SDK wurden nur zwei Arten von Cache Zustands Speicher unterstützt: auf dem Datenträger und im Arbeitsspeicher. Beide Typen haben bestimmte Daten, insbesondere Lizenzen für geschützte Inhalte und Richtlinien Informationen, in Klartext gespeichert.

Um die Sicherheitslage des SDK zu verbessern, haben wir Unterstützung für eine zweite Art von Cache Cache hinzugefügt, die plattformspezifische kryptografische APIs verwendet, um die Datenbank und ihren Inhalt zu schützen.

Die Anwendung definiert den Cachetyp beim Laden des Profils als Teil der- `FileProfileSettings` ,- `PolicyProfileSettings` oder- `ProtectionProfileSettings` Objekte. Der Cachetyp ist für die Lebensdauer des Profils statisch. Für das Ändern in einen anderen Typ von Cache Speichertyp muss das vorhandene Profil zerstört und ein neues erstellt werden.

## <a name="cache-storage-types"></a>Cache Speichertypen

Ab MIP SDK Release 1,3 sind die folgenden Speicher Cache Typen verfügbar.

| type            | Zweck                                                                                                                         |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| InMemory        | Verwaltet den Speicher Cache im Arbeitsspeicher in der Anwendung.                                                                       |
| OnDisk          | Speichert die Datenbank auf dem Datenträger in dem Verzeichnis, das im Einstellungs Objekt bereitgestellt wird. Die Datenbank wird als Klartext gespeichert.              |
| Ondiskverschlüsselt | Speichert die Datenbank auf dem Datenträger in dem Verzeichnis, das im Einstellungs Objekt bereitgestellt wird. Die Datenbank wird mit betriebssystemspezifischen APIs verschlüsselt. |

Jede **Engine** , die von der Anwendung generiert wird, generiert einen neuen Verschlüsselungsschlüssel.

Der Cache Speicher wird über eines der Profile Einstellungs Objekte über die- `mip::CacheStorageType` enum festgelegt.

```cpp 
FileProfile::Settings profileSettings(mMipContext,
    mip::CacheStorageType::OnDiskEncrypted, // Define the storage type to use.
    mAuthDelegate,
    std::make_shared<sample::consent::ConsentDelegateImpl>(),
    std::make_shared<FileProfileObserver>());
```

## <a name="when-to-use-each-type"></a>Verwendungszwecke der einzelnen Typen

Der Cache Speicher ist wichtig für die Verwaltung des Offline Zugriffs auf zuvor entschlüsselte Informationen. Außerdem wird sichergestellt, dass die Leistung für Entschlüsselungs Vorgänge gewährleistet ist, wenn Daten bereits verarbeitet wurden.

- **In Memory-Speicher**: Verwenden Sie diesen Speichertyp für langlebige Prozesse, in denen das Beibehalten der Richtlinien-oder Lizenz Cache Informationen über Dienst Neustarts nicht erforderlich ist.
- **Auf** dem Datenträger: Verwenden Sie diesen Speichertyp für Anwendungen, bei denen Prozesse möglicherweise häufig beendet und gestartet werden, aber Richtlinien-, Lizenz-und Dienst Ermittlungs Cache über Neustarts hinweg beibehalten müssen. Dieser Speicher Cachetyp ist Klartext und eignet sich daher besser für Server Arbeits Auslastungen, bei denen Benutzer keinen Zugriff auf den Zustands Speicher haben. Beispiele hierfür wären ein Windows-Dienst oder ein Linux-Daemon, der auf einem Server ausgeführt wird, oder eine SaaS-Anwendung, bei der nur die Dienst Administratoren Zugriff auf die Zustandsdaten haben würden.
- **Auf Datenträger und verschlüsselt**: Verwenden Sie diesen Speichertyp für Anwendungen, bei denen Prozesse möglicherweise häufig beendet und gestartet werden, aber Richtlinien-, Lizenz-und Dienst Ermittlungs Cache zwischen Neustarts beibehalten müssen. Dieser Speicher Cache ist verschlüsselt und eignet sich daher besser für Arbeitsstations Anwendungen, in denen ein Benutzer die Zustands Datenbank durchsuchen und ermitteln kann. Mithilfe der Verschlüsselung können Sie sicherstellen, dass Benutzer, die nicht über den Inhalt der Richtlinie oder den Schutz von Inhalten verfügen, im Klartext auf zugreifen können. Es ist wichtig zu beachten, dass die Daten in allen Fällen mit Schlüsseln verschlüsselt werden, auf die der Benutzer möglicherweise zugreifen kann. Ein geschickter Angreifer kann den Cache mit minimalem Aufwand entschlüsseln, dies verhindert jedoch Manipulationen und durchsuchen.

## <a name="supported-platforms-for-encryption"></a>Unterstützte Plattformen für die Verschlüsselung

| Plattform          | Version                | Notizen                                                                                                                               |
| ----------------- | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft Windows | Windows 8 und höher    | Windows 7 unterstützt nur cachestoragetype:: ondisk.                                                                                    |
| macOS             | High Sierra oder höher  |                                                                                                                                     |
| Ubuntu Linux      | 16,04 und höher        | Erfordert das [secretservice](https://developer.gnome.org/libsecret/unstable/SecretService.html) -und das `LinuxEncryptedCache` Feature-Flag. |
| Android           | Android 7,0 oder höher   |                                                                                                                                     |
| iOS               | Alle unterstützten Versionen |                                                                                                                                     |

Während das MIP SDK andere Linux-Distributionen unterstützt, haben wir die Cache Verschlüsselung nicht auf RedHat Enterprise Linux, CentOS oder Debian getestet.

> [!NOTE]
> Das featureflag zum Aktivieren des Cache Speichers unter Linux wird über `mip::MipContext::CreateWithCustomFeatureSettings()`

## <a name="cache-storage-database-tables"></a>Cache Speicher-Datenbanktabellen

Das MIP SDK verwaltet zwei Datenbanken für den Cache. Eine ist für die Schutz-APIs und die Beibehaltung der Schutz Zustands Details. Das andere gilt für die Richtlinien-APIs und die Verwaltung von Richtlinien Details und Dienst Informationen. Beide werden in dem Pfad gespeichert, der im Settings-Objekt unter **mip\mip.Policies.sqlite3** und **mip\mip.Protection.sqlite3** definiert ist.

### <a name="protection-database"></a>Schutz Datenbank

| Tabelle         | Zweck                                                        | Verschlüsselt |
| ------------- | -------------------------------------------------------------- | --------- |
| Authinfostore | Speichert die Details der Authentifizierungs Aufforderung.                       | Nein        |
| Genehmistore  | Speichert Zustimmungs Ergebnisse für die einzelnen Engines.                        | Nein        |
| Dnsinfostore  | Speichert Ergebnisse der DNS-Suche für SDK-Schutz Vorgänge.        | Nein        |
| Enginestore   | Speichert Engine-Details, zugeordnete Benutzer und benutzerdefinierte Client Daten. | Nein        |
| KeyStore      | Speichert symmetrische Verschlüsselungsschlüssel für jede Engine.              | Ja       |
| Lizenz Speicher  | Speichert Lizenzinformationen für zuvor entschlüsselte Daten.  | Ja       |
| Sdinfostore   | Speichert Dienst Ermittlungsergebnisse.                              | Nein        |

### <a name="policy-database"></a>Richtlinien Datenbank

| Tabelle           | Zweck                                                          | Verschlüsselt |
| --------------- | ---------------------------------------------------------------- | --------- |
| KeyStore        | Speichert symmetrische Verschlüsselungsschlüssel für jede Engine.                | Ja       |
| Richtlinien        | Speichert Bezeichnungs Richtlinien Informationen für jeden Benutzer.                   | Ja       |
| Richtlinienurl     | Speichert die URL des Back-End-Richtlinien diensdienstanders             | Nein        |
| Sensitivität     | Speichert Klassifizierungsregeln für eine bestimmte Benutzer Richtlinie.          | Ja       |
| Sensitivityurls | Speichert die Dienst-URL der Back-End-vertraulichkeitsrichtlinie für bestimmte | Nein        |

## <a name="database-size-considerations"></a>Aspekte der Datenbankgröße

Die Datenbankgröße hängt von zwei Faktoren ab: der Menge der Module, die dem Cache hinzugefügt werden, und der Anzahl der zwischengespeicherten Schutz Lizenzen. Ab MIP SDK 1,3 gibt es keinen Mechanismus zum Bereinigen des Lizenz Caches, wenn diese ablaufen. Es muss ein externer Prozess vorhanden sein, um den Cache zu entfernen, wenn er größer als gewünscht ist.

Der wichtigste Teil des Daten Bank Wachstums ist der Schutz Lizenz Cache. Wenn das Lizenzierungs Caching nicht erforderlich ist, weil die Dienst Roundtrips die Leistung der Anwendung nicht beeinträchtigen oder der Cache zu groß werden kann, kann der Lizenz Cache deaktiviert werden. Dies wird erreicht, indem `CanCacheLicenses` für das-Objekt auf false festgelegt wird `FileProfile::Settings` .

```cpp
FileProfile::Settings profileSettings(mMipContext,
    mip::CacheStorageType::OnDiskEncrypted,
    mAuthDelegate,
    std::make_shared<sample::consent::ConsentDelegateImpl>(),
    std::make_shared<FileProfileObserver>());

profileSettings.SetCanCacheLicenses(false);
```

### <a name="caching-api-engines"></a>Caching-API-Engines

In der Regel wird im MIP SDK für jeden Benutzer, der einen API-Vorgang ausführt, eine API-Engine erstellt und eine Schnittstelle für alle Vorgänge bereitgestellt, die im Auftrag einer authentifizierten Identität ausgeführt werden. Wie in den [Profilen "Profiles and Engines Concepts](concept-profile-engine-cpp.md)" beschrieben, gibt es für die Datei-Engine, die policyengine oder das Schutzmodul jeweils `CREATED` zwei Zustände `LOADED` Eine Engine muss erstellt und geladen werden, damit Sie SDK-Vorgänge ausführen kann. Wenn eine Engine nicht verwendet wird, speichert die API die Engine zwischen und speichert Sie `CREATED` so lange wie möglich im Zustand, abhängig von den verfügbaren Ressourcen. Die Profilklasse der jeweiligen API bietet auch eine-Methode `UnloadEngineAsync` , um dies explizit zu erreichen.

Jedes Modul verfügt über einen eindeutigen Bezeichner `id` , der in allen Engine-Verwaltungs Vorgängen verwendet wird. Die Client Anwendung kann eine ID explizit bereitstellen, oder das SDK kann eine ID generieren, wenn Sie nicht von der Anwendung bereitgestellt wird. Wenn ein eindeutiger Bezeichner zum Zeitpunkt der Erstellung der Engine mithilfe von Engine-Einstellungs Objekten bereitgestellt wird und das Zwischenspeichern wie oben beschrieben im API-Profil aktiviert ist, können dieselben Engines immer dann verwendet werden, wenn der Benutzer einen Vorgang mit dem SDK ausführt. Befolgen Sie die Code Ausschnitte zum Erstellen `[mip::FileEngine](./concept-profile-engine-file-engine-cpp.md#create-file-engine-settings)` einer `[mip::PolicyEngine](./concept-profile-engine-policy-engine-cpp.md#implementation-create-policy-engine-settings)` .

Wenn Sie eine vorhandene Engine-ID nicht bereitstellen, führt dies zu zusätzlichen Dienst Roundtrips zum Abrufen der Richtlinie und zum Abrufen von Lizenzen, die möglicherweise bereits für die vorhandene Engine zwischengespeichert wurden. Durch das Zwischenspeichern der Engine-ID wird der SDK-Offline Zugriff auf zuvor entschlüsselte Informationen und allgemeine Leistungsverbesserungen beeinträchtigt.