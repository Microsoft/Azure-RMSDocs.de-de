---
title: mip::FileProfile::Observer-Klasse
description: 'Dokumentiert die MIP:: File Profile-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: fef75e5990a89a5a52dd1810bc15b62d1d82171b
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054901"
---
# <a name="class-mipfileprofileobserver"></a>mip::FileProfile::Observer-Klasse 
[Observer](class_mip_fileprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual ~Observer()  | _Noch nicht dokumentiert._
public virtual void onloadsuccess (Konstante Std\<:: shared_ptr MIP:: File profile\>& Profile, Konst Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void onloadfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void onlistenginessuccess (Konstante Std::\<Vector Std:: String\>& engineids, Konst Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void onlistenginesfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
öffentliches virtuelles void-onunloadenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public virtual void onunloadenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public virtual void onaddenginesuccess (Konstante Std::\<shared_ptr MIP:: fileengine\>& Engine, Konst Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void onaddenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
public virtual void ondeleteenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void ondeleteenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
public virtual void OnPolicyChanged(const std::string& engineId)  |  Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
public virtual void onaddpolicyenginestarting (bool requirespolicyfetch)  |  Wird vor der Erstellung der Engine aufgerufen, um zu beschreiben, ob die Richtlinien Daten der Richtlinien-Engine vom Server abgerufen werden müssen oder ob Sie aus lokal zwischengespeicherten Daten erstellt werden können.
geschützte Observer()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="observer-function"></a>~ Observer-Funktion
_Noch nicht dokumentiert._

  
### <a name="onloadsuccess-function"></a>Onloadsuccess-Funktion
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
  
### <a name="onloadfailure-function"></a>Onloadfailure-Funktion
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
  
### <a name="onlistenginessuccess-function"></a>Onlistenginessuccess-Funktion
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
  
### <a name="onlistenginesfailure-function"></a>Onlistenginesfailure-Funktion
Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
  
### <a name="onunloadenginesuccess-function"></a>Onunloadenginesuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
  
### <a name="onunloadenginefailure-function"></a>Onunloadenginefailure-Funktion
Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
  
### <a name="onaddenginesuccess-function"></a>Onaddenginesuccess-Funktion
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
  
### <a name="onaddenginefailure-function"></a>Onaddenginefailure-Funktion
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
  
### <a name="ondeleteenginesuccess-function"></a>Ondeleteenginesuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
  
### <a name="ondeleteenginefailure-function"></a>Ondeleteenginefailure-Funktion
Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
  
### <a name="onpolicychanged-function"></a>Onpolicychanged-Funktion
Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
  
### <a name="onaddpolicyenginestarting-function"></a>Onaddpolicyenginestarting-Funktion
Wird vor der Erstellung der Engine aufgerufen, um zu beschreiben, ob die Richtlinien Daten der Richtlinien-Engine vom Server abgerufen werden müssen oder ob Sie aus lokal zwischengespeicherten Daten erstellt werden können.

Parameter:  
* **requiresPolicyFetch**: Beschreibt, ob Engine-Daten über HTTP abgerufen werden müssen oder ob Sie aus dem Cache geladen werden.


Dieser optionale Rückruf kann von einer Anwendung verwendet werden, um darüber informiert zu werden, ob ein addengineasync-Vorgang einen HTTP-Vorgang (mit der zugehörigen Verzögerung) erfordert.
  
### <a name="observer-function"></a>Observer-Funktion
_Noch nicht dokumentiert._
