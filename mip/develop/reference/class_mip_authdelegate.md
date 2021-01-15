---
title: klassenauthdelegat
description: 'Dokumentiert die authdelegat:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: afe0dd79217942a767211f7959c898e098bd8f38
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212160"
---
# <a name="class-authdelegate"></a>klassenauthdelegat 
Delegat für Vorgänge im Zusammenhang mit der Authentifizierung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual bool AcquireOAuth2Token (Konstante Identität& Identität, konstant OAuth2Challenge& Challenge, OAuth2Token& Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
public virtual bool AcquireOAuth2Token (Konstante Identität& Identität, konstant OAuth2Challenge& Challenge, Konstante Std:: shared_ptr \<void\>& context, OAuth2Token& Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
  
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