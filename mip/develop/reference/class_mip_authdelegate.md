---
title: klassenauthdelegat
description: 'Dokumentiert die authdelegat:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 9a971a7d0e8cf78baa5231225da620c9e1c8fa47
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567268"
---
# <a name="class-authdelegate"></a>klassenauthdelegat 
Delegat für Vorgänge im Zusammenhang mit der Authentifizierung.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual bool AcquireOAuth2Token (Konstante Identität& Identität, konstant OAuth2Challenge& Challenge, OAuth2Token& Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
public virtual bool AcquireOAuth2Token (Konstante Identität& Identität, konstant OAuth2Challenge& Challenge, Konstante Std:: shared_ptr \<void\>& context, OAuth2Token& Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
  
## <a name="members"></a>Members
  
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