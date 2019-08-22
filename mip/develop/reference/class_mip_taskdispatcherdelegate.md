---
title: 'MIP:: taskdispatcherdelegat-Klasse'
description: 'Dokumentiert die MIP:: taskdispatcherdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 0455f446cddd7db1c05f0f7e7b76b33496810cf1
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69883026"
---
# <a name="class-miptaskdispatcherdelegate"></a>MIP:: taskdispatcherdelegat-Klasse 
Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public void DispatchTask(const std::string& taskId, std::function\<void()\> task)  |  Ausführen einer Aufgabe in einem Hintergrund Thread.
öffentliches void dispatchtask (Konstante Std:: String & taskId, Std:: Function\<void ()\> Task, int64_t Delay)  |  Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.
public void ExecuteTaskOnIndependentThread(const std::string& taskId, std::function\<void()\> task)  |  Sofortiges Ausführen einer Aufgabe in einem unabhängigen Thread.
public bool canceltask (Konstante Std:: String & taskId)  |  Abbrechen einer Hintergrundaufgabe
öffentliches void cancelalltasks ()  |  Alle Hintergrundaufgaben abbrechen.
  
## <a name="members"></a>Member
  
### <a name="dispatchtask-function"></a>Dispatchtask-Funktion
Ausführen einer Aufgabe in einem Hintergrund Thread.

Parameter:  
* **taskId**: ID zur eindeutigen Identifizierung einer Aufgabe 


* **Aufgabe**: Auszuführende Funktion


  
### <a name="dispatchtask-function"></a>Dispatchtask-Funktion
Führt eine Aufgabe in einem Hintergrund Thread mit der angegebenen Verzögerung aus.

Parameter:  
* **taskId**: ID zur eindeutigen Identifizierung einer Aufgabe 


* **Aufgabe**: Auszuführende Funktion 


* **Verzögerung**: Verzögerung (in Sekunden) vor dem Ausführen der Aufgabe


  
### <a name="executetaskonindependentthread-function"></a>Executetaskonindependentthread-Funktion
Sofortiges Ausführen einer Aufgabe in einem unabhängigen Thread.

Parameter:  
* **taskId**: ID zur eindeutigen Identifizierung einer Aufgabe 


* **Aufgabe**: Auszuführende Funktion


  
### <a name="canceltask-function"></a>Canceltask-Funktion
Abbrechen einer Hintergrundaufgabe

Parameter:  
* **taskId**: ID des abzubrechenden Tasks



  
**Gibt Folgendes zurück**: True, wenn die Aufgabe erfolgreich abgebrochen wurde, andernfalls false.
  
### <a name="cancelalltasks-function"></a>Cancelalltasks-Funktion
Alle Hintergrundaufgaben abbrechen.