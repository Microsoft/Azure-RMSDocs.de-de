---
title: Klasse taskdispatcherdelegat
description: 'Dokumentiert die taskdispatcherdeleg:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: b7cd2267b795540a8bb4035a695f5b34f0580b87
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764285"
---
# <a name="class-taskdispatcherdelegate"></a>Klasse taskdispatcherdelegat 
Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void dispatchtask (Konstanten Std:: String& TaskID, Std:: Function\<void ()\> -Aufgabe)  |  Ausführen einer Aufgabe in einem Hintergrund Thread.
öffentliches void dispatchtask (Konstante Std:: String& TaskID, Std:: Function\<void ()\> Task, int64_t Delta seconds)  |  Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.
öffentliches void executetaskonindependentthread (Konstanten Std:: String& TaskID, Std:: Function\<void ()\> -Aufgabe)  |  Sofortiges Ausführen einer Aufgabe in einem unabhängigen Thread.
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