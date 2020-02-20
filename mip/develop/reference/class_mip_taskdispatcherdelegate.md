---
title: 'MIP:: taskdispatcherdelegat-Klasse'
description: 'Dokumentiert die MIP:: taskdispatcherdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: dca6a5fa04b62abf23f0116f63fd4a91c6081da0
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489332"
---
# <a name="class-miptaskdispatcherdelegate"></a>MIP:: taskdispatcherdelegat-Klasse 
Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void dispatchtask (konstant Std:: String & taskId, Std:: function\<void ()\> Aufgabe)  |  Ausführen einer Aufgabe in einem Hintergrund Thread.
öffentliches void dispatchtask (Konstanten Std:: String & taskId, Std:: function\<void ()\> Task, int64_t Delta seconds)  |  Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.
öffentliches void executetaskonindependentthread (konstant Std:: String & taskId, Std:: function\<void ()\> Aufgabe)  |  Sofortiges Ausführen einer Aufgabe in einem unabhängigen Thread.
public bool canceltask (Konstante Std:: String & taskId)  |  Abbrechen einer Hintergrundaufgabe
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