---
title: Die Klasse „mip::ProtectionEngine::Observer“
description: Referenz zur Klasse „mip::ProtectionEngine::Observer“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 9999b450d614b4465f151f0b2df80892a83bc143
ms.sourcegitcommit: 4cd90fcf94ac6e2543d8be10e6e29e8218d5fd9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49651344"
---
# <a name="class-mipprotectionengineobserver"></a>mip::ProtectionEngine::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionEngine](class_mip_protectionengine.md) empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnGetTemplatesSuccess(const std::shared_ptr<std::vector<std::string>>& templateIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void OnGetTemplatesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
public virtual void OnGetRightsForLabelIdSuccess(const std::shared_ptr<std::vector<std::string>>& rights, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.
public virtual void OnGetRightsForLabelIdFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden
public virtual void OnGetGrantingLabelIdsSuccess(const std::shared_ptr<std::vector<std::string>>& labelIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn Bezeichnungs-IDs erfolgreich abgerufen wurden.
public virtual void OnGetGrantingLabelIdsFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn Bezeichnungs-IDs für den Benutzer abgerufen werden
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess"></a>OnGetTemplatesSuccess
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templateIds**: Verweis auf die Liste der abzurufenden Vorlagen 


* **context**: Der gleiche Kontext, der an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure) weitergeleitet.
  
### <a name="ongettemplatesfailure"></a>OnGetTemplatesFailure
Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.

Parameter:  
* **error**: Ein [Fehler](class_mip_error.md), der beim Abrufen von Vorlagen aufgetreten ist 


* **context**: Der gleiche Kontext, der an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure) weitergeleitet.
  
### <a name="ongetrightsforlabelidsuccess"></a>OnGetRightsForLabelIdSuccess
Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.

Parameter:  
* **rights**: eine Referenz zu der Liste mit abgerufenen Rechten 


* **context**: derselbe Kontext, der an [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) oder [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure) weitergeleitet.
  
### <a name="ongetrightsforlabelidfailure"></a>OnGetRightsForLabelIdFailure
Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden

Parameter:  
* **error**: Ein [Fehler](class_mip_error.md), der beim Abrufen von Rechten aufgetreten ist 


* **context**: derselbe Kontext, der an [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) oder [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure) weitergeleitet.
  
### <a name="ongetgrantinglabelidssuccess"></a>OnGetGrantingLabelIdsSuccess
Wird aufgerufen, wenn Bezeichnungs-IDs erfolgreich abgerufen wurden.

Parameter:  
* **labelIds**: ein Verweis auf die Liste der abgerufenen Bezeichnungs-IDs 


* **context**: derselbe Kontext, der an [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) oder [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure) weitergeleitet.
  
### <a name="ongetgrantinglabelidsfailure"></a>OnGetGrantingLabelIdsFailure
Wird aufgerufen, wenn Bezeichnungs-IDs für den Benutzer abgerufen werden

Parameter:  
* **error**: Ein [Fehler](class_mip_error.md), der beim Abrufen von Bezeichnungs-IDs aufgetreten ist 


* **context**: derselbe Kontext, der an [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) oder [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure) weitergeleitet.
