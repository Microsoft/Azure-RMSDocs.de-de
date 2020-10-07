---
title: 'Übersicht: Microsoft Information Protection SDK'
description: Microsoft Information Protection (MIP) stellt die Vereinheitlichung der Klassifizierungs-, Bezeichnungs- und Schutzdienste von Microsoft in eine einzelne Verwaltungsoberfläche und ein SDK (Software Development Kit) dar.
author: msmbaldwin
ms.service: information-protection
ms.topic: overview
ms.date: 01/18/2019
ms.author: mbaldwin
ms.openlocfilehash: 32f2895d8b52a5fd63d5c764eebb78736b1917a9
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91588324"
---
# <a name="overview"></a>Übersicht

## <a name="microsoft-information-protection"></a>Microsoft Information Protection

Microsoft Information Protection (MSIP) stellt die Vereinheitlichung der Klassifizierungs-, Bezeichnungs- und Schutzdienste von Microsoft dar:

- Die vereinheitlichte Verwaltung wird in Microsoft 365, Azure Information Protection, Windows Information Protection und anderen Microsoft-Diensten bereitgestellt. 
- Drittanbieter können das MSIP SDK für die Integration in Anwendungen mithilfe eines konsistenten Standardschemas für die Bezeichnung von Daten und eines Schutzdiensts verwenden.

* [Was ist Office 365 Security and Compliance Center?](/office365/securitycompliance/)
* [Was ist Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
* [Wie funktioniert der Schutz in Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

## <a name="microsoft-information-protection-sdk"></a>Microsoft Information Protection SDK

Das MSIP SDK stellt die Bezeichnungs- und Schutzdienste des Office 365 Security & Compliance Center für Anwendungen und Dienste von Drittanbietern zur Verfügung. Entwickler können das SDK verwenden, um native Unterstützung für das Anwenden von Bezeichnungen und Schutz auf Dateien zu erstellen. Entwickler können darüber argumentieren, welche Maßnahmen ergriffen werden sollten, wenn bestimmte Bezeichnungen ermittelt werden. Außerdem können sie über MIP-verschlüsselte Informationen diskutieren. 

Die Bezeichnungen und der Schutz, die auf Informationen der Microsoft-Dienste angewendet werden, sind **konsistent**. Die Konsistenz ermöglicht Anwendungen und Diensten, die MIP unterstützen, Bezeichnungen auf eine allgemeine, vorhersehbare Weise zu lesen und zu schreiben.

Folgende gehören zu den allgemeinen Anwendungsfällen von MIP SDK:

* Eine Branchenanwendung, die Klassifizierungsbezeichnungen beim Exportieren auf Dateien anwendet.
* Eine CAD-/CAM-Entwurfsanwendung stellt native Unterstützung für Bezeichnungen von Microsoft Information Protection bereit.
* Ein Sicherheitsbroker für Cloudzugriff oder eine Lösung für das Verhindern von Datenverlust argumentiert über Daten hinweg, die mit Azure Information Protection verschlüsselt wurden.

Eine ausführlichere Liste finden Sie unter [API concepts (API-Konzepte)](concept-apis-use-cases.md).

Das MIP SDK wird auf den folgenden Plattformen unterstützt:

[!INCLUDE [MIP SDK platform support](../includes/mip-sdk-platform-support.md)]

## <a name="next-steps"></a>Nächste Schritte

Jetzt sind Sie bereit für Ihre ersten Schritte mit dem SDK. Zunächst müssen Sie das [Setup des MSIP SDK und die Konfigurationsschritte durchführen](setup-configure-mip.md). Durch diese Schritte wird sichergestellt, dass Ihr Microsoft 365-Abonnement und der Clientcomputer ordnungsgemäß eingerichtet werden.