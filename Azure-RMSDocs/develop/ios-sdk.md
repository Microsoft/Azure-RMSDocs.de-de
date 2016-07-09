---
title: Einrichten von iOS und OS X | Azure RMS
description: "iOS- und OS X-Anwendungen können das RMS SDK 4.2 verwenden, um mithilfe von AAD RM integrierte Datenschutzfunktionen in ihrer Anwendung zu aktivieren."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b31e5b72-e65e-450a-b1b8-d46e81e9fb34
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: 821fe1c361dc38b1e33ac66208122de165d02020


---

# Einrichten von iOS und OS X

iOS- und OS X-Anwendungen können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in der Anwendung mithilfe von Azure Active Directory Rights Management (AAD RM) zu ermöglichen.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

**Hinweis**  Diese SDK bietet keine Unterstützung für iPod Touch.


-   [Voraussetzungen](#prerequisites)
-   [Optional](#optional)
-   [Konfigurieren der Entwicklungsumgebung](#configuring_your_development_environment)
-   [Weitere Informationen](#see_also)

## Voraussetzungen

Die folgende Software wird auf Ihrem Entwicklungssystem empfohlen:

-   OS X ist für alle iOS-Entwicklung erforderlich.
-   Xcode Version 6.0 und höher

    Xcode ist im [Mac App Store](https://developer.apple.com/technologies/mac/) erhältlich.

-   Das MS RMS SDK 4.2-Paket für iOS und OS X. Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).

    Dieses SDK kann für Entwicklungen für iOS 7.0 und OS X 10.8 und höher verwendet werden.

-   Authentifizierungsbibliothek: Wir empfehlen die Verwendung der [Azure AD-Authentifizierungsbibliothek (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx). Es können jedoch auch andere Authentifizierungsbibliotheken verwendet werden, die OAuth 2.0 unterstützen.

    Weitere Informationen finden Sie unter [ADAL für iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios) oder [ADAL für OS X](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/tree/OSXUniversal).

Unter [Neuheiten](release-notes.md) finden Sie Informationen zu API-Updates, Versionshinweise und häufig gestellte Fragen (FAQ).

## Optional

Unsere UI-Bibliothek bietet Entwicklern, die keine eigene benutzerdefinierte Benutzeroberfläche erstellen möchten, eine wiederverwendbare Benutzeroberfläche für Nutzungs- und Schutzverfahren. Nutzen Sie die [UI-Bibliothek und Beispiel-App für iOS](https://github.com/AzureAD/rms-sdk-ui-for-ios).

## Konfigurieren der Entwicklungsumgebung

-   Um ein neues Projekt zu erstellen, klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.
-   Wählen Sie **Single View Application**.

    ![Erstellen eines neuen Projekts](../media/iOS-Project.png)

-   Geben Sie einen Namen und einen Bezeichner für das neue Projekt ein.

    ![Benennen Sie Ihr Projekt](../media/iOS-project-options.png)

-   Klicken Sie auf **Weiter**, und wählen Sie den Speicherort für das Projekt aus.
-   Um das **MSRightsManagement**-Framework für iOS-Frameworks hinzuzufügen, ziehen Sie den Ordner ".framework" aus dem SDK-Installationsordner in den Abschnitt **Frameworks** des **Projektnavigators**.

    ![Legen Sie einen Speicherort fest](../media/ios-add-dependencies-01a.png)

-   Aktivieren Sie das Optionsfeld **Create groups for any added folders**, und deaktivieren Sie das Kontrollkästchen **Copy items into destination group's folder (if needed)**.

    Auf diese Weise bleibt der Verweis auf den SDK-Installationsordner erhalten, anstatt eine Kopie zu erstellen.

    ![Legen Sie den Verweis auf den SDK-Installationsordner fest](../media/iOS-create-groups.png)

-   Um das MS RMS SDK 4.2 für das Ressourcenpaket hinzuzufügen, ziehen Sie die Datei MSRightsManagementResources.bundle aus dem Ordner "MSRightsManagement.framework/Resources" in den Abschnitt **Frameworks** des Projektnavigators.

    ![Hinzufügen einer Ressourcengruppe](../media/iOS-add-resource-bundle-02a.png)

-   Aktivieren Sie wie beim Kopieren des Frameworks das Optionsfeld **Create groups for any added folders**, und deaktivieren Sie das Kontrollkästchen **Copy items into destination group's folder (if needed)**.
-   Das SDK basiert auf anderen Frameworks wie: **CoreData**, **MessageUI**, **SystemConfiguration**, **Libresolv** und **Security**. Um diese Frameworks hinzuzufügen, wechseln Sie zum Abschnitt **Linked Frameworks and Libraries** des Zielbereichs **Zusammenfassung**. Erweitern Sie diesen Abschnitt, um die Frameworks hinzuzufügen.

    Die Frameworks **UIKit** und **Foundation** sind erforderlich und in der Regel standardmäßig vorhanden.

    ![Hinzufügen von Ressourcen](../media/iOS-add-libraries.png)

-   Fügen Sie im Zielbereich unter **Buildeinstellungen** das Flag **-ObjC** zu **Other Linker Flags** hinzu.

    ![Hinzufügen von Buildeinstellungen](../media/iOS-linker-flags.png)

-   Der **Projektnavigator** sollte jetzt in etwa diese Struktur haben.

    ![Prüfen des Projekts](../media/iOS-verify-setup-01a.png)

-   Sie können jetzt Ihre eigenen neuen iOS/OS X-Apps erstellen.

### Siehe auch

* [Erste Schritte](get-started.md)

* [Neuheiten](release-notes.md)

* [Begriffe und Konzepte für Entwickler](core-concepts.md)

* [iOS/OS X-API-Referenz](/rights-management/sdk/4.2/api/ios/ios)

 

 






<!--HONumber=Jul16_HO2-->


