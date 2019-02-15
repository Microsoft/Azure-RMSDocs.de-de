---
title: Best Practices zu Sicherheitsthemen für Information Protection
description: RMS-fähige Anwendungen werden am besten mithilfe der bewährten Methoden von Information Protection erstellt.
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 12/13/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.assetid: 4e9f72d5-9e7c-43e1-bb8a-5972dd22dcee
ms.service: information-protection
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 0a9d8c0c6c86481dbce38d2cafde1c37c54b7b3e
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252859"
---
# <a name="security-best-practices-for-information-protection"></a>Best Practices zu Sicherheitsthemen für Information Protection

Das Software Development Kit (SDK) für Information Protection stellt ein stabiles System zum Veröffentlichen und Nutzen geschützter Informationen aller Art bereit. Um ein möglichst sicheres System zu erhalten, müssen für Information Protection aktivierte Anwendungen unter Berücksichtigung der Best Practices erstellt werden. Anwendungen sind gemeinsam dafür zuständig, die Sicherheit dieses Ökosystems aufrechtzuerhalten. Durch Identifizieren und Minimieren von Sicherheitsrisiken, die bei der Anwendungsentwicklung entstehen, lässt sich die Sicherheit bei der Software-Implementierung erhöhen.

Diese Informationen ergänzen den Vertrag, der unterzeichnet werden muss, um die digitalen Zertifikate für Anwendungen zu erhalten, die die SDKs verwenden.

## <a name="subjects-not-covered"></a>Nicht behandelte Inhalte

Zwar handelt es sich bei den folgenden Themen um wichtige Überlegungen zum Erstellen einer Entwicklungsumgebung und sicherer Anwendungen, sie werden jedoch nicht in diesem Artikel behandelt:

- **Verwaltung des Softwareentwicklungsprozesses** – Konfigurationsverwaltung, Schützen von Quellcode, Minimieren des Zugriffs auf Code nach dem Debuggen sowie Zuweisen von Prioritäten zu Fehlern. Für einige Kunden ist ein sichererer Softwareentwicklungsprozess von höchster Bedeutung. Einige Kunden schreiben den Ablauf eines Entwicklungsprozesses sogar vor.
- **Häufige Codierungsfehler** – Informationen zur Vermeidung von Pufferüberläufen. Es wird empfohlen, die aktuelle Ausgabe von „Writing Secure Code“ von Michael Howard und David LeBlanc (Microsoft Press, 2002) zu Rate zu ziehen, um mehr über diese allgemeinen Bedrohungen und Möglichkeiten zu ihrer Minimierung zu erfahren.
- **Social Engineering** – Enthält Informationen über prozedur- und strukturbezogene Sicherheitsmaßnahmen, mit denen Sie sich gegen eine unerwünschte Verwendung von Code durch Entwickler oder andere Personen innerhalb der Organisation des Herstellers schützen können.
- **Physische Sicherheit**: Enthält Informationen über das Sperren des Zugriffs auf Ihre Codebasis sowie über das Signieren von Zertifikaten.
- **Bereitstellung und Verteilung von Vorabversionen**: Enthält Informationen über das Verteilen Ihrer Betasoftware.
- **Netzwerkverwaltung**: Enthält Informationen über Angriffserkennungssysteme in Ihren physischen Netzwerken.

## <a name="threat-models-and-mitigations"></a>Bedrohungsmodelle und Risikominderung

Besitzer digitaler Informationen müssen die Umgebungen, in denen ihre Objekte entschlüsselt werden, auswerten können. Informationen zu den Mindestsicherheitsstandards können Informationsbesitzern als Framework dienen, um die Sicherheitsstufe der Anwendungen zu verstehen und zu bewerten.

In einigen Sektoren, z.B. bei Behörden und im Gesundheitswesen, gibt es Prozesse und Standards zur Zertifizierung und Akkreditierung, die möglicherweise für Ihr Produkt gelten. Allein durch das Befolgen dieser Mindestsicherheitsempfehlungen werden die individuellen Akkreditierungsanforderungen Ihrer Kunden jedoch nicht erfüllt. Diese Sicherheitsstandards sollen Sie jedoch bei der Vorbereitung auf aktuelle und zukünftige Kundenanforderungen unterstützen. Jede Investition, die Sie schon frühzeitig im Entwicklungszyklus tätigen, wird Ihrer Anwendung zugutekommen. Bei diesen Richtlinien handelt es sich um Empfehlungen, nicht um ein formelles Microsoft-Zertifizierungsprogramm.

In einem Rights Management-Dienstsystem werden Sicherheitsrisiken in verschiedene Hauptkategorien zusammengefasst:

- **Lecks**: Informationen werden an nicht autorisierten Orten angezeigt.
- **Beschädigung**: Software oder Daten werden in nicht autorisierter Weise geändert.
- **Verweigerung**: Eine Computerressource steht für die Nutzung nicht zur Verfügung.

Bei diesen Themen geht es hauptsächlich um Probleme mit Lecks. Die Integrität eines API-Systems hängt von seiner Fähigkeit ab, Informationen langfristig zu schützen und nur berechtigten Entitäten Zugriff zu gewähren. In diesen Themen werden auch Probleme durch Beschädigungen behandelt. Probleme durch Verweigerungen werden hingegen nicht thematisiert.

Microsoft führt keine Tests bezüglich der Einhaltung des Mindeststandards durch und prüft auch nicht die Ergebnisse derartiger Tests. Es obliegt dem Partner sicherzustellen, dass die Mindeststandards erfüllt werden. Microsoft stellt zwei zusätzliche Empfehlungsstufen zur Verfügung, um häufige Bedrohungen zu minimieren. Hierbei handelt es sich im Allgemeinen um ergänzende Vorschläge. Bei den bevorzugten Empfehlungen wird beispielsweise davon ausgegangen, dass die Mindeststandards erfüllt wurden – sofern anwendbar und nicht anderweitig spezifiziert.

|Standardstufe|Beschreibung|
|---|---|
|Mindeststandard| Eine Anwendung, die geschützte Informationen verarbeitet, muss vor dem Signieren des von Microsoft zur Verfügung gestellten Produktionszertifikats den Mindeststandard erfüllen. Partner verwenden im Allgemeinen das Produktionshierarchiezertifikat zum Zeitpunkt des letzten Releases der Software. Mit den eigenen internen Tests eines Partners wird überprüft, ob die Anwendung diesen Mindeststandard erfüllt. Das Erfüllen des Mindeststandards stellt keine von Microsoft bestätigte Sicherheitsgarantie dar und darf auch nicht als solche ausgelegt werden. Microsoft führt keine Tests bezüglich der Einhaltung des Mindeststandards durch und prüft auch nicht die Ergebnisse derartiger Tests. Es obliegt dem Partner sicherzustellen, dass die Mindeststandards erfüllt werden.|
|Empfohlener Standard| Die empfohlenen Richtlinien sind richtungsweisend für erhöhte Anwendungssicherheit und lassen darauf schließen, wie sich das SDK möglicherweise entwickelt, wenn mehr Sicherheitskriterien implementiert werden. Anbieter können ihre Anwendungen durch Einhalten dieser strikteren Richtlinien mit erhöhter Sicherheit auf dem Markt differenzieren.|
|Bevorzugter Standard| Dieser Standard ist die höchste Sicherheitsstufe, die derzeit festgelegt werden kann. Anbieter, die ihre Anwendungen als äußerst sicher vermarkten möchten, sollten sich für diese Stufe entscheiden. Anwendungen, die diesem Standard entsprechen, sind bei Angriffen wahrscheinlich dem geringsten Risiko ausgesetzt.|

## <a name="malicious-software"></a>Schadsoftware

Microsoft hat Mindeststandards definiert, die Ihre Anwendung erfüllen muss, um Inhalte vor Schadsoftware zu schützen.

### <a name="importing-malicious-software-by-using-address-tables"></a>Importieren von Schadsoftware durch Verwenden von Adresstabellen

Das Information Protection-SDK unterstützt keine Änderungen am Code zur Laufzeit oder Änderungen an der Importadresstabelle (IAT). Eine Importadresstabelle wird für jede DLL erstellt, die in Ihren Prozessraum geladen wird. Sie gibt die Adressen aller von Ihrer Anwendung importierten Funktionen an. Ein häufiger Angriff ist die Änderung der IAT-Einträge in Ihrer Anwendung, sodass diese auf die Schadsoftware zeigen. Wenn das SDK diesen Angriffstyp erkennt, wird die Anwendung beendet.

### <a name="minimum-standard"></a>Mindeststandard

- Während der Ausführung kann die Importadresstabelle im Anwendungsprozess nicht geändert werden. In Ihrer Anwendung sind viele der Funktionen festgelegt, die zur Laufzeit über Adresstabellen aufgerufen werden. Diese Tabellen können während oder nach der Laufzeit nicht verändert werden. Diese Einschränkung bedeutet unter anderem, dass Sie keine Codeprofile in einer Anwendung erstellen können, die mithilfe des Produktionszertifikats signiert ist.
- Sie können die **DebugBreak**-Funktion nicht aus einer im Manifest angegebenen DLL aufrufen.
- Sie können **LoadLibrary** nicht aufrufen, wenn das Flag **DONT_RESOLVE_DLL_REFERENCES** festgelegt ist. Das Flag weist das Ladeprogramm an, die Bindung an die importierten Module zu überspringen, was die Änderung der Importadresstabelle zur Folge hat.
- Sie können das verzögerte Laden nicht verändern, indem Sie den Linkerschalter /DELAYLOAD zur Laufzeit oder später ändern.
- Sie können das verzögerte Laden auch nicht verändern, indem Sie Ihre eigene Version der Hilfsfunktion Delayimp.lib bereitstellen.
- Sie können keine Module entladen, die durch authentifizierte Module verzögert geladen wurden, während die Information Protection-SDK-Umgebung existiert.
- Sie können den Linkerschalter **`/DELAY:UNLOAD`** nicht zum Aktivieren des Entladevorgangs der verzögerten Module verwenden.

## <a name="incorrectly-interpreting-license-rights"></a>Fehlerhafte Interpretation von Lizenzrechten

Wenn Ihre Anwendung die in der SDK-Veröffentlichungslizenz aufgeführten Rechte nicht ordnungsgemäß interpretiert und durchsetzt, könnten Sie möglicherweise Informationen in einer Weise zur Verfügung stellen, die vom Besitzer der Informationen nicht beabsichtigt wurde. Beispiel: Eine Anwendung erlaubt einem Benutzer, unverschlüsselte Informationen auf ein neues Medium zu speichern, während die Veröffentlichungslizenz lediglich das Recht gewährt, die Informationen anzuzeigen.

### <a name="azure-information-protection-aip"></a>Azure Information Protection (AIP)

Das System zum Schutz von Informationen fasst Rechte in einigen Gruppierungen zusammen. Weitere Informationen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](../configure-usage-rights.md).

Mit AIP kann ein Benutzer Informationen auf Wunsch verschlüsseln. Die Informationen haben keinen eigenen Schutz. Wenn ein Benutzer das Recht zur Entschlüsselung hat, gestattet die API diese Entschlüsselung. Die Anwendung ist verantwortlich für die Verwaltung bzw. den Schutz dieser Informationen, nachdem sie unverschlüsselt vorliegen. Eine Anwendung ist für die Verwaltung ihrer Umgebung und Schnittstelle verantwortlich, um eine nicht autorisierte Nutzung von Informationen zu verhindern. Beispiel: Deaktivieren der Schaltflächen **Drucken** und **Kopieren**, wenn eine Lizenz nur das Recht zum ANZEIGEN gewährt. Ihre Testsuite sollte überprüfen, ob sich Ihre Anwendung im Hinblick auf alle von ihr erkannten Lizenzrechte ordnungsgemäß verhält.

### <a name="minimum-standard"></a>Mindeststandard

- Die Kundenimplementierung von XrML v.1.2-Rechten sollte mit den Definitionen dieser Rechte übereinstimmen, die in den XrML-Spezifikationen beschrieben sind. Letztere finden Sie auf der XrML-Website, http://www.xrml.org). Alle für Ihre Anwendung spezifischen Rechte müssen für sämtliche Entitäten definiert werden, die auf Ihre Anwendung möglicherweise zugreifen.
- Ihre Testsuite und Ihr Testprozess sollten überprüfen, ob Ihre Anwendung im Hinblick auf die von der Anwendung unterstützten Rechte ordnungsgemäß agiert. Sie sollten auch sicherstellen, dass sie bei nicht unterstützten Rechten **nicht** reagiert.
- Wenn Sie eine veröffentlichende Anwendung erstellen, müssen Sie Informationen zur Verfügung stellen, die die verwendeten inhärenten Rechte erklären. Dies umfasst Rechte, die von der veröffentlichenden Anwendung unterstützt bzw. nicht unterstützt werden, sowie Angaben, wie diese Rechte interpretiert werden sollen. Darüber hinaus sollte auf der Benutzeroberfläche für den Endbenutzer klar ersichtlich sein, welche Auswirkungen jedes der gewährten oder verweigerten Rechte für eine bestimmte Information hat.
- Jedes Recht, das durch Einschluss in neue, von einer Anwendung implementierte Rechte abstrahiert wurde, muss der neuen Terminologie zugeordnet werden. Beispiel: Ein neues Recht, genannt MANAGER, beinhaltet möglicherweise Rechte wie Drucken, Kopieren und Bearbeiten als abstrahierte Rechte.

### <a name="recommended-standard"></a>Empfohlener Standard

Zurzeit keine.

### <a name="preferred-standard"></a>Bevorzugter Standard

Zurzeit keine.

## <a name="next-steps"></a>Nächste Schritte

Best Practices für das Implementieren von Anwendungen mittels AIP-SDK umfassen die folgenden Artikel:

- [Bedrohungsmodelle und Minimierungen](https://msdn.microsoft.com/library/aa362751.aspx)
- [Angriffe auf die Sicherheit](https://msdn.microsoft.com/library/aa362736.aspx)
