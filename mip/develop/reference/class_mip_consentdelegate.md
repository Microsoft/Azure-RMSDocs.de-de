---
title: 'MIP:: einvernehmdelegat-Klasse'
description: 'Dokumentiert die MIP:: genehmidelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: da2dffa6b24afa54de099a1eed885c0aa3046c98
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70055251"
---
# <a name="class-mipconsentdelegate"></a>MIP:: einvernehmdelegat-Klasse 
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
* **URL**: Die URL, für die das SDK Benutzer Zustimmung erfordert



  
**Gibt Folgendes zurück**: Eine Zustimmungs-Aufzählung mit der Entscheidung des Benutzers.
Wenn das SDK die Zustimmung des Benutzers mit dieser Methode anfordert, sollte die Clientanwendung dem Benutzer die URL anzeigen. Clientanwendungen sollten eine Möglichkeit bieten, die Zustimmung des Benutzers einzuholen und die entsprechende Zustimmungsenumeration zurückzugeben, die der Entscheidung des Benutzers entspricht.