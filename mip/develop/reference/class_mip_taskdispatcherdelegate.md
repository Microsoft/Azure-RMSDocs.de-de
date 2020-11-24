---
title: Klasse taskdispatcherdelegat
description: 'Dokumentiert die taskdispatcherdeleg:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 057ba0d4de58ab4dedf8d3e2f8b2a42b0e5f969a
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567031"
---
# <a name="class-taskdispatcherdelegate"></a>Klasse taskdispatcherdelegat 
Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void dispatchtask (Konstanten Std:: String& TaskID, Std:: Function- \<void()\> Aufgabe)  |  Ausführen einer Aufgabe in einem Hintergrund Thread.
öffentliches void dispatchtask (Konstanten Std:: String& TaskID, Std:: Function \<void()\> Task, int64_t Delta seconds)  |  Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.
öffentliches void executetaskonindependentthread (Konstanten Std:: String& TaskID, Std:: Function- \<void()\> Aufgabe)  |  Sofortiges Ausführen einer Aufgabe in einem unabhängigen Thread.
public bool canceltask (Konstante Std:: String& TaskID)  |  Abbrechen einer Hintergrundaufgabe
öffentliches void cancelalltasks ()  |  Alle Hintergrundaufgaben abbrechen.
  
## <a name="members"></a>Members
  
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