---
title: Azure Information Protection-Clientdateien und Verwendungsprotokollierung
description: Informationen zu den Clientdateien und zur Verwendungsprotokollierung für den Azure Information Protection-Client für Windows
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 56214db01a603cde5a09de99d49868bc353c4ce6
ms.sourcegitcommit: d0012de76c9156dd9239f7ba09c044a4b42ffc71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "75675719"
---
# <a name="admin-guide-azure-information-protection-client-files-and-client-usage-logging"></a>Administratorhandbuch: Azure Information Protection-Clientdateien und Clientverwendungsprotokollierung

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

> [!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection Client (klassisch)** und die Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021**eingestellt. Dieser Zeitrahmen ermöglicht es allen aktuellen Azure Information Protection Kunden, mithilfe der Microsoft Information Protection Unified-Beschriftungs Plattform zu unserer vereinheitlichten Bezeichnungs Lösung zu wechseln. Weitere Informationen finden Sie in der offiziellen [veralteten Notiz](https://aka.ms/aipclassicsunset).

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
    
    - Bezeichnung festlegen (unten): Informations-ID 101
    
    - Bezeichnung festlegen (höher): Informations-ID 101
    
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
    
    - Automatisch  
    
    - System (zum Anmelden und Herunterladen der Richtlinie)
    
    - Standardwert
    
- Bezeichnung vor und nach Aktion 
    
- Schutz vor und nach Aktion
    
- Benutzerausrichtung (falls zutreffend)

- Benutzerdefinierte Berechtigungen (falls zutreffend), die die [Nutzungsrechte über ihren Codierungsnamen](../configure-usage-rights.md#usage-rights-and-descriptions) für die angegebenen Benutzer, Gruppen der Organisationen einschließen.

Die Ereignisse für Outlook warnen, begründen und blockieren Nachrichten erfordern erweiterte Client Einstellungen. Weitere Informationen finden Sie unter [Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent).


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie alle Protokolldateien ermittelt haben, die dem Azure Information Protection-Client zugeordnet sind, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

