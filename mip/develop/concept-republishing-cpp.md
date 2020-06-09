---
title: Erneutes Veröffentlichen im MIP SDK
description: In diesem Artikel erfahren Sie, wie Sie das Szenario für die Wiederverwendung des Schutz Handlers für das erneute Veröffentlichen von Szenarien verstehen.
author: Pathak-Aniket
ms.service: information-protection
ms.topic: conceptual
ms.date: 05/01/2020
ms.author: v-anikep
ms.openlocfilehash: 87be5fd0cc0650687a0c2b8ddf3b9b34e05d9c88
ms.sourcegitcommit: a1feede30ac1f54e900e52eb45b3e6634e0f13f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84548291"
---
# <a name="republishing-c"></a>Wiederveröffentlichung (C++)

## <a name="overview"></a>Übersicht

Diese Übersicht konzentriert sich auf das erneute Veröffentlichen im MIP SDK. Dies ist ein spezielles Szenario, das auftritt, wenn eine Anwendung einem Benutzer die Bearbeitung der Datei gestatten muss, aber die ursprünglichen [Veröffentlichungs Lizenz](https://techcommunity.microsoft.com/t5/enterprise-mobility-security/licenses-and-certificates-and-how-ad-rms-protects-and-consumes/ba-p/247309) Informationen über Besitzer, Rechte, Inhalts Schlüssel usw. erhalten möchte.

Das Muster könnte etwa wie folgt aussehen:

- Ein Benutzer öffnet ein geschütztes Dokument zur Bearbeitung.
- Der Benutzer darf nur die Datei bearbeiten können, wenn ihm die entsprechenden Rechte erteilt wurden.
- Der Benutzer bearbeitet das Dokument und speichert es dann.

Der MIP SDK-Pseudo Code zum Ausführen dieser Aufgabe kann wie folgt aussehen:

- Erstellen `mip::FileHandler` Sie eine, die auf die Zieldatei zeigt.
- Speichert den, der `mip::ProtectionHandler` von der-Methode verfügbar gemacht wird `mip::FileHandler` `GetProtection()` .
- Überprüfen Sie, ob der Benutzer über **Bearbeitungs** Rechte verfügt, indem Sie `AccessCheck()` Methode aufrufen
- Verwenden `mip::FileHandler` Sie `GetDecryptedTemporaryFileAsync()` oder `GetDecryptedTemporaryStreamAsync()` , um eine temporäre entschlüsselte Ausgabe zu erhalten.
- Bearbeiten Sie die temporären Dateien, und speichern Sie Sie.
- Erstellen Sie eine neue `mip::FileHandler` -Instanz, die auf die temporäre Datei verweist, und verwenden Sie die- `SetProtection()` Methode, um die gespeicherte als-Parameter bereitzustellen `mip::ProtectionHandler`
- Führen Sie für die Änderung einen Commit aus.

Die Verwendung `mip::ProtectionHandler` von aus der ursprünglichen Datei, Besitzer, Inhalts-ID, Inhalts Schlüssel usw. wird auf dem bearbeiteten Dokument beibehalten. Dieses neuveröffentlichungs Szenario erfordert, dass die Anwendung einen Verweis auf die ursprüngliche-Version beibehält `mip::ProtectionHandler` .

## <a name="implementation"></a>Implementierung

Wie bereits erläutert, macht die- `mip::FileHandler` Klasse Methoden zum Lesen, schreiben und Entfernen von Bezeichnungen und Schutz Informationen verfügbar. Die vollständige Liste der unterstützten Vorgänge finden Sie in der [API-Referenz](./reference/class_mip_filehandler.md#summary).

In diesem Szenario werden die folgenden Methoden von verwendet `mip::FileHandler` :

- `GetProtection()`
- `CommitAsync()`
- `GetDecryptedTemporaryFileAsync()`
- `SetProtection()`

Das Szenario verwendet auch `mip::ProtectionHandler` , das die Funktionen zum Verschlüsseln und entschlüsseln geschützter Streams und Puffer, zum Durchführen von Zugriffs Überprüfungen, zum Abrufen der Veröffentlichungs Lizenz und zum Abrufen von Attributen aus den geschützten Informationen verfügbar macht. Die- `AccessCheck()` Methode wird verwendet, um zu überprüfen, ob der Benutzer berechtigt ist, die Datei zu bearbeiten.

Überprüfen Sie die Schnellstarts unter "nächste Schritte", und stellen Sie sicher, dass die Anwendung die Bezeichnungen erstellt und erfolgreich auflisten kann, um dieses Szenario zum erneuten schützen erfolgreich abzuschließen.

## <a name="create-a-protection-handler-from-the-file-and-decrypt-the-file"></a>Erstellen Sie einen Schutz Handler aus der Datei, und entschlüsseln Sie die Datei.

`mip::ProtectionHandler`macht die Funktionen zum Verschlüsseln und entschlüsseln geschützter Streams und Puffer, zum Durchführen von Zugriffs Überprüfungen, zum Abrufen der Veröffentlichungs Lizenz und zum Abrufen von Attributen aus den geschützten Informationen verfügbar. `mip::ProtectionHandler`Objekte werden erstellt, indem entweder ein Schutz Deskriptor oder eine serialisierte Veröffentlichungs Lizenz bereitgestellt wird. In diesem Anwendungsfall wird die Veröffentlichungs Lizenz implizit verwendet, wenn die Veröffentlichungs Lizenz beim Entschlüsseln von bereits geschütztem Inhalt oder beim Schutz von Inhalten verwendet wird, in denen die Lizenz bereits erstellt wurde.

`mip::FileHandler`macht eine Methode mit dem Namen verfügbar `GetProtection()` , die `mip::ProtectionHandler` aus der Datei abruft, die dem zugeordnet ist `mip::FileHandler` . Nachdem das `mip::ProtectionHandler` Objekt abgerufen wurde, kann das gleiche verwendet werden, um die Zugriffsebenen des Benutzers zu überprüfen, die Datei zu entschlüsseln und die Datei später zu verschlüsseln, nachdem Sie bearbeitet wurde.

`mip::ProtectionHandler``AccessCheck()`wird verwendet, um zu überprüfen, ob der Benutzer über ein bestimmtes Recht auf die Datei verfügt, und gibt abhängig vom Ergebnis eine boolesche Antwort zurück. Um beispielsweise zu überprüfen, ob der Benutzer über die Berechtigung zum Bearbeiten verfügt, müssen Sie die-Methode mit dem Wert "Edit" (Bearbeiten) abrufen. Wenn das Ergebnis *true*ist, können Sie es dem Benutzer ermöglichen, die Datei zu bearbeiten. Nachdem das **Bearbeitungs** Recht überprüft wurde, verwenden `mip::FileHandler` `GetDecryptedTemporaryFileAsync()` Sie, um die temporäre entschlüsselte Datei abzurufen.

Weitere Informationen zu den verschiedenen Benutzerrechten finden Sie unter [Benutzerrechte für Azure Information Protection](/azure/information-protection/configure-usage-rights).

 > [!IMPORTANT]
 > Zugriffs Überprüfungen und-Erzwingungen sind ausschließlich für den Anwendungsentwickler durchzuführen. Ein Benutzer mit Ansichts rechten ist in der Lage, die geschützten Informationen zu entschlüsseln. Es liegt an der Anwendung, die dem Benutzer gewährten Rechte zu überprüfen und diese Rechte über Information Protection-Steuerelemente zu erzwingen, z. b. das verhindern von Kopien, das Bearbeiten oder das durch nehmen von Screenshots. Wenn Sie Schutz Steuerungen nicht ordnungsgemäß implementieren, kann dies zu sensiblen Informationen führen.

## <a name="save-and-publish-the-edited-file-by-applying-protection"></a>Speichern und Veröffentlichen der bearbeiteten Datei durch Anwenden des Schutzes

Nachdem die Datei entschlüsselt wurde, kann Sie bearbeitet werden. Nachdem der Bearbeitungsvorgang abgeschlossen ist, kann ein Commit für die Änderungen durchgeführt werden. Erstellen Sie ein- `IFileHandler` Objekt mithilfe der obigen temporären Datei für die Verarbeitung der Datei mit Commit. Die temporäre Datei kann dann mithilfe des `IProtectionHandler` aus der ursprünglichen Datei abgerufenen Objekts geschützt werden.

## <a name="next-steps"></a>Nächste Schritte

- [Lesen Sie den Schnellstart für die Wiederveröffentlichung für C++](quick-file-republishing-cpp.md)
- [Überprüfen der erneuten Veröffentlichung: [Lesen Sie den Schnellstart für die Wiederveröffentlichung für C++](quick-file-republishing-cpp.md) für C. #](quick-file-republishing-csharp.md)