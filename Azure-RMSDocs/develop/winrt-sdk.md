---
title: Windows Store-Setup | Azure RMS
description: Windows Store-Anwendungen können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in ihrer Anwendung zu aktivieren.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2720aa0e-0d37-469f-be99-678bf95a9c51
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: b7317dcd85cf8dd1792dee583a96bfa370673b4d
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071793"
---
# <a name="windows-store-setup"></a>Windows Store-Setup

Windows Store-Anwendungen können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Informationsschutz in der Anwendung mithilfe von Azure Active Directory Rights Management (AAD RM) zu ermöglichen.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

-   [Voraussetzungen](#prerequisites)
-   [Optional](#optional)
-   [Konfigurieren der Entwicklungsumgebung](#configuring-your-development-environment)
-   [Siehe auch](#see-also)

## <a name="prerequisites"></a>Voraussetzungen


Sie benötigen auf Ihrem Entwicklungssystem die folgende Software:

-   [Windows 8.1](https://windows.microsoft.com/windows-8/meet)-Betriebssystem
-   [Windows SDK für Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)
-   Microsoft [Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/) oder höher oder Visual Studio Express 2012, das im Windows SDK für Windows 8.0/8.1 enthalten ist
-   Das MS RMS SDK 4.2-Paket für Windows Store-Anwendungen Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).
-   Authentifizierungsbibliothek: Die Verwendung der [Azure AD-Authentifizierungsbibliothek](https://msdn.microsoft.com/library/jj573266.aspx) wird empfohlen. Auch andere Authentifizierungsbibliotheken können verwendet werden.

Im Thema zu den [Neuheiten](release-notes.md) finden Sie Informationen zu API-Updates, Geräte- und Umgebungsinformationen, Versionshinweise und häufig gestellte Fragen (FAQ).

## <a name="optional"></a>Optional

Unsere UI-Bibliothek bietet Entwicklern, die keine eigene benutzerdefinierte Benutzeroberfläche erstellen möchten, eine wiederverwendbare Benutzeroberfläche für Nutzungs- und Schutzverfahren. Nutzen Sie die [UI-Bibliothek für Windows Store-Apps](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore). Außerdem stellen wir eine Beispielanwendung für eine Windows Store-App bereit: [RMS-Beispielanwendung für Windows Store](https://github.com/AzureADSamples/rms-samples-for-windowsstore).

## <a name="configuring-your-development-environment"></a>Konfigurieren der Entwicklungsumgebung


-   Öffnen Sie Visual Studio.
-   Klicken Sie auf **Datei**, **Neu** und anschließend auf **Projekt**.
-   Klicken Sie im Dialogfeld **Neues Projekt** auf **Visual C\#**, und wählen Sie **Leere App (Windows)** aus. Klicken Sie anschließend auf **OK**.

    ![Erstellen eines neuen Projekts](../media/winrtsetup-newproj.png)

-   Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Verweis hinzufügen** aus, um das Dialogfeld **Verweis hinzufügen** zu öffnen.

    ![Hinzufügen eines Verweises](../media/winrtsetup-addref.png)

-   Klicken Sie im Dialogfeld **Verweis hinzufügen** auf **Durchsuchen**, und wählen Sie die Datei *Microsoft.RightsManagment.dll* aus, die sich in dem Ordner befindet, in den Sie das SDK-Paket extrahiert haben.
-   **Verwaltete Apps**: Zum Erstellen einer verwalteten App müssen Sie diesen Verweis hinzufügen. Wählen Sie **Windows 8.1**-&gt;**Erweiterungen** aus, und aktivieren Sie das Kontrollkästchen für das **Windows Visual C++-Laufzeitpaket für Windows**.

    ![Hinzufügen von Erweiterungen](../media/winrtsetup-refmngr.png)

-   **Hinzufügen von Funktionen**: Ihre Anwendung benötigt die Funktion „Internet (Client & Server)“, um das SDK verwenden zu können. Um diese Funktion Ihrer App hinzuzufügen, öffnen Sie die Datei *Package.appxmanifest* im Projekt, und navigieren Sie zur Registerkarte **Funktionen**.

Sie können jetzt Ihre eigenen neuen Windows Store-Apps erstellen.

### <a name="see-also"></a>Weitere Informationen

[Erste Schritte](get-started.md)

[Neuerungen](release-notes.md)

[Begriffe und Konzepte für Entwickler](core-concepts.md)

[Windows 8](https://windows.microsoft.com/windows-8/meet)

[Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/)

[Windows-API-Referenz](https://msdn.microsoft.com/library/dn891914.aspx)
