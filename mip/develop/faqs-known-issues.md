---
title: Häufig gestellte Fragen und bekannte Probleme – Microsoft Information Protection SDK
description: Häufig gestellte Fragen zum Microsoft Information Protection SDK (MIP SDK) und Hilfestellung zur Fehlerbehandlung bei Problemen und Fehlern
author: msmbaldwin
ms.service: information-protection
ms.topic: troubleshooting
ms.date: 03/05/2019
ms.author: mbaldwin
ms.openlocfilehash: 0f7fd7ebceb38700953d8b3e33daf5385176afa0
ms.sourcegitcommit: 7420cf0200c90687996124424a254c289b11a26f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844284"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>Microsoft Information Protection (MIP) SDK: Häufig gestellte Fragen und Probleme

Dieser Artikel enthält Antworten auf häufig gestellte Fragen (FAQs) und Anleitungen zur Fehlerbehandlung für bekannte Probleme und häufige Fehler.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="metadata-storage-changes"></a>Metadatenspeicheränderungen

Wir [haben kürzlich angekündigt](https://aka.ms/mipsdkmetadata) , dass wir eine Änderung am Speicherort der Bezeichnungs Metadaten für Office-Dateien (Word, Excel, PowerPoint) vornehmen, um neue Features in Office 365, SharePoint Online und anderen Diensten zu unterstützen.

#### <a name="metadata-faq"></a>FAQ zu Metadaten

**Frage**: Wann werden die ersten Features verfügbar, die diesen neuen Speicherort erfordern?

- Wir gehen davon aus, dass die ersten Features im zweiten Quartal des Kalenderjahres 2021 verfügbar sein werden. Kunden können sich zuvor an der privaten oder öffentlichen Vorschau anmelden.  

**Frage**: sind andere Formate betroffen, z. b. PDF?

- Nein, nur Office-Dateien, insbesondere Word-, Excel-und PowerPoint-Dateien.

**Frage**: gibt es eine bestimmte Version des MIP SDK, die erforderlich ist?

- MIP SDK 1,7 und höher sind vollständig kompatibel.

**Frage**: gibt es eine bestimmte Version des Office-Clients, die benötigt wird oder diesen Speicher verwenden?

- Wenn Features angekündigt werden, wird der Office-Client aktualisiert, um den neuen Speicherort zu nutzen. Die neuen Speicherorte werden erst verwendet, wenn die Features von Mandanten Administratoren aktiviert wurden.

**Frage**: werden die vorhandenen Metadaten, die als benutzerdefinierte Eigenschaft in gespeichert werden, in *custom.xml* auf dem neuesten Stand gehalten werden?

- Nein. Wenn das Dokument zum ersten Mal gespeichert wird, nachdem der neue Speicherort aktiviert wurde, werden die Bezeichnungs Metadaten an den neuen Speicherort verschoben. Über geschriebene Metadaten [`LabelingOptions.ExtendedProperties`](/dotnet/api/microsoft.informationprotection.file.labelingoptions.extendedproperties?view=mipsdk-dotnet-1.7#Microsoft_InformationProtection_File_LabelingOptions_ExtendedProperties) verbleiben in *custom.xml*.

**Frage**: ist es möglich, die Bezeichnungs Metadaten ohne MIP SDK zu lesen? 

- Ja, aber Sie müssen eigenen Code implementieren, um die Datei zu analysieren und die Informationen zu extrahieren.

**Frage**: derzeit ist es einfach, die Bezeichnung zu "lesen", indem die Schlüssel-Wert-Paar-Zeichen folgen aus der Datei extrahiert werden. Ist das Lesen auf diese Weise weiterhin möglich? 

- Ja, die Metadaten sind weiterhin in der zu lesenden Office-Datei verfügbar. Es sollte jedoch beachtet werden, dass Ihre Anwendung wissen muss, ob der neue Featuresatz aktiviert ist, um zu ermitteln, welcher Abschnitt autoritativ ist (custom.xml vs. labelinfo.xml). Überprüfen von [MS-offcrypto: Labelinfo im Vergleich zu benutzerdefinierten Dokumenteigenschaften | Microsoft-Dokumentation.](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341) für Implementierungsdetails.
  
**Frage**: Wie kann ich ermitteln, ob die neuen Features aktiviert sind? 

- Wir geben diese Informationen an, wenn wir uns mit den featureveröffentlichungsdates nähern. 

**Frage**: wie werden Bezeichnungen migriert?

- Die folgende Logik wird verwendet, um zu bestimmen, welcher Abschnitt gelesen und zum Lesen oder Schreiben von Bezeichnungs Daten verwendet wird.

| Aktion                                                                                                | Feature nicht aktiviert                                                                    | Feature aktiviert                                              |
| ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Lesen                                                                                                  | Bezeichnung in custom.xml (ungeschützt) oder doc SummaryInfo (geschützt).                      | Wenn die Bezeichnung in labelinfo.xml vorhanden ist, handelt es sich um die effektive Bezeichnung.<br> Wenn labelinfo.xml keine Bezeichnung enthält, ist die Bezeichnung in custom.xml oder doc SummaryInfo die effektive Bezeichnung. |
| Schreiben                                                                                                 | Alle neuen Bezeichnungen werden in custom.xml (ungeschützt) oder doc SummaryInfo (geschützt) geschrieben. | Alle neuen Bezeichnungen werden in labelinfo.xml geschrieben.                 |


<br>
<br>

### <a name="file-parsing"></a>Dateiverarbeitung

**Frage**: kann ich in dieselbe Datei schreiben, die zurzeit mit dem Datei-SDK gelesen wird?

Das MIP SDK unterstützt das gleichzeitige lesen und Schreiben derselben Datei nicht. Alle gekennzeichneten Dateien führen zu einer *Kopie* der Eingabedatei, auf die die Bezeichnungs Aktionen angewendet werden. Die Anwendung muss den ursprünglichen durch die bezeichnete Datei ersetzen.

### <a name="sdk-string-handling"></a>SDK-Zeichen folgen Behandlung

**Frage**: wie verarbeitet das SDK Zeichen folgen und welchen Zeichen Folgentyp sollte ich in meinem Code verwenden?

Das SDK ist für die plattformübergreifende Verwendung konzipiert und nutzt [UTF-8](https://wikipedia.org/wiki/UTF-8) (8-Bit Unicode Transformation Format) für die Zeichenfolgenverarbeitung. Die genaue Verarbeitung hängt von der verwendeten Plattform ab:

| Plattform        | Anleitungen                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Windows-systemeigen  | Für C++ SDK-Clients wird der C++-Standard Bibliothekstyp [`std::string`](https://wikipedia.org/wiki/C%2B%2B_string_handling) zum Übergeben von Zeichen folgen an/von API-Funktionen verwendet. Die Konvertierung von/in UTF-8 wird intern vom MSIP SDK verwaltet. Wenn eine API `std::string` zurückgibt, müssen Sie die UTF-8-Codierung erwarten und diese beim Konvertieren der Zeichenfolge entsprechend verwalten. In einigen Fällen wird eine Zeichenfolge als Teil eines `uint8_t`-Vektors zurückgegeben (z.B. eine Veröffentlichungslizenz), sollte aber wie ein undurchsichtiger Blob behandelt werden.<br><br>Weitere Informationen und Beispiele finden Sie hier:<ul><li>[WideCharToMultiByte-Funktion](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte) zur Unterstützung beim Konvertieren von Breitzeichen-Zeichenfolgen in Multibyte, z.B. UTF-8.<li>Die folgenden Beispieldateien sind im [SDK-Download](setup-configure-mip.md#configure-your-client-workstation) enthalten:<ul><li>Beispielhafte Zeichenfolgen-Hilfsprogrammfunktionen in `file\samples\common\string_utils.cpp` zum Konvertieren in/aus UTF-8-Breitzeichen-Zeichenfolgen.<li>Eine Implementierung von `wmain(int argc, wchar_t *argv[])` in `file\samples\file\main.cpp`, die die vorhergehenden Zeichenfolgen-Konvertierungsfunktionen verwendet.</li></ul></ul> |
| .NET            | Für SDK-Clients für .NET verwenden alle Zeichenfolgen die standardmäßige UTF-16-Codierung und ist keine spezielle Konvertierung erforderlich. Die Konvertierung von/in UTF-16 wird intern vom MSIP SDK verwaltet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Andere Plattformen | Alle anderen Plattformen, die vom MSIP SDK unterstützt werden, bieten native Unterstützung für UTF-8.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

## <a name="issues-and-errors-reference"></a>Referenz zu Problemen und Fehlern

### <a name="error-file-format-not-supported"></a>Fehler: „Nicht unterstütztes Dateiformat“  

**Frage**: Warum erhalte ich die folgende Fehlermeldung, wenn ich versuche, eine PDF-Datei zu schützen oder zu bezeichnen?

> Nicht unterstütztes Dateiformat

Diese Ausnahme tritt beim Versuch auf, eine PDF-Datei zu schützen oder zu bezeichnen, die digital signiert oder mit einem Kennwort geschützt ist. Weitere Informationen zum Schützen und Bezeichnen von PDF-Dateien finden Sie unter [Neue Unterstützung für die PDF-Verschlüsselung mit Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757).

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>Fehlermeldung: Die abgerufene Konformitätsrichtlinie konnte nicht analysiert werden.  

**Frage**: Warum erhalte ich nach dem Herunterladen des MIP SDK den folgenden Fehler, und es wird versucht, das Datei Beispiel zum Auflisten aller Bezeichnungen zu verwenden?

> Ein Fehler ist aufgetreten. Die abgerufene Konformitätsrichtlinie konnte nicht analysiert werden. Fehler: [class mip::CompliancePolicyParserException] Tag wurde nicht gefunden: Richtlinie, NodeType: 15, Name: Kein Name gefunden, Wert: , Vorgänger: <SyncFile><Content>, correlationId:[34668a40-blll-4ef8-b2af-00005aa674z9]

Dieser Fehler weist darauf hin, dass Sie Ihre Bezeichnungen nicht von Azure Information Protection zur vereinheitlichten Bezeichnung migriert haben. Unter [Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center](/azure/information-protection/configure-policy-migrate-labels) erfahren Sie, wie Sie Bezeichnungen migrieren und dann eine Bezeichnungsrichtlinie in Office 365 Security & Compliance Center erstellen. 

### <a name="error-nopolicyexception-label-policy-did-not-contain-data"></a>Fehler: "nopolicyexception: die Bezeichnungs Richtlinie enthielt keine Daten"

**Frage**: Warum erhalte ich die folgende Fehlermeldung, wenn ich versuche, eine Bezeichnung oder Listen Bezeichnungen über MIP SDK zu lesen?

> Nopolicyexception: die Bezeichnungs Richtlinie enthielt keine Daten, CorrelationId = GUID, CorrelationId. Description = policyprofile, nopolicyerror. Category = syncfile, nopolicyerror. Category = syncfile

Dieser Fehler zeigt an, dass eine Bezeichnungs Richtlinie nicht im Microsoft Security and Compliance Center veröffentlicht wurde. Befolgen Sie die Anweisungen unter [Erstellen und Konfigurieren von Vertraulichkeits Bezeichnungen und deren Richtlinien](/microsoft-365/compliance/create-sensitivity-labels) zum Konfigurieren der Bezeichnung.

### <a name="error-systemcomponentmodelwin32exception-loadlibrary-failed"></a>Fehler: "System. ComponentModel. Win32Exception: Fehler bei LoadLibrary"

**Frage**: Warum erhalte ich bei Verwendung des MIP SDK .NET-Wrappers den folgenden Fehler:

> System. ComponentModel. Win32Exception: Fehler bei LoadLibrary für: [sdk_wrapper_dotnet.dll] beim Aufrufen von MIP.Initialize ().

Die Anwendung verfügt nicht über die erforderliche Laufzeit oder wurde nicht als Release erstellt. Weitere Informationen finden [Sie unter sicherstellen, dass Ihre APP über die erforderliche Laufzeit verfügt](setup-configure-mip.md#ensure-your-app-has-the-required-runtime) . 

### <a name="error-proxyautherror-exception"></a>Fehler: "proxyautherror Exception"

**Frage**: Warum erhalte ich bei Verwendung des MIP SDK den folgenden Fehler:

> "Proxyauthentieronerror: die Proxy Authentifizierung wird nicht unterstützt."

Das MIP SDK unterstützt nicht die Verwendung von authentifizierten Proxys. Um diese Meldung zu beheben, sollten Proxy Administratoren die Microsoft Information Protection-Dienst Endpunkte festlegen, um den Proxy zu umgehen. Eine Liste mit diesen Endpunkten finden Sie auf der Seite [URLs und IP-Adressbereiche von Office 365](/office365/enterprise/urls-and-ip-address-ranges) . Das MIP SDK erfordert, dass `*.protection.outlook.com` (Zeile 9) und die Azure Information Protection Dienst Endpunkte (Zeile 73) die Proxy Authentifizierung umgehen.