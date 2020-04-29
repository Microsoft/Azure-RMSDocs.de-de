---
title: removewatermarkaction-Klasse
description: 'Dokumentiert die removewatermarkaction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 93c99a0bd66df636de618629ff25d7f37d0cddd8
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760509"
---
# <a name="class-removewatermarkaction"></a>removewatermarkaction-Klasse 
Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector\<Std:: String\>& getuielementnames ()  |  Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte
public ActionType GetType() const  |  Ruft den Typ der Aktion ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementnames-function"></a>Getuielementnames-Funktion
Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte

  
**Rückgabe**: Eine Liste mit Namen der Benutzeroberflächenelemente.
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der Aktion ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.