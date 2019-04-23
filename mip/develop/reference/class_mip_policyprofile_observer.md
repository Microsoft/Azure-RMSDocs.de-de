---
title: mip::PolicyProfile::Observer-Klasse
description: Dokumentiert die mip::policyprofile-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: f9ff2448b3ae09e094189e85b15b2fabad12321e
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60184551"
---
# <a name="class-mippolicyprofileobserver"></a>mip::PolicyProfile::Observer-Klasse 
[Observer](class_mip_policyprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche virtuelle "void" OnLoadSuccess (const Std:: shared_ptr\<PolicyProfile\>& Profil, const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void OnListEnginesSuccess(const std::vector\<std::string\>& engineIds, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void OnListEnginesFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
öffentliche virtuelle "void" OnUnloadEngineSuccess (const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public virtual void OnUnloadEngineFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
öffentliche virtuelle "void" OnAddEngineSuccess (const Std:: shared_ptr\<"policyengine"\>&-Engine, const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
öffentliche virtuelle "void" OnAddEngineStarting (Bool RequiresPolicyFetch)  |  Wird aufgerufen, vor der Erstellung von beschreiben, und zwar unabhängig davon, ob der-Engine die Daten vom Server abgerufen werden müssen oder ob es von lokal zwischengespeicherten Daten erstellt werden kann.
public virtual void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
öffentliche virtuelle "void" OnDeleteEngineSuccess (const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void OnDeleteEngineFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
public virtual void OnPolicyChanged(const std::string& engineId)  |  Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde oder die geladene benutzerdefinierte Empfindlichkeit geändert haben.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess-function"></a>OnLoadSuccess-Funktion
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Das aktuelle Profil, über das der Vorgang gestartet wird. 


* **Kontext**: der Kontext, die die LoadAsync-Vorgang an.


  
### <a name="onloadfailure-function"></a>OnLoadFailure-Funktion
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **error**: Der Fehler, durch den der Ladevorgang fehlgeschlagen ist. 


* **Kontext**: der Kontext, die die LoadAsync-Vorgang an.


  
### <a name="onlistenginessuccess-function"></a>OnListEnginesSuccess-Funktion
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs 


* **Kontext**: der Kontext, der für den Betrieb ListEnginesAsync übergeben.


  
### <a name="onlistenginesfailure-function"></a>OnListEnginesFailure-Funktion
Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Auflisten der Engine fehlgeschlagen ist. 


* **Kontext**: der Kontext, der für den Betrieb ListEnginesAsync übergeben.


  
### <a name="onunloadenginesuccess-function"></a>OnUnloadEngineSuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.

Parameter:  
* **Kontext**: der Kontext, der für den Betrieb UnloadEngineAsync übergeben.


  
### <a name="onunloadenginefailure-function"></a>OnUnloadEngineFailure-Funktion
Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Entladen der Engine fehlgeschlagen ist. 


* **Kontext**: der Kontext, der für den Betrieb UnloadEngineAsync übergeben.


  
### <a name="onaddenginesuccess-function"></a>OnAddEngineSuccess-Funktion
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.

Parameter:  
* **Engine**: das neu hinzugefügte Modul 


* **Kontext**: übergeben Sie der Kontext für den Betrieb von AddEngineAsync


  
### <a name="onaddenginestarting-function"></a>OnAddEngineStarting-Funktion
Wird aufgerufen, vor der Erstellung von beschreiben, und zwar unabhängig davon, ob der-Engine die Daten vom Server abgerufen werden müssen oder ob es von lokal zwischengespeicherten Daten erstellt werden kann.

Parameter:  
* **requiresPolicyFetch**: Beschreibt, ob die Daten über HTTP abgerufen werden müssen oder wenn sie aus dem Cache geladen wird


Diese optionale Rückruf kann von einer Anwendung verwendet werden, um darüber informiert werden, unabhängig davon, ob ein Vorgang AddEngineAsync ein HTTP-Vorgangs (mit der zugehörigen Verzögerung) benötigt wird wird abgeschlossen.
  
### <a name="onaddenginefailure-function"></a>OnAddEngineFailure-Funktion
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.

Parameter:  
* **error**: der Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **Kontext**: der Kontext, der für den Betrieb von AddEngineAsync übergeben.


  
### <a name="ondeleteenginesuccess-function"></a>OnDeleteEngineSuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **Kontext**: der Kontext, der für den Betrieb DeleteEngineAsync übergeben.


  
### <a name="ondeleteenginefailure-function"></a>OnDeleteEngineFailure-Funktion
Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **Kontext**: der Kontext, der für den Betrieb DeleteEngineAsync übergeben.


  
### <a name="onpolicychanged-function"></a>OnPolicyChanged-Funktion
Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde oder die geladene benutzerdefinierte Empfindlichkeit geändert haben.

Parameter:  
* **engineId**: Die Engine 


Zum Laden der neuen Richtlinie muss AddEngineAsync erneut mit der angegebenen Engine-ID aufgerufen werden.