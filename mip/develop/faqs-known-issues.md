---
title: Häufig gestellte Fragen und bekannte Probleme – Microsoft Information Protection SDK
description: Häufig gestellte Fragen zum Microsoft Information Protection SDK (MIP SDK) und Hilfestellung zur Fehlerbehandlung bei Problemen und Fehlern
author: msmbaldwin
ms.service: information-protection
ms.topic: troubleshooting
ms.collection: M365-security-compliance
ms.date: 03/05/2019
ms.author: mbaldwin
ms.openlocfilehash: 97b9fdb53c103eac94e62ddb6438c57e4c9f45cc
ms.sourcegitcommit: 50e6b94bdb387cfa35d0e565b1e89f9e69563a63
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57581724"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>Microsoft Information Protection (MIP) SDK: Häufig gestellte Fragen und Probleme

Dieser Artikel enthält Antworten auf häufig gestellte Fragen (FAQs) und Anleitungen zur Fehlerbehandlung für bekannte Probleme und häufige Fehler.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen 

### <a name="sdk-string-handling"></a>Behandlung von SDK-Zeichenfolgen

**Frage**: Wie werden die Zeichenfolgen für das SDK behandelt und welche Art von Zeichenfolge sollte ich in meinem Code verwenden?

Das SDK ist für die plattformübergreifende Verwendung konzipiert und nutzt [UTF-8](https://wikipedia.org/wiki/UTF-8) (8-Bit Unicode Transformation Format) für die Zeichenfolgenverarbeitung. Die genaue Verarbeitung hängt von der verwendeten Plattform ab:

| Platform | Leitlinien |
|-|-|
| Windows-systemeigen | Für SDK-Clients für C++ wird der C++-Standardbibliothektyp [`std::string`](https://wikipedia.org/wiki/C%2B%2B_string_handling) für die Übergabe von Zeichenfolgen an/aus API-Funktionen verwendet. Die Konvertierung von/in UTF-8 wird intern vom MSIP SDK verwaltet. Wenn eine API `std::string` zurückgibt, müssen Sie die UTF-8-Codierung erwarten und diese beim Konvertieren der Zeichenfolge entsprechend verwalten. In einigen Fällen wird eine Zeichenfolge als Teil eines `uint8_t`-Vektors zurückgegeben (z.B. eine Veröffentlichungslizenz), sollte aber wie ein undurchsichtiger Blob behandelt werden.<br><br>Weitere Informationen und Beispiele finden Sie hier:<ul><li>[WideCharToMultiByte-Funktion](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte) zur Unterstützung beim Konvertieren von Breitzeichen-Zeichenfolgen in Multibyte, z.B. UTF-8.<li>Die folgenden Beispieldateien sind im [SDK-Download](setup-configure-mip.md#configure-your-client-workstation) enthalten:<ul><li>Beispielhafte Zeichenfolgen-Hilfsprogrammfunktionen in `file\samples\common\string_utils.cpp` zum Konvertieren in/aus UTF-8-Breitzeichen-Zeichenfolgen.<li>Eine Implementierung von `wmain(int argc, wchar_t *argv[])` in `file\samples\file\main.cpp`, die die vorhergehenden Zeichenfolgen-Konvertierungsfunktionen verwendet.</li></ul></ul>|
| .NET | Für SDK-Clients für .NET verwenden alle Zeichenfolgen die standardmäßige UTF-16-Codierung und ist keine spezielle Konvertierung erforderlich. Die Konvertierung von/in UTF-16 wird intern vom MSIP SDK verwaltet. |
| Andere Plattformen | Alle anderen Plattformen, die vom MSIP SDK unterstützt werden, bieten native Unterstützung für UTF-8. |

## <a name="issues-and-errors-reference"></a>Referenz zu Problemen und Fehlern

### <a name="error-file-format-not-supported"></a>Fehler: "File-Format nicht unterstützt"  

**Frage**: Warum erhalte ich den folgenden Fehler beim Schützen oder eine PDF-Datei zu bezeichnen?

> Nicht unterstütztes Dateiformat

Diese Ausnahme resultiert aus der Versuch, schützen oder Bezeichnung eine PDF-Datei, die digital signiert wurde oder ein Kennwort geschützt. Weitere Informationen zum Schützen und Bezeichnen von PDF-Dateien finden Sie unter [Neue Unterstützung für die PDF-Verschlüsselung mit Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757).

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>Fehler: "Fehler beim Analysieren der abgerufenen Konformitätsrichtlinie"  

**Frage**: Warum erhalte ich den folgenden Fehler, nach dem das MIP SDK herunterladen und es wird versucht, das Beispiel zu verwenden, um alle Bezeichnungen aufzulisten?

> Ein Fehler ist aufgetreten: Fehler beim Analysieren der Konformitätsrichtlinie abgerufen. Fehler bei der: [Klasse mip::CompliancePolicyParserException] das Tag nicht gefunden: NodeType-Richtlinie: 15, Name: Kein Name gefunden, Wert:, Vorgänger: <SyncFile> <Content>, CorrelationId: [34668a40-Blll-4ef8-b2af-00005aa674z9]

Dies gibt an, dass Sie Ihre Bezeichnungen von Azure Information Protection, das einheitliche Funktionen für Bezeichnung noch nicht migriert. Unter [Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center](/azure/information-protection/configure-policy-migrate-labels) erfahren Sie, wie Sie Bezeichnungen migrieren und dann eine Bezeichnungsrichtlinie in Office 365 Security & Compliance Center erstellen. 

### <a name="error-systemcomponentmodelwin32exception-loadlibrary-failed"></a>Fehler: "System.ComponentModel.Win32Exception: LoadLibrary konnte"

**Frage**: Warum erhalte ich die Fehlermeldung bei Verwendung der MIP SDK .NET Wrapper?

> System.ComponentModel.Win32Exception: LoadLibrary konnte für: [sdk_wrapper_dotnet.dll] beim MIP aufrufen. Initialize().

Ihre Anwendung verfügt nicht über die erforderliche Laufzeit, oder nicht als Version erstellt wurde. Finden Sie unter [stellen Sie sicher, Ihre app verfügt über die erforderliche Laufzeit](setup-configure-mip.md#ensure-your-app-has-the-required-runtime) für Weitere Informationen. 
