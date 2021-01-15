---
title: removewatermarkaction-Klasse
description: 'Dokumentiert die removewatermarkaction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 2c140461d0cf8b01b25893900191563b1fe3c8b0
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98213163"
---
# <a name="class-removewatermarkaction"></a>removewatermarkaction-Klasse 
Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector \<std::string\>& getuielementnames ()  |  Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte
public ActionType GetType() const  |  Ruft den Typ der Aktion ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementnames-function"></a>Getuielementnames-Funktion
Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte

  
**Rückgabe**: Eine Liste mit Namen der Benutzeroberflächenelemente.
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der Aktion ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.