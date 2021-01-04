---
title: Azure Information Protection klassischer Client Dateien und Verwendungs Protokollierung
description: Informationen zu den klassischen Client Dateien und Verwendungs Protokollierung für den Azure Information Protection klassischen Client für Windows.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 09/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ROBOTS: NOINDEX
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: d314c7554b993f328428962a9947b725365969e0
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97807381"
---
# <a name="admin-guide-azure-information-protection-classic-client-files-and-client-usage-logging"></a>Administrator Handbuch: Azure Information Protection klassischer Client Dateien und Client Verwendungs Protokollierung

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>***Relevant für:** [Klassischer Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Nachdem Sie den Azure Information Protection klassischen Client installiert haben, müssen Sie möglicherweise wissen, wo sich Dateien befinden, und überwachen, wie der Client verwendet wird.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Dateispeicherorte für den Azure Information Protection-Client

Clientdateien:    

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Clientprotokolldateien und aktuell installierte Richtliniendatei:

- Für 64-Bit- und 32-Bit-Betriebssysteme: **%localappdata%\Microsoft\MSIP**

## <a name="usage-logging-for-the-azure-information-protection-classic-client"></a>Verwendungs Protokollierung für den Azure Information Protection klassischen Client

Der Client protokolliert die Benutzeraktivität im lokalen Windows-Ereignisprotokoll **Anwendungs-und Dienst Protokolle**  >  **Azure Information Protection**. Die Ereignisse umfassen die folgenden Informationen:

- Clientversion, Richtlinien-ID

- IP-Adressen des angemeldeten Benutzers

- Dateiname und Speicherort

- Aktion:

    - Bezeichnung festlegen: Informations-ID 101
    
    - Bezeichnung festlegen (unten): Informations-ID 102
    
    - Bezeichnung festlegen (höher): Informations-ID 103
    
    - Bezeichnung entfernen: Informations-ID 104
    
    - Empfohlene QuickInfo für die Bezeichnung: Informationen 105
    
    - Benutzerdefinierten Schutz anwenden: Informations-ID 201
    
    - Benutzerdefinierten Schutz entfernen: Informations-ID 202
    
    - Outlook-Warnmeldung: Informations-ID 301
    
    - Outlook-rechtfertigen Nachricht: Informations-ID 302
    
    - Outlook-Block Meldung: Informations-ID 303
    
    - Anmelden (betriebsbereit): Informations-ID 902
    
    - Richtlinie herunterladen (betriebsbereit): Informations-ID 901
    
- Aktionsquelle:
    
    - Manuell 
    
    - Empfohlen
    
    - Automatic  
    
    - System (zum Anmelden und Herunterladen der Richtlinie)
    
    - Standard
    
- Bezeichnung vor und nach Aktion 
    
- Schutz vor und nach Aktion
    
- Benutzerausrichtung (falls zutreffend)

- Benutzerdefinierte Berechtigungen (falls zutreffend), die die [Nutzungsrechte über ihren Codierungsnamen](../configure-usage-rights.md#usage-rights-and-descriptions) für die angegebenen Benutzer, Gruppen der Organisationen einschließen.

Die Ereignisse für Outlook warnen, begründen und blockieren Nachrichten erfordern erweiterte Client Einstellungen. Weitere Informationen finden Sie unter [Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent).


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie alle Protokolldateien ermittelt haben, die dem Azure Information Protection-Client zugeordnet sind, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Dokumentkontrolle](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

