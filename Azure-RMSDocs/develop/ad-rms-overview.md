---
title: Übersicht über das RMS SDK 2.1 | Azure RMS
description: Microsoft Rights Management Services (RMS) ist eine Datenschutztechnologie, die zum Schutz digitaler Informationen vor nicht autorisierter Verwendung beiträgt.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: B546B6C1-ADC1-4EBD-95E2-B4A74E4E980B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 5f6628c9a09b1b881c3e2c211d1c54e044b6d3b4
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60179881"
---
# <a name="overview"></a>Übersicht

Das Rights Management Services SDK 2.1 ist eine Datenschutztechnologie, die zum Schutz digitaler Informationen vor nicht autorisierter Verwendung beiträgt. Über Ihre rechtlich geschützte Anwendung können Inhaltsbesitzer definieren, wer ihren Inhalt öffnen, ändern, drucken, weiterleiten oder andere Aktionen damit ausführen kann.

AD RMS umfasst sowohl [Server](ad-rms-server.md)- als auch [Client](ad-rms-client.md)komponenten. Der Server, der unter Azure oder Windows Server ausgeführt wird, umfasst mehrere Webdienste.

Die [Clientkomponente](ad-rms-client.md) kann auf einem Client- oder Serverbetriebssystem ausgeführt werden und enthält Funktionen, mit denen eine Anwendung Inhalte verschlüsseln und entschlüsseln, Vorlagen und Sperrlisten abrufen, Lizenzen und Zertifikate von einem Server erwerben und andere Rights Management-Aufgaben ausführen kann.

Weitere Informationen finden Sie unter [Anwendungstypen](application-types.md).

Im Folgenden sind nur einige Szenarios aufgeführt, in denen mit dem Rights Management Services SDK 2.1 erstellte Anwendungen eingesetzt werden können.

-   Eine Anwaltskanzlei möchte verhindern, dass vertrauliche E-Mail-Nachrichten ausgedruckt oder weitergeleitet werden.
-   Die Entwickler von CAD/CAM-Software möchten den Zugriff auf eine kleine Gruppe von Benutzern in der Entwicklungsabteilung beschränken, ohne Kennwörter verwenden zu müssen.
-   Die Besitzer einer Grafikdesign-Website möchten eine Lizenz verwenden, die das kostenlose Anzeigen der Bilder in niedriger Auflösung zulässt, jedoch für den Zugriff auf die Versionen in hoher Auflösung eine Zahlung erfordert.
-   Der Besitzer einer Onlinedokumentbibliothek möchten die Rechte zum Anzeigen, Drucken oder Bearbeiten der Dokumente auf Grundlage der Identität des Benutzers aktivieren.
-   Ein Unternehmen möchte vertrauliche Informationen zu Mitarbeitern auf einer internen Website veröffentlichen, auf der die Anzeige- und Bearbeitungsrechte auf bestimmte Benutzer beschränkt sind.

Weitere Informationen zu AD RMS-Server, AD RMS-Client und deren Funktionalität finden Sie im TechNet in der [Dokumentation zu AD RMS für IT-Spezialisten](https://TechNet.Microsoft.Com/library/cc771234.aspx).

In den übrigen Themen in diesem Abschnitt werden die RMS-Architektur und ihre Implementierung behandelt.

## <a name="in-this-section"></a>Inhalt dieses Abschnitts

| Thema | Beschreibung |
|-------|-------------|
|[Client](ad-rms-client.md) |In diesem Thema werden der Zweck und die Funktion des Rights Management Service Client 2.1 beschrieben. |
|[Server](ad-rms-server.md) | In diesem Thema werden der Zweck und die Funktionen des RMS-Servers für Azure und Windows Server beschrieben.|


## <a name="related-topics"></a>Verwandte Themen

* [RMS-Konzepte](application-types.md)
* [Erste Schritte](getting-started-with-ad-rms-2-0.md)
* [Dokumentation zu AD RMS für IT-Spezialisten](https://technet.microsoft.com/library/cc771234.aspx)
