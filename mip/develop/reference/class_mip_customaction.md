---
title: mip::CustomAction-Klasse
description: 'Dokumentiert die MIP:: CustomAction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 7e78d11cc85af5550a4d6ab235b3754d72b2c012
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70055164"
---
# <a name="class-mipcustomaction"></a>mip::CustomAction-Klasse 
[CustomAction](class_mip_customaction.md) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Ruft den Aktionsnamen ab.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& GetProperties () Konstanten  |  Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
  
## <a name="members"></a>Member
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Aktionsnamen ab.

  
**Gibt Folgendes zurück**: Ein Aktionsname, falls vorhanden, eine leere Zeichenfolge.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab

  
**Gibt Folgendes zurück**: Eine Liste von Schlüssel-Wert-Paaren.