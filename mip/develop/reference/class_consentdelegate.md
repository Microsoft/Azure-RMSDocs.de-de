---
title: ConsentDelegate-Klasse
description: Referenz für die ConsentDelegate-Klasse
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 841049b1e6b369eb2f6a34d9701ed34eca028af6
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446361"
---
# <a name="class-consentdelegate"></a>ConsentDelegate-Klasse 
Delegat für Vorgänge, die eine Zustimmung erfordern.
Dieser Delegat wird von einer Clientanwendung implementiert, damit dem Benutzer zum richtigen Zeitpunkt eine Benachrichtigung mit einer Zustimmungsanforderung angezeigt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public Consent GetUserConsent(const std::string& url)  |  Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt anfordert.
  
## <a name="members"></a>Member
  
### <a name="consent"></a>Consent
Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt anfordert.

Parameter:  
* **url**: die URL, für die der SDK die Benutzerzustimmung benötigt



  
**Rückgabe**: eine Zustimmungsenumeration mit der Entscheidung des Benutzers
Wenn das SDK die Zustimmung des Benutzers mit dieser Methode anfordert, sollte die Clientanwendung dem Benutzer die URL anzeigen. Clientanwendungen sollten eine Möglichkeit bieten, die Zustimmung des Benutzers einzuholen und die entsprechende Zustimmungsenumeration zurückzugeben, die der Entscheidung des Benutzers entspricht.