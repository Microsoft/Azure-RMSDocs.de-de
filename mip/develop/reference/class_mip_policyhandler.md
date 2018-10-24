---
title: Die Klasse „mip::PolicyHandler“
description: Referenz zur Klasse „mip::PolicyHandler“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 23de5616558a298189cb885727d69a20373a3609
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445936"
---
# <a name="class-mippolicyhandler"></a>Die Klasse „mip::PolicyHandler“ 
Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr<ContentLabel> GetSensitivityLabel(const ExecutionState& state)  |  Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.
public std::vector<std::shared_ptr<Action>> ComputeActions(const ExecutionState& state)  |  Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.
 public void NotifyCommittedActions(const ExecutionState& state)  |  Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden
  
## <a name="members"></a>Member
  
### <a name="contentlabel"></a>ContentLabel
Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.

Parameter:  
* **state:** der aktuelle Inhaltsstatus 



  
**Rückgabe:** die derzeit auf den Inhalt angewendete Bezeichnung Wenn keine Bezeichnung vorhanden ist, ist die Rückgabe leer
  
### <a name="action"></a>Aktion
Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.

Parameter:  
* **state**: Der aktuelle Ausführungsstatus des Inhalts, für den die Regeln ausgeführt werden. 



  
**Rückgabe**: Liste der Aktionen, die auf den Inhalt angewendet werden sollten.
  
### <a name="notifycommittedactions"></a>NotifyCommittedActions
Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden

Parameter:  
* **state:** der aktuelle Ausführungsstatus des Inhalts, nachdem die Aktionen committet wurden 


: Dieser Aufruf sendet ein Überprüfungsereignis