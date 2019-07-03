---
title: Azure Information Protection-Clientdateien und Verwendungsprotokollierung
description: Informationen zu den Clientdateien und zur Verwendungsprotokollierung für den Azure Information Protection-Client für Windows
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b6391df8ae2e31303f5b369963389abe3005a1bd
ms.sourcegitcommit: a5f595f8a453f220756fdc11fd5d466c71d51963
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67521649"
---
# <a name="admin-guide-azure-information-protection-client-files-and-client-usage-logging"></a>Administratorhandbuch: Azure Information Protection-Clientdateien und Clientverwendungsprotokollierung

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Nachdem Sie den Azure Information Protection-Client installiert haben, müssen Sie möglicherweise wissen, wo die Dateien gespeichert sind und zudem überwachen, wie der Client verwendet wird.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Dateispeicherorte für den Azure Information Protection-Client

Clientdateien:   

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Clientprotokolldateien und aktuell installierte Richtliniendatei:

- Für 64-Bit- und 32-Bit-Betriebssysteme: **%localappdata%\Microsoft\MSIP**

## <a name="usage-logging-for-the-azure-information-protection-client"></a>Verwendungsprotokollierung für den Azure Information Protection-Client

Der Client protokolliert die Benutzeraktivität im lokalen Windows-Ereignisprotokoll **Anwendungen und Dienste** > **Azure Information Protection**. Die Ereignisse umfassen die folgenden Informationen:

- Clientversion, Richtlinien-ID

- IP-Adressen des angemeldeten Benutzers

- Dateiname und Speicherort

- Aktion:

    - Bezeichnung festlegen: Informations-ID 101
    
    - Bezeichnung festlegen (niedriger): Informations-ID 101
    
    - Bezeichnung festlegen (höher): Informations-ID 101
    
    - Bezeichnung entfernen: Informations-ID 104
    
    - Empfohlene Bezeichnungs-QuickInfo: Information 105
    
    - Benutzerdefinierten Schutz anwenden: Informations-ID 201
    
    - Benutzerdefinierten Schutz entfernen: Informations-ID 202
    
    - Outlook-Warnmeldung: Informations-ID 301
    
    - Outlook-Legitimationsmeldung: Informations-ID 302
    
    - Outlook-Blockiermeldung: Informations-ID 303
    
    - Anmelden (betriebsbereit): Informations-ID 902
    
    - Richtlinie herunterladen (betriebsbereit): Informations-ID 901
    
- Aktionsquelle:
    
    - Manuell 
    
    - Empfohlen
    
    - Automatisch  
    
    - System (zum Anmelden und Herunterladen der Richtlinie)
    
    - Default
    
- Bezeichnung vor und nach Aktion 
    
- Schutz vor und nach Aktion
    
- Benutzerausrichtung (falls zutreffend)

- Benutzerdefinierte Berechtigungen (falls zutreffend), die die [Nutzungsrechte über ihren Codierungsnamen](../configure-usage-rights.md#usage-rights-and-descriptions) für die angegebenen Benutzer, Gruppen der Organisationen einschließen.

Warnen, begründen und blockiert die Ereignisse für Outlook Nachrichten müssen Sie den aktuellen Client für die allgemeine Verfügbarkeit und erweiterte Clienteinstellungen. Weitere Informationen finden Sie unter [Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent).

Weitere Informationen zur verwendungsprotokollierung für den Schutzdienst finden Sie unter [protokollieren und analysieren die Verwendung der Schutz von Azure Information Protection](../log-analyze-usage.md)

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie alle Protokolldateien ermittelt haben, die dem Azure Information Protection-Client zugeordnet sind, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

