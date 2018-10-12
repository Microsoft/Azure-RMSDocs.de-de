---
title: Microsoft Information Protection-Klasse „PolicyProfile Observer“
description: Referenz für die Microsoft Information Protection-Klasse „PolicyProfile Observer“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5de2156f4906c14e4ebc1418df8acb092c089d7d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446872"
---
# <a name="class-mippolicyprofileobserver"></a>mip::PolicyProfile::Observer-Klasse 
[Observer](class_mip_policyprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<PolicyProfile>& profile, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void OnListEnginesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
public virtual void OnUnloadEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public virtual void OnUnloadEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public virtual void OnAddEngineSuccess(const std::shared_ptr<PolicyEngine>& engine, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void OnDeleteEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
 public virtual void OnPolicyChanged(const std::string& engineId)  |  Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Das aktuelle Profil, über das der Vorgang gestartet wird. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **error**: Der Fehler, durch den der Ladevorgang fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Auflisten der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.

Parameter:  
* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onunloadenginefailure"></a>OnUnloadEngineFailure
Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Entladen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Der Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.

Parameter:  
* **engineId**: Die Engine 


Zum Laden der neuen Richtlinie muss AddEngineAsync erneut mit der angegebenen Engine-ID aufgerufen werden.