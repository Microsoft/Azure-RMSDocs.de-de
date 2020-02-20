---
title: 'MIP:: AsyncControl-Klasse'
description: 'Dokumentiert die MIP:: AsyncControl-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: afef25cef1363d5275581a774279c97d61239f4b
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77492765"
---
# <a name="class-mipasynccontrol"></a>MIP:: AsyncControl-Klasse 
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