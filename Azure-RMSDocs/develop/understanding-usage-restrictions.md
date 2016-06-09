---
# required metadata

title: Grundlegendes zu Nutzungseinschränkungen | Azure RMS
description: Für alle RMS-fähigen Anwendungen müssen Nutzungseinschränkungen erzwungen werden.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Grundlegendes zu Nutzungseinschränkungen

Für alle RMS-fähigen Anwendungen müssen Nutzungseinschränkungen erzwungen werden. Eine Nutzungseinschränkung liegt vor, wenn ein Benutzer eine Aktion durchführen möchte (z.B. das Drucken eines Dokuments) und die RMS-Richtlinie für dieses Dokument keine Berechtigung bzw. kein Recht für die Durchführung der Aktion gewährt (z.B. das Recht DRUCKEN).

Die Berechtigungen eines Benutzers für ein Dokument können mit der [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck)-Funktion abgefragt werden.

## Grundlegendes zu Nutzungseinschränkungen

-   Kennenlernen der standardmäßigen RMS-Rechte

    Eine Übersicht über alle RMS-Rechte, die von der Anwendung erzwungen werden können, finden Sie unter [Referenz für die Nutzungseinschränkung](usage-restriction-reference.md).

    Beachten Sie hierbei, dass unter Umständen von der Anwendung definierte Rechte erstellt werden, die speziell für Ihre Situation gelten und über die standardmäßigen RMS-Rechte hinausreichen.

-   Identifizieren von Erzwingungspunkten für die Nutzungseinschränkung

    Ein *Erzwingungspunkt für die Nutzungseinschränkung* ist ein Punkt in der Ablaufsteuerung der Anwendung, an dem Sie eine Nutzungseinschränkung erzwingen müssen. Das Thema [Referenz für die Nutzungseinschränkung](usage-restriction-reference.md) enthält mehrere Beispiele für häufige Erzwingungspunkte.

    Bewerten Sie Ihre eigene Anwendung, um zu ermitteln, welche Erzwingungspunkte für die Nutzungseinschränkung gelten.

    In Ihrer Anwendung sind unter Umständen nicht alle Erzwingungspunkte erforderlich, die unter [Referenz für die Nutzungseinschränkung](usage-restriction-reference.md) beschrieben sind. Falls Ihre Anwendung für Benutzer beispielsweise das Drucken von Inhalten nicht zulässt, muss keine Prüfung auf das Recht **IPC\_GENERIC\_PRINT** durchgeführt werden.

-   Aktualisieren des Codes zum Durchführen einer Zugriffsüberprüfung an jedem Erzwingungspunkt

    Eine Anleitung, wie Sie bestimmte Rechte durchsetzen, finden Sie unter [Referenz für die Nutzungseinschränkung](usage-restriction-reference.md).

## Verwandte Themen

* [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck)
* [Referenz für die Nutzungseinschränkung](usage-restriction-reference.md)
 

 


<!--HONumber=Jun16_HO2-->


