---
title: 'MIP:: taskdispatcherdelegat-Klasse'
description: 'Dokumentiert die MIP:: taskdispatcherdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: d5237bf999f7ad704fd303783a9fbdc506b58ed2
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056763"
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