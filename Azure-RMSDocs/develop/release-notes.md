---
title: Neuheiten und Versionshinweise | Azure RMS
description: "Beschreibt wichtige Änderungen und Funktionen in dieser neuen Version des RMS SDK."
author: bruceperlerms
manager: mbaldwin
ms.date: 10/31/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 60e64b1fb1184aaa51b6664ecb5288d6ff861413
ms.openlocfilehash: 04364bc5daec881fe3c55d5cd41e7be11ac91ae7


---

# <a name="whats-new-and-release-notes"></a>Neuheiten und Anmerkungen zu dieser Version

## <a name="whats-new"></a>Neuheiten
Das Microsoft Rights Management SDK 4.2 ermöglicht eine noch einfachere und flexiblere Aktivierung der RMS-Anwendung. In diesem Thema werden wichtige Änderungen und Funktionen in der Version des RMS SDK beschrieben.

### <a name="new-for-june-2016"></a>Neu ab Juni 2016

- **Unterstützung moderner Authentifizierung**: Diese ermöglicht in RMS-fähigen Apps die Anmeldung mithilfe der Active Directory-Authentifizierungsbibliothek (Active Directory Authentication Library; ADAL). Dadurch werden Anmeldefunktionen wie Multi-Factor Authentication (MFA), SAML-basierte Identitätsanbieter (Drittanbieter) mit RMS-Clientanwendungen und die smartcard- und zertifikatbasierte Authentifizierung aktiviert. Außerdem müssen RMS-fähige Apps nicht mehr das Standardauthentifizierungsprotokoll verwenden.
- **Unterstützung von Dokumentkontrolle**: Entwickler können nun die Dokumentkontrolle aktivieren, wenn sie Dokumente in ihren Apps schützen
- Leistungsverbesserungen
- Fehlerbehebungen


### <a name="december-2015-update"></a>Dezember 2015-Update

Mit dieser Version liegt das RMS SDK für Geräte jetzt in Version 4.2 mit folgenden Ergänzungen vor:

-   Dokumentenverfolgung, nur RMS Online für iOS/OS X- und Android-Betriebssysteme.

    Details und Anleitungen für iOS/OS X erhalten Sie in der [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx)-Klasse. Hier finden Sie Nachverfolgungsinformationen sowie die zusätzliche Registrierungsmethode für die Dokumentnachverfolgung mit [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx). Ähnliche Ergänzungen sind für Android für [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx) und [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) vorhanden.

    Eine ausführliche Beschreibung der Dokumentnachverfolgungsfunktion finden Sie unter [Vorgehensweise: Verwenden von Dokumentenverfolgung](how-to-use-document-tracking.md).

-   Eine Reihe synchroner Methoden, die parallel zu den asynchronen Versionen für die Android-API verwendet werden:

    [Synchrone CustomProtectedInputStream.create-Methode](https://msdn.microsoft.com/library/mt631362.aspx)

    [Synchrone CustomProtectedOutputStream.create-Methode](https://msdn.microsoft.com/library/mt631363.aspx)

    [Synchrone ProtectedFileInputStream.create-Methode](https://msdn.microsoft.com/library/mt631375.aspx)

    [Synchrone ProtectedFileOutputStream.create-Methode](https://msdn.microsoft.com/library/mt631376.aspx)

    [Synchrone TemplateDescriptor.getTemplates-Methode](https://msdn.microsoft.com/library/mt631380.aspx)

    [Synchrone UserPolicy.acquire-Methode](https://msdn.microsoft.com/library/mt631384.aspx)

    [Synchrone Methode** UserPolicy.create (PolicyDescriptor…)](https://msdn.microsoft.com/library/mt631385.aspx)

    [Synchrone UserPolicy.create-Methode (TempalteDescriptor…)](https://msdn.microsoft.com/library/mt631386.aspx)

-   Der Android-API wurde eine neue [ProtectedBuffer](https://msdn.microsoft.com/library/mt631369.aspx)-Klasse hinzugefügt.
-   Updates zur Verbesserung der Fehlermeldungen und der Problembehandlung.
-   Beträchtliche Leistungssteigerungen für kryptografische Operationen.

### <a name="july-2015-update-adds-support-for-linux-c-development"></a>Juli 2015-Update – Unterstützung für Linux/C++-Entwicklung hinzugefügt

Diese Version bietet folgende Zusätze:

-   RMS SDK 4.1 für Linux-Plattformen

    Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).

### <a name="may-2015-update-adds-logging-control"></a>Mai 2015-Update – Steuerung der Protokollierung hinzugefügt

Diese Version unterstützt Folgendes:

-   iOS

    App-Verschlüsselung und -Entschlüsselung können unabhängig und parallel ausgeführt werden.

    Weitere Informationen finden Sie unter [MSProtector](https://msdn.microsoft.com/library/mt210993.aspx).

    Aktivierte Steuerungseinstellungen auf Protokollebene.

    Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren der Fehler- und Leistungsprotokollierung](enabling-logging.md).

    Unterstützung zum Löschen des Caches hinzugefügt.

    Weitere Informationen finden Sie unter [MSProtection:resetStateWithCompletionBlock](https://msdn.microsoft.com/library/mt210991.aspx).

### <a name="february-2015-update-adds-windows-store-application-support"></a>Februar 2015-Update – Unterstützung für Windows Store-Anwendung hinzugefügt

Diese Version bietet Unterstützung für Windows Store-Anwendungen sowie funktionale Parität mit der Windows Phone-, Android- und iOS/OS X-Version des RMS SDK 4.1.

### <a name="january-2015-update-adds-winphone-platform-support"></a>Januar 2015-Update – Unterstützung für WinPhone-Plattform hinzugefügt

Diese Version bietet Unterstützung für das Windows Phone-Betriebssystem sowie funktionale Parität mit der Android- und iOS/OS X-Version des RMS SDK 4.1.

### <a name="october-2014-update-upgrade-to-microsoft-rms-sdk-41"></a>Oktober 2014-Update – Upgrade auf Microsoft RMS SDK 4.1

Die Version 4.1 des RMS SDK fügt die folgenden neuen Features für Google Android und Apple iOS/OS X hinzu.

-   Android und iOS/OS X-SDK-API-Erweiterungen zur Verarbeitung der *Benutzerzustimmung*, sodass SDK-Verhalten vom Benutzer bestätigt werden können. Aktuell werden als Zustimmungstypen die Dokumentenverfolgung und der Zugriff auf unbekannte AD RMS-Dienst-URLs unterstützt.

    Weitere Informationen finden Sie im Beispiel der Android-API-Version der [ConsentCallback-Schnittstelle](https://msdn.microsoft.com/library/dn833503.aspx).

-   iOS 8 und OS X 10.10 (Yosemite) werden jetzt unterstützt. Auch gab es aufgrund von Xcode 6 Änderungen bei den Eigenschaftsnamen.

    Beispiel: MSUserPolicy.name wurde in [MSUserPolicy.policyName](https://msdn.microsoft.com/library/dn790799.aspx) geändert.

## <a name="release-notes"></a>Anmerkungen zu dieser Version

Dieser Abschnitt enthält Informationen über die aktuelle und die vorherigen Versionen der Microsoft Rights Management SDK 4.x-APIs, die Sie als Entwickler berücksichtigen sollten.

**AD RMS SDK 4.1: Global verfügbare Versionen der iOS/OS X- und Android-Plattformen**

-   **AD RMS-Unterstützung**: IT-Administratoren können RMS-fähige Apps auf mobilen Geräten mit den neuen Erweiterungen für mobile Geräte des AD RMS-Servers verwenden.
-   **Offlineverarbeitung**: Endbenutzer können auf RMS-geschützten Daten offline zugreifen.
-   **Getrennte Authentifizierung**: Entwickler können ihre eigene Authentifizierungsbibliothek für Azure RMS und AD RMS (oder die empfohlene [Azure AD-Authentifizierungsbibliothek (Azure AD Authentication Library; ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx)) verwenden.
-   **Getrennte Benutzeroberfläche**: Entwickler können ihre Benutzeroberfläche zum Schutz und zur Nutzung von RMS-geschützten Dokumenten konfigurieren.
-   **Überarbeitete API**: Entwickler können jetzt von einer einfachen und transparenten Verschlüsselungs- und Entschlüsselungs-API profitieren, die mit minimalem Aufwand ein konsistentes RMS-Verhalten bietet.

**Auf allen Plattformen**

-   Die RMS SDK 4.x-APIs sind nicht *threadsicher*.

**Android**

-   Wenn Sie eine Beispiel-App auf einem Kindle-Gerät von Amazon® verwenden, um PTXT-Anlagen anzuzeigen, müssen Sie die Datei zum Anzeigen herunterladen.

    **Lösung**: Dies ist ein bekanntes Problem, auf das später noch eingegangen wird.

-   Eine Anwendung, die das SDK verwendet, stürzt möglicherweise ab, wenn mehrere Instanzen zulässig sind.

    **Lösung**: Stellen Sie sicher, dass die Anwendung nicht mehrere Instanzaufrufe auf der Android-API zulässt.

-   Bei Verwendung der Methode [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array, int offset, int length) mit einer vom Wert *array.length* abweichenden Länge kann der Inhalt später nicht mit dem SDK verwendet werden.

    **Lösung**: Dies ist ein bekanntes Problem. Übergeben Sie zur Vermeidung dessen entweder ein *byte \[\]*-Array mit einem Längenwert gleich dem length-Parameter, oder verwenden Sie die Methode [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array).

**iOS und OS X**

-   Unsere iOS- und OS X-SDKs unterstützen zwei portugiesische Dialekte. Leider wird aufgrund eines Fehlers derzeit die erste Lokalisierung nicht vollständig unterstützt. Aufgrund dieses Fehlers wird Portugiesisch nicht vollständig unterstützt. Der meiste Text wurde übersetzt, aber nicht die Benutzeroberfläche.

    1. Portugiesisch

    2. Portugiesisch (Portugal)

**Nur iOS**

-   Das RMS SDK 4.x zeigt keine Netzwerkaktivität an.

    Dies ist gemäß den Apple Human Interface Guidelines (Richtlinien für menschliche Schnittstellen) ein bekanntes optionales Verhalten für iOS.

**Nur OS X**

-   Das RMS SDK 4.x zeigt keine Netzwerkaktivität an.

    Dies ist gemäß den Apple Human Interface Guidelines (Richtlinien für menschliche Schnittstellen) ein bekanntes optionales Verhalten für OS X.

-   **Lösung**: Wenn Sie eine Anwendung mit mehreren Dokumentschnittstellen (Multiple Document Interface, MDI) mithilfe unseres OS X SDK erstellen, gehen Sie wie folgt vor.

    Die folgenden Methoden dürfen nicht gleichzeitig ausgeführt werden. Verwenden Sie zum Überwachen des Ausführungsabschlusses den erwähnten Blockansatz.

    - [MSProtectedData.protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx)
    - [MSCustomProtectedData.customProtectedDataWithPolicy](https://msdn.microsoft.com/library/dn758315.aspx)



**Hinweis**  MDI-Anwendungen werden von unserer iOS-API nicht unterstützt.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Alle Plattformen**

**F**: Ich sehe im Schutz-Workflow keine Benutzeroberfläche zur Auswahl von **benutzerdefinierten Berechtigungen**. Warum?

**A**: Dies ist ein bekanntes Problem, auf das später noch eingegangen wird.

**F**: Wie erhalte ich die neue Organisationsmandanten, um das SDK und Beispielanwendungen zu testen?

**A**: Um Anmeldeinformationen für Azure AD RMS-Testorganisationen anzufordern, senden Sie eine E-Mail an <rmcstbeta@microsoft.com>.

**F**: Ich sehe hier in der Dokumentation keine Erörterung der Testhierarchie. Warum?

**A**: Es gibt bei den neuen AD RMS SDKs kein Testhierarchiekonzept. Sie arbeiten immer mit der Produktionshierarchie.

**F**: In Version 2.1 des RMS SDK war ein generiertes Manifest für jede Anwendung erforderlich, die Datenschutz implementiert. Gilt dies auch für Version 4.0 und höhere SDK-Versionen?

**A**: Nein, ab Version 3.0 des Rights Management SDK und höher sind keine Manifeste mehr erforderlich.

**Android**

**F**: Mit welchen Entwicklungsumgebungen wurde das SDK getestet?

**A**: Eclipse Juno mit der Google-API 15 und höher.

**F**: Kann ich zum Abbrechen die cancel()-Methode vom UI-Thread aufrufen?
**A**: Sie sollten cancel() aus einem Nicht-UI-Thread aufrufen, da ansonsten möglicherweise die Netzwerkverbindung getrennt wird.

**iOS**

**F**: Welche Plattformen wurden für die SDK-Entwicklung überprüft?

**A**: Xcode 5.0 mit iOS 7 und höher.

**F**: Ich habe die cancel()-Methode für einen Vorgang aufgerufen, erhalte jedoch immer noch die Benachrichtigung, dass der Vorgang abgeschlossen wurde. Warum?

**A**: Nicht alle Vorgänge können abgebrochen werden, weshalb ein Abbruchvorgang so gut wie möglich ausgeführt wird.

**OS X**

**F**: Das Beispiel-App-Framework wurde für Xcode 5 angepasst. Kann ich trotzdem Xcode 4.6 verwenden?

**A**: Das OS X-SDK funktioniert nur mit Xcode 4.6 und höher sowie OS X 10.8 und höher.

 

 



<!--HONumber=Nov16_HO1-->


