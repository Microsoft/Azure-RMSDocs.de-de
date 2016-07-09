---
title: Neuheiten und Versionshinweise | Azure RMS
description: "Beschreibt wichtige Änderungen und Funktionen in dieser neuen Version des RMS SDK."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 06/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: eccc0ba9c13e0c35c8d0c8877ce92f9b99e83835


---

# Neuheiten und Versionshinweise

## Neuheiten
Das Microsoft Rights Management SDK 4.2 ermöglicht eine noch einfachere und flexiblere Aktivierung der RMS-Anwendung. In diesem Thema werden wichtige Änderungen und Funktionen in der neuen Version des RMS SDK beschrieben.

-   [Neu ab Juni 2016](#new_for_June_2016)
-   [Dezember 2015-Update](#december_2015_update)
-   [Juli 2015-Update – Unterstützung für Linux/C++-Entwicklung hinzugefügt](#july_2015_update_-_adds_support_for_linux___c___development)
-   [Mai 2015-Update – Steuerung der Protokollierung hinzugefügt](#may_2015_update_-_adds_logging_control)
-   [Februar 2015-Update – Unterstützung für Windows Store-Anwendung hinzugefügt](#february_2015_update_-_adds_windows_store_application_support)
-   [Januar 2015-Update – Unterstützung für WinPhone-Plattform hinzugefügt](#january_2015_update_-_adds_winphone_platform_support)
-   [Oktober 2014-Update – Upgrade auf Microsoft RMS SDK 4.1](#october_2014_update_-_upgrade_to_microsoft_rms_sdk_4.1)
-   [Anmerkungen zu dieser Version](#release-notes)
-   [Häufig gestellte Fragen](#frequently_asked_questions)

### Neu ab Juni 2016

- **Unterstützung moderner Authentifizierung**: Diese ermöglicht in RMS-fähigen Apps die Anmeldung mithilfe der Active Directory-Authentifizierungsbibliothek (Active Directory Authentication Library; ADAL). Dadurch werden Anmeldefunktionen wie Multi-Factor Authentication (MFA), SAML-basierte Identitätsanbieter (Drittanbieter) mit RMS-Clientanwendungen und die smartcard- und zertifikatbasierte Authentifizierung aktiviert. Außerdem müssen RMS-fähige Apps nicht mehr das Standardauthentifizierungsprotokoll verwenden.
- **Unterstützung von Dokumentkontrolle**: Entwickler können nun die Dokumentkontrolle aktivieren, wenn sie Dokumente in ihren Apps schützen 
- Leistungsverbesserungen
- Fehlerbehebungen


### Dezember 2015-Update

Mit dieser Version liegt das RMS SDK für Geräte jetzt in Version 4.2 mit folgenden Ergänzungen vor:

-   Dokumentenverfolgung, nur RMS Online für iOS/OS X- und Android-Betriebssysteme.

    Details und Anleitungen für iOS/OS X erhalten Sie in der [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc)-Klasse. Hier finden Sie Nachverfolgungsinformationen sowie die zusätzliche Registrierungsmethode für die Dokumentenverfolgung mit [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc). Ähnliche Ergänzungen sind für Android für [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) und [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy) vorhanden.

    Eine ausführliche Beschreibung der Dokumentenverfolgungsfunktion finden Sie unter [**Vorgehensweise: Verwenden von Dokumentenverfolgung**](how-to-use-document-tracking.md).

-   Eine Reihe synchroner Methoden, die parallel zu den asynchronen Versionen für die Android-API verwendet werden:

    [**Synchrone CustomProtectedInputStream.create-Methode**](/rights-management/sdk/4.2/api/android/customprotectedinputstream#msipcthin2_customprotectedinputstream_create_synchronous_method_java)

    [**Synchrone CustomProtectedOutputStream.create-Methode**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**Synchrone ProtectedFileInputStream.create-Methode**](/rights-management/sdk/4.2/api/android/protectedfileinputstream#msipcthin2_protectedfileinputstream_create_synchronous_method)

    [**Synchrone ProtectedFileOutputStream.create-Methode**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**Synchrone TemplateDescriptor.getTemplates-Methode**](/rights-management/sdk/4.2/api/android/templatedescriptor#msipcthin2_templatedescriptor_gettemplates_synchronous_method_java)

    [**Synchrone UserPolicy.acquire-Methode**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_acquire_synchronous_method_java)

    [**Synchrone UserPolicy.create-Methode (PolicyDescriptor…)**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_policydescriptor_______synchronous_method_java)

    [**Synchrone UserPolicy.create-Methode (TempalteDescriptor…)**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_templatedescriptor_______synchronous_method_java)

-   Der Android-API-Klasse wurde eine neue [**ProtectedBuffer**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_protectedbuffer_class)-Klasse hinzugefügt.
-   Updates zur Verbesserung der Fehlermeldungen und der Problembehandlung.
-   Beträchtliche Leistungssteigerungen für kryptografische Operationen.

### Juli 2015-Update – Unterstützung für Linux/C++-Entwicklung hinzugefügt

Diese Version bietet folgende Zusätze:

-   RMS SDK 4.1 für Linux-Plattformen

    Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).

### Mai 2015-Update – Steuerung der Protokollierung hinzugefügt

Diese Version unterstützt Folgendes:

-   iOS

    App-Verschlüsselung und -Entschlüsselung können unabhängig und parallel ausgeführt werden.

    Weitere Informationen finden Sie unter [**MSProtector**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msprotector_class_objc).

    Aktivierte Steuerungseinstellungen auf Protokollebene.

    Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren der Fehler- und Leistungsprotokollierung](enabling-logging.md).

    Unterstützung zum Löschen des Caches hinzugefügt.

    Weitere Informationen finden Sie unter [**MSProtection:resetStateWithCompletionBlock**](/rights-management/sdk/4.2/api/iOS/msprotection#msipcthin2_msprotection_resetstatewithcompletionblock_method_objc).

### Februar 2015-Update – Unterstützung für Windows Store-Anwendung hinzugefügt

Diese Version bietet Unterstützung für Windows Store-Anwendungen sowie funktionale Parität mit der Windows Phone-, Android- und iOS/OS X-Version des RMS SDK 4.1.

### Januar 2015-Update – Unterstützung für WinPhone-Plattform hinzugefügt

Diese Version bietet Unterstützung für das Windows Phone-Betriebssystem sowie funktionale Parität mit der Android- und iOS/OS X-Version des RMS SDK 4.1.

## Oktober 2014-Update – Upgrade auf Microsoft RMS SDK 4.1

Die Version 4.1 des RMS SDK fügt die folgenden neuen Features für Google Android und Apple iOS/OS X hinzu.

-   Android und iOS/OS X-SDK-API-Erweiterungen zur Verarbeitung der *Benutzerzustimmung*, sodass SDK-Verhalten vom Benutzer bestätigt werden können. Aktuell werden als Zustimmungstypen die Dokumentenverfolgung und der Zugriff auf unbekannte AD RMS-Dienst-URLs unterstützt.

    Weitere Informationen finden Sie im Beispiel der Android-API-Version der [**ConsentCallback-Schnittstelle**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_consentcallback_interface_java).

-   iOS 8 und OS X 10.10 (Yosemite) werden jetzt unterstützt. Auch gab es aufgrund von Xcode 6 Änderungen bei den Eigenschaftsnamen.

    Beispiel: MSUserPolicy.name wurde geändert in [**MSUserPolicy.policyName**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_name_property_objc).

## Anmerkungen zu dieser Version

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

-   Bei Verwendung der Methode [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] array, int offset, int length)** mit einer vom Wert *array.length* abweichenden Länge kann der Inhalt später nicht mit dem SDK verwendet werden.

    **Lösung**: Dies ist ein bekanntes Problem. Übergeben Sie zur Vermeidung dessen entweder ein **byte \[\]**-Array mit einem Längenwert gleich dem length-Parameter, oder verwenden Sie die Methode [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] array)**.

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

    - [**protectedDataWithProtectedFile**](/rights-management/sdk/4.2/api/iOS/msprotecteddata#msipcthin2_msprotecteddata_protecteddatawithprotectedfile_completionblock_method_objc)
    - [**customProtectedDataWithPolicy**](/rights-management/sdk/4.2/api/iOS/mscustomprotecteddata#msipcthin2_mscustomprotecteddata_customprotecteddatawithpolicy_protecteddata_contentstartposition_contentsize_completionblock_method_objc)



**Hinweis**  MDI-Anwendungen werden von unserer iOS-API nicht unterstützt.

## Häufig gestellte Fragen

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

 

 



<!--HONumber=Jul16_HO2-->


