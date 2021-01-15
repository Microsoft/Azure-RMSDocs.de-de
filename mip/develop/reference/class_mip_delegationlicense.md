---
title: delegationlicense der Klasse
description: 'Dokumentiert die delegationlicense:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: cfb719a68650b2159574dd6f8d92fb3d0c15a2c1
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98224970"
---
# <a name="class-delegationlicense"></a>delegationlicense der Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector \<uint8_t\>& getserializeddelegationjsonlicense ()  |  Ruft die Delegierungs Lizenz ab.
Public Konstanten Std:: Vector \<uint8_t\>& getserializeduserlicense (Schutz Handler::P relicencformat-Format)  |  Ruft die Benutzerlizenz ab, wenn angefordert.
Public Konstanten Std:: String& GetUser ()  |  Ruft den Benutzer ab, für den diese Lizenz erstellt wurde.
  
## <a name="members"></a>Member
  
### <a name="getserializeddelegationjsonlicense-function"></a>Getserializeddelegationjsonlicense-Funktion
Ruft die Delegierungs Lizenz ab.

  
**Returns**: serialisierte Lizenz: Diese Lizenz ist an die Identität des Benutzers gebunden, von dem die Anforderung stammt.
  
### <a name="getserializeduserlicense-function"></a>Getserializeduserlicense-Funktion
Ruft die Benutzerlizenz ab, wenn angefordert.

Parameter:  
* **Format**: Lizenzformat



  
**Gibt Folgendes zurück**: serialisierte Benutzerlizenz, wenn angefordert, andernfalls leerer Vektor diese Lizenz wird an den Delegierten Benutzer in der Anforderung gebunden.
  
### <a name="getuser-function"></a>GetUser-Funktion
Ruft den Benutzer ab, für den diese Lizenz erstellt wurde.

  
**Gibt Folgendes zurück**: der Benutzer