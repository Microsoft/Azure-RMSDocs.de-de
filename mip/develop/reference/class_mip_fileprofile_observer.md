---
title: 'class file profile:: Observer'
description: 'Dokumentiert die File profile:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 4dd3ff426e92fdd28cac211eb6953b8d30eb5ae5
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81762748"
---
# <a name="class-fileprofileobserver"></a>class file profile:: Observer 
Observer-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Alle Fehler erben von mip::Error. Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual ~Observer()  | _Noch nicht dokumentiert._
public virtual void onloadsuccess (Konstante Std::\<shared_ptr MIP:: fileprofile\>& Profile, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void onloadfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void onlistenginessuccess (Konstante Std::\<Vector Std:: String\>& engineids, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void onlistenginesfailure (konstant Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
öffentliches virtuelles void-onunloadenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
öffentliches virtuelles void-onunloadenginefailure (Konstante Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public virtual void onaddenginesuccess (Konstante Std::\<shared_ptr MIP:: fileengine\>& Engine, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
öffentliches virtuelles void-onaddenginefailure (Konstante Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
öffentliches virtuelles void ondeleteenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void ondeleteenginefailure (konstant Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
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
* **requirespolicyfetch**: Beschreibt, ob Engine-Daten über HTTP abgerufen werden müssen, oder ob Sie aus dem Cache geladen werden.


Dieser optionale Rückruf kann von einer Anwendung verwendet werden, um darüber informiert zu werden, ob ein addengineasync-Vorgang einen HTTP-Vorgang (mit der zugehörigen Verzögerung) erfordert.
  
### <a name="observer-function"></a>Observer-Funktion
_Noch nicht dokumentiert._
