---
title: Einrichten von iOS und OS X | Azure RMS
description: iOS- und OS X-Anwendungen können das RMS SDK 4.2 verwenden, um mithilfe von AAD RM integrierte Datenschutzfunktionen in der Anwendung zu aktivieren.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b31e5b72-e65e-450a-b1b8-d46e81e9fb34
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 392bfa5e76bd0e07212fd47042b514a243a652dd
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333448"
---
# <a name="ios-and-os-x-setup"></a>iOS- und OS X-Setup

iOS- und OS X-Anwendungen können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in der Anwendung mithilfe von Azure Rights Management (Azure RMS) zu ermöglichen.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

**Hinweis:**   Diese SDK bietet keine Unterstützung für iPod Touch.


-   [Voraussetzungen](#prerequisites)
-   [Optional](#optional)
-   [Konfigurieren der Entwicklungsumgebung](#configuring-your-development-environment)
-   [Siehe auch](#see-also)

## <a name="prerequisites"></a>Voraussetzungen

Die folgende Software wird auf Ihrem Entwicklungssystem empfohlen:

-   OS X ist für alle iOS-Entwicklung erforderlich.
-   Xcode Version 6.0 und höher

    Xcode ist im [Mac App Store](https://developer.apple.com/technologies/mac/) erhältlich.

-   Das MS RMS SDK 4.2-Paket für iOS und OS X. Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).

    Dieses SDK kann für Entwicklungen für iOS 7.0 und OS X 10.8 und höher verwendet werden.

-   Authentifizierungsbibliothek: Es wird empfohlen, die [Azure AD-Authentifizierungsbibliothek (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx) zu verwenden. Es können jedoch auch andere Authentifizierungsbibliotheken verwendet werden, die OAuth 2.0 unterstützen.

    Weitere Informationen finden Sie unter [ADAL für iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios) oder [ADAL für OS X](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/tree/OSXUniversal).

Unter [Neuheiten](release-notes.md) finden Sie Informationen zu API-Updates, Versionshinweise und häufig gestellte Fragen (FAQ).

## <a name="optional"></a>Optional

Unsere UI-Bibliothek bietet Entwicklern, die keine eigene benutzerdefinierte Benutzeroberfläche erstellen möchten, eine wiederverwendbare Benutzeroberfläche für Nutzungs- und Schutzverfahren. Nutzen Sie die [UI-Bibliothek und Beispiel-App für iOS](https://github.com/AzureAD/rms-sdk-ui-for-ios).

## <a name="configuring-your-development-environment"></a>Konfigurieren der Entwicklungsumgebung

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

-   Um das MS RMS SDK 4.2 für das Ressourcenpaket hinzuzufügen, ziehen Sie die Datei „MSRightsManagementResources.bundle“ aus dem Ordner „MSRightsManagement.framework/Resources“ in den Abschnitt **Frameworks** des Projektnavigators.

    ![Hinzufügen einer Ressourcengruppe](../media/iOS-add-resource-bundle-02a.png)

-   Aktivieren Sie wie beim Kopieren des Frameworks das Optionsfeld **Create groups for any added folders**, und deaktivieren Sie das Kontrollkästchen **Copy items into destination group's folder (if needed)**.
-   Das SDK basiert auf anderen Frameworks, z. B.: **CoreData**, **MessageUI**, **SystemConfiguration**, **Libresolv** und **Security**. Um diese Frameworks hinzuzufügen, wechseln Sie zum Abschnitt **Linked Frameworks and Libraries** des Zielbereichs **Zusammenfassung**. Erweitern Sie diesen Abschnitt, um die Frameworks hinzuzufügen.

    Die Frameworks **UIKit** und **Foundation** sind erforderlich und in der Regel standardmäßig vorhanden.

    ![Hinzufügen von Ressourcen](../media/iOS-add-libraries.png)

-   Fügen Sie im Zielbereich unter **Buildeinstellungen** das Flag **-ObjC** zu **Other Linker Flags** hinzu.

    ![Hinzufügen von Buildeinstellungen](../media/iOS-linker-flags.png)

-   Der **Projektnavigator** sollte jetzt in etwa diese Struktur haben.

    ![Prüfen des Projekts](../media/iOS-verify-setup-01a.png)

-   Sie können jetzt Ihre eigenen neuen iOS/OS X-Apps erstellen.

### <a name="see-also"></a>Weitere Informationen

* [Erste Schritte](get-started.md)

* [Neuerungen](release-notes.md)

* [Begriffe und Konzepte für Entwickler](core-concepts.md)

* [iOS/OS X-API-Referenz](https://msdn.microsoft.com/library/dn758306.aspx)
