---
title: Klasse mip::AuthDelegate
description: Dokumentiert die mip::authdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: b6278d605dfbb9a9c4cf0cf1282a159c456c5561
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651995"
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

