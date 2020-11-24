---
title: Class policyhandler
description: 'Dokumentiert die policyhandler:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: b70643c9db84cef329b64e515bef5c7c47801718
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567379"
---
# <a name="class-policyhandler"></a>Class policyhandler 
Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr\<ContentLabel\> GetSensitivityLabel(const ExecutionState& state)  |  Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.
Public Std:: Vector \<std::shared_ptr\<Action\> \> computeactions (Konstante executionstate& State)  |  Führt die Regeln im Handler basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.
public void NotifyCommittedActions(const ExecutionState& state)  |  Wird aufgerufen, wenn die berechneten Aktionen angewendet wurden und die Daten auf den Datenträger committet wurden
  
## <a name="members"></a>Members
  
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