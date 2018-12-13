---
title: RMS-Entwicklerhandbuch | Azure RMS
description: Drei Generationen von Rights Management-SDK sind jetzt verfügbar.
keywords: ''
author: bryanla
manager: mbaldwin
ms.author: bryanla
ms.date: 12/11/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 0510ead4-2fe7-4269-885b-fe16bcc69888
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: c94965a6007ea93e657e719c6c9cd963cf54e66c
ms.sourcegitcommit: 1cd4edd4ba1eb5e10cb61628029213eda316783a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266442"
---
# <a name="rms-developers-guide"></a>RMS-Entwicklerhandbuch

## <a name="overview"></a>Übersicht ##
Drei Generationen des Rights Management-SDK sind jetzt verfügbar: **Microsoft Rights Management SDK 4.2** für Android, iOS/OS X, Windows-Geräte und Linux, **Microsoft Rights Management SDK 2.1** für Windows Desktop-Clients und das nicht mehr verfügbare **AD RMS SDK**.

## <a name="software-development-kits"></a>Softwareentwicklungskits ##
| SDK | Beschreibung |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Ein vereinfachtes Toolset der nächsten Generation, das eine einfache Entwicklung ermöglicht, um Ihren Android-, iOS-, Mac OS X-, Windows Phone/RT- und Linux/C++-Geräte-Apps den Schutz von Informationen über Microsoft Rights Management-Dienste zu ermöglichen |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Ein leistungsstarkes SDK-Angebot für Entwickler von Windows-Desktopanwendungen und serverbasierte Lösungsanbieter, um Rights Management für die Produkte zu ermöglichen|
|[AD RMS SDK](/azure/information-protection/develop/) |** Hinweis ** AD RMS SDK, das vom Client in "Msdrm.dll" bereitgestellte Funktionen nutzt, steht für die Verwendung in Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows Server 7, Windows Server 2008 und Windows Vista zur Verfügung. Es kann in nachfolgenden Versionen geändert oder entfernt werden. Verwenden Sie stattdessen Microsoft Rights Management Services SDK 2.1, das vom Client in "Msipc.dll" bereitgestellte Funktionen nutzt.|
|[AD RMS-Skripterstellungs-API](/azure/information-protection/develop/) | Wird zum Erstellen von Skripts zum Verwalten einer AD RMS-Installation verwendet|

## <a name="code-samples-and-tools"></a>Codebeispiele und Tools ##
Diese Sammlung von durch Microsoft bereitgestellten RMS-Codebeispielen und Entwicklersupporttools umfasst alle unterstützten Betriebssysteme – Android, iOS/OS X, Windows Phone und Windows-Desktop – und wird in regelmäßigen Abständen aktualisiert, um die Kompatibilität mit dem unterstützten SDK beizubehalten.

| Element | Betriebssystem | Unterstützende SDK-Version | Beschreibung |
|------|------------------|------------------------|-------------|
| [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows Desktop | [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) und höheren Versionen des 2.x-SDK | **IpcManagedAPI** ist eine .NET (C#)-Darstellung des RMS SDK 2.1, die auf einfache Weise die RMS-Aktivierung Ihre verwaltete Anwendung ermöglicht.|
| [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) | Windows Desktop | [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) und höheren Versionen des 2.x-SDK| **IPCNotepad** ist eine RMS-fähige Beispielanwendung, die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige Anwendung zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollten.|
| [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms)|Windows Desktop|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) und höheren Versionen des 2.x-SDK|**IpcDlp** ist eine RMS-fähige DLP-Anwendung (Data Leak Protection), die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige DLP-Anwendung mithilfe der Datei-API zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollte.|
| [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows Desktop|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) und höheren Versionen des 2.x-SDK|**IpcAzureApp** ist ein Beispiel für die Verwendung des RMS SDK in Azure-Anwendungen, um Daten im Azure Blob-Speicher zu schützen.|
| [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows Desktop|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) und höheren Versionen des 2.x-SDK|**RmsDocumentInspector** ist ein Tool, mit dem Sie Informationen zu einer beliebigen RMS-geschützten Datei erhalten können, wie z. B. Inhalts-ID oder Benutzerrechte.|
| [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows Desktop|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) und höheren Versionen des 2.x-SDK|**RmsFileWatcher** ist ein Beispiel, das veranschaulicht, wie eine Windows-Anwendung erstellt wird, die Verzeichnisse im Dateisystem überwacht, und RMS-Schutzrichtlinien bei jeder Änderung anwendet, z. B. beim Hinzufügen oder Ändern einer Datei.|
| [Szenarien für die Verwendung von iOS/OS X](https://msdn.microsoft.com/library/dn758307(v=vs.85).aspx) |iOS/OS X|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) und höheren Versionen des 4.x-SDK|Codebeispiele für **Objective C** stellen wichtige Entwicklungsszenarien dar, um Sie mit dem RMS SDK vertraut zu machen. Beispiele umfassen die Verwendung des MPF-Formats (Microsoft Protected File), benutzerdefinierte Dateiformate sowie benutzerdefinierte Steuerelemente der Benutzeroberfläche.|
| [UI-Bibliothek und Beispiel-App](https://github.com/AzureAD/rms-sdk-ui-for-ios) |iOS|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) und höheren Versionen des 4.x-SDK|**UI-Bibliothek und Beispiel-App für iOS** auf GitHub, damit Sie schnell einsteigen und unsere Standardoberfläche in Ihren Apps wiederverwenden können.|
| [UI-Bibliothek und Beispiel-App](https://github.com/AzureAD/rms-sdk-ui-for-android) |Android|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) und höheren Versionen des 4.x-SDK|**UI-Bibliothek und Beispiel-App für Android** auf GitHub, damit Sie schnell einsteigen und unsere Standardoberfläche in Ihren Apps wiederverwenden können.|
| [Szenarien für die Verwendung von Android](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) |Android|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) und höheren Versionen des 4.x-SDK|**Java-Codebeispiele** stellen wichtige Entwicklungsszenarien dar, um Sie mit dem RMS SDK vertraut zu machen. Beispiele umfassen die Verwendung des MPF-Formats (Microsoft Protected File), benutzerdefinierte Dateiformate sowie benutzerdefinierte Steuerelemente der Benutzeroberfläche.|