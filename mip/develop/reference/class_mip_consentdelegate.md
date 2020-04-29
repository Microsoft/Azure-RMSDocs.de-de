---
title: ConsentDelegate-Klasse
description: 'Dokumentiert die "genehmidelegat:: nicht definierte"-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: d6c4efddf5b70c1a4a97f0b036cffa107a6cac3e
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763435"
---
# <a name="class-consentdelegate"></a>ConsentDelegate-Klasse 
Delegat für Vorgänge, die eine Zustimmung erfordern
Dieser Delegat wird von einer Clientanwendung implementiert, damit dem Benutzer zum richtigen Zeitpunkt eine Benachrichtigung mit einer Zustimmungsanforderung angezeigt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Consent GetUserConsent(const std::string& url)  |  Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt anfordert.
  
## <a name="members"></a>Member
  
### <a name="getuserconsent-function"></a>Getuserconsent-Funktion
Wird aufgerufen, wenn das SDK die Benutzerzustimmung für die Verbindung mit einem Dienstendpunkt anfordert.

Parameter:  
* **url**: die URL, für die der SDK die Benutzerzustimmung benötigt



  
**Rückgabe**: eine Zustimmungsenumeration mit der Entscheidung des Benutzers
Wenn das SDK die Zustimmung des Benutzers mit dieser Methode anfordert, sollte die Clientanwendung dem Benutzer die URL anzeigen. Clientanwendungen sollten eine Möglichkeit bieten, die Zustimmung des Benutzers einzuholen und die entsprechende Zustimmungsenumeration zurückzugeben, die der Entscheidung des Benutzers entspricht.