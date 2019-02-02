---
title: Die Klasse „mip::PolicyHandler“
description: Dokumentiert die mip::policyhandler-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: ca644716d730a43d4455919b7555852e770e0cda
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651495"
---
# <a name="class-mippolicyhandler"></a>Die Klasse „mip::PolicyHandler“ 
Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<ContentLabel\> GetSensitivityLabel (const ExecutionState & State)  |  Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.
Public Std:: vector\<Std:: shared_ptr\<Aktion\> \> ComputeActions (const ExecutionState & State)  |  Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.
public void NotifyCommittedActions(const ExecutionState& state)  |  Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden
  
## <a name="members"></a>Member
  
### <a name="getsensitivitylabel-function"></a>GetSensitivityLabel-Funktion
Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.

Parameter:  
* **state**: Aktuellen Status des Inhalts 



  
**Gibt**: Die Bezeichnung, die derzeit auf den Inhalt angewendet wird. Wenn keine Bezeichnung vorhanden ist, ist die Rückgabe leer
  
### <a name="computeactions-function"></a>ComputeActions-Funktion
Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.

Parameter:  
* **state**: Der aktuelle Ausführungsstatus des Inhalts, für den die Regeln ausgeführt werden. 



  
**Gibt**: Liste der Aktionen, die auf den Inhalt angewendet werden soll.
  
### <a name="notifycommittedactions-function"></a>NotifyCommittedActions-Funktion
Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden

Parameter:  
* **state:** der aktuelle Ausführungsstatus des Inhalts, nachdem die Aktionen committet wurden 


: Dieser Aufruf sendet dann ein Überwachungsereignis