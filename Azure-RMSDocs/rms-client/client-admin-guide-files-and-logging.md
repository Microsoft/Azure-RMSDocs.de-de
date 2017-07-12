---
title: Azure Information Protection-Clientdateien und Verwendungsprotokollierung
description: "Informationen zu den Clientdateien und zur Verwendungsprotokollierung für den Azure Information Protection-Client für Windows"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: bf695772d545daca602903e156903da2aadaae7a
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="azure-information-protection-client-files-and-client-usage-logging" class="xliff"></a>

# Azure Information Protection-Clientdateien und Clientverwendungsprotokollierung

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Nachdem Sie den Azure Information Protection-Client installiert haben, müssen Sie möglicherweise wissen, wo die Dateien gespeichert sind und zudem überwachen, wie der Client verwendet wird.

<a id="file-locations-for-the-azure-information-protection-client" class="xliff"></a>

## Dateispeicherorte für den Azure Information Protection-Client

Clientdateien:   

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Clientprotokolldateien und aktuell installierte Richtliniendatei:

- Für 64-Bit- und 32-Bit-Betriebssysteme: **%localappdata%\Microsoft\MSIP**

<a id="usage-logging-for-the-azure-information-protection-client" class="xliff"></a>

## Verwendungsprotokollierung für den Azure Information Protection-Client

Der Client protokolliert die Benutzeraktivität im lokalen Windows-**Anwendungen und Dienste**-Ereignisprotokoll, **Azure Information Protection**. Die Ereignisse umfassen die folgenden Informationen:

- Datum, Clientversion, Richtlinien-ID

- Angemeldeter Benutzername, Computername

- Dateiname und Speicherort

- Aktion:

    - Bezeichnung festlegen: Informationen ID 101
    
    - Bezeichnung festlegen (niedriger): Informations-ID 102
    
    - Bezeichnung festlegen (höher): Informations-ID 103
    
    - Bezeichnung entfernen: Informations-ID 104
   
    - Empfohlener Tipp: Information 105
    
    - Benutzerdefinierten Schutz anwenden: Informations-ID 201
    
    - Benutzerdefinierten Schutz entfernen: Informations-ID 202
    
    - Anmelden (betriebsbereit): Informations-ID 902
    
    - Richtlinie herunterladen (betriebsbereit): Informations-ID 901
    
- Aktionsquelle:
    
    - Manuell 
    
    - Empfohlen
    
    - Automatisch  
    
    - System (zum Anmelden und Herunterladen der Richtlinie)
    
- Bezeichnung vor und nach Aktion 
    
- Schutz vor und nach Aktion
    
- Benutzerausrichtung (falls zutreffend)
    

Informationen zur Verwendungsprotokollierung für den Azure Rights Management-Dienst finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).



<a id="next-steps" class="xliff"></a>

## Nächste Schritte
Nachdem Sie alle Protokolldateien ermittelt haben, die dem Azure Information Protection-Client zugeordnet sind, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
