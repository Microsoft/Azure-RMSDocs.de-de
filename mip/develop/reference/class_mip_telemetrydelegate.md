---
title: Class telemetrydelegat
description: 'Dokumentiert die telemetrydeleg:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 40e9c3a695f70af8051ef2a6e89ad232a7c09f54
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98224958"
---
# <a name="class-telemetrydelegate"></a>Class telemetrydelegat 
Eine Klasse, die die Schnittstelle zu den MIP SDK-Überwachungs-/telemetriebenachrichtigungen definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void-Beschreib Ereignis Ereignis (Konstante Std:: shared_ptr \<TelemetryEvent\>&-Ereignis)  |  Protokolliert ein Diagnose Ereignis.
public void Flush()  |  Alle Ereignisse in der Warteschlange leeren (z. b. aufgrund des herunter Fahrens)
  
## <a name="members"></a>Member
  
### <a name="writeevent-function"></a>Funktion "schreiteevent"
Protokolliert ein Diagnose Ereignis.

Parameter:  
* **Ereignis**: Ereignis, das protokolliert werden soll


  
### <a name="flush-function"></a>Flush-Funktion
Alle Ereignisse in der Warteschlange leeren (z. b. aufgrund des herunter Fahrens)