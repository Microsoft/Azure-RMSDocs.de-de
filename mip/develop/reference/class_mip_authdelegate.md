---
title: 'MIP:: authdelegat-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: b865a26b9cfd96cf4beafa2eb712917405f1dd5c
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884506"
---
# <a name="class-mipauthdelegate"></a>MIP:: authdelegat-Klasse 
Delegat für Vorgänge im Zusammenhang mit der Authentifizierung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual bool AcquireOAuth2Token (Konstante MIP:: Identity & Identity, Reas OAuth2Challenge & Challenge, OAuth2Token & Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
public virtual bool AcquireOAuth2Token (Konst MIP:: Identity & Identity, konstant OAuth2Challenge & Challenge, Konstanten Std:: shared_ptr\<void\>& context, OAuth2Token & Token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.
  
## <a name="members"></a>Member
  
### <a name="acquireoauth2token-function"></a>AcquireOAuth2Token-Funktion
Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.

Parameter:  
* **Identität**: 


* **Herausforderung**: 


* **Token**: 


> Veraltet Diese Methode wird in Kürze als veraltet markiert, da Sie den Kontext Parameter akzeptiert. Wenn die neue Version implementiert wurde, muss diese Version nicht implementiert werden.
  
### <a name="acquireoauth2token-function"></a>AcquireOAuth2Token-Funktion
Diese Methode wird aufgerufen, wenn ein Authentifizierungs Token für die Richtlinien-Engine mit der angegebenen Identität und der angegebenen Abfrage erforderlich ist. Der Client sollte zurückgeben, ob das Abrufen des Tokens erfolgreich war. Bei erfolgreicher Ausführung sollte das angegebene Tokenobjekt initialisiert werden.

Parameter:  
* **Identität**: Benutzer, für den ein Token angefordert wird 


* **Herausforderung**: OAuth2 Challenge 


* **Kontext**: Nicht transparenter Kontext, der von der Host Anwendung an die MIP-API übermittelt wurde. 


* **Token**: [output] Base64-codiertes OAuth2-Token

