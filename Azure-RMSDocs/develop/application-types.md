---
title: Anwendungstypen | Azure RMS
description: Dieses Thema behandelt die Typen von Anwendungen, die Sie als rechtlich geschützte Anwendung erstellen können.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 0e67a086fb0fa3d1134a5f7768940b81c48947fd
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "95567517"
---
# <a name="application-types"></a>Anwendungstypen


Dieses Thema behandelt die Typen von Anwendungen, die Sie als rechtlich geschützte Anwendung erstellen können.

Die folgenden Anwendungstypen werden derzeit vom Rights Management Services SDK 2.1 unterstützt.

## <a name="simple-applications"></a>Einfache Anwendungen

Bei einer einfachen Anwendung kann es sich um ein Befehlszeilenprogramm handeln, das zum Verschlüsseln einer gegebenen Datei erstellt wird. Ein Beispiel für eine einfache, rechtlich geschützte Anwendung finden Sie in unserer Implementierung von *IPCHelloWorld* unter [Entwickeln Ihrer Anwendung](developing-your-application.md).

### <a name="server-mode-applications"></a>Servermodusanwendungen

Der *Servermodus* ist für nicht interaktive Anwendungen vorgesehen, die RMS-geschützte Inhalte nutzen, schützen oder verarbeiten. Ein Beispiel wäre eine Anwendung zur *Verhinderung von Datenverlusten*, die als Dienst auf einem Dateiserver ausgeführt wird und automatisch vertrauliche Dokumente schützt. Ein Beispiel für diesen Anwendungstyp finden Sie unter [IpcDlp Beispiel](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcDlpApp) .

Wenn Ihre Anwendung den *Servermodus* verwendet, sollte sie sich automatisch beim RMS-Server authentifizierten. Anders als beim *Clientmodus*, öffnet das RMS SDK 2.1 keine Anmeldeaufforderung, wenn die automatische Authentifizierung fehlschlägt. Zudem wird bei der Ausführung im *Servermodus* kein Anwendungsmanifest benötigt.

Weitere Informationen zum Festlegen des API-Sicherheitsmodus finden Sie unter [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md).

### <a name="rich-client-applications"></a>Rich-Client-Anwendungen

Eine Rich-Client-Anwendung ermöglicht den Benutzern das Anzeigen und Bearbeiten von Daten über eine grafische Benutzeroberfläche (GUI). Häufig sind die in dieser GUI dargestellten Daten sehr wertvoll und vertraulich, sodass sie vor Diebstahl oder einer versehentlichen Offenlegung geschützt werden müssen. Die Datenschutzunterstützung verbessert in der Regel vorhandene Szenarien, ist jedoch nicht die primäre Motivation für die Entwicklung einer solchen Anwendung.

Der Einsatz des RMS SDK 2.1 für Rich-Client-Anwendungen erleichtert Folgendes:

-   Sicherstellen, dass diese Daten stets verschlüsselt sind.

-   Verhindern, dass Benutzer Daten in ein ungeschütztes Format extrahieren (z. B. das Kopieren und Einfügen über die Zwischenablage verhindern).

Microsoft Notepad ist eine einfache Rich-Client-Anwendung. Microsoft Office ist eine komplexere Rich-Client-Anwendung.

Weitere Informationen zum Schutz Ihrer Anwendung finden Sie unter [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md).

## <a name="related-topics"></a>Verwandte Themen

- [IpcDlp-Beispiel](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
- [Entwickeln Ihrer Anwendung](developing-your-application.md)
- [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md)
- [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md)
