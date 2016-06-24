---
# required metadata

title: Anleitung für Entwickler und Informationen | Azure RMS
description: Dieses Thema enthält spezifische Leitfäden für mehrere wichtige Entwicklungsszenarien.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Anleitung für Entwickler und Informationen

Dieser Abschnitt enthält spezifische Leitfäden für mehrere wichtige Entwicklungsszenarien sowie allgemeine Informationen zur Entwicklung mit diesem SDK. Die Szenarien in diesem Abschnitt gelten speziell für diese Version des Rights Management Services SDK 2.1 und können sich in nachfolgenden Versionen ändern.
- [Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung](how-to-use-adal-authentication.md): Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory-Authentifizierungsbibliothek (ADAL).
- [Exemplarische Vorgehensweise: Hinzufügen expliziter Besitzerrechte](add-explicit-owner-rights.md): In Ihrer Anwendung sollten explizit Rechte vom Typ &quot;Besitzer&quot; hinzugefügt werden, wenn eine Lizenz von Grund auf neu erstellt wird ([IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)).
- [Exemplarische Vorgehensweise: Debuggen einer rechtlich geschützten Anwendung](debugging-applications-that-use-ad-rms.md): In diesem Thema wird veranschaulicht, wie Sie Ihre Anwendung debuggen und das Windows-Ereignisprotokoll verwenden.
- [Exemplarische Vorgehensweise: Aktivieren von Dokumentennachverfolgung und -widerruf](tracking-content.md): Dieses Thema bietet grundlegende Anleitungen zum Implementieren der Dokumentennachverfolgung für Inhalte sowie Beispielcode für Metadaten-Aktualisierungen und zum Erstellen einer Schaltfläche **Verwendung nachverfolgen** für Ihre App.
- [Exemplarische Vorgehensweise: Aktivieren von E-Mail-Benachrichtigungen](how-to-enable-email-notification.md): Mit E-Mail-Benachrichtigungen können Besitzer von geschützten Inhalten benachrichtigt werden, wenn auf ihre Inhalte zugegriffen wird.
- [Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md): In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert.
- [Exemplarische Vorgehensweise: Installieren und Konfigurieren eines RMS-Servers](how-to-install-and-configure-an-rms-server.md): In diesem Thema werden die Schritte zum Herstellen einer Verbindung mit einem RMS-Server oder Azure RMS zum Testen der rechtlich geschützten Anwendung behandelt.
- [Exemplarische Vorgehensweise: Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md): Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)-Funktion verwenden.
- [Exemplarische Vorgehensweise: Verwenden der Verschlüsselung](working-with-encryption.md): Dieses Thema erläutert unsere Verschlüsselungspakete und zeigt einige Codeausschnitte für deren Verwendung.
- [Anwendungstypen](application-types.md): Dieses Thema behandelt die Typen von Anwendungen, die Sie als rechtlich geschützte Anwendung erstellen können.
- [Datei-API-Konfiguration](file-api-configuration.md): Das Datei-API-Verhalten kann durch Einstellungen in der Registrierung konfiguriert werden.
- [Unterstützte Dateiformate](supported-file-formats.md): Die Datei-API unterstützt native Formate und PFile-Formate.
- [Unterstützte Plattformen](supported-platforms.md): In diesem Thema werden die vom RMS SDK 2.1 unterstützten Client- und Serverplattformen identifiziert.
- [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md): Für alle RMS-fähigen Anwendungen müssen Nutzungseinschränkungen erzwungen werden.
- [Referenz für die Nutzungseinschränkung](usage-restriction-reference.md): Nutzungseinschränkungen werden durch die in diesem Thema aufgeführten Konstanten definiert.

 
## Verwandte Themen ##
* [Übersicht](ad-rms-overview.md)
 

 


<!--HONumber=Jun16_HO2-->


