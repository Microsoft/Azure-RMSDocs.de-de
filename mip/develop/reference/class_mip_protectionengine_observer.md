---
title: mip::ProtectionEngine::Observer-Klasse
description: Dokumentiert die mip::protectionengine-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 48dc726b8f541d8163cceb16e330f160b6d6bafb
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651631"
---
# <a name="class-mipprotectionengineobserver"></a>mip::ProtectionEngine::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionEngine](class_mip_protectionengine.md) empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche virtuelle "void" OnGetTemplatesSuccess (const Std:: shared_ptr\<Std:: vector\<Std:: String\>\>& TemplateIds, const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void OnGetTemplatesFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
öffentliche virtuelle "void" OnGetRightsForLabelIdSuccess (const Std:: shared_ptr\<Std:: vector\<Std:: String\>\>& Rechte, const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.
public virtual void OnGetRightsForLabelIdFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess-function"></a>OnGetTemplatesSuccess-Funktion
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templateIds**: Ein Verweis auf die Liste der Vorlagen abgerufen. 


* **context**: Der gleiche Kontext, der übergeben wurde [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function)


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess-function) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure-function) weitergeleitet.
  
### <a name="ongettemplatesfailure-function"></a>OnGetTemplatesFailure-Funktion
Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.

Parameter:  
* **error**: [Fehler](class_mip_error.md) , aufgetreten ist, beim Abrufen der Vorlagen 


* **context**: Der gleiche Kontext, der übergeben wurde [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function)


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess-function) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure-function) weitergeleitet.
  
### <a name="ongetrightsforlabelidsuccess-function"></a>OnGetRightsForLabelIdSuccess-Funktion
Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.

Parameter:  
* **Rechte**: Ein Verweis auf die Liste der Rechte abgerufen. 


* **context**: Der gleiche Kontext, der übergeben wurde [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function)


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) oder [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function) weitergeleitet.
  
### <a name="ongetrightsforlabelidfailure-function"></a>OnGetRightsForLabelIdFailure function
Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden

Parameter:  
* **error**: [Fehler](class_mip_error.md) , der beim Abrufen der Rechte aufgetreten ist 


* **context**: Der gleiche Kontext, der übergeben wurde [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function)


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) oder [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function) weitergeleitet.