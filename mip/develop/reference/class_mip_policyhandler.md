---
title: Die Klasse „mip::PolicyHandler“
description: Dokumentiert die MIP::p olicyhandler-Klasse des Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 7185af867a94e4b72663f818d5d1f7233e4219b3
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69883808"
---
# <a name="class-mippolicyhandler"></a>Die Klasse „mip::PolicyHandler“ 
Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<contentlabel\> getsensitivitylabel (Konstante executionstate & State)  |  Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.
Public Std:: Vector\<Std:: shared_ptr\<Action\> \> computeactions (Konstante executionstate & State)  |  Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.
public void NotifyCommittedActions(const ExecutionState& state)  |  Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden
  
## <a name="members"></a>Member
  
### <a name="getsensitivitylabel-function"></a>Getsensitivitylabel-Funktion
Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.

Parameter:  
* **state**: Aktueller Status des Inhalts. 



  
**Gibt Folgendes zurück**: Die Bezeichnung, die zurzeit auf den Inhalt angewendet wird. Wenn keine Bezeichnung vorhanden ist, ist die Rückgabe leer
  
### <a name="computeactions-function"></a>Computeactions-Funktion
Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.

Parameter:  
* **state**: Der aktuelle Ausführungsstatus des Inhalts, für den die Regeln ausgeführt werden. 



  
**Gibt Folgendes zurück**: Liste der Aktionen, die auf den Inhalt angewendet werden sollen.
  
### <a name="notifycommittedactions-function"></a>Notifycommittedactions-Funktion
Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden

Parameter:  
* **State**: der aktuelle Ausführungs Zustand des Inhalts, nachdem für die Aktionen ein Commit ausgeführt wurde. 


: Dieser Befehl sendet ein Audit-Ereignis.