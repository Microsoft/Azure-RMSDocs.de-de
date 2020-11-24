---
title: AsyncControl-Klasse
description: 'Dokumentiert die AsyncControl:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 7058ccdcac0133bc708a81d5e7342f61c48994f9
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567274"
---
# <a name="class-asynccontrol"></a>AsyncControl-Klasse 
Klasse zum Abbrechen des asynchronen Vorgangs.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentlicher boolescher Abbruch ()  |  Wenn Sie "Abbrechen" aufrufen, wird versucht, die Aufgabe abzubrechen. bei erfolgreicher Ausführung wird der entsprechende OnFailure-Rückruf mit "MIP:: operationcancellederror" aufgerufen. Diese Funktion ist abhängig vom delegatdispatcher-Delegaten (.
  
## <a name="members"></a>Members
  
### <a name="cancel-function"></a>Cancel-Funktion
Wenn Sie "Abbrechen" aufrufen, wird versucht, die Aufgabe abzubrechen. bei erfolgreicher Ausführung wird der entsprechende OnFailure-Rückruf mit "MIP:: operationcancellederror" aufgerufen. Diese Funktion ist abhängig vom delegatdispatcher-Delegaten (.
  
**Siehe auch**: MIP:: taskdispatcherdelegat),

  
**Gibt Folgendes zurück**: false, wenn das abbruchsignal nicht gesendet werden kann, andernfalls true.
Halten Sie keinen starken Verweis auf ein AsyncControl-Objekt in einem Task Vervollständigungs Block.