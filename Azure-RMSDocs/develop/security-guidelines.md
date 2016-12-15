---
title: "Bewährte Sicherheitsmethoden | Microsoft Information Protection"
description: "RMS-fähige Anwendungen werden am besten mithilfe der bewährten Methoden von Azure Information Protection erstellt."
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.date: 12/06/2016
ms.topic: article
ms.prod: 
ms.assetid: 4e9f72d5-9e7c-43e1-bb8a-5972dd22dcee
ms.service: information-protection
ms.technology: techgroup-identity
ms.suite: ems
ms.reviewer: kartikk
translationtype: Human Translation
ms.sourcegitcommit: 2142a13d742b2dc0b59c3b996db69406cd818149
ms.openlocfilehash: b225a923b7f067fd7dc0ca67742275e399a8aa7c

---

# <a name="security-best-practices-for-azure-information-protection"></a>Best Practices zu Sicherheitsthemen für Azure Information Protection

Das Software Development Kit (SDK) für Azure Information Protection (AIP) stellt ein stabiles System zum Veröffentlichen und Nutzen geschützter Informationen aller Art berei. Um ein möglichst sicheres AIP-System zu erzielen, müssen AIP-fähige Anwendungen unter Berücksichtigung der Best Practices für AIP erstellt werden. Alle AIP-fähigen Anwendungen sind gemeinsam dafür zuständig, die Sicherheit dieses Ökosystems aufrecht zu erhalten. Durch Identifizieren und Minimieren von Sicherheitsrisiken, die bei der Anwendungsentwicklung entstehen, lässt sich die Sicherheit bei der Software-Implementierung erhöhen.

Best Practices für die Implementierung von Anwendungen mithilfe des Software Development Kits (SDK) für Azure Information Protection umfassen die folgenden Vorschlagskategorien:
- [Bedrohungsmodelle und Minimierungen](https://msdn.microsoft.com/en-us/library/aa362751.aspx)
- [Angriffe auf die Sicherheit](https://msdn.microsoft.com/en-us/library/aa362736.aspx)

Diese Informationen ergänzen den Vertrag, der unterzeichnet werden muss, um die für die Anwendungsimplementierung mithilfe des AIP-SDKs erforderlichen Zertifikate zu erhalten.

## <a name="subjects-not-covered-in-these-topics"></a>In diesen Themen nicht enthaltene Inhalte
In diesen Themen werden folgende Probleme kurz beschrieben, deren Kenntnis für das Erstellen einer Entwicklungsumgebung und einer sicheren Anwendung wichtig ist:
- **Verwaltung des Softwareentwicklungsprozesses**: Enthält Informationen über die Konfigurationsverwaltung, das Schützen von Quellcode, das Minimieren des Zugriffs auf gedebuggten Code und das Zuweisen von Prioritäten zu Fehlern. Für einige unserer Kunden ist ein sichererer Softwareentwicklungsprozess von höchster Bedeutung. Einige Kunden schreiben den Ablauf eines Entwicklungsprozesses sogar vor.
- **Häufige Codierungsfehler**: Enthält Informationen dazu, wie Pufferüberläufe vermieden werden können. Es wird empfohlen, die aktuelle Ausgabe von „Writing Secure Code“ von Michael Howard und David LeBlanc (Microsoft Press, 2002) zu Rate zu ziehen, um mehr über diese allgemeinen Bedrohungen und Möglichkeiten zu ihrer Minimierung zu erfahren.
- **Social Engineering**: Enthält Informationen über prozedur- und strukturbezogene Sicherheitsmaßnahmen, mit denen Sie sich gegen unerwünschte Verwendung von Code durch Entwickler oder andere Personen innerhalb der Organisation des Herstellers schützen können.
- **Physische Sicherheit**: Enthält Informationen über das Sperren des Zugriffs auf Ihre Codebasis sowie über das Signieren von Zertifikaten.
- **Bereitstellung und Verteilung von Vorabversionen**: Enthält Informationen über das Verteilen Ihrer Betasoftware.
- **Netzwerkverwaltung**: Enthält Informationen über Angriffserkennungssysteme in Ihren physischen Netzwerken.

## <a name="threat-models-and-mitigations"></a>Bedrohungsmodelle und Minimierungen
Besitzer digitaler Informationen müssen die Umgebungen, in denen ihre Ressourcen entschlüsselt werden, auswerten können. Informationen zu minimalen Sicherheitsstandards können Informationsbesitzern als Framework dienen, um die Sicherheitsstufe der Anwendungen zu verstehen und zu bewerten, denen sie ihre Informationen anvertrauen.

In einigen Sektoren, z.B. bei Behörden und im Gesundheitswesen, gibt es Prozesse und Standards zur Zertifizierung und Akkreditierung, die möglicherweise für Ihr Produkt gelten. Allein durch das Befolgen dieser minimalen Sicherheitsempfehlungen werden die individuellen Akkreditierungsanforderungen Ihrer Kunden jedoch nicht erfüllt. Diese Sicherheitsstandards sollen Sie jedoch bei der Vorbereitung auf aktuelle und zukünftige Kundenanforderungen unterstützen. Jede Investition, die Sie schon frühzeitig im Entwicklungszyklus tätigen, wird Ihrer Anwendung zugutekommen. Es handelt sich hier um Empfehlungen, nicht um ein formelles Microsoft-Zertifizierungsprogramm.

In einem Rights Management-Dienstsystem werden Sicherheitsrisiken in verschiedene Hauptkategorien zusammengefasst:
- **Lecks**: Informationen werden an nicht autorisierten Orten angezeigt.
- **Beschädigung**: Software oder Daten werden in nicht autorisierter Weise geändert.
- **Verweigerung**: Eine Computeressource steht für die Nutzung nicht zur Verfügung.

Bei diesen Themen geht es hauptsächlich um Probleme mit Lecks. Die Integrität eines API-Systems hängt von seiner Fähigkeit ab, Informationen langfristig zu schützen und nur berechtigten Entitäten Zugriff zu gewähren. In diesen Themen werden auch Probleme durch Beschädigungen behandelt. Probleme durch Verweigerungen werden hingegen nicht thematisiert.

Testergebnisse, die das Erfüllen des Mindeststandards betreffen, werden von Microsoft nicht getestet oder überprüft. Es obliegt der alleinigen Verantwortung des Partners, dass diese Mindeststandards erfüllt werden. Microsoft stellt zwei zusätzliche Empfehlungsstufen zur Verfügung, um häufige Bedrohungen zu minimieren. Im Allgemeinen sind diese Vorschläge als additiv zu betrachten. Zum Beispiel wird bei den bevorzugten Empfehlungen davon ausgegangen, dass die Mindeststandards erfüllt wurden – sofern anwendbar und nicht anderweitig spezifiziert.

|Standardstufe|    Beschreibung|
|---|---|
|Mindeststandard|  Eine Anwendung, die AIP-geschützte Informationen verarbeitet, muss vor dem Signieren des von Microsoft zur Verfügung gestellten Produktionszertifikats so eingerichtet werden, dass sie den Mindeststandard erfüllt. In der Regel verwenden Partner das Produktionshierarchiezertifikat nur bei der endgültigen Veröffentlichung der Software, wenn durch die internen, von den Partnern selbst durchgeführten Tests bestätigt wurde, dass die Anwendung diesen Mindeststandard erfüllen. Das Erfüllen des Mindeststandards stellt keine von Microsoft bestätigte Sicherheitsgarantie dar und darf auch nicht als solche ausgelegt werden. Testergebnisse, die das Erfüllen des Mindeststandards betreffen, werden von Microsoft nicht getestet oder überprüft. Es obliegt der alleinigen Verantwortung des Partners, dass diese Mindeststandards erfüllt werden.|
|Empfohlener Standard|  Die empfohlenen Richtlinien sind richtungsweisend für erhöhte Anwendungssicherheit und lassen darauf schließen, wie sich AIP möglicherweise entwickelt, wenn mehr Sicherheitskriterien implementiert werden. Anbieter können versuchen, ihre Anwendungen durch Einhalten dieser strikteren Richtlinien mit erhöhter Sicherheit auf dem Markt zu differenzieren.|
|Bevorzugter Standard|    Dies ist die höchste Sicherheitsstufe, die derzeit festgelegt werden kann. Anbieter, die ihre Anwendungen als äußerst sicher vermarkten möchten, sollten sich für diese Stufe entscheiden. Anwendungen, die diesem Standard entsprechen, sind bei Angriffen wahrscheinlich dem geringsten Risiko ausgesetzt.|




## <a name="malicious-software"></a>Schadsoftware
Microsoft hat Mindeststandards definiert, die Ihre Anwendung erfüllen muss, um Inhalte vor Schadsoftware zu schützen.

### <a name="importing-malicious-software-by-using-address-tables"></a>Importieren von Schadsoftware durch Verwenden von Adresstabellen
Änderungen am Code zur Laufzeit oder Änderungen an der Importadresstabelle (IAT) werden von AIP nicht unterstützt. Eine Importadresstabelle wird für jede DLL erstellt, die in Ihren Prozessraum geladen wird. Sie gibt die Adressen aller von Ihrer Anwendung importierten Funktionen an. Ein häufiger Angriff ist die Änderung der IAT-Einträge in Ihrer Anwendung, sodass diese auf die Schadsoftware zeigen. Wenn AIP diesen Angriffstyp erkennt, wird die Anwendung beendet.

### <a name="minimum-standard"></a>Mindeststandard
- Während der Ausführung kann die Importadresstabelle im Anwendungsprozess nicht geändert werden. – In Ihrer Anwendung sind viele der Funktionen festgelegt, die zur Laufzeit über Adresstabellen aufgerufen werden. Diese können während oder nach der Laufzeit nicht verändert werden. Dies bedeutet unter anderem, dass Sie keine Codeprofile in einer Anwendung erstellen können, die mithilfe des Produktionszertifikats signiert ist.
- Sie können die **DebugBreak**-Funktion nicht aus einer im Manifest angegebenen DLL aufrufen.
- Sie können **LoadLibrary** nicht aufrufen, wenn das Flag **DONT_RESOLVE_DLL_REFERENCES** festgelegt ist. Das Flag weist das Ladeprogramm an, die Bindung an die importierten Module zu überspringen, was die Änderung der Importadresstabelle zur Folge hat.
- Sie können das verzögerte Laden nicht verändern, indem Sie den Linkerschalter „/DELAYLOAD“ zur Laufzeit oder später ändern.
- Sie können das verzögerte Laden auch nicht verändern, indem Sie Ihre eigenen Version der Hilfsfunktion „Delayimp.lib“ bereitstellen.
- Sie können keine Module entladen, die durch authentifizierte Module verzögert geladen wurden, während die AIP-Umgebung existiert.
- Die können den Linkerschalter **/DELAY:UNLOAD** nicht zum Aktivieren des Entladevorgangs der verzögerten Module verwenden.


## <a name="incorrectly-interpreting-license-rights"></a>Fehlerhafte Interpretation von Lizenzrechten

Wenn Ihre Anwendung die in der AIP-Veröffentlichungslizenz aufgeführten Rechte nicht ordnungsgemäß interpretiert und durchsetzt, könnten Sie möglicherweise Informationen in einer Weise zur Verfügung stellen, die vom Besitzer der Informationen nicht beabsichtigt wurde. Beispiel: Eine Anwendung erlaubt einem Benutzer, unverschlüsselte Informationen auf ein neues Medium zu speichern, während die Veröffentlichungslizenz lediglich das Recht gewährt, die Informationen anzuzeigen.

Das AIP-System fasst Rechte in einigen Gruppierungen zusammen. Weitere Informationen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](../deploy-use/configure-usage-rights.md).

### <a name="azure-information-protection"></a>Azure Information Protection  
AIP lässt Benutzern die Wahl, ob sie Informationen verschlüsseln. Die Informationen selbst verfügen über keinen eigenen Schutz. Wenn ein Benutzer das Recht besitzt, Informationen zu verschlüsseln, wird dies von AIP zugelassen, und die Anwendung sorgt für die Verwaltung und den Schutz dieser Informationen, sobald sie unverschlüsselt vorliegen. Eine Anwendung ist für die Verwaltung ihrer Umgebung und Benutzeroberfläche zuständig, um eine nicht autorisierte Nutzung von Informationen zu verhindern. Hierfür können z.B. die Schaltflächen **Drucken** und **Kopieren** deaktiviert werden, wenn eine Lizenz nur die Berechtigung zur Wiedergabe gewährt. Ihre Testsuite sollte überprüfen, ob sich Ihre Anwendung im Hinblick auf alle von ihr erkannten Lizenzrechte ordnungsgemäß verhält.

### <a name="minimum-standard"></a>Mindeststandard
- Die Kundenimplementierung von XrML v.1.2-Rechten sollte mit den Definitionen dieser Rechte übereinstimmen, wie in den XrML-Spezifikationen beschrieben. Diese stehen auf der XrML-Website (http://www.xrml.org) zur Verfügung. Alle für Ihre Anwendung spezifischen Rechte müssen für sämtliche Entitäten definiert werden, die auf Ihre Anwendung möglicherweise zugreifen.
- Ihre Testsuite und Ihr Testprozess sollten überprüfen, ob Ihre Anwendung im Hinblick auf die von der Anwendung unterstützten Rechte ordnungsgemäß agiert, und ob sie bei nicht unterstützten Rechte entsprechend nicht agiert.
- Wenn Sie eine Anwendung für die Veröffentlichung erstellen, müssen Sie Informationen zur Verfügung stellen, in denen erläutert wird, welche inhärenten Rechte von der Anwendung unterstützt werden und wie diese Rechte interpretiert werden sollten. Darüber hinaus sollte auf der Benutzeroberfläche für den Endbenutzer klar ersichtlich sein, welche Auswirkungen jedes der gewährten oder verweigerten Rechte für eine bestimmte Information hat.

- Jedes Recht, das durch Einschluss in neue, von einer Anwendung implementierte Rechte abstrahiert wurde, muss der neuen Terminologie zugeordnet werden. Beispiel: Ein neues Recht, genannt MANAGER, beinhaltet möglicherweise Rechte wie Drucken, Kopieren und Bearbeiten als abstrahierte Rechte.
Empfohlener Standard: zurzeit keiner.
Bevorzugter Standard: zurzeit keiner.



<!--HONumber=Dec16_HO2-->


