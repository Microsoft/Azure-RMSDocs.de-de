---
title: Die Klasse „mip::ProtectionProfile::Observer“
description: Referenz zur Klasse „mip::ProtectionProfile::Observer“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3678e6c1e1659f28b2f1dcc36f61295a8d29393e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446429"
---
# <a name="class-mipprotectionprofileobserver"></a>mip::ProtectionProfile::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md) empfängt.
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<ProtectionProfile>& profile, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void OnListEnginesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.
public virtual void OnAddEngineSuccess(const std::shared_ptr<ProtectionEngine>& engine, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void OnDeleteEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Ein Verweis auf das neu erstellte [ProtectionProfile](class_mip_protectionprofile.md)


* **context**: Der gleiche Kontext, der an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) übergeben. Derselbe Kontext wird dann an [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure) weitergeleitet.
  
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **error**: Ein [Fehler](class_mip_error.md), der während des Ladens aufgetreten ist 


* **context**: Der gleiche Kontext, der an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) übergeben. Derselbe Kontext wird dann an [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure) weitergeleitet.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs 


* **context**: derselbe Kontext, der an [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync) übergeben wurde


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.

Parameter:  
* **error**: Fehler, durch den das Auflisten der Engines fehlgeschlagen ist 


* **context**: derselbe Kontext, der an [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync) übergeben wurde


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.

Parameter:  
* **engine**: neu erstellte Engine 


* **context**: derselbe Kontext, der an [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync) übergeben wurde


  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: der Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **context**: derselbe Kontext, der an [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync) übergeben wurde


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **context**: derselbe Kontext, der an [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync) übergeben wurde


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: Der Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **context**: derselbe Kontext, der an [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync) übergeben wurde

