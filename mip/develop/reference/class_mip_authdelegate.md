---
title: Klasse mip::AuthDelegate
description: Dokumentiert die mip::authdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: cf6ea43b36518f2eec74b9ed0f8682466aa6b64d
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56258010"
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

