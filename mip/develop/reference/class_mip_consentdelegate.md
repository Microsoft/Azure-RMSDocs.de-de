---
title: Klasse mip::ConsentDelegate
description: Dokumentiert die mip::consentdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 69ffbe72ac9d8241115fecd5bbae28052fb93e33
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333227"
---
# <a name="class-mipconsentdelegate"></a>Klasse mip::ConsentDelegate 
Delegat für Vorgänge, die eine Zustimmung erfordern
Dieser Delegat wird von einer Clientanwendung implementiert, damit dem Benutzer zum richtigen Zeitpunkt eine Benachrichtigung mit einer Zustimmungsanforderung angezeigt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Consent GetUserConsent(const std::string& url)  |  Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt anfordert.
  
## <a name="members"></a>Member
  
### <a name="getuserconsent-function"></a>GetUserConsent-Funktion
Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt anfordert.

Parameter:  
* **url**: Die URL für die das SDK die benutzerzustimmung erfordert



  
**Gibt**: Eine Enumeration der Zustimmung mit Entscheidung des Benutzers.
Wenn das SDK die Zustimmung des Benutzers mit dieser Methode anfordert, sollte die Clientanwendung dem Benutzer die URL anzeigen. Clientanwendungen sollten eine Möglichkeit bieten, die Zustimmung des Benutzers einzuholen und die entsprechende Zustimmungsenumeration zurückzugeben, die der Entscheidung des Benutzers entspricht.
