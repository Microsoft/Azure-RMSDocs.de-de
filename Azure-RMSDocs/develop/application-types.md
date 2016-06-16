---
# required metadata

title: Anwendungstypen | Azure RMS
description: Dieses Thema behandelt die Typen von Anwendungen, die Sie als rechtlich geschützte Anwendung erstellen können.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Anwendungstypen


Dieses Thema behandelt die Typen von Anwendungen, die Sie als rechtlich geschützte Anwendung erstellen können.

Die folgenden Anwendungstypen werden derzeit von Rights Management Services SDK 2.1 unterstützt.

## Einfache Anwendungen

Bei einer einfachen Anwendung kann es sich um ein Befehlszeilenprogramm handeln, das zum Verschlüsseln einer gegebenen Datei erstellt wird. Ein Beispiel für eine einfache rechtlich geschützte Anwendung finden Sie unter [IPCHelloWorld – Beispielanwendung](how-to-build-your-first-application.md).

### Servermodusanwendungen

Der *Servermodus* ist für nicht interaktive Anwendungen vorgesehen, die RMS-geschützte Inhalte nutzen, schützen oder verarbeiten. Ein Beispiel wäre eine Anwendung zur *Verhinderung von Datenverlusten*, die als Dienst auf einem Dateiserver ausgeführt wird und automatisch vertrauliche Dokumente schützt. Ein Beispiel für diesen Anwendungstyp finden Sie unter [IpcDlp Beispiel](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d) .

Wenn Ihre Anwendung den *Servermodus* verwendet, sollte sie sich automatisch beim RMS-Server authentifizierten. Anders als beim *Clientmodus*, öffnet das RMS SDK 2.1 keine Anmeldeaufforderung, wenn die automatische Authentifizierung fehlschlägt. Zudem wird bei der Ausführung im *Servermodus* kein Anwendungsmanifest benötigt.

Weitere Informationen zum Festlegen des API-Sicherheitsmodus finden Sie unter [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md).

### Rich-Client-Anwendungen

Eine Rich-Client-Anwendung ermöglicht den Benutzern das Anzeigen und Bearbeiten von Daten über eine grafische Benutzeroberfläche (GUI). Häufig sind die in dieser GUI dargestellten Daten sehr wertvoll und vertraulich, sodass sie vor Diebstahl oder einer versehentlichen Offenlegung geschützt werden müssen. Die Datenschutzunterstützung verbessert in der Regel vorhandene Szenarien, ist jedoch nicht die primäre Motivation für die Entwicklung einer solchen Anwendung.

Der Einsatz von RMS SDK 2.1 für Rich-Client-Anwendungen erleichtert Folgendes:

-   Sicherstellen, dass diese Daten stets verschlüsselt sind.

-   Verhindern, dass Benutzer Daten in ein ungeschütztes Format extrahieren (z. B. das Kopieren und Einfügen über die Zwischenablage verhindern).

Microsoft Notepad ist eine einfache Rich-Client-Anwendung. Microsoft Office ist eine komplexere Rich-Client-Anwendung.

Weitere Informationen zum Schutz Ihrer Anwendung finden Sie unter [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md).

## Verwandte Themen

* [IpcDlp-Beispiel](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
* [IPCHelloWorld – Beispielanwendung](how-to-build-your-first-application.md)
* [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md)
* [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md)


<!--HONumber=Jun16_HO2-->

