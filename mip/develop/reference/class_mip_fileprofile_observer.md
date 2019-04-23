---
title: mip::FileProfile::Observer-Klasse
description: 'Beschreibt die Klasse:: fileprofile-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 7b9c3440d577e9ba2e08bdba6ed890d3a480c783
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60174101"
---
# <a name="class-mipfileprofileobserver"></a>mip::FileProfile::Observer-Klasse 
[Observer](class_mip_fileprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual ~Observer()  | _Noch nicht dokumentiert._
public virtual void OnLoadSuccess(const std::shared_ptr\<mip::FileProfile\>& profile, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void OnListEnginesSuccess(const std::vector\<std::string\>& engineIds, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void OnListEnginesFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
öffentliche virtuelle "void" OnUnloadEngineSuccess (const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public virtual void OnUnloadEngineFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public virtual void OnAddEngineSuccess(const std::shared_ptr\<mip::FileEngine\>& engine, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
öffentliche virtuelle "void" OnDeleteEngineSuccess (const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void OnDeleteEngineFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
public virtual void OnPolicyChanged(const std::string& engineId)  |  Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
öffentliche virtuelle "void" OnAddPolicyEngineStarting (Bool RequiresPolicyFetch)  |  Wird aufgerufen, vor der Erstellung von beschreiben, und zwar unabhängig davon, ob die Richtlinien-Engine die Daten vom Server abgerufen werden müssen oder ob es von lokal zwischengespeicherten Daten erstellt werden kann.
geschützte Observer()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="observer-function"></a>~ Observer-Funktion
_Noch nicht dokumentiert._

  
### <a name="onloadsuccess-function"></a>OnLoadSuccess-Funktion
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
  
### <a name="onloadfailure-function"></a>OnLoadFailure-Funktion
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
  
### <a name="onlistenginessuccess-function"></a>OnListEnginesSuccess-Funktion
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
  
### <a name="onlistenginesfailure-function"></a>OnListEnginesFailure-Funktion
Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
  
### <a name="onunloadenginesuccess-function"></a>OnUnloadEngineSuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
  
### <a name="onunloadenginefailure-function"></a>OnUnloadEngineFailure-Funktion
Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
  
### <a name="onaddenginesuccess-function"></a>OnAddEngineSuccess-Funktion
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
  
### <a name="onaddenginefailure-function"></a>OnAddEngineFailure-Funktion
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
  
### <a name="ondeleteenginesuccess-function"></a>OnDeleteEngineSuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
  
### <a name="ondeleteenginefailure-function"></a>OnDeleteEngineFailure-Funktion
Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
  
### <a name="onpolicychanged-function"></a>OnPolicyChanged-Funktion
Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
  
### <a name="onaddpolicyenginestarting-function"></a>OnAddPolicyEngineStarting-Funktion
Wird aufgerufen, vor der Erstellung von beschreiben, und zwar unabhängig davon, ob die Richtlinien-Engine die Daten vom Server abgerufen werden müssen oder ob es von lokal zwischengespeicherten Daten erstellt werden kann.

Parameter:  
* **requiresPolicyFetch**: Beschreibt, ob die Daten über HTTP abgerufen werden müssen oder wenn sie aus dem Cache geladen wird


Diese optionale Rückruf kann von einer Anwendung verwendet werden, um darüber informiert werden, unabhängig davon, ob ein Vorgang AddEngineAsync ein HTTP-Vorgangs (mit der zugehörigen Verzögerung) benötigt wird wird abgeschlossen.
  
### <a name="observer-function"></a>Observer-Funktion
_Noch nicht dokumentiert._
