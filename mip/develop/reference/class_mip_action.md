---
title: mip::Action-Klasse
description: 'MIP:: Action-Klasse von der Microsoft Information Protection (MIP) SDK-Dokumente.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 2a3ef2340aacefc9679ddad011be17991929face
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650526"
---
# <a name="class-mipaction"></a>mip::Action-Klasse 
Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.