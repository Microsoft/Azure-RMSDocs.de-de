---
title: Klasse mip::TaskDispatcherDelegate
description: Dokumentiert die mip::taskdispatcherdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 568a6df614370769556cd3634070e199beb4da5b
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574430"
---
# <a name="class-miptaskdispatcherdelegate"></a>Klasse mip::TaskDispatcherDelegate 
Eine Klasse, die die Schnittstelle an den Verteiler des MIP SDK Aufgabe definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public void DispatchTask(const std::string& taskId, std::function\<void()\> task)  |  Führen Sie eine Aufgabe in einem Hintergrundthread.
public void DispatchTask(const std::string& taskId, std::function\<void()\> task, int64_t delay)  |  Führen Sie eine Aufgabe in einem Hintergrundthread mit der angegebenen Verzögerung.
public void ExecuteTaskOnIndependentThread(const std::string& taskId, std::function\<void()\> task)  |  Führen Sie sofort eine Aufgabe auf einem unabhängigen Thread an.
public Bool CancelTask (const Std:: String & "TaskID")  |  Abbrechen einer Hintergrundaufgabe an.
Öffentliche void CancelAllTasks()  |  Kündigen Sie alle Hintergrundaufgaben.
  
## <a name="members"></a>Member
  
### <a name="dispatchtask-function"></a>DispatchTask-Funktion
Führen Sie eine Aufgabe in einem Hintergrundthread.

Parameter:  
* **taskId**: Die ID zur eindeutigen Identifizierung eine Aufgabe 


* **task**: Funktion, die ausgeführt werden


  
### <a name="dispatchtask-function"></a>DispatchTask-Funktion
Führen Sie eine Aufgabe in einem Hintergrundthread mit der angegebenen Verzögerung.

Parameter:  
* **taskId**: Die ID zur eindeutigen Identifizierung eine Aufgabe 


* **task**: Funktion, die ausgeführt werden 


* **delay**: Verzögerung (in Sekunden) vor dem Ausführen der Aufgabe


  
### <a name="executetaskonindependentthread-function"></a>ExecuteTaskOnIndependentThread-Funktion
Führen Sie sofort eine Aufgabe auf einem unabhängigen Thread an.

Parameter:  
* **taskId**: Die ID zur eindeutigen Identifizierung eine Aufgabe 


* **task**: Funktion, die ausgeführt werden


  
### <a name="canceltask-function"></a>CancelTask-Funktion
Abbrechen einer Hintergrundaufgabe an.

Parameter:  
* **taskId**: Die ID einer Aufgabe abbrechen



  
**Gibt**: True, wenn der Task wurde erfolgreich abgebrochen, andernfalls "false"
  
### <a name="cancelalltasks-function"></a>CancelAllTasks-Funktion
Kündigen Sie alle Hintergrundaufgaben.