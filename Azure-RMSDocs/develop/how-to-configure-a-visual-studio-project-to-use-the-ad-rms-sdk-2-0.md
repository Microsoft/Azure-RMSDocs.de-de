---
title: Konfigurieren von Visual Studio | Azure RMS
description: Anleitung zum Konfigurieren eines Visual Studio-Projekts für die Verwendung des RMS SDK 2.1
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: d36938daf4dbcbe86331ec6852dfe4ecb04a2959
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68792404"
---
# <a name="configure-visual-studio"></a>Konfigurieren von Visual Studio

Dieser Artikel enthält Informationen zum Konfigurieren eines Visual Studio-Projekts für die Verwendung des Rights Management Services SDK 2.1.

## <a name="prerequisites"></a>Vorraussetzungen

-   [Installieren des SDK](install-the-rms-sdk.md)

**Anweisungen**

### <a name="step-1-configure-a-visual-studio-project-to-use-rmssdk21"></a>Schritt 1: Konfigurieren eines Visual Studio-Projekts für die Verwendung des RMS SDK 2.1

Diese Schritte sind spezifisch für Microsoft Visual Studio 2010. Wenn Sie eine andere Version von Microsoft Visual Studio verwenden, kann das Dialogfeld für Einstellungen bei Ihnen etwas anders aussehen.

Diese Anweisungen gelten für die Erstellung einer systemeigenen 32-Bit-Anwendung erstellen.

1.  Fügen Sie Ihrem Visual Studio 2010-Projekt das Includeverzeichnis für das RMS SDK 2.1 hinzu.

    Wählen Sie unter **Konfigurationseigenschaften** die Option **VC++-Verzeichnisse** aus, und fügen Sie das Includeverzeichnis für das RMS SDK 2.1 **$(MSIPCSDKDIR)\\inc** dem Feld **Includeverzeichnisse** hinzu.

    ![Feld „Includeverzeichnisse“ in „Konfigurationseigenschaften“](../media/include_directories.png)

2.  Fügen Sie Ihrem Visual Studio 2010-Projekt das RMS SDK 2.1-Bibliotheksverzeichnis hinzu.

    Wählen Sie unter **Konfigurationseigenschaften** die Option **VC++-Verzeichnisse** aus, und fügen Sie dem Feld **Bibliotheksverzeichnisse** das RMS SDK 2.1-Bibliotheksverzeichnis für Ihre Plattform hinzu.

    -   Verwenden Sie für Win32 **$(MSIPCSDKDIR)\\lib**.
    -   Verwenden Sie für x64 **$(MSIPCSDKDIR)\\lib\\x64**.

    ![Feld „Bibliotheksverzeichnisse“ in „Konfigurationseigenschaften“](../media/library_directories.png)

3.  Fügen Sie die RMS SDK 2.1-Bibliotheksdateien als Visual Studio 2010-Abhängigkeiten hinzu.

    Wählen Sie unter **Linker** die Option **Eingabe** aus, und fügen Sie die RMS SDK 2.1-Bibliotheksdateien **Msipc.lib** und **Msipc\_s.lib** dem Feld **Zusätzliche Abhängigkeiten** hinzu.

    ![Feld für Bibliotheksabhängigkeiten unter „Linker“](../media/additional_dependencies.png)

4.  Fügen Sie die RMS SDK 2.1-DLL (Dynamic Link Library) als eine verzögert geladene DLL hinzu.

    Wählen Sie unter **Linker** die Option **Eingabe** aus, und fügen Sie die RMS SDK 2.1-DLL-Datei **Msipc.dll** dem Feld **Verzögert geladene DLLs** hinzu.

    ![Feld für verzögert geladene Bibliotheken unter „Linker“](../media/delay_loaded.png)

5.  Erstellen Sie die Versionsinformationen für die resultierende Binärdatei.

    Wählen Sie unter **Projektmappen-Explorer** die Optio **Ressourcendateien**, und fügen Sie den Namen der Binärdatei dem Feld **Originaldateiname** hinzu.

    ![Feld „Ressourcendateien“ im Projektmappen-Explorer](../media/original_file_name.png)

## <a name="related-topics"></a>Verwandte Themen

* [Installieren des SDK](install-the-rms-sdk.md)
