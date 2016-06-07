---
# required metadata

title: Hinweise für Entwickler | Azure RMS
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
** Dieser SDK-Inhalt ist nicht aktuell. Für kurze Zeit finden Sie die [aktuelle Version](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) der Dokumentation auf MSDN. **
# Hinweise für Entwickler

Dieser Abschnitt enthält spezifische Leitfäden für mehrere wichtige Entwicklungsszenarien. Die Szenarien in diesem Abschnitt gelten speziell für diese Version des Rights Management Services SDK 2.1 und können sich in nachfolgenden Versionen ändern.

- [Hinzufügen expliziter Besitzerrechte](add-explicit-owner-rights.md): In Ihrer Anwendung sollten explizit Rechte vom Typ &quot;Besitzer&quot; hinzugefügt werden, wenn eine Lizenz von Grund auf neu erstellt wird ([IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)).
- [Häufige Fehlerbedingungen und Lösungen](common-error-conditions-and-solutions.md): Dieses Thema umfasst die häufigsten Fehlermeldungen, die auftreten können, wenn Sie die RMS SDK 2.1-Entwicklertools verwenden.
- [Aktivieren von E-Mail-Benachrichtigungen](how-to-enable-email-notification.md): Mit E-Mail-Benachrichtigungen können Besitzer von geschützten Inhalten benachrichtigt werden, wenn auf ihre Inhalte zugegriffen wird.
- [Datei-API-Konfiguration](file-api-configuration.md): Das Datei-API-Verhalten kann durch Einstellungen in der Registrierung konfiguriert werden.
- [IIPCHelloWorld – Beispielanwendung](how-to-build-your-first-application.md): Dieses Thema enthält eine Anleitung zum Erstellen einer rechtlich geschützten Beispielanwendung.
- [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md): Sie können wählen, in welchem Sicherheitsmodus Ihre Datei-API-Anwendung ausgeführt wird, indem Sie die [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)-Funktion verwenden.
- [Unterstützte Dateiformate](supported-file-formats.md): Die Datei-API unterstützt native Formate und PFile-Formate.
- [Nachverfolgung von Inhalten](tracking-content.md): Dieses Thema enthält grundlegende Leitfäden zum Implementieren der Dokumentnachverfolgung von Inhalten, die durch das RMS SDK 2.1 geschützt sind.
- [Verwenden der Verschlüsselung](working-with-encryption.md): Dieses Thema erläutert unsere Verschlüsselungspakete und zeigt einige Codeausschnitte für deren Verwendung.

 

## Verwandte Themen ##
* [Übersicht](ad-rms-overview.md)
* [Vorgehensweise](how-to-use-msipc.md)
 

 


<!--HONumber=Jun16_HO1-->


