---
title: mip::PolicyProfile::Observer-Klasse
description: Dokumentiert die MIP::p olicyprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 1315f4c1289c63184b8fa029b3668b363b88b143
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054196"
---
# <a name="class-mippolicyprofileobserver"></a>mip::PolicyProfile::Observer-Klasse 
[Observer](class_mip_policyprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onloadsuccess (Konstante Std::\<shared_ptr policyprofile\>& Profile, Konst Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void onloadfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void onlistenginessuccess (Konstante Std::\<Vector Std:: String\>& engineids, Konst Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void onlistenginesfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
öffentliches virtuelles void-onunloadenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public virtual void onunloadenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public virtual void onaddenginesuccess (Konstante Std::\<shared_ptr policyengine\>& Engine, Konst Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void onaddenginestarting (bool requirespolicyfetch)  |  Wird vor der Erstellung der Engine aufgerufen, um zu beschreiben, ob die Richtlinien Daten der Engine vom Server abgerufen werden müssen oder ob Sie aus lokal zwischengespeicherten Daten erstellt werden können.
public virtual void onaddenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
public virtual void ondeleteenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void ondeleteenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
public virtual void OnPolicyChanged(const std::string& engineId)  |  Wird aufgerufen, wenn sich die Richtlinie für die Engine mit der angegebenen ID geändert hat oder wenn die geladenen benutzerdefinierten Empfindlichkeits Typen geändert wurden.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess-function"></a>Onloadsuccess-Funktion
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Das aktuelle Profil, über das der Vorgang gestartet wird. 


* **context**: der an den LoadAsync-Vorgang über gegebene Kontext.


  
### <a name="onloadfailure-function"></a>Onloadfailure-Funktion
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **error**: Der Fehler, durch den der Ladevorgang fehlgeschlagen ist. 


* **context**: der an den LoadAsync-Vorgang über gegebene Kontext.


  
### <a name="onlistenginessuccess-function"></a>Onlistenginessuccess-Funktion
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs 


* **context**: der an den listenginesasync-Vorgang über gegebene Kontext.


  
### <a name="onlistenginesfailure-function"></a>Onlistenginesfailure-Funktion
Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Auflisten der Engine fehlgeschlagen ist. 


* **context**: der an den listenginesasync-Vorgang über gegebene Kontext.


  
### <a name="onunloadenginesuccess-function"></a>Onunloadenginesuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.

Parameter:  
* **context**: der an den unloadengineasync-Vorgang über gegebene Kontext.


  
### <a name="onunloadenginefailure-function"></a>Onunloadenginefailure-Funktion
Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Entladen der Engine fehlgeschlagen ist. 


* **context**: der an den unloadengineasync-Vorgang über gegebene Kontext.


  
### <a name="onaddenginesuccess-function"></a>Onaddenginesuccess-Funktion
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.

Parameter:  
* **Engine**: das neu hinzugefügte Modul 


* **Kontext**: der an den addengineasync-Vorgang über gegebene Kontext.


  
### <a name="onaddenginestarting-function"></a>Onaddenginestarting-Funktion
Wird vor der Erstellung der Engine aufgerufen, um zu beschreiben, ob die Richtlinien Daten der Engine vom Server abgerufen werden müssen oder ob Sie aus lokal zwischengespeicherten Daten erstellt werden können.

Parameter:  
* **requiresPolicyFetch**: Beschreibt, ob Engine-Daten über HTTP abgerufen werden müssen oder ob Sie aus dem Cache geladen werden.


Dieser optionale Rückruf kann von einer Anwendung verwendet werden, um darüber informiert zu werden, ob ein addengineasync-Vorgang einen HTTP-Vorgang (mit der zugehörigen Verzögerung) erfordert.
  
### <a name="onaddenginefailure-function"></a>Onaddenginefailure-Funktion
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.

Parameter:  
* **error**: der Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **context**: der an den addengineasync-Vorgang über gegebene Kontext.


  
### <a name="ondeleteenginesuccess-function"></a>Ondeleteenginesuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **context**: der an den deleteengineasync-Vorgang über gegebene Kontext.


  
### <a name="ondeleteenginefailure-function"></a>Ondeleteenginefailure-Funktion
Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **context**: der an den deleteengineasync-Vorgang über gegebene Kontext.


  
### <a name="onpolicychanged-function"></a>Onpolicychanged-Funktion
Wird aufgerufen, wenn sich die Richtlinie für die Engine mit der angegebenen ID geändert hat oder wenn die geladenen benutzerdefinierten Empfindlichkeits Typen geändert wurden.

Parameter:  
* **engineId**: Die Engine 


Zum Laden der neuen Richtlinie muss AddEngineAsync erneut mit der angegebenen Engine-ID aufgerufen werden.