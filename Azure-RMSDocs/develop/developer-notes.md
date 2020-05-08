---
title: Azure Information Protection SDK 2.1-Entwicklerhandbuch | Microsoft-Dokumentation
description: Themen mit Vorgehensweisen zur Entwicklung mit dem AIP SDK 2.1
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 01/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: 620464886d40c3f152a32f07952a924eee72920f
ms.sourcegitcommit: 298843953f9792c5879e199fd1695abf3d25aa70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2020
ms.locfileid: "82971811"
---
# <a name="developer-guidance"></a>Anleitung für Entwickler

Dieser Abschnitt enthält spezifische Leitfäden für mehrere wichtige Entwicklungsszenarien sowie allgemeine Informationen zur Entwicklung mit diesem SDK. Die Szenarien in diesem Abschnitt gelten speziell für diese Version des Rights Management Services SDK 2.1 und können sich in nachfolgenden Versionen ändern.
- [Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md): Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory-Authentifizierungsbibliothek (ADAL).
- Gewusst [wie: Hinzufügen expliziter Besitzer Rechte:](add-explicit-owner-rights.md) Ihre Anwendung sollte explizit die Rechte "Besitzer" hinzufügen, wenn eine Lizenz von Grund auf neu erstellt wird ([ipckreatelicensefromscratch](https://msdn.microsoft.com/library/hh535256.aspx)).
- [Exemplarische Vorgehensweise: Debuggen einer rechtlich geschützten Anwendung](debugging-applications-that-use-ad-rms.md): In diesem Thema wird veranschaulicht, wie Sie Ihre Anwendung debuggen und das Windows-Ereignisprotokoll verwenden.
- [Exemplarische Vorgehensweise: Bereitstellen einer App in einen Mandanten eines Kunden](how-to-deploy-app.md): Zeigt die Schritte zum Bereitstellen einer App aus dessen Entwicklungs-Azure AD-Mandanten zu einem Produktions-Azure AD-Mandanten.
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

 
## <a name="related-topics"></a>Zugehörige Themen
* [Übersicht](ad-rms-overview.md)
