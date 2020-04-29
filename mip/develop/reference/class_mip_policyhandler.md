---
title: Class policyhandler
description: 'Dokumentiert die policyhandler:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: c46b72f3a040204b4485da14f00f38ca69fa8222
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760956"
---
# <a name="class-policyhandler"></a>Class policyhandler 
Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<contentlabel\> getsensitivitylabel (Konstanten executionstate& State)  |  Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.
Public Std:: Vector\<Std:: shared_ptr\<Action\> \> computeactions (Konstanten executionstate& State)  |  Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.
public void NotifyCommittedActions(const ExecutionState& state)  |  Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden
  
## <a name="members"></a>Member
  
### <a name="getsensitivitylabel-function"></a>Getsensitivitylabel-Funktion
Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.

Parameter:  
* **State**: Aktueller Status des Inhalts. 



  
**Rückgabe:** die derzeit auf den Inhalt angewendete Bezeichnung Wenn keine Bezeichnung vorhanden ist, ist die Rückgabe leer
  
### <a name="computeactions-function"></a>Computeactions-Funktion
Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.

Parameter:  
* **State**: der aktuelle Ausführungs Zustand des Inhalts, auf dem die Regeln ausgeführt werden. 



  
**Rückgabe**: Liste der Aktionen, die auf den Inhalt angewendet werden sollten.
  
### <a name="notifycommittedactions-function"></a>Notifycommittedactions-Funktion
Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden

Parameter:  
* **State**: der aktuelle Ausführungs Zustand des Inhalts, nachdem für die Aktionen ein Commit ausgeführt wurde. 


: Dieser Befehl sendet ein Audit-Ereignis.