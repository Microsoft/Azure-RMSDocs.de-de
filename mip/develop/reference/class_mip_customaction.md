---
title: mip::CustomAction-Klasse
description: 'Dokumentiert die MIP:: CustomAction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 450ae0e455f74c6cb9b1f6b0b6d8aded9b30b2bd
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73558910"
---
# <a name="class-mipcustomaction"></a>mip::CustomAction-Klasse 
CustomAction ist eine generische Aktionsklasse, die alle untergeordneten Eigenschaften der Aktion als Eigenschaften Sammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Ruft den Aktionsnamen ab.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& GetProperties () Konstanten  |  Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
  
## <a name="members"></a>Member
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Aktionsnamen ab.

  
**Rückgabe**: Ein Aktionsname, falls vorhanden, andernfalls eine leere Zeichenfolge.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab

  
**Rückgabe**: Eine Schlüssel-Wert-Paar-Liste.