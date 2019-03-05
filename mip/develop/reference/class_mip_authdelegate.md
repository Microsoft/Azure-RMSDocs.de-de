---
title: Klasse mip::AuthDelegate
description: Dokumentiert die mip::authdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: bcc38bf4b55ca99cf926138279223a4140f7bbf4
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330609"
---
# <a name="class-mipauthdelegate"></a>Klasse mip::AuthDelegate 
Delegat für die Authentifizierung bezogene Vorgänge.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Bool AcquireOAuth2Token (const MIP:: Identity, Identität, const OAuth2Challenge & Herausforderung OAuth2Token & token)  |  Diese Methode wird aufgerufen, wenn ein Authentifizierungstoken für die Richtlinien-Engine, mit der angegebenen Identität und die angegebene Abfrage erforderlich ist. Der Client sollte zurückgegeben werden, ob Abrufen des Authentifizierungstokens erfolgreich war. Wenn erfolgreich, sollte das angegebene token Objekt initialisiert werden.
  
## <a name="members"></a>Member
  
### <a name="acquireoauth2token-function"></a>AcquireOAuth2Token-Funktion
Diese Methode wird aufgerufen, wenn ein Authentifizierungstoken für die Richtlinien-Engine, mit der angegebenen Identität und die angegebene Abfrage erforderlich ist. Der Client sollte zurückgegeben werden, ob Abrufen des Authentifizierungstokens erfolgreich war. Wenn erfolgreich, sollte das angegebene token Objekt initialisiert werden.

Parameter:  
* **identity**: 


* **challenge**: 


* **token**:

