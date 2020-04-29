---
title: CustomAction-Klasse
description: 'Dokumentiert die CustomAction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 82f6ccc0e44fc5d055a1b4785c33d473dbedabf6
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763380"
---
# <a name="class-customaction"></a>CustomAction-Klasse 
CustomAction ist eine generische Aktionsklasse, die alle untergeordneten Eigenschaften der Aktion als Eigenschaften Sammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Ruft den Aktionsnamen ab.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\> \>& GetProperties () Konstanten  |  Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
  
## <a name="members"></a>Member
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Aktionsnamen ab.

  
**Rückgabe**: Ein Aktionsname, falls vorhanden, andernfalls eine leere Zeichenfolge.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab

  
**Rückgabe**: Eine Schlüssel-Wert-Paar-Liste.