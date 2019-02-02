---
title: mip::CustomAction-Klasse
description: 'Beschreibt die Klasse:: CustomAction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 49840aebf5d49e91671145d0c5dc9e3b6d8e4694
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650645"
---
# <a name="class-mipcustomaction"></a>mip::CustomAction-Klasse 
[CustomAction](class_mip_customaction.md) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Ruft den Aktionsnamen ab.
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetProperties() const  |  Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Aktionsnamen ab.

  
**Gibt**: Ein Aktionsnamen, sofern vorhanden; andernfalls eine leere Zeichenfolge.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab

  
**Gibt**: Ein Schlüssel-Wert-Paar-Liste.
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.