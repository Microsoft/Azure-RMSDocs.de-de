---
title: Häufig gestellte Fragen und bekannte Probleme – Microsoft Information Protection SDK
description: Häufig gestellte Fragen zum Microsoft Information Protection SDK (MIP SDK) und Hilfestellung zur Fehlerbehandlung bei Problemen und Fehlern
author: msmbaldwin
ms.service: information-protection
ms.topic: troubleshooting
ms.collection: M365-security-compliance
ms.date: 03/05/2019
ms.author: mbaldwin
ms.openlocfilehash: 78dc655d8244378fcc37b22030d3060fd291ef16
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "60175467"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>Microsoft Information Protection (MIP) SDK: Häufig gestellte Fragen und Probleme

Dieser Artikel enthält Antworten auf häufig gestellte Fragen (FAQs) und Anleitungen zur Fehlerbehandlung für bekannte Probleme und häufige Fehler.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen 

### <a name="sdk-string-handling"></a>SDK-Zeichen folgen Behandlung

**Frage**: wie verarbeitet das SDK Zeichen folgen und welchen Zeichen Folgentyp sollte ich in meinem Code verwenden?

Das SDK ist für die plattformübergreifende Verwendung konzipiert und nutzt [UTF-8](https://wikipedia.org/wiki/UTF-8) (8-Bit Unicode Transformation Format) für die Zeichenfolgenverarbeitung. Die genaue Verarbeitung hängt von der verwendeten Plattform ab:

| Plattform | Leitlinien |
|-|-|
| Windows-systemeigen | Für SDK-Clients für C++ wird der C++-Standardbibliothektyp [`std::string`](https://wikipedia.org/wiki/C%2B%2B_string_handling) für die Übergabe von Zeichenfolgen an/aus API-Funktionen verwendet. Die Konvertierung von/in UTF-8 wird intern vom MSIP SDK verwaltet. Wenn eine API `std::string` zurückgibt, müssen Sie die UTF-8-Codierung erwarten und diese beim Konvertieren der Zeichenfolge entsprechend verwalten. In einigen Fällen wird eine Zeichenfolge als Teil eines `uint8_t`-Vektors zurückgegeben (z.B. eine Veröffentlichungslizenz), sollte aber wie ein undurchsichtiger Blob behandelt werden.<br><br>Weitere Informationen und Beispiele finden Sie hier:<ul><li>[WideCharToMultiByte-Funktion](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte) zur Unterstützung beim Konvertieren von Breitzeichen-Zeichenfolgen in Multibyte, z.B. UTF-8.<li>Die folgenden Beispieldateien sind im [SDK-Download](setup-configure-mip.md#configure-your-client-workstation) enthalten:<ul><li>Beispielhafte Zeichenfolgen-Hilfsprogrammfunktionen in `file\samples\common\string_utils.cpp` zum Konvertieren in/aus UTF-8-Breitzeichen-Zeichenfolgen.<li>Eine Implementierung von `wmain(int argc, wchar_t *argv[])` in `file\samples\file\main.cpp`, die die vorhergehenden Zeichenfolgen-Konvertierungsfunktionen verwendet.</li></ul></ul>|
| .NET | Für SDK-Clients für .NET verwenden alle Zeichenfolgen die standardmäßige UTF-16-Codierung und ist keine spezielle Konvertierung erforderlich. Die Konvertierung von/in UTF-16 wird intern vom MSIP SDK verwaltet. |
| Andere Plattformen | Alle anderen Plattformen, die vom MSIP SDK unterstützt werden, bieten native Unterstützung für UTF-8. |

## <a name="issues-and-errors-reference"></a>Referenz zu Problemen und Fehlern

### <a name="error-file-format-not-supported"></a>Fehler: „Nicht unterstütztes Dateiformat“  

**Frage**: Warum erhalte ich die folgende Fehlermeldung, wenn ich versuche, eine PDF-Datei zu schützen oder zu bezeichnen?

> Dateiformat wird nicht unterstützt.

Diese Ausnahme tritt beim Versuch auf, eine PDF-Datei zu schützen oder zu bezeichnen, die digital signiert oder mit einem Kennwort geschützt ist. Weitere Informationen zum Schützen und Bezeichnen von PDF-Dateien finden Sie unter [Neue Unterstützung für die PDF-Verschlüsselung mit Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757).

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>Fehlermeldung: Die abgerufene Konformitätsrichtlinie konnte nicht analysiert werden.  

**Frage**: Warum erhalte ich nach dem Herunterladen des MIP SDK den folgenden Fehler, und es wird versucht, das Datei Beispiel zum Auflisten aller Bezeichnungen zu verwenden?

> Es ist ein Fehler aufgetreten: Fehler beim Analysieren der erworbenen Konformitäts Richtlinie. Fehler mit: [Class MIP:: compliancepolicyparameterexception] Tag nicht gefunden: Policy, NodeType: 15, Name: kein Name gefunden, Wert:, Vorgänger: <SyncFile><Content>, CorrelationId: [34668a40-BLLL-4ef8-b2af-00005aa674z9]

Dies bedeutet, dass Sie Ihre Bezeichnungen nicht von Azure Information Protection zur vereinheitlichten Bezeichnung migriert haben. Unter [Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center](/azure/information-protection/configure-policy-migrate-labels) erfahren Sie, wie Sie Bezeichnungen migrieren und dann eine Bezeichnungsrichtlinie in Office 365 Security & Compliance Center erstellen. 

### <a name="error-systemcomponentmodelwin32exception-loadlibrary-failed"></a>Fehler: "System. ComponentModel. Win32Exception: Fehler bei LoadLibrary"

**Frage**: Warum erhalte ich bei Verwendung des MIP SDK .NET-Wrappers den folgenden Fehler:

> System. ComponentModel. Win32Exception: Fehler bei LoadLibrary für: [sdk_wrapper_dotnet. dll], wenn MIP aufgerufen wird. Initialisieren ().

Die Anwendung verfügt nicht über die erforderliche Laufzeit oder wurde nicht als Release erstellt. Weitere Informationen finden [Sie unter sicherstellen, dass Ihre APP über die erforderliche Laufzeit verfügt](setup-configure-mip.md#ensure-your-app-has-the-required-runtime) . 

### <a name="error-proxyautherror-exception"></a>Fehler: "proxyautherror Exception"

**Frage**: Warum erhalte ich bei Verwendung des MIP SDK den folgenden Fehler:

> "Proxyauthentieronerror: die Proxy Authentifizierung wird nicht unterstützt."

Das MIP SDK unterstützt nicht die Verwendung von authentifizierten Proxys. Um diese Meldung zu beheben, sollten Proxy Administratoren die Microsoft Information Protection-Dienst Endpunkte festlegen, um den Proxy zu umgehen. Eine Liste mit diesen Endpunkten finden Sie auf der Seite [URLs und IP-Adressbereiche von Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) . MIP SDK erfordert, dass `*.protection.outlook.com` (Zeile 9) und die Azure Information Protection Dienst Endpunkte (Zeile 73) die Proxy Authentifizierung umgehen.
