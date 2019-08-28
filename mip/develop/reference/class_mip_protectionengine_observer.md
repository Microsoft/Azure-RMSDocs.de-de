---
title: mip::ProtectionEngine::Observer-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 8985b5646849338213855017da042538a27c935b
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70057637"
---
# <a name="class-mipprotectionengineobserver"></a>mip::ProtectionEngine::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionEngine](class_mip_protectionengine.md) empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void ongettemplatessuccess (Konst Std:: shared_ptr\<Std:: Vector\<Std:: String\>\>& templateids, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void ongettemplatesfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
public virtual void OnGetRightsForLabelIdSuccess (Konst Std:: shared_ptr\<Std:: Vector\<Std:: String\>\>& Rights, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.
public virtual void OnGetRightsForLabelIdFailure (konstant Std:: exception_ptr & Error, Konstante Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess-function"></a>Ongettemplatessuccess-Funktion
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templateids**: Ein Verweis auf die Liste der abgerufenen Vorlagen. 


* **Kontext**: Der Kontext, der an "Schutz Modul [:: gettemplatesasync](class_mip_protectionengine.md#gettemplatesasync-function) " übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess-function) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure-function) weitergeleitet.
  
### <a name="ongettemplatesfailure-function"></a>Ongettemplatesfailure-Funktion
Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.

Parameter:  
* **Fehler**: [Fehler](class_mip_error.md) beim Abrufen von Vorlagen. 


* **Kontext**: Der Kontext, der an "Schutz Modul [:: gettemplatesasync](class_mip_protectionengine.md#gettemplatesasync-function) " übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess-function) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure-function) weitergeleitet.
  
### <a name="ongetrightsforlabelidsuccess-function"></a>OnGetRightsForLabelIdSuccess-Funktion
Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.

Parameter:  
* **Rechte**: Ein Verweis auf die Liste der abgerufenen Rechte. 


* **Kontext**: Derselbe Kontext, der an "Schutz Modul:: GetRightsForLabelIdAsync" übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: GetRightsForLabelIdAsync" übergeben. derselbe Kontext wird unverändert an Schutz Module [:: Observer:: OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) oder schutzengine [:: Observer:: OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function) weitergeleitet.
  
### <a name="ongetrightsforlabelidfailure-function"></a>OnGetRightsForLabelIdFailure-Funktion
Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden

Parameter:  
* **Fehler**: [Fehler](class_mip_error.md) beim Abrufen der Rechte. 


* **Kontext**: Derselbe Kontext, der an "Schutz Modul:: GetRightsForLabelIdAsync" übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: GetRightsForLabelIdAsync" übergeben, und derselbe Kontext wird unverändert an Schutz Modul [:: Observer:: OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) weitergeleitet. oder Schutz- [Engine:: Observer:: OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function)