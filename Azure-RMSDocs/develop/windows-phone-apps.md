---
title: Einrichten von Windows Phone | Azure RMS
description: Windows Phone-Anwendungen können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in ihrer Anwendung zu aktivieren.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e25a446e-b977-4736-9c65-7711171fb0e1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 541315cba8d1c14d7284ac6f15c38728fbd4a553
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568366"
---
# <a name="windows-phone-setup"></a>Windows Phone-Setup

[!INCLUDE [deprecation notice](../includes/deprecation-warning.md)]

Windows Phone-Apps können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Informationsschutz in der Anwendung mithilfe von Azure Active Directory Rights Management (AAD RM) zu ermöglichen.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

-   [Voraussetzungen](#prerequisites)
-   [Konfigurieren der Entwicklungsumgebung](#configuring-your-development-environment)
-   [Siehe auch](#see-also)

## <a name="prerequisites"></a>Voraussetzungen


Sie benötigen die folgende Software auf Ihrem Entwicklungssystem:

-   Das [Windows 8.1](https://windows.microsoft.com/windows-8/meet)-Betriebssystem.
-   [Windows Phone 8.1 Development Tools (SDK)](https://developer.microsoft.com/windows/downloads/sdk-archive)
-   Microsoft [Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/) oder höher oder Visual Studio Express 2012, das in Windows Phone SDK 8.0/8.1 enthalten ist
-   Das MS RMS SDK 4.2-Paket für Windows Phone. Weitere Informationen finden Sie unter " [Get Started](get-started.md)".
-   Authentifizierungsbibliothek: Wir empfehlen die Verwendung der [Azure AD-Authentifizierungsbibliothek](/previous-versions/azure/jj573266(v=azure.100)). Auch andere Authentifizierungsbibliotheken können verwendet werden.

Im Thema zu den [Neuigkeiten](release-notes.md) finden Sie Informationen zu API-Updates, Geräte- und Umgebungsinformationen, Versionshinweise und häufig gestellte Fragen (FAQ).

Sehen Sie sich die Informationen im Leitfaden für die [Windows Phone-Entwicklung](/previous-versions/windows/apps/ff402535(v=vs.105)) an

## <a name="configuring-your-development-environment"></a>Konfigurieren der Entwicklungsumgebung


-   Öffnen Sie *Visual Studio*.
-   Klicken Sie auf **Datei**. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.
-   Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual \# C** aus, wählen Sie **leere app (Windows Phone)** aus, und klicken Sie dann auf **OK**.

    ![Erstellen eines neuen Projekts](../media/wpsetup-newproj.png)

-   Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Verweis hinzufügen** aus, um das Dialogfeld **Verweis hinzufügen** zu öffnen.

    ![Hinzuzufügender Verweis](../media/wpsetup-addref.png)

-   Klicken Sie auf **Durchsuchen** unten links im Dialogfeld **Verweis hinzufügen**, und wählen Sie die *Microsoft.RightsManagment.dll*-Datei aus, die sich in dem Ordner befindet, in dem Sie das Paket extrahiert haben.
-   **Verwaltete apps** : zum Aufbauen einer verwalteten App müssen Sie diesen Verweis hinzufügen. Wählen Sie **Windows 8.1** - &gt; **Erweiterungen** aus, und aktivieren Sie das Kontrollkästchen für **Windows Visual C++ Runtime Package for Windows** .

    ![Hinzufügen von Erweiterungen](../media/wpsetup-refmngr.png)

-   **Hinzufügen von Funktionen** – Ihre Anwendung benötigt die Funktion „Internet (Client & Server)“, um das SDK verwenden zu können. Um diese Funktion Ihrer App hinzuzufügen, öffnen Sie die Datei *Package.appxmanifest* im Projekt, und navigieren Sie zur Registerkarte **Funktionen**.

Sie können jetzt Ihre eigenen neuen Windows Phone-Apps erstellen.

### <a name="see-also"></a>Weitere Informationen

[Erste Schritte](get-started.md)

[Neuigkeiten](release-notes.md)

[Wichtige Konzepte](core-concepts.md)

[Windows Phone-Entwicklung](/previous-versions/windows/apps/ff402535(v=vs.105))

[Windows-API-Referenz](/previous-versions/windows/desktop/msipcthin2/winrt)

[Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/)

[Windows Phone SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)