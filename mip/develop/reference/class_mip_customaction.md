---
title: CustomAction-Klasse
description: 'Dokumentiert die CustomAction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: d1fb231d76ba2b5f076d42bbeeff95618c7386f3
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98211701"
---
# <a name="class-customaction"></a>CustomAction-Klasse 
CustomAction ist eine generische Aktionsklasse, die alle untergeordneten Eigenschaften der Aktion als Eigenschaften Sammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Ruft den Aktionsnamen ab.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& GetProperties () Konstanten  |  Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
  
## <a name="members"></a>Member
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Aktionsnamen ab.

  
**Rückgabe**: Ein Aktionsname, falls vorhanden, andernfalls eine leere Zeichenfolge.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab

  
**Rückgabe**: Eine Schlüssel-Wert-Paar-Liste.