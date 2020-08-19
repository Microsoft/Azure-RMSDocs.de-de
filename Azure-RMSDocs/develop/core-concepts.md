---
title: Azure Information Protection SDK 4.2-Entwicklerhandbuch | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Microsoft Rights Management SDK 4,2 AD RMS aktivierte Anwendungen erstellen können, die Active Directory Rechte Verwaltungsdienste (AD RMS) nutzen.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 01/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ae67523a-c094-44da-86b8-739bedba7111
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 4b0ac76c42202286540ee8a469cc7066a70e9973
ms.sourcegitcommit: dc50f9a6c2f66544893278a7fd16dff38eef88c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88564345"
---
# <a name="rights-management-sdk42-developer-guidance"></a>Rights Management SDK 4,2 Entwickler Leit Faden

Ziel des Microsoft Rights Management SDK 4.2 ist es, die Erstellung von AD RMS-fähigen Anwendungen, für die Active Directory Rights Management Services (AD RMS) genutzt wird, so weit wie möglich zu vereinfachen.

Die folgenden Themen sollen Ihnen als Unterstützung für den Entwurfsprozess zur Entwicklung von RMS-fähigen Anwendungen dienen.

- [Vorgehensweise: Registrieren Ihrer App für Azure AD und Aktivieren der App für RMS](authentication-integration.md): Beschreibt die Grundlagen der Benutzerauthentifizierung für Ihre RMS-fähige Anwendung.
- [Vorgehensweise: Aktivieren der Fehler- und Leistungsprotokollierung](enabling-logging.md): Mit dem RMS SDK 4.2 wird das Hochladen von Diagnose- und Leistungsprotokollen über eine einzelne Geräteeigenschaft verwaltet.
- Gewusst [wie: Verwenden integrierter Rechte](built-in-rights-usage-restriction-reference.md) : erläutert die integrierten Rechte, die von der RMS SDK 4,2 bereitstellt werden, und die Nutzungseinschränkungen, die eine APP erzwingen sollte, um diese Einschränkungen zu berücksichtigen.
- [Vorgehensweise: Verwenden der Dokumentnachverfolgung](how-to-use-document-tracking.md): Zum Verwenden der Funktion für die Dokumentnachverfolgung sind einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung beim Dienst erforderlich.
