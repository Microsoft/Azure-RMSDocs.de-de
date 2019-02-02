---
title: mip::JustifyAction-Klasse
description: 'Dokumentiert die MIP:: justifyaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: e52a38f8ca25ecb8cc8ae470cb77164abb2b6ec8
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650682"
---
# <a name="class-mipjustifyaction"></a>mip::JustifyAction-Klasse 
Diese [Aktion](class_mip_action.md) fordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Einstellen der Antwort im Ausführungsstatus an.
  
**Weitere Informationen finden Sie unter:** [mip::ExecutionState::IsDowngradeJustified](class_mip_executionstate.md#isdowngradejustified-function)
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.