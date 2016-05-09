---
# required metadata

title: Vorteile dieses SDKs | Azure RMS
description: Dieses Thema beschreibt, warum RMS SDK 2.1 eine bedeutende Verbesserung gegenüber des ursprünglichen Active Directory Rights Management Services-SDKs ist.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ee4989d6-3903-4ed2-ac62-d5692e2ef494

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# Vorteile dieses SDKs
Dieses Thema beschreibt, warum Rights Management Services SDK 2.1 eine deutliche Verbesserung gegenüber des ursprünglichen [Active Directory Rights Management Services-SDKs](https://msdn.microsoft.com/library/Cc530379) in Bezug auf erforderlichen Entwicklungsaufwand zum Erstellen einer Rechte-fähigen Anwendung ist.

**API-Oberfläche** – Die API-Oberfläche wurde erheblich durch Abstraktion reduziert, sodass Sie von vielen Details der Back-End-Implementierung befreit sind. Von einer API-Oberfläche mit 84 Funktionen für RMS SDK enthält das RMS-SDK 2.1 nur 20 API-Funktionen. Die meisten Anwendungen müssen nur einen kleinen Teil dieser API-Oberfläche verwenden.

**Vorbereitungszeit** – Mit dem RMS-SDK 2.1 können Sie eine schrittweise Anleitung ausführen, um zu ermitteln, welche Ressourcen der Anwendung vertraulich sind und wie Sie sie schützen können. Das ist anders als beim RMS-SDK, bei dem Sie umfassende Kenntnisse der Zertifikate, Formate und Topologien benötigten und komplexen Code für Multithreading schreiben mussten.

**Unterstützung mehrerer Topologien** – Mit dem RMS-SDK 2.1 können Sie die wiederholte Codeerstellung minimieren. Ihre Anwendung sollte mit allen Topologien funktionieren, da wir die Topologiekomplexität abseits des Entwicklers abstrahieren. Mit dem RMS-SDK mussten Sie alle unterstützten Topologien verstehen und dann speziellen Code für jede schreiben und testen.

**Zukunftssicher** – Das RMS-SDK 2.1 hilft dabei, die wiederholte Erstellung des Rechte-fähigen Codes zu minimieren. Ihre Anwendung sollte in jeder RMS-Umgebung funktionieren und automatisch neue Funktionen nutzen, wenn aktualisierte Kernfunktionen veröffentlicht werden. Das ist anders als beim AD RMS-SDK, bei dem Sie die Anwendung aktualisieren mussten, um explizit alle neuen Features zu nutzen.

**Wichtiger Hinweis**  
Alle Themen in der ursprünglichen [Active Directory Rights Management Services-SDK](https://msdn.microsoft.com/library/Cc530379) in der MSDN Library beginnen nun mit der folgenden Unterstützungsaussage:

Das AD RMS-SDK, das Funktionen nutzt, die vom Client in „Msdrm.dll“ bereitgestellt werden, kann in Windows Server 2008, Windows Vista, Windows Server 2008 R2, Windows 7, Windows Server 2012 und Windows 8 verwendet werden. Es kann in nachfolgenden Versionen geändert oder entfernt werden. Verwenden Sie stattdessen das [Active Directory Rights Management Services SDK 2.1](microsoft-information-protection-and-control-client-portal.md), das Funktionen nutzt, die vom Client in *Msipc.dll* bereitgestellt werden.

 

## Verwandte Themen ##
* [Übersicht](ad-rms-overview.md)
* [Active Directory Rights Management Services-SDK](https://msdn.microsoft.com/library/Cc530379)
* [Rights Management Services SDK 2.1](microsoft-information-protection-and-control-client-portal.md)
 

 


<!--HONumber=Apr16_HO3-->


