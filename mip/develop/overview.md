---
title: 'Übersicht: Microsoft Information Protection SDK'
description: Microsoft Information Protection (MIP) stellt die Vereinheitlichung der Klassifizierungs-, Bezeichnungs- und Schutzdienste von Microsoft in eine einzelne Verwaltungsoberfläche und ein SDK (Software Development Kit) dar.
author: BryanLa
ms.service: information-protection
ms.topic: overview
ms.date: 01/18/2019
ms.author: bryanla
ms.openlocfilehash: 77d8fb8d32c0f75be49b29e95316f8da873d14c6
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651138"
---
# <a name="overview"></a>Übersicht

## <a name="microsoft-information-protection"></a>Microsoft Information Protection

Microsoft Information Protection (MIP) ist die Zusammenführung von Microsoft Klassifizierung, Bezeichnung und Datenschutzdienste genutzt:

- Die vereinheitlichte Verwaltung wird über Office 365, Azure Information Protection, Windows Information Protection und andere Microsoft-Dienste hinweg bereitgestellt. 
- Drittanbieter können das MIP SDK für die Integration von Anwendungen mithilfe einer einheitlichen Bezeichnung Schema und Protection-Dienst verwenden.

* [Was ist Office 365 Security and Compliance Center?](https://docs.microsoft.com/office365/securitycompliance/)
* [Was ist Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
* [Wie funktioniert der Schutz in Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

## <a name="microsoft-information-protection-sdk"></a>Microsoft Information Protection SDK

Das MIP SDK macht die Dienste Bezeichnung und Schutz von Office 365 Security & Compliance Center auf Drittanbieter-Anwendungen und Dienste verfügbar. Entwickler können das SDK verwenden, um native Unterstützung für das Anwenden von Bezeichnungen und Schutz auf Dateien zu erstellen. Entwickler können darüber argumentieren, welche Maßnahmen ergriffen werden sollten, wenn bestimmte Bezeichnungen ermittelt werden. Außerdem können sie über MIP-verschlüsselte Informationen diskutieren. 

Die Bezeichnungen und der Schutz, die auf Informationen der Microsoft-Dienste angewendet werden, sind **konsistent**. Die Konsistenz ermöglicht Anwendungen und Diensten, die MIP unterstützen, Bezeichnungen auf eine allgemeine, vorhersehbare Weise zu lesen und zu schreiben.

Folgende gehören zu den allgemeinen Anwendungsfällen von MIP SDK:

* Eine Branchenanwendung, die Klassifizierungsbezeichnungen beim Exportieren auf Dateien anwendet.
* Eine CAD-/CAM-Entwurfsanwendung stellt native Unterstützung für Bezeichnungen von Microsoft Information Protection bereit.
* Ein Sicherheitsbroker für Cloudzugriff oder eine Lösung für das Verhindern von Datenverlust argumentiert über Daten hinweg, die mit Azure Information Protection verschlüsselt wurden.

Eine ausführlichere Liste finden Sie unter [API concepts (API-Konzepte)](concept-apis-use-cases.md).

## <a name="next-steps"></a>Nächste Schritte

Jetzt sind Sie bereit für Ihre ersten Schritte mit dem SDK. Im ersten Schritt müssen Sie tun [führen Sie die MIP SDK-Setup und Konfiguration Schritte](setup-configure-mip.md). Diese Schritte werden Stellen Sie Ihr Office 365-Abonnement, und Clientcomputer ordnungsgemäß eingerichtet wurden.

