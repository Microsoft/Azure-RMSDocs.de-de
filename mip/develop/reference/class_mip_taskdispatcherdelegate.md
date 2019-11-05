---
title: 'MIP:: taskdispatcherdelegat-Klasse'
description: 'Dokumentiert die MIP:: taskdispatcherdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: e73a03b842b1216bcc4ef71941ca4bc0b0233945
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73559960"
---
# <a name="class-miptaskdispatcherdelegate"></a>MIP:: taskdispatcherdelegat-Klasse 
Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void dispatchtask (konstant Std:: String & taskId, Std:: function\<void ()\> Aufgabe)  |  Ausführen einer Aufgabe in einem Hintergrund Thread.
öffentliches void dispatchtask (konstant Std:: String & taskId, Std:: function\<void ()\> Task, int64_t Delta seconds)  |  Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.
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