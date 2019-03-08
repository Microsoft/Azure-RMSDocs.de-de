---
title: Erste Schritte | Azure RMS
description: Die RMS SDK 2.1-Plattform ermöglicht Entwicklern das Erstellen von Anwendungen, die den RMS-Datenschutz nutzen.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 728113C9-FCF9-4280-BE1D-6AF5C15E449E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 3ea3ff7e8099521123a9cc2e27ed349ee1c091b5
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331493"
---
# <a name="getting-started"></a>Erste Schritte

Die Rights Management Services SDK 2.1-Plattform ermöglicht Entwicklern das Erstellen von Anwendungen, die den RMS-Datenschutz über einen RMS-Server oder Azure RMS nutzen. Die Plattform handhabt komplexe Sicherheitsmethoden wie die Schlüsselverwaltung, Verschlüsselung und Entschlüsselung. Zudem bietet sie eine vereinfachte API, um die Anwendungsentwicklung zu erleichtern.

## <a name="get-started-with-rmssdk21"></a>Erste Schritte mit RMS SDK 2.1

In diesem Thema werden Sie durch die Einrichtung Ihrer rechtlich geschützten Anwendung und deren Ausführung in einer Testumgebung geführt. In den folgenden Themen wird beschrieben, wie Sie Ihre Entwicklungsumgebung einrichten. Die Informationen sind in der Reihenfolge angegeben, in der Sie die Aufgaben ggf. durchführen können.

## <a name="in-this-sections"></a>Abschnitte

| Thema | Beschreibung |
|-------|-------------|
| [Anmerkungen zu dieser Version](release-notes-rtm.md) | Dieses Thema enthält wichtige Informationen zu dieser und früheren Versionen von RMS SDK 2.1.|
| [Installieren des SDK](install-the-rms-sdk.md) | In diesem Thema werden Sie durch die Installation der Entwicklertools geführt.|
| [Konfigurieren von Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md) | Dieses Thema enthält Anleitungen zum Konfigurieren eines Visual Studio-Projekts für die Verwendung des RMS SDK 2.1.|
| [Entwickeln Ihrer Anwendung](developing-your-application.md) | Dieses Thema bietet grundlegende Anleitungen hinsichtlich der wichtigsten Aspekte einer RMS-fähigen Anwendung, und es kann als Grundlage für die Entwicklung eigener Anwendungen herangezogen werden.|
| [Testen der Anwendung](how-to-set-up-your-test-environment.md) |Dieses Thema enthält Anleitungen zum Einrichten von Anwendungstests.|
| [Bereitstellen in der Produktion](deploying-your-application.md) |Dieses Thema führt Sie durch die Bereitstellungsoptionen für die rechtlich geschützte Anwendung.|


Verwenden Sie RMS SDK 2.1 gemäß der Anleitung in den folgenden Themen:

- [Installieren des SDK](install-the-rms-sdk.md)
- [Konfigurieren von Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
- [Entwickeln Ihrer Anwendung](developing-your-application.md)
- [Testen der Anwendung](how-to-set-up-your-test-environment.md)
- [Bereitstellen in der Produktion](deploying-your-application.md)

### <a name="why-use-rmssdk21-for-protecting-your-content"></a>Gründe für die Verwendung von RMS SDK 2.1 zum Schutz von Inhalten

Für Entwickler, die ihren neuen und vorhandenen Clientanwendungen RMS-Unterstützung hinzufügen möchten, kann das RMS SDK 2.1 die folgenden Aufgaben erleichtern:

-   Verfassen verwaltbarer, kompatibler und stabiler RMS-fähigen Anwendung.
-   Dauerhaftes Verschlüsseln von Benutzerdaten. Die Daten bleiben verschlüsselt, unabhängig von der Umgebung, dem Gerät oder Betriebssystem.
-   Erzwingen eines umfangreichen Satzes von Nutzungsbeschränkungen, wie z. B. Verhindern von Bildschirmaufnahmen von sensiblen Daten.
-   Unterstützung von unternehmensweiten Schutzrichtlinien.
-   Unterstützung neuer Authentifizierungsmechanismen und Verschlüsselungsalgorithmen, sobald sie verfügbar sind.

Das RMS SDK 2.1 unterstützt verschiedene wichtige Client- und Serverplattformen. Weitere Informationen finden Sie unter [Unterstützte Plattformen](supported-platforms.md).

## <a name="core-principles"></a>Kernprinzipien

**Einfachheit** – Das Feedback und die Verwendungsmuster zum AD RMS SDK 1.0 wurden analysiert, und anhand dieser Daten wurden die schwierigsten Programmieraufgaben vereinfacht oder automatisiert. Unter Verwendung des RMS SDK 2.1 erstellte RMS-Anwendungen erfordern in der Regel 5 bis 10 Mal weniger RMS-Codezeilen als RMS-Anwendungen, die mit AD RMS SDK 1.0 geschrieben werden.
**Einmal schreiben** – RMS SDK 2.1-Anwendungen müssen nicht mit Codeänderungen aktualisiert oder neu kompiliert werden, um mit den neuesten RMS-Funktionen zu funktionieren. RMS-Funktionen werden in einer vorhandenen Anwendung verfügbar, wenn sie auf dem RMS-Server hinzugefügt werden.
**Konsistenz** – Das RMS SDK 2.1 erleichtert das Schreiben von Anwendungen, die verschiedene RMS-Konfigurationen auf konsistente Weise erfüllen. Bei Verwendung des SDK müssen Sie, der Anwendungsentwickler, auch einen deutlich geringeren Anteil der RMS-Benutzeroberfläche neu erstellen, sodass ein einheitliches Erscheinungsbild gefördert wird und eine geringere Notwendigkeit zur Schulung der Benutzer besteht.

## <a name="related-topics"></a>Verwandte Themen

* [RMS-Entwicklerhandbuch](developers-guide.md)
