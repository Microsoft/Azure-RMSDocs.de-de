---
title: CustomAction-Klasse
description: 'Dokumentiert die CustomAction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: fc67920b517f3a9f75c395b42350cec9d75b23b3
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567172"
---
# <a name="class-customaction"></a>CustomAction-Klasse 
CustomAction ist eine generische Aktionsklasse, die alle untergeordneten Eigenschaften der Aktion als Eigenschaften Sammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Ruft den Aktionsnamen ab.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& GetProperties () Konstanten  |  Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
  
## <a name="members"></a>Members
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Aktionsnamen ab.

  
**Rückgabe**: Ein Aktionsname, falls vorhanden, andernfalls eine leere Zeichenfolge.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab

  
**Rückgabe**: Eine Schlüssel-Wert-Paar-Liste.