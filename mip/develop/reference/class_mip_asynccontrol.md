---
title: AsyncControl-Klasse
description: 'Dokumentiert die AsyncControl:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 7d21002c9bf90014a57eeb9b666f706e2b41f68d
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212211"
---
# <a name="class-asynccontrol"></a>AsyncControl-Klasse 
Klasse zum Abbrechen des asynchronen Vorgangs.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentlicher boolescher Abbruch ()  |  Wenn Sie "Abbrechen" aufrufen, wird versucht, die Aufgabe abzubrechen. bei erfolgreicher Ausführung wird der entsprechende OnFailure-Rückruf mit "MIP:: operationcancellederror" aufgerufen. Diese Funktion ist abhängig vom delegatdispatcher-Delegaten (.
  
## <a name="members"></a>Member
  
### <a name="cancel-function"></a>Cancel-Funktion
Wenn Sie "Abbrechen" aufrufen, wird versucht, die Aufgabe abzubrechen. bei erfolgreicher Ausführung wird der entsprechende OnFailure-Rückruf mit "MIP:: operationcancellederror" aufgerufen. Diese Funktion ist abhängig vom delegatdispatcher-Delegaten (.
  
**Siehe auch**: MIP:: taskdispatcherdelegat),

  
**Gibt Folgendes zurück**: false, wenn das abbruchsignal nicht gesendet werden kann, andernfalls true.
Halten Sie keinen starken Verweis auf ein AsyncControl-Objekt in einem Task Vervollständigungs Block.