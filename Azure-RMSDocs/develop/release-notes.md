---
title: Anmerkungen zu dieser Version von Rights Management Services SDK v4. x
description: Weitere Informationen finden Sie unter Neuerungen und Versions Hinweise für das Microsoft Rights Management Service SDK v4. x Juli 2017 und frühere Versionen.
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 12/11/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.custom: has-adal-ref
ms.openlocfilehash: 63beff811a9a9d6d08cfb7d2119c976e91097109
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568381"
---
# <a name="whats-new-and-release-notes"></a>Neues und Anmerkungen zu dieser Version

[!INCLUDE [deprecation notice](../includes/deprecation-warning.md)]

## <a name="whats-new"></a>Neues

In diesem Thema werden wichtige Änderungen und Funktionen in dieser neuen Version von RMS SDK v4. x beschrieben.

-   [Neues im Juli 2017](#new-for-july-2017)
-   [Update vom Oktober 2016](#october-2016-update)
-   [Update vom Juni 2016](#june-2016-update)
-   [Update vom Dezember 2015](#december-2015-update)
-   [Update vom Juli 2015 – Unterstützung für Linux/C++-Entwicklung hinzugefügt](#july-2015-update---adds-support-for-linux--c-development)
-   [Update von Mai 2015-hinzufügen der Protokollierungs Steuerung](#may-2015-update---adds-logging-control)
-   [Update vom Februar 2015 – Unterstützung für Windows Store-Anwendung hinzugefügt](#february-2015-update---adds-windows-store-application-support)
-   [Update vom Januar 2015 – Unterstützung für WinPhone-Plattform hinzugefügt](#january-2015-update---adds-winphone-platform-support)
-   [Update vom Oktober 2014 – Upgrade auf Microsoft RMS SDK 4.1](#october-2014-update---upgrade-to-microsoft-rms-sdk-41)
-   [Versionshinweise](#release-notes)
-   [Häufig gestellte Fragen](#frequently-asked-questions)

### <a name="new-for-july-2017"></a>Neues im Juli 2017

Das Update im Juli umfasst die überarbeitete SDK-Version 4.2.5.

- Android SDK: Ihre App kann nun mit dem Android SDK **die Protokollierungsstufe ad hoc festlegen**. Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren der Fehler- und Leistungsprotokollierung](/information-protection/develop/enabling-logging).
- Das iOS SDK unterstützt keine Protokollierungsstufen.
- Das SDK gibt nun einen Fehler bei einem NULL-Zugriffstoken zurück.

### <a name="october-2016-update"></a>Update vom Oktober 2016

- Implementierung mehrerer Back-End-Fehlerbehebungen
- Aktivierung von Bitcode für das Apple iOS/OS X SDK

### <a name="june-2016-update"></a>Update vom Juni 2016

- **Unterstützung moderner Authentifizierung**: Ermöglicht in RMS-fähigen Apps die Anmeldung mithilfe der Active Directory Authentication Library (ADAL). Dadurch werden Anmeldefunktionen wie Multi-Factor Authentication (MFA), SAML-basierte Identitätsanbieter (Drittanbieter) mit RMS-Clientanwendungen sowie die smartcard- und zertifikatbasierte Authentifizierung aktiviert. Außerdem müssen RMS-fähige Apps nicht mehr das Standardauthentifizierungsprotokoll verwenden.
- **Unterstützung der Dokumentnachverfolgung**: Entwickler können nun die Dokumentnachverfolgung aktivieren, wenn sie Dokumente in ihren Apps schützen.
- Leistungsverbesserungen
- Behebung von Programmfehlern

### <a name="december-2015-update"></a>Update vom Dezember 2015

Mit diesem Release liegt das RMS SDK für Geräte jetzt in Version 4.2 mit folgenden Ergänzungen vor:

-   Dokumentnachverfolgung, nur RMS Online, für iOS/OS X- und Android-Betriebssysteme.

    Details und Nutzungshinweise für iOS/OS X sind in der [MSLicenseMetadata](/previous-versions/windows/desktop/msipcthin2/mslicensemetadata-class-objc)-Klasse enthalten. Hier finden Sie Nachverfolgungsinformationen sowie die zusätzliche Registrierungsmethode für die Dokumentnachverfolgung mit [MSUserPolicy](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-interface-objc). Ähnliche Ergänzungen sind für Android für [LicenseMetadata](/previous-versions/windows/desktop/msipcthin2/licensemetadata-interface-java) und [UserPolicy](/previous-versions/windows/desktop/msipcthin2/userpolicy-class-java) vorhanden.

    Eine ausführliche Beschreibung der Dokumentnachverfolgungsfunktion finden Sie unter [Vorgehensweise: Verwenden der Dokumentenverfolgung](how-to-use-document-tracking.md).

-   Eine Reihe synchroner Methoden, die parallel zu den asynchronen Versionen für die Android-API verwendet werden:

    [Synchrone CustomProtectedInputStream.create-Methode](/previous-versions/windows/desktop/msipcthin2/customprotectedinputstream-create-synchronous-method-java)

    [Synchrone CustomProtectedOutputStream.create-Methode](/previous-versions/windows/desktop/msipcthin2/customprotectedoutputstream-create-synchronous-method)

    [Synchrone ProtectedFileInputStream.create-Methode](/previous-versions/windows/desktop/msipcthin2/protectedfileinputstream-create-synchronous-method)

    [Synchrone ProtectedFileOutputStream.create-Methode](/previous-versions/windows/desktop/msipcthin2/protectedfileoutputstream-create-synchronous-method-java)

    [Synchrone TemplateDescriptor.getTemplates-Methode](/previous-versions/windows/desktop/msipcthin2/templatedescriptor-gettemplates-synchronous-method-java)

    [Synchrone UserPolicy.acquire-Methode](/previous-versions/windows/desktop/msipcthin2/userpolicy-acquire-synchronous-method-java)

    [Synchrone UserPolicy.create (Policydescriptor…)-Methode**](/previous-versions/windows/desktop/msipcthin2/userpolicy-create-policydescriptor-------synchronous-method-java)

    [Synchrone UserPolicy.create (TemplateDescriptor…)-Methode](/previous-versions/windows/desktop/msipcthin2/userpolicy-create-templatedescriptor-------synchronous-method-java)

-   Der Android-API wurde eine neue [ProtectedBuffer](/previous-versions/windows/desktop/msipcthin2/protectedbuffer-class)-Klasse hinzugefügt.
-   Updates zur Verbesserung der Fehlermeldungen und der Problembehandlung.
-   Beträchtliche Leistungssteigerungen für kryptografische Vorgänge.

### <a name="july-2015-update---adds-support-for-linux--c-development"></a>Update vom Juli 2015 – Unterstützung für Linux/C++-Entwicklung hinzugefügt

Diese Version umfasst folgende Updates:

-   RMS SDK 4.1 für Linux-Plattformen

    Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).

### <a name="may-2015-update---adds-logging-control"></a>Update vom Mai 2015 – Steuerung der Protokollierung hinzugefügt

Mit dieser Version wird Unterstützung für folgende Updates bereitgestellt:

-   iOS

    App-Verschlüsselung und -Entschlüsselung können unabhängig und parallel ausgeführt werden.

    Weitere Informationen finden Sie unter [MSProtector](/previous-versions/windows/desktop/msipcthin2/msprotector-class-objc).

    Steuerungseinstellungen auf Protokollebene aktiviert.

    Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren der Fehler- und Leistungsprotokollierung](enabling-logging.md).

    Unterstützung zum Löschen des Caches hinzugefügt.

    Weitere Informationen finden Sie unter [MSProtection:resetStateWithCompletionBlock](/previous-versions/windows/desktop/msipcthin2/msprotection-resetstatewithcompletionblock-method-objc).

### <a name="february-2015-update---adds-windows-store-application-support"></a>Update vom Februar 2015 – Unterstützung für Windows Store-Anwendung hinzugefügt

Diese Version bietet Unterstützung für Windows Store-Anwendungen sowie funktionale Parität mit der Windows Phone-, Android- und iOS/OS X-Version des RMS SDK 4.1.

### <a name="january-2015-update---adds-winphone-platform-support"></a>Update vom Januar 2015 – Unterstützung für WinPhone-Plattform hinzugefügt

Diese Version bietet Unterstützung für das Windows Phone-Betriebssystem sowie funktionale Parität mit der Android- und iOS/OS X-Version des RMS SDK 4.1.

### <a name="october-2014-update---upgrade-to-microsoft-rms-sdk-41"></a>Update vom Oktober 2014 – Upgrade auf Microsoft RMS SDK 4.1

Die Version 4.1 des RMS SDK bietet die folgenden neuen Features für Google Android und Apple iOS/OS X.

-   Android und iOS/OS X SDK-API-Erweiterungen zur Verarbeitung der *Benutzerzustimmung*, sodass SDK-Verhalten vom Benutzer bestätigt werden können. Aktuell werden als Zustimmungstypen die Dokumentnachverfolgung und der Zugriff auf unbekannte AD RMS-Dienst-URLs unterstützt.

    Weitere Informationen finden Sie im Beispiel der Android-API-Version der [ConsentCallback-Schnittstelle](/previous-versions/windows/desktop/msipcthin2/consentcallback-interface-java).

-   iOS 8 und OS X 10.10 (Yosemite) werden jetzt unterstützt. Aufgrund von Xcode 6 gab es einige Änderungen bei den Eigenschaftsnamen.

    Beispiel: MSUserPolicy.name wurde in [MSUserPolicy.policyName](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-name-property-objc) geändert.

## <a name="release-notes"></a>Versionshinweise

Dieser Abschnitt enthält Informationen zur aktuellen und vorherigen Versionen der Microsoft Rights Management SDK 4.x-APIs, die Sie als Entwickler berücksichtigen sollten.

**AD RMS SDK 4.1: Version für globale Verfügbarkeit für iOS/OS X- und Android-Plattformen**

-   **AD RMS-Unterstützung**: IT-Administratoren können RMS-fähige Apps auf mobilen Geräten mit den neuen Erweiterungen für mobile Geräte des AD RMS-Servers verwenden.
-   **Offlinenutzung**: Endbenutzer können auf RMS-geschützte Daten offline zugreifen.
-   **Getrennte Authentifizierung**: Entwickler können ihre eigene Authentifizierungsbibliothek für Azure RMS und AD RMS (oder die empfohlene Azure AD-Authentifizierungsbibliothek ([Azure AD Authentication Library; ADAL)](/previous-versions/azure/jj573266(v=azure.100))) verwenden.
-   **Getrennte Benutzeroberfläche**: Entwickler können ihre Benutzeroberfläche zum Schutz und zur Nutzung von RMS-geschützten Dokumenten konfigurieren.
-   **Überarbeitete API**: Entwickler können nun eine einfache und transparente Verschlüsselungs- und Entschlüsselungs-API verwenden, die mit minimalem Aufwand ein konsistentes RMS-Verhalten bietet.

**Auf allen Plattformen**

-   Die RMS SDK 4.x-APIs sind nicht *threadsicher*.

**Android**

-   Wenn Sie eine Beispiel-App auf einem Kindle-Gerät von Amazon® verwenden, um PTXT-Anlagen anzuzeigen, müssen Sie die Datei zum Anzeigen herunterladen.

    **Lösung**: Ein bekanntes Problem, das in der Zukunft behoben wird.

-   Eine Anwendung, die das SDK verwendet, stürzt möglicherweise ab, wenn mehrere Instanzen zulässig sind.

    **Lösung**: Stellen Sie sicher, dass die Anwendung nicht mehrere Instanzaufrufe auf der Android-API zulässt.

-   Bei Verwendung der Methode [protectedfileoutputstream](/previous-versions/windows/desktop/msipcthin2/protectedfileoutputstream-class-java). Write (Byte \[ \] Array, int Offset, int length) mit einer anderen Länge als der *Array. length* -Wert kann der Inhalt später nicht mit dem SDK verwendet werden.

    **Lösung**: Dies ist ein bekanntes Problem. Um dieses Problem zu beheben, übergeben Sie entweder immer ein *\[ \] Bytearray* mit dem gleichen Längen Wert wie der length-Parameter, oder verwenden Sie die Methode [protectedfileoutputstream](/previous-versions/windows/desktop/msipcthin2/protectedfileoutputstream-class-java). Write (Byte \[ \] Array).

**iOS und OS X**

-   Die iOS und OS X SDKs unterstützen zwei portugiesische Dialekte. Leider wird aufgrund eines Fehlers derzeit die erste Lokalisierung nicht vollständig unterstützt. Aufgrund dieses Fehlers wird Portugiesisch nicht vollständig unterstützt. Der meiste Text ist übersetzt, aber nicht die Benutzeroberfläche.

    1. Portugiesisch

    2. Portugiesisch (Portugal)

**Nur iOS**

-   Das RMS SDK 4.x zeigt keine Netzwerkaktivität an.

    Dies ist gemäß den Apple Human Interface Guidelines (Apple-Richtlinien für Design von Anwendungen) ein bekanntes optionales Verhalten für iOS.

**Nur OS X**

-   Das RMS SDK 4.x zeigt keine Netzwerkaktivität an.

    Dies ist gemäß den Apple Human Interface Guidelines (Apple-Richtlinien für Design von Anwendungen) ein bekanntes optionales Verhalten für OS X.

-   **Lösung**: Wenn Sie eine Anwendung mit mehreren Dokumentschnittstellen (Multiple Document Interface, MDI) mithilfe unseres OS X SDK erstellen möchten, gehen Sie wie folgt vor.

    Die folgenden Methoden dürfen nicht gleichzeitig ausgeführt werden. Verwenden Sie zum Überwachen des Ausführungsabschlusses den erwähnten Blockansatz.

    - [MSProtectedData.protectedDataWithProtectedFile](/previous-versions/windows/desktop/msipcthin2/msprotecteddata-protecteddatawithprotectedfile-completionblock-method-objc)
    - [MSCustomProtectedData.customProtectedDataWithPolicy](/previous-versions/windows/desktop/msipcthin2/mscustomprotecteddata-customprotecteddatawithpolicy-protecteddata-contentstartposition-contentsize-completionblock-method-objc)



**Hinweis**    MDI-Anwendungen werden von unserer IOS-API nicht unterstützt.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Alle Plattformen**

**F**: Ich sehe im Schutzworkflow keine Benutzeroberfläche zur Auswahl von **benutzerdefinierten Berechtigungen**. Warum?

**A**: Dies ist ein bekanntes Problem, das in der Zukunft behoben wird.

**F**: Wie erhalte ich neue Organisationsmandanten, um das SDK und Beispielanwendungen zu testen?

**A**: Um Anmeldeinformationen für Azure AD RMS-Testorganisationen anzufordern, senden Sie eine E-Mail an <rmcstbeta@microsoft.com>.

**F**: Ich sehe hier in der Dokumentation keine Erläuterung der Testhierarchie. Warum?

**A**: Es gibt bei den neuen AD RMS SDKs kein Testhierarchiekonzept. Sie arbeiten immer mit der Produktionshierarchie.

**F**: In Version 2.1 des RMS SDK war ein generiertes Manifest für jede Anwendung erforderlich, die Datenschutz implementiert. Gilt dies auch für Version 4.0 und neuere SDK-Versionen?

**A**: Nein, ab Version 3.0 des Rights Management SDK sind keine Manifeste mehr erforderlich.

**Android**

**F**: Mit welchen Entwicklungsumgebungen wurde das SDK getestet?

**A**: Eclipse Juno mit der Google-API 15 und höher.

**F**: Kann ich zum Abbrechen die cancel()-Methode aus dem UI-Thread aufrufen?
**A**: Sie sollten cancel() aus einem Nicht-UI-Thread aufrufen, da ansonsten möglicherweise die Netzwerkverbindung getrennt wird.

**iOS**

**F**: Welche Plattformen wurden für die SDK-Entwicklung überprüft?

**A**: Xcode 5.0 mit iOS 7 und höher.

**F**: Ich habe die cancel()-Methode für einen Vorgang aufgerufen, erhalte jedoch immer noch die Benachrichtigung, dass der Vorgang abgeschlossen wurde. Warum?

**A**: Nicht alle Vorgänge können abgebrochen werden, weshalb ein Abbruchvorgang so gut wie möglich ausgeführt wird.

**OS x**

**F**: Das Beispiel-App-Framework wurde an Xcode 5 angepasst. Kann ich trotzdem Xcode 4.6 verwenden?

**A**: Das OS X SDK funktioniert nur mit Xcode 4.6 und höher sowie OS X 10.8 und höher.