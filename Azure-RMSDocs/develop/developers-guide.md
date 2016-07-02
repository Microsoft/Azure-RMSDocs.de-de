---
title: Entwicklerhandbuch | Azure RMS
description: "Überblick über die verwendeten Entwicklertools, SDKs, zusätzliche Bibliotheken und Codebeispiele."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a22e6bd0-8ce8-45b4-9a32-273126ab831e
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: c9d5ec961989283c5201a81f862b2da45ed64340


---

# Entwicklerhandbuch

## Übersicht ##
Dieses Handbuch bietet einen Überblick über unsere Rights Management SDK-Produktfamilie und einer wachsenden Zahl von Tools und Codebeispielen, die alle unterstützten Plattformen abdecken. 

## Softwareentwicklungskits ##
Aktuell sind drei Generationen von RMS SDKs erhältlich, die in der nachstehenden Tabelle dargestellt werden.

| SDK | Beschreibung |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Ein vereinfachtes Toolset der nächsten Generation, das eine einfache Entwicklung ermöglicht, um Ihren Android-, iOS-, Mac OS X-, Windows Phone/RT- und Linux/C++-Geräte-Apps den Schutz von Informationen über Microsoft Rights Management-Dienste zu ermöglichen |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Ein leistungsstarkes SDK-Angebot für Entwickler von Windows-Desktopanwendungen und serverbasierte Lösungsanbieter, um Rights Management für die Produkte zu ermöglichen|
|[AD RMS SDK](https://msdn.microsoft.com/library/cc530379(v=vs.85).aspx)|** Hinweis ** – Das AD RMS SDK, das vom Client in „Msdrm.dll“ bereitgestellte Funktionen nutzt, steht für die Verwendung in Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows Server 7, Windows Server 2008 und Windows Vista zur Verfügung. Es kann in nachfolgenden Versionen geändert oder entfernt werden. Verwenden Sie stattdessen Microsoft Rights Management Services SDK 2.1, das vom Client in "Msipc.dll" bereitgestellte Funktionen nutzt.|
|[AD RMS-Skripterstellungs-API](https://msdn.microsoft.com/en-us/library/bb968797(v=vs.85).aspx)| Wird zum Erstellen von Skripts zum Verwalten einer AD RMS-Installation verwendet|

## Codebeispiele und Tools
Diese Sammlung von durch Microsoft bereitgestellten RMS-Codebeispielen und Entwicklersupporttools umfasst alle unterstützten Betriebssysteme – Android, iOS/OS X, Windows Phone und Windows-Desktop – und wird in regelmäßigen Abständen aktualisiert, um die Kompatibilität mit dem unterstützten SDK beizubehalten.

### Android

Folgendes kann auf Android unterstützt durch [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) und höhere Versionen des 4.x-SDKs ausgeführt werden.

- [UI-Bibliothek und Beispiel-App](https://github.com/AzureAD/rms-sdk-ui-for-android) auf GitHub, damit Sie schnell einsteigen und unsere Standardoberfläche in Ihren Apps wiederverwenden können.
- [Android-Verwendungsszenarios](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) in Java stellen wichtige Entwicklungsszenarios dar, um Sie mit dem RMS-SDK vertraut zu machen. Beispiele umfassen die Verwendung des MPF-Formats (Microsoft Protected File), benutzerdefinierte Dateiformate sowie benutzerdefinierte Steuerelemente der Benutzeroberfläche.

### iOS/OS X

Folgendes kann auf iOS/OS X unterstützt durch [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) und höhere Versionen des 4.x-SDKs ausgeführt werden.

- [iOS/OS X-Verwendungsszenarios](https://msdn.microsoft.com/en-us/library/dn758307(v=vs.85).aspx) in Objective C stellen wichtige Entwicklungsszenarios dar, um Sie mit dem RMS-SDK vertraut zu machen. Beispiele umfassen die Verwendung des MPF-Formats (Microsoft Protected File), benutzerdefinierte Dateiformate sowie benutzerdefinierte Steuerelemente der Benutzeroberfläche.
- [UI-Bibliothek und Beispiel-App](https://github.com/AzureAD/rms-sdk-ui-for-ios) auf GitHub, damit Sie schnell einsteigen und unsere Standardoberfläche in Ihren Apps wiederverwenden können. **Nur unter iOS** unterstützt.

### Windows Desktop

Folgendes kann auf Windows-Desktop unterstützt durch [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) und höhere Versionen des 2.x-SDKs ausgeführt werden.

- [Durch PFILE geschützte PDF-Datei lesen](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) ist ein einfaches Codebeispiel in unserem RMS Developer's Corner-Blog, das die MSIPC-Datei-API zum Entschlüsseln und Öffnen eines durch PFILE geschützten PDF-Dokuments verwendet.
- [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist eine .NET (C#)-Darstellung des RMS SDK 2.1, die auf einfache Weise die RMS-Aktivierung Ihre verwaltete Anwendung ermöglicht.
- [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) ist eine RMS-fähige Beispielanwendung, die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige Anwendung zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollten.
- [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist eine RMS-fähige DLP-Anwendung (Data Leak Protection), die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige DLP-Anwendung mithilfe der Datei-API zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollte.
- [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Beispiel für die Verwendung des RMS SDK in Azure-Anwendungen, um Daten im Azure Blob-Speicher zu schützen.
- [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Tool, mit dem Sie Informationen zu einer beliebigen RMS-geschützten Datei erhalten können, wie z. B. Inhalts-ID oder Benutzerrechte.
- [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Beispiel, das veranschaulicht, wie eine Windows-Anwendung erstellt wird, die Verzeichnisse im Dateisystem überwacht, und RMS-Schutzrichtlinien bei jeder Änderung anwendet, z. B. beim Hinzufügen oder Ändern einer Datei.

### Windows Store und Windows Phone

- [UI-Bibliothek für Windows Store](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore) – eine UI-Bibliothek für Microsoft RMS SDK v4.1 für Windows Store-Anwendungen. Diese Bibliothek ist optional, und Entwickler können eine eigene Benutzeroberfläche erstellen, wenn Sie Microsoft RMS SDK v4.1 verwenden.

- [UI-Bibliothek für Windows Phone](https://github.com/AzureAD/rms-sdk-ui-for-winphone) – eine UI-Bibliothek für Microsoft RMS SDK v4.1 für Windows Phone-Anwendungen. Diese Bibliothek ist optional, und Entwickler können eine eigene Benutzeroberfläche erstellen, wenn Sie Microsoft RMS SDK v4.1 verwenden.

- [Beispielanwendung](https://github.com/Azure-Samples/active-directory-dotnet-rms-windowsstore) – Das Beispiel für Microsoft RMS SDK v4.1 für Windows Store-Anwendungen stellt ein grundlegendes Verbrauchsbeispiel für die Plattform bereit.



<!--HONumber=Jun16_HO4-->


