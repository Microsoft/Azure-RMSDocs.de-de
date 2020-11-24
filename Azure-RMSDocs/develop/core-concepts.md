---
title: Azure Information Protection SDK 4.2-Entwicklerhandbuch | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Microsoft Rights Management SDK 4,2 AD RMS aktivierte Anwendungen erstellen können, die Active Directory Rechte Verwaltungsdienste (AD RMS) nutzen.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 01/23/2017
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ae67523a-c094-44da-86b8-739bedba7111
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 957f347381b4de8abe4f828d4fd7903c0a0e62f3
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "95567496"
---
# <a name="rights-management-sdk42-developer-guidance"></a>Rights Management SDK 4,2 Entwickler Leit Faden

Ziel des Microsoft Rights Management SDK 4.2 ist es, die Erstellung von AD RMS-fähigen Anwendungen, für die Active Directory Rights Management Services (AD RMS) genutzt wird, so weit wie möglich zu vereinfachen.

Die folgenden Themen sollen Ihnen als Unterstützung für den Entwurfsprozess zur Entwicklung von RMS-fähigen Anwendungen dienen.

- [Vorgehensweise: Registrieren Ihrer App für Azure AD und Aktivieren der App für RMS](authentication-integration.md): Beschreibt die Grundlagen der Benutzerauthentifizierung für Ihre RMS-fähige Anwendung.
- [Vorgehensweise: Aktivieren der Fehler- und Leistungsprotokollierung](enabling-logging.md): Mit dem RMS SDK 4.2 wird das Hochladen von Diagnose- und Leistungsprotokollen über eine einzelne Geräteeigenschaft verwaltet.
- Gewusst [wie: Verwenden integrierter Rechte](built-in-rights-usage-restriction-reference.md) : erläutert die integrierten Rechte, die von der RMS SDK 4,2 bereitstellt werden, und die Nutzungseinschränkungen, die eine APP erzwingen sollte, um diese Einschränkungen zu berücksichtigen.
- [Vorgehensweise: Verwenden der Dokumentnachverfolgung](how-to-use-document-tracking.md): Zum Verwenden der Funktion für die Dokumentnachverfolgung sind einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung beim Dienst erforderlich.
