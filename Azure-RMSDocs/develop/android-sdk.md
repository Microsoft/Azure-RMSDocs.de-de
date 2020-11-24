---
title: Android-Setup | Azure RMS
description: Android-Apps können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in ihrer Anwendung zu aktivieren.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 986f6932-159b-4791-bd1a-7640a83ee792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: 24de585a77268611115342154a55cf6d78c443ad
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95567970"
---
# <a name="android-setup"></a>Android-Setup

[!INCLUDE [deprecation notice](../includes/deprecation-warning.md)]

Android-Apps können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in der Anwendung mithilfe von Azure Active Directory Rights Management (AAD RM) zu aktivieren.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

-   [Voraussetzungen](#prerequisites)
-   [Optional](#optional)
-   [Konfigurieren der Entwicklungsumgebung](#configuring-your-development-environment)
-   [Siehe auch](#see-also)

## <a name="prerequisites"></a>Voraussetzungen

Die folgende Software wird auf Ihrem Entwicklungssystem empfohlen:

-   Betriebssystem Windows oder OS X zum Ausführen der [Eclipse](https://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html)-Entwicklungsumgebung.
-   In diesem Handbuch wird davon ausgegangen, dass Sie das Eclipse-SDK ab Eclipse Juno 4.2 und eine Standardinstallation verwenden.
-   Java ab Java 1.6.
-   [Android Developer Tools (ADT)-Plug-In](https://developer.android.com/studio/install). Hinweis – Sie werden unter Umständen aufgefordert, Eclipse zum Abschließen der Installation neu zu starten.



-   Das MS RMS SDK 4.2-Paket für Android. Weitere Informationen finden Sie unter " [Get Started](get-started.md)".

    Dieses SDK kann zur Anwendungsentwicklung für Android 4.0.3 (API-Ebene 15) und höher eingesetzt werden.

-   Authentifizierungsbibliothek: Wir empfehlen die Verwendung der [Azure AD-Authentifizierungsbibliothek (ADAL)](/previous-versions/azure/jj573266(v=azure.100)). Es können jedoch auch andere Authentifizierungsbibliotheken verwendet werden, die OAuth 2.0 unterstützen.

    Weitere Informationen finden Sie unter [ADAL für Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android).

    **Hinweis**    Wenn Ihre Anwendung die Adal-Bibliothek nicht als OAuth 2,0-Authentifizierungs Bibliothek verwendet, sollten Sie diese Anleitung für Android, [einige SecureRandom-Gedanken](https://android-developers.blogspot.com/2013/08/some-securerandom-thoughts.html), lesen.



Unter [Neuheiten](release-notes.md) finden Sie Informationen zu API-Updates, Versionshinweise und häufig gestellte Fragen (FAQ).

## <a name="optional"></a>Optional

Unsere UI-Bibliothek bietet Entwicklern, die keine eigene benutzerdefinierte UI erstellen möchten, eine wiederverwendbare UI zur Nutzung und zum Schutz. Nutzen Sie die [UI-Bibliothek und Beispiel-App für Android](https://github.com/AzureAD/rms-sdk-ui-for-android).

## <a name="configuring-your-development-environment"></a>Konfigurieren der Entwicklungsumgebung

**Hinweis**    MS RMS SDK 4,2 Preview-Version: in dieser Vorschauversion wurden die Screenshots nicht aktualisiert, um die Änderung des Namens der Pfade von com/Microsoft/Protection zu com/Microsoft/righzmanagment anzuzeigen. Der Text wurde allerdings aktualisiert.


-   Öffnen Sie die Eclipse-Entwicklungsumgebung.
-   Um ein neues Android-Anwendungsprojekt zu erstellen, klicken Sie im Menü **File** auf **New**, klicken Sie auf **Project**, und wählen Sie dann **Android Application Project** aus.

    ![Erstellen einer neuen Android-Anwendung](../media/Android-setup-01c.png)

-   Geben Sie den Anwendungsnamen ein. Projektname und Paketname werden auf der Grundlage des Anwendungsnamens eingetragen.
-   Klicken Sie auf **Weiter**, und wählen Sie aus, wo der Arbeitsbereich erstellt werden soll.

    ![Eingeben des Anwendungsnamens](../media/Android-setup-02a.jpg)

-   Klicken Sie auf **Next**, und wählen Sie ein Symbol für Ihre App aus.

    ![Auswählen eines Symbols für Ihre App](../media/Android-setup-03.png)

-   Klicken Sie auf **Next**, und wählen Sie **Blank Activity** aus, um die Aktivität zu erstellen.

    ![Erstellen der Aktivität](../media/Android-setup-04.png)

-   Klicken Sie auf **Next**, und geben Sie einen Namen für die Aktivität ein. Sie können *mainactivity* als Standardnamen mit dem Layoutnamen *Activity \_ Main* belassen.

    ![Angeben eines Namens für die Aktivität](../media/Android-setup-05a.jpg)

-   Klicken Sie auf **Fertig stellen**.

    ![Beenden der Erstellung](../media/Android-setup-06.jpg)

-   Das Projekt wurde zusammen mit der Hauptaktivitätsklasse *MainActivity.java* erstellt.

**Verweisen auf das SDK**

- Navigieren Sie zu dem Ordner, in dem Sie den *ADRMS \_ Android- \_sdk.zip* extrahiert haben. Stellen Sie sicher, dass die Dateien, stellen Sie sicher, dass *.classpath*-, *.projekt*- und *project.properties*-Dateien im Ordner "SDK > com > Microsoft > Rights Management" nicht als schreibgeschützt gekennzeichnet sind.
- Um auf das SDK zu verweisen, müssen Sie das SDK in den Arbeitsbereich importieren.

  Klicken Sie in Eclipse auf **File**. Klicken Sie im Menü **Datei** auf **Importieren**. Wählen Sie im Dialogfeld **Import** die Option **Android / Existing Android Code into Workspace** aus.

  ![Importieren in den Arbeitsbereich](../media/Android-setup-07.png)

- Klicken Sie auf **Weiter**. Navigieren Sie zu dem Ordner, in dem Sie den *ADRMS \_ Android- \_sdk.zip* extrahiert haben. Das SDK sollte angezeigt werden, in der Liste als **com.microsoft.rightsmanagement** angezeigt werden.

  ![Navigieren zum Auswählen des Ordners](../media/Android-setup-08c.jpg)

- Wenn Sie auf **Finish** klicken, wird das SDK-Projekt als gleichgeordnetes Element der zuvor erstellten Anwendung angezeigt.

  ![Das SDK-Projekt wird als Ihrer Anwendung gleichgeordnet angezeigt](../media/Android-setup-09.jpg)

- Klicken Sie mit der rechten Maustaste auf das Symbol **Project**, und zeigen Sie die Eigenschaften für das Projekt an.
- Navigieren Sie zu der Registerkarte **Android**.
- Klicken Sie auf **Add**, und wählen Sie dann die Bibliothek *com.microsoft.rightsmanagement* im Arbeitsbereich aus.

  ![Hinzufügen der Bibliothek](../media/Android-setup-10b.jpg)

- Klicken Sie auf **OK**.

  Da MS RMS SDK 4,2 eine Verbindung mit Aad RM herstellt, muss die Anwendung über das **Internet** verfügen und auf den **\_ Netzwerk \_ Status zugreifen**. Öffnen Sie dazu die Datei *AndroidManifest.xml* im Stammverzeichnis des Projekts.

  Um die Berechtigungen hinzuzufügen, klicken Sie auf **Add** und wählen dann **Uses Permissions**.

  ![Hinzufügen von Berechtigungen](../media/Android-setup-11d.jpg)

- Sie können diesen Schritt überprüfen, indem Sie das Manifest in der Text-Editor-Ansicht anzeigen. Vergewissern Sie sich, dass die folgenden Zeilen angezeigt werden:

  ```
  <uses-sdk
       android:minSdkVersion="15"
       android:targetSdkVersion="19"/>
  <uses-permission android:name="android.permission.INTERNET"/>
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
  <uses-permission/>
  ```

**Hinweis**    Das SDK verwendet *Android. Support. v4*

-   Sie können jetzt Ihre eigenen neuen Android-Apps erstellen.

### <a name="see-also"></a>Weitere Informationen

[Erste Schritte](get-started.md)

[Neuigkeiten](release-notes.md)

[Begriffe und Konzepte für Entwickler](core-concepts.md)

[Android-API-Referenz](/previous-versions/windows/desktop/msipcthin2/android)