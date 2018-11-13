---
title: Häufig gestellte Fragen und bekannte Probleme – Microsoft Information Protection SDK
description: Häufig gestellte Fragen zum Microsoft Information Protection SDK (MIP SDK) und Hilfestellung zur Fehlerbehandlung bei Problemen und Fehlern
author: BryanLa
ms.service: information-protection
ms.topic: troubleshooting
ms.date: 10/19/2018
ms.author: bryanla
ms.openlocfilehash: f213b31d9b0e41ea9c1e076055a90e9f62b31b3a
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223924"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>Microsoft Information Protection (MIP) SDK: Häufig gestellte Fragen und Probleme

Dieser Artikel enthält Antworten auf häufig gestellte Fragen (FAQs) und Anleitungen zur Fehlerbehandlung für bekannte Probleme und häufige Fehler.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen 

### <a name="question-which-platforms-are-supported-by-the-mip-sdk"></a>Frage: Welche Plattformen unterstützt das MSIP SDK?

Das MIP SDK wird auf den folgenden Plattformen unterstützt:

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

### <a name="question-how-does-the-sdk-handle-strings-and-what-string-type-should-i-be-using-in-my-code"></a>Frage: Wie verarbeitet das SDK Zeichenfolgen, und welchen Zeichenfolgentyp sollte ich in meinem Code verwenden?

Das SDK ist für die plattformübergreifende Verwendung konzipiert und nutzt [UTF-8](https://wikipedia.org/wiki/UTF-8) (8-Bit Unicode Transformation Format) für die Zeichenfolgenverarbeitung. Die genaue Verarbeitung hängt von der verwendeten Plattform ab:

| Plattform | Leitlinien |
|-|-|
| Windows-systemeigen | Für SDK-Clients für C++ wird der C++-Standardbibliothektyp [`std::string`](https://wikipedia.org/wiki/C%2B%2B_string_handling) für die Übergabe von Zeichenfolgen an/aus API-Funktionen verwendet. Die Konvertierung von/in UTF-8 wird intern vom MSIP SDK verwaltet. Wenn eine API `std::string` zurückgibt, müssen Sie die UTF-8-Codierung erwarten und diese beim Konvertieren der Zeichenfolge entsprechend verwalten. In einigen Fällen wird eine Zeichenfolge als Teil eines `uint8_t`-Vektors zurückgegeben (z.B. eine Veröffentlichungslizenz), sollte aber wie ein undurchsichtiger Blob behandelt werden.<br><br>Weitere Informationen und Beispiele finden Sie hier:<ul><li>[WideCharToMultiByte-Funktion](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte) zur Unterstützung beim Konvertieren von Breitzeichen-Zeichenfolgen in Multibyte, z.B. UTF-8.<li>Die folgenden Beispieldateien sind im [SDK-Download](setup-configure-mip.md#configure-your-client-workstation) enthalten:<ul><li>Beispielhafte Zeichenfolgen-Hilfsprogrammfunktionen in `file\samples\common\string_utils.cpp` zum Konvertieren in/aus UTF-8-Breitzeichen-Zeichenfolgen.<li>Eine Implementierung von `wmain(int argc, wchar_t *argv[])` in `file\samples\file\main.cpp`, die die vorhergehenden Zeichenfolgen-Konvertierungsfunktionen verwendet.</li></ul></ul>|
| .NET | Für SDK-Clients für .NET verwenden alle Zeichenfolgen die standardmäßige UTF-16-Codierung und ist keine spezielle Konvertierung erforderlich. Die Konvertierung von/in UTF-16 wird intern vom MSIP SDK verwaltet. |
| Andere Plattformen | Alle anderen Plattformen, die vom MSIP SDK unterstützt werden, bieten native Unterstützung für UTF-8. |

## <a name="issues-and-errors-reference"></a>Referenz zu Problemen und Fehlern

### <a name="error-file-format-not-supported"></a>Fehler: „Nicht unterstütztes Dateiformat“  

| Fehler | Lösung |
|-|-|
|*Nicht unterstütztes Dateiformat*| Diese Ausnahme resultiert aus dem Versuch, eine PDF-Datei zu schützen oder zu bezeichnen, die digital signiert wurde oder mit einem Kennwort geschützt ist. Weitere Informationen zum Schützen und Bezeichnen von PDF-Dateien finden Sie unter [Neue Unterstützung für die PDF-Verschlüsselung mit Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757).|

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>Fehlermeldung: Die abgerufene Konformitätsrichtlinie konnte nicht analysiert werden.  

Sie haben das MSIP SDK heruntergeladen und die Beispielanwendungen ausgeführt. Sie möchten mithilfe des Dateibeispiels alle Bezeichnungen auflisten, doch Sie erhalten die folgende Fehlermeldung:

| Fehler | Lösung |
|-|-|
|*Ein Fehler ist aufgetreten. Die abgerufene Konformitätsrichtlinie konnte nicht analysiert werden. Fehler: [class mip::CompliancePolicyParserException] Tag wurde nicht gefunden: Richtlinie, NodeType: 15, Name: Kein Name gefunden, Wert: , Vorgänger: <SyncFile><Content>, correlationId:[34668a40-blll-4ef8-b2af-00005aa674z9]*| Das bedeutet, dass Sie Ihre Bezeichnungen nicht von Azure Information Protection zur einheitlichen Bezeichnungsumgebung migriert haben. Unter [Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center](/azure/information-protection/configure-policy-migrate-labels) erfahren Sie, wie Sie Bezeichnungen migrieren und dann eine Bezeichnungsrichtlinie in Office 365 Security & Compliance Center erstellen. Sobald das abgeschlossen ist, wird das Beispiel erfolgreich ausgeführt.|
