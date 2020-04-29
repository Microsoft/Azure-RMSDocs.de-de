---
title: AsyncControl-Klasse
description: 'Dokumentiert die AsyncControl:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: d032abf9fe7192cfe6ccfd5890d6585aaa2ba645
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763658"
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