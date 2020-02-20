---
title: 'MIP:: einvernehmdelegat-Klasse'
description: 'Dokumentiert die MIP:: genehmidelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: bbeca67a1ffcd5a7b159883c97a2eb3a08bfb3e2
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77490318"
---
# <a name="class-mipconsentdelegate"></a>MIP:: einvernehmdelegat-Klasse 
Delegat für Vorgänge, die eine Zustimmung erfordern.
Dieser Delegat wird von einer Clientanwendung implementiert, damit dem Benutzer zum richtigen Zeitpunkt eine Benachrichtigung mit einer Zustimmungsanforderung angezeigt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Consent GetUserConsent(const std::string& url)  |  Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt erfordert.
  
## <a name="members"></a>Member
  
### <a name="getuserconsent-function"></a>Getuserconsent-Funktion
Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt erfordert.

Parameter:  
* **url**: die URL, für die der SDK die Benutzerzustimmung benötigt



  
**Rückgabe**: eine Zustimmungsenumeration mit der Entscheidung des Benutzers
Wenn das SDK die Zustimmung des Benutzers mit dieser Methode anfordert, sollte die Clientanwendung dem Benutzer die URL anzeigen. Clientanwendungen sollten eine Möglichkeit bieten, die Zustimmung des Benutzers einzuholen und die entsprechende Zustimmungsenumeration zurückzugeben, die der Entscheidung des Benutzers entspricht.