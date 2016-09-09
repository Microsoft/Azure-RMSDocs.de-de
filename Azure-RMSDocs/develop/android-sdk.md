---
title: Android-Setup | Azure RMS
description: "Android-Apps können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in ihrer Anwendung zu aktivieren."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 986f6932-159b-4791-bd1a-7640a83ee792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: de012d0d85bff0e33fef0b4c53291a997d4b4e89
ms.openlocfilehash: f89ed307eae4ee14f2e463f7fb6d7e2bd07eccd0


---

# Android-Setup

Android-Apps können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in der Anwendung mithilfe von Azure Active Directory Rights Management (AAD RM) zu aktivieren.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

-   [Voraussetzungen](#prerequisites)
-   [Optional](#optional)
-   [Konfigurieren der Entwicklungsumgebung](#configuring-your-development-environment)
-   [Weitere Informationen](#see-also)

## Voraussetzungen

Die folgende Software wird auf Ihrem Entwicklungssystem empfohlen:

-   Betriebssystem Windows oder OS X zum Ausführen der [Eclipse](http://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html)-Entwicklungsumgebung.
-   In diesem Handbuch wird davon ausgegangen, dass Sie das Eclipse-SDK ab Eclipse Juno 4.2 und eine Standardinstallation verwenden.
-   Java ab Java 1.6.
-   [Android Developer Tools (ADT)-Plug-In](http://developer.android.com/sdk/installing/index.html). Hinweis – Sie werden unter Umständen aufgefordert, Eclipse zum Abschließen der Installation neu zu starten.

     

-   Das MS RMS SDK 4.2-Paket für Android. Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).

    Dieses SDK kann zur Anwendungsentwicklung für Android 4.0.3 (API-Ebene 15) und höher eingesetzt werden.

-   Authentifizierungsbibliothek: Wir empfehlen die Verwendung der [Azure AD-Authentifizierungsbibliothek (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx). Es können jedoch auch andere Authentifizierungsbibliotheken verwendet werden, die OAuth 2.0 unterstützen.

    Weitere Informationen finden Sie unter [ADAL für Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android).

    **Hinweis**: Wenn Ihre Anwendung die ADAL-Bibliothek nicht als OAuth 2.0-Authentifizierungsbibliothek verwendet, sollten Sie diese Hinweise zu Android lesen: [Some SecureRandom Thoughts](http://android-developers.blogspot.com/2013/08/some-securerandom-thoughts.html) (Überlegungen zu SecureRandom).

     

Unter [Neuheiten](release-notes.md) finden Sie Informationen zu API-Updates, Versionshinweise und häufig gestellte Fragen (FAQ).

## Optional

Unsere UI-Bibliothek bietet Entwicklern, die keine eigene benutzerdefinierte UI erstellen möchten, eine wiederverwendbare UI zur Nutzung und zum Schutz. Nutzen Sie die [UI-Bibliothek und Beispiel-App für Android](https://github.com/AzureAD/rms-sdk-ui-for-android).

## Konfigurieren der Entwicklungsumgebung

**Hinweis** MS RMS SDK 4.2 Preview-Version: In dieser Vorabversion wurden die Screenshots nicht aktualisiert, um die Änderung des Pfads von com/microsoft/protection in com/microsoft/rightsmanagment widerzuspiegeln. Der Text wurde allerdings aktualisiert.

 
-   Öffnen Sie die Eclipse-Entwicklungsumgebung.
-   Um ein neues Android-Anwendungsprojekt zu erstellen, klicken Sie im Menü **File** auf **New**, klicken Sie auf **Project**, und wählen Sie dann **Android Application Project** aus.

    ![Erstellen einer neuen Android-Anwendung](../media/Android-setup-01c.png)

-   Geben Sie den Namen der Anwendung ein. Projektname und Paketname werden auf der Grundlage des Anwendungsnamens eingetragen.
-   Klicken Sie auf **Weiter**, und wählen Sie aus, wo der Arbeitsbereich erstellt werden soll.

    ![Eingeben des Anwendungsnamens](../media/Android-setup-02a.jpg)

-   Klicken Sie auf **Next**, und wählen Sie ein Symbol für Ihre App aus.

    ![Auswählen eines Symbols für Ihre App](../media/Android-setup-03.png)

-   Klicken Sie auf **Next**, und wählen Sie **Blank Activity** aus, um die Aktivität zu erstellen.

    ![Erstellen der Aktivität](../media/Android-setup-04.png)

-   Klicken Sie auf **Next**, und geben Sie einen Namen für die Aktivität ein. Bei Verwendung des Layoutnamens *activity\_main* können Sie den Standardnamen *MainActivity* übernehmen.

    ![Angeben eines Namens für die Aktivität](../media/Android-setup-05a.jpg)

-   Klicken Sie auf **Fertig stellen**.

    ![Beenden der Erstellung](../media/Android-setup-06.jpg)

-   Das Projekt wurde zusammen mit der Hauptaktivitätsklasse *MainActivity.java* erstellt.

**Verweisen auf das SDK**

-   Navigieren Sie zu dem Ordner, in den Sie die Datei *adrms\_android\_sdk.zip* extrahiert haben. Stellen Sie sicher, dass die Dateien, stellen Sie sicher, dass *.classpath*-, *.projekt*- und *project.properties*-Dateien im Ordner "SDK > com > Microsoft > Rights Management" nicht als schreibgeschützt gekennzeichnet sind.
-   Um auf das SDK zu verweisen, müssen Sie das SDK in den Arbeitsbereich importieren.

    Klicken Sie in Eclipse auf **File**. Klicken Sie im Menü **File** auf **Import**. Wählen Sie im Dialogfeld **Import** die Option **Android / Existing Android Code into Workspace** aus.

    ![Importieren in den Arbeitsbereich](../media/Android-setup-07.png)

-   Klicken Sie auf **Weiter**. Navigieren Sie zu dem Ordner, in den Sie die Datei *adrms\_android\_sdk.zip* extrahiert haben, und wählen Sie ihn aus. Das SDK sollte angezeigt werden, in der Liste als **com.microsoft.rightsmanagement** angezeigt werden.

    ![Navigieren zum Auswählen des Ordners](../media/Android-setup-08c.jpg)

-   Wenn Sie auf **Finish** klicken, wird das SDK-Projekt als gleichgeordnetes Element der zuvor erstellten Anwendung angezeigt.

    ![Das SDK-Projekt wird als Ihrer Anwendung gleichgeordnet angezeigt](../media/Android-setup-09.jpg)

-   Klicken Sie mit der rechten Maustaste auf das Symbol **Project**, und zeigen Sie die Eigenschaften für das Projekt an.
-   Navigieren Sie zu der Registerkarte **Android**.
-   Klicken Sie auf **Add**, und wählen Sie dann die Bibliothek *com.microsoft.rightsmanagement* im Arbeitsbereich aus.

    ![Hinzufügen der Bibliothek](../media/Android-setup-10b.jpg)

-   Klicken Sie auf **OK**.

    Da das MS RMS SDK 4.2 eine Verbindung mit AAD RM herstellt, müssen der Anwendung die Berechtigungen **INTERNET** und **ACCESS\_NETWORK\_STATE** gewährt werden. Öffnen Sie dazu die Datei *AndroidManifest.xml* im Stammverzeichnis des Projekts.

    Um die Berechtigungen hinzuzufügen, klicken Sie auf **Add** und wählen dann **Uses Permissions**.

    ![Hinzufügen der Berechtigungen](../media/Android-setup-11d.jpg)

-   Sie können diesen Schritt überprüfen, indem Sie das Manifest in der Text-Editor-Ansicht anzeigen. Vergewissern Sie sich, dass die folgenden Zeilen angezeigt werden:


    <uses-sdk      android:minSdkVersion="15"      android:targetSdkVersion="19"/> <uses-permission android:name="android.permission.INTERNET"/> <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/> <uses-permission/>


**Hinweis** Das SDK verwendet *android.support.v4*.

-   Sie können jetzt Ihre eigenen neuen Android-Apps erstellen.

### Siehe auch

[Erste Schritte](get-started.md)

[Neuheiten](release-notes.md)

[Begriffe und Konzepte für Entwickler](core-concepts.md)

[Android-API-Referenz](android-namespaces.md)

 

 



<!--HONumber=Sep16_HO1-->


