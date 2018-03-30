---
title: Einrichten von Windows Phone | Azure RMS
description: Windows Phone-Anwendungen können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Datenschutz in ihrer Anwendung zu aktivieren.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e25a446e-b977-4736-9c65-7711171fb0e1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: e606703aa764f8e4fea009131f41c9394ebb29fb
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2018
---
# <a name="windows-phone-setup"></a>Windows Phone-Setup


Windows Phone-Apps können das Microsoft Rights Management SDK 4.2 verwenden, um den integrierten Informationsschutz in der Anwendung mithilfe von Azure Active Directory Rights Management (AAD RM) zu ermöglichen.

Dieses Thema führt Sie durch das Einrichten der Umgebung zum Erstellen eigener neuer Apps.

-   [Voraussetzungen](#prerequisites)
-   [Konfigurieren der Entwicklungsumgebung](#configuring-your-development-environment)
-   [Siehe auch](#see-also)

## <a name="prerequisites"></a>Voraussetzungen


Sie benötigen die folgende Software auf Ihrem Entwicklungssystem:

-   Das [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet)-Betriebssystem.
-   [Windows Phone 8.1 Development Tools (SDK)](http://dev.windowsphone.com/en-us/downloadsdk)
-   Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview) oder höher oder Visual Studio Express 2012, das in Windows Phone SDK 8.0/8.1 enthalten ist
-   Das MS RMS SDK 4.2-Paket für Windows Phone. Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).
-   Authentifizierungsbibliothek: Wir empfehlen die Verwendung der [Azure AD-Authentifizierungsbibliothek](https://msdn.microsoft.com/library/jj573266.aspx). Auch andere Authentifizierungsbibliotheken können verwendet werden.

Im Thema zu den [Neuigkeiten](release-notes.md) finden Sie Informationen zu API-Updates, Geräte- und Umgebungsinformationen, Versionshinweise und häufig gestellte Fragen (FAQ).

Sehen Sie sich die Informationen im Leitfaden für die [Windows Phone-Entwicklung](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx) an

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

### <a name="see-also"></a>Weitere Informationen

[Erste Schritte](get-started.md)

[Neuerungen](release-notes.md)

[Kernkonzepte](core-concepts.md)

[Windows Phone-Entwicklung](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx)

[Windows-API-Referenz](https://msdn.microsoft.com/library/dn891914.aspx)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Windows Phone SDK](http://dev.windowsphone.com/en-us/downloadsdk)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]