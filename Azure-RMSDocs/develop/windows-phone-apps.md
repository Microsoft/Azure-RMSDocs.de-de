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
ms.openlocfilehash: 08981ab13862eed815609eaad4c6733ec205e0a1
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68792090"
---
# <a name="windows-phone-setup"></a>Windows Phone-Setup


Windows Phone-Apps können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Informationsschutz in der Anwendung mithilfe von Azure Active Directory Rights Management (AAD RM) zu ermöglichen.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

-   [Erforderliche Komponenten](#prerequisites)
-   [Konfigurieren der Entwicklungsumgebung](#configuring-your-development-environment)
-   [Siehe auch](#see-also)

## <a name="prerequisites"></a>Vorraussetzungen


Sie benötigen die folgende Software auf Ihrem Entwicklungssystem:

-   Das [Windows 8.1](https://windows.microsoft.com/windows-8/meet)-Betriebssystem.
-   [Windows Phone 8.1 Development Tools (SDK)](https://developer.microsoft.com/windows/downloads/sdk-archive)
-   Microsoft [Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/) oder höher oder Visual Studio Express 2012, das in Windows Phone SDK 8.0/8.1 enthalten ist
-   Das MS RMS SDK 4.2-Paket für Windows Phone. Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).
-   Authentifizierungsbibliothek: Die Verwendung der [Azure AD-Authentifizierungsbibliothek](https://msdn.microsoft.com/library/jj573266.aspx) wird empfohlen. Auch andere Authentifizierungsbibliotheken können verwendet werden.

Im Thema zu den [Neuheiten](release-notes.md) finden Sie Informationen zu API-Updates, Geräte- und Umgebungsinformationen, Versionshinweise und häufig gestellte Fragen (FAQ).

Sehen Sie sich die Informationen im Leitfaden für die [Windows Phone-Entwicklung](https://msdn.microsoft.com/library/windowsphone/develop/ff402535.aspx) an

## <a name="configuring-your-development-environment"></a>Konfigurieren der Entwicklungsumgebung


-   Öffnen Sie *Visual Studio*.
-   Klicken Sie auf **Datei**. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.
-   Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C\#** und anschließend **Leere App (Windows Phone)** aus, und klicken Sie anschließend auf **OK**.

    ![Erstellen eines neuen Projekts](../media/wpsetup-newproj.png)

-   Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Verweis hinzufügen** aus, um das Dialogfeld **Verweis hinzufügen** zu öffnen.

    ![Hinzufügen eines Verweises](../media/wpsetup-addref.png)

-   Klicken Sie auf **Durchsuchen** unten links im Dialogfeld **Verweis hinzufügen**, und wählen Sie die *Microsoft.RightsManagment.dll*-Datei aus, die sich in dem Ordner befindet, in dem Sie das Paket extrahiert haben.
-   **Verwaltete Apps**: Zum Erstellen einer verwalteten App müssen Sie diesen Verweis hinzufügen. Wählen Sie **Windows 8.1**-&gt;**Erweiterungen** aus, und aktivieren Sie das Kontrollkästchen für **das Windows Visual C++-Laufzeitpaket für Windows**.

    ![Hinzufügen von Erweiterungen](../media/wpsetup-refmngr.png)

-   **Hinzufügen von Funktionen** – Ihre Anwendung benötigt die Funktion „Internet (Client & Server)“, um das SDK verwenden zu können. Um diese Funktion zu Ihrer App hinzuzufügen, öffnen Sie die Datei *Package.appxmanifest* im Projekt, und navigieren Sie zur Registerkarte **Funktionen**.

Sie können jetzt Ihre eigenen neuen Windows Phone-Apps erstellen.

### <a name="see-also"></a>Siehe auch

[Erste Schritte](get-started.md)

[Neuerungen](release-notes.md)

[Kernkonzepte](core-concepts.md)

[Windows Phone-Entwicklung](https://msdn.microsoft.com/library/windowsphone/develop/ff402535.aspx)

[Windows-API-Referenz](https://msdn.microsoft.com/library/dn891914.aspx)

[Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/)

[Windows Phone SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)
