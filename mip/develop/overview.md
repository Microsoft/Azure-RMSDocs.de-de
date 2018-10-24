---
title: 'Übersicht: Microsoft Information Protection SDK'
description: Microsoft Information Protection (MIP) stellt die Vereinheitlichung der Klassifizierungs-, Bezeichnungs- und Schutzdienste von Microsoft in eine einzelne Verwaltungsoberfläche und ein SDK (Software Development Kit) dar.
author: BryanLa
ms.service: information-protection
ms.topic: overview
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 775ae3d524947c8300de0e011b92c2cad106905a
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251725"
---
# <a name="overview"></a>Übersicht

## <a name="microsoft-information-protection"></a>Microsoft Information Protection

Microsoft Information Protection (MIP) stellt die Vereinheitlichung der Klassifizierungs-, Bezeichnungs- und Schutzdienste von Microsoft in eine einzelne Verwaltungsoberfläche und ein SDK (Software Development Kit) dar. Die vereinheitlichte Verwaltung wird über Office 365, Azure Information Protection, Windows Information Protection und andere Microsoft-Dienste hinweg bereitgestellt. Drittanbieter können das SDK für die Integration in Anwendungen mithilfe eines konsistenten Standardschemas für die Bezeichnung von Daten und eines Standardschutzdiensts verwenden.

* [Was ist Office 365 Security and Compliance Center?](https://docs.microsoft.com/office365/securitycompliance/)
* [Was ist Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
* [Wie funktioniert der Schutz in Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

## <a name="microsoft-information-protection-sdk"></a>Microsoft Information Protection SDK

Das MIP SDK stellt die Bezeichnungs- und Schutzdienste des Office 365 Security and Compliance Centers für Anwendungen und Dienste von Drittanbietern zur Verfügung. Entwickler können das SDK verwenden, um native Unterstützung für das Anwenden von Bezeichnungen und Schutz auf Dateien zu erstellen. Entwickler können darüber argumentieren, welche Maßnahmen ergriffen werden sollten, wenn bestimmte Bezeichnungen ermittelt werden. Außerdem können sie über MIP-verschlüsselte Informationen diskutieren. 

Die Bezeichnungen und der Schutz, die auf Informationen der Microsoft-Dienste angewendet werden, sind **konsistent**. Die Konsistenz ermöglicht Anwendungen und Diensten, die MIP unterstützen, Bezeichnungen auf eine allgemeine, vorhersehbare Weise zu lesen und zu schreiben.

Folgende gehören zu den allgemeinen Anwendungsfällen von MIP SDK:

* Eine Branchenanwendung, die Klassifizierungsbezeichnungen beim Exportieren auf Dateien anwendet.
* Eine CAD-/CAM-Entwurfsanwendung stellt native Unterstützung für Bezeichnungen von Microsoft Information Protection bereit.
* Ein Sicherheitsbroker für Cloudzugriff oder eine Lösung für das Verhindern von Datenverlust argumentiert über Daten hinweg, die mit Azure Information Protection verschlüsselt wurden.

Eine ausführlichere Liste finden Sie unter [API concepts (API-Konzepte)](concept-apis-use-cases.md).

## <a name="next-steps"></a>Nächste Schritte

Jetzt sind Sie bereit für Ihre ersten Schritte mit dem SDK. Zunächst müssen Sie die [Schritte zum Einrichten und Konfigurieren des MIP SDKs](setup-configure-mip.md) ausführen, um sicherzustellen, dass Ihr Office 365-Abonnement und Ihr Clientcomputer ordnungsgemäß eingerichtet sind.

