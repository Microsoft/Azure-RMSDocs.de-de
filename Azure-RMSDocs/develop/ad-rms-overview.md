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
ms.custom: dev
ms.openlocfilehash: 001cace1cdc3a9fd3e5cc1dd1a06a77215bd438c
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95567979"
---
# <a name="overview-of-rights-management-services-sdk-21"></a>Übersicht über Rights Management Services SDK 2,1

Das Rights Management Services SDK 2.1 ist eine Datenschutztechnologie, die zum Schutz digitaler Informationen vor nicht autorisierter Verwendung beiträgt. Über Ihre rechtlich geschützte Anwendung können Inhaltsbesitzer definieren, wer ihren Inhalt öffnen, ändern, drucken, weiterleiten oder andere Aktionen damit ausführen kann.

AD RMS umfasst sowohl [Server](ad-rms-server.md)- als auch [Client](ad-rms-client.md)komponenten. Der Server, der unter Azure oder Windows Server ausgeführt wird, umfasst mehrere Webdienste.

Die [Client](ad-rms-client.md) Komponente kann entweder auf einem Client-oder Server Betriebssystem ausgeführt werden und enthält Funktionen, mit denen eine Anwendung Inhalte verschlüsseln und entschlüsseln, Vorlagen und Sperr Listen abrufen, Lizenzen und Zertifikate von einem Server erwerben und andere Rechte Verwaltungsaufgaben ausführen kann.

Weitere Informationen finden Sie unter [Anwendungs Typen](application-types.md).

Im Folgenden sind nur einige Szenarios aufgeführt, in denen mit dem Rights Management Services SDK 2.1 erstellte Anwendungen eingesetzt werden können.

-   Eine Anwaltskanzlei möchte verhindern, dass vertrauliche E-Mail-Nachrichten ausgedruckt oder weitergeleitet werden.
-   Die Entwickler von CAD/CAM-Software möchten den Zugriff auf eine kleine Gruppe von Benutzern in der Entwicklungsabteilung beschränken, ohne Kennwörter verwenden zu müssen.
-   Die Besitzer einer Grafikdesign-Website möchten eine Lizenz verwenden, die das kostenlose Anzeigen der Bilder in niedriger Auflösung zulässt, jedoch für den Zugriff auf die Versionen in hoher Auflösung eine Zahlung erfordert.
-   Der Besitzer einer Onlinedokumentbibliothek möchten die Rechte zum Anzeigen, Drucken oder Bearbeiten der Dokumente auf Grundlage der Identität des Benutzers aktivieren.
-   Ein Unternehmen möchte vertrauliche Informationen zu Mitarbeitern auf einer internen Website veröffentlichen, auf der die Anzeige- und Bearbeitungsrechte auf bestimmte Benutzer beschränkt sind.

Weitere Informationen zu AD RMS-Server, AD RMS-Client und deren Funktionalität finden Sie im TechNet in der [Dokumentation zu AD RMS für IT-Spezialisten](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771234(v=ws.10)).

In den übrigen Themen in diesem Abschnitt werden die RMS-Architektur und ihre Implementierung behandelt.

## <a name="in-this-section"></a>In diesem Abschnitt

| Thema | BESCHREIBUNG |
|-------|-------------|
|[Client](ad-rms-client.md) |In diesem Thema werden der Zweck und die Funktion des Rights Management Service Client 2.1 beschrieben. |
|[Server](ad-rms-server.md) | In diesem Thema werden der Zweck und die Funktionen des RMS-Servers für Azure und Windows Server beschrieben.|


## <a name="related-topics"></a>Verwandte Themen

* [RMS-Konzepte](application-types.md)
* [Erste Schritte](getting-started-with-ad-rms-2-0.md)
* [Dokumentation zu AD RMS für IT-Spezialisten](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771234(v=ws.10))