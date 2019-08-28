---
title: 'MIP:: authdelegat-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: f1f2a9f1f1f61d381cbf0da58cfdef9cad6044e2
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056294"
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

