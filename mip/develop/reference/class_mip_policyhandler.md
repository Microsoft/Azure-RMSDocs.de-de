---
title: Die Klasse „mip::PolicyHandler“
description: Dokumentiert die mip::policyhandler-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6c5979706b9868bd7d0b6b1adad5d96bd5d3e0ce
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57329589"
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
