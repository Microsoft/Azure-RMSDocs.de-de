---
title: Azure Information Protection SDK 2.1-Entwicklerhandbuch | Microsoft-Dokumentation
description: Themen mit Vorgehensweisen zur Entwicklung mit dem AIP SDK 2.1
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5df7da98abf4e7c8e39b610fe374d67cf2954338
ms.openlocfilehash: 1c10eb8f7a68138761931d1c8a1715a03b7ff0a9


---

# <a name="developer-guidance"></a>Anleitung für Entwickler

Dieser Abschnitt enthält spezifische Leitfäden für mehrere wichtige Entwicklungsszenarien sowie allgemeine Informationen zur Entwicklung mit diesem SDK. Die Szenarien in diesem Abschnitt gelten speziell für diese Version des Rights Management Services SDK 2.1 und können sich in nachfolgenden Versionen ändern.
- [Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md): Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory-Authentifizierungsbibliothek (ADAL).
- [Exemplarische Vorgehensweise: Hinzufügen expliziter Besitzerrechte](add-explicit-owner-rights.md): In Ihrer Anwendung sollten explizit Rechte vom Typ „Besitzer“ hinzugefügt werden, wenn eine Lizenz von Grund auf neu erstellt wird ([IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)).
- [Exemplarische Vorgehensweise: Debuggen einer rechtlich geschützten Anwendung](debugging-applications-that-use-ad-rms.md): In diesem Thema wird veranschaulicht, wie Sie Ihre Anwendung debuggen und das Windows-Ereignisprotokoll verwenden.
- [Exemplarische Vorgehensweise: Aktivieren von Dokumentennachverfolgung und -widerruf](tracking-content.md): Dieses Thema bietet grundlegende Anleitungen zum Implementieren der Dokumentennachverfolgung für Inhalte sowie Beispielcode für Metadaten-Aktualisierungen und zum Erstellen einer Schaltfläche **Verwendung nachverfolgen** für Ihre App.
- [Exemplarische Vorgehensweise: Aktivieren von E-Mail-Benachrichtigungen](how-to-enable-email-notification.md): Mit E-Mail-Benachrichtigungen können Besitzer von geschützten Inhalten benachrichtigt werden, wenn auf ihre Inhalte zugegriffen wird.
- [Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md): In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert.
- [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md): In diesem Thema werden die Schritte zum Herstellen einer Verbindung mit einem RMS-Server oder Azure RMS zum Testen der rechtlich geschützten Anwendung behandelt.
- [Exemplarische Vorgehensweise: Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md): Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)-Funktion verwenden.
- [Exemplarische Vorgehensweise: Verwenden der Verschlüsselung](working-with-encryption.md): Dieses Thema erläutert unsere Verschlüsselungspakete und zeigt einige Codeausschnitte für deren Verwendung.
- [Anwendungstypen](application-types.md): Dieses Thema behandelt die Typen von Anwendungen, die Sie als rechtlich geschützte Anwendung erstellen können.
- [Datei-API-Konfiguration](file-api-configuration.md): Das Datei-API-Verhalten kann durch Einstellungen in der Registrierung konfiguriert werden.
- [Sicherheitsrichtlinien](security-guidelines.md): Bieten Anwendungsentwicklern Anleitungen und Informationen für ein effizientes Arbeiten mit dem AIP-Ökosystem.
- [Unterstützte Dateiformate](supported-file-formats.md): Die Datei-API unterstützt native Formate und PFile-Formate.
- [Unterstützte Plattformen](supported-platforms.md): In diesem Thema werden die vom RMS SDK 2.1 unterstützten Client- und Serverplattformen identifiziert.
- [Grundlegendes zu Nutzungsbeschränkungen](understanding-usage-restrictions.md): Sämtliche RMS-fähigen Anwendungen müssen Nutzungseinschränkungen erzwingen, die durch die in diesem Thema aufgeführten Konstanten definiert sind.

 
## <a name="related-topics"></a>Verwandte Themen
* [Übersicht](ad-rms-overview.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


