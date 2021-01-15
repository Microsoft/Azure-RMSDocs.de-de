---
title: ConsentDelegate-Klasse
description: 'Dokumentiert die "genehmidelegat:: nicht definierte"-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 62ea631159a2658432a1b62ff47c635c05f63fcf
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215492"
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