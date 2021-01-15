---
title: Klasse taskdispatcherdelegat
description: 'Dokumentiert die taskdispatcherdeleg:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: f8f84b51200ff630b6158f7b02ca88e2a3d21e25
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212874"
---
# <a name="class-taskdispatcherdelegate"></a>Klasse taskdispatcherdelegat 
Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void dispatchtask (Konstanten Std:: String& TaskID, Std:: Function- \<void()\> Aufgabe)  |  Ausführen einer Aufgabe in einem Hintergrund Thread.
öffentliches void dispatchtask (Konstanten Std:: String& TaskID, Std:: Function \<void()\> Task, int64_t Delta seconds)  |  Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.
öffentliches void executetaskonindependentthread (Konstanten Std:: String& TaskID, Std:: Function- \<void()\> Aufgabe)  |  Sofortiges Ausführen einer Aufgabe in einem unabhängigen Thread.
public bool canceltask (Konstante Std:: String& TaskID)  |  Abbrechen einer Hintergrundaufgabe
öffentliches void cancelalltasks ()  |  Alle Hintergrundaufgaben abbrechen.
  
## <a name="members"></a>Member
  
### <a name="dispatchtask-function"></a>Dispatchtask-Funktion
Ausführen einer Aufgabe in einem Hintergrund Thread.

Parameter:  
* **TaskID**: ID zum eindeutigen Identifizieren einer Aufgabe 


* **Aufgabe**: ausgeführte Funktion


  
### <a name="dispatchtask-function"></a>Dispatchtask-Funktion
Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.

Parameter:  
* **TaskID**: ID zum eindeutigen Identifizieren einer Aufgabe 


* **Aufgabe**: ausgeführte Funktion 


* **Delta Sekunden**: Verzögerung (in Sekunden) vor dem Ausführen der Aufgabe


  
### <a name="executetaskonindependentthread-function"></a>Executetaskonindependentthread-Funktion
Sofortiges Ausführen einer Aufgabe in einem unabhängigen Thread.

Parameter:  
* **TaskID**: ID zum eindeutigen Identifizieren einer Aufgabe 


* **Aufgabe**: ausgeführte Funktion


  
### <a name="canceltask-function"></a>Canceltask-Funktion
Abbrechen einer Hintergrundaufgabe

Parameter:  
* **TaskID**: ID des abzubrechenden Tasks



  
**Gibt zurück**: true, wenn die Aufgabe erfolgreich abgebrochen wurde, andernfalls false.
  
### <a name="cancelalltasks-function"></a>Cancelalltasks-Funktion
Alle Hintergrundaufgaben abbrechen.