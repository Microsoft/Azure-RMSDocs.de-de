---
title: 'MIP:: authdelegat-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 30907f3bf4a08f72305a59290c8cbd891def44c9
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77490607"
---
# <a name="class-mipauthdelegate"></a>MIP:: authdelegat-Klasse 
Delegat für Vorgänge im Zusammenhang mit der Authentifizierung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual bool AcquireOAuth2Token (Konstante MIP:: Identity & Identity, Reas OAuth2Challenge & Challenge, OAuth2Token & Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
public virtual bool AcquireOAuth2Token (Konst MIP:: Identity & Identity, konstant OAuth2Challenge & Challenge, Konstante Std:: shared_ptr\<void\>& Kontext, OAuth2Token & Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
  
## <a name="members"></a>Member
  
### <a name="acquireoauth2token-function"></a>AcquireOAuth2Token-Funktion
Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.

Parameter:  
* **Identität**: Benutzer, für den ein Token angefordert wird 


* **Challenge**: OAuth2 Challenge 


* **Token**: [output] Base64-codiertes OAuth2-Token



  
**Gibt Folgendes zurück**: true, wenn das Token erfolgreich abgerufen wurde, andernfalls false bei Fehler, wenn der tokenausgabeparameter eine Fehlermeldung enthält, wird er in die noauthtokenerror-Ausnahme eingefügt, die später für die Anwendung ausgelöst wird.
> Veraltet: Diese Methode wird in Kürze als veraltet markiert, um den Kontext Parameter zu akzeptieren. Wenn die neue Version implementiert wurde, muss diese Version nicht implementiert werden.
  
### <a name="acquireoauth2token-function"></a>AcquireOAuth2Token-Funktion
Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.

Parameter:  
* **Identität**: Benutzer, für den ein Token angefordert wird 


* **Challenge**: OAuth2 Challenge 


* **Kontext**: nicht transparenter Kontext, der von der Host Anwendung an die MIP-API übermittelt wurde. 


* **Token**: [output] Base64-codiertes OAuth2-Token



  
**Gibt Folgendes zurück**: true, wenn das Token erfolgreich abgerufen wurde, andernfalls false bei Fehler, wenn der tokenausgabeparameter eine Fehlermeldung enthält, wird er in die noauthtokenerror-Ausnahme eingefügt, die später für die Anwendung ausgelöst wird.