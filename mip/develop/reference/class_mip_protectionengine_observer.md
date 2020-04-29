---
title: 'Class schutzengine:: Observer'
description: 'Dokumentiert die schutzengine:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: ca1f9c3251df30166b123ae31c8e3c5fceef67fc
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764604"
---
# <a name="class-protectionengineobserver"></a>Class schutzengine:: Observer 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionEngine empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void ongettemplatessuccess (Konstante Std\<:: Vector Std:: shared_ptr\<templateDescriptor\> \>& templatedescriptors, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void ongettemplatesfailure (Konstante Std:: exception_ptr& Error, Konstante Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
public virtual void OnGetRightsForLabelIdSuccess (Konst Std:: shared_ptr\<Std:: Vector\<Std:: String\> \>& Rights, Konstante Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.
öffentliches virtuelles void-OnGetRightsForLabelIdFailure (konstant Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden
public virtual void onloadusercertsuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Benutzerzertifikat erfolgreich geladen wurde.
public virtual void onloadusercertfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Benutzerzertifikat geladen wurde.
public virtual void onregistercontentfortrackingandrevocationsuccess (Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung erfolgreich war.
öffentliches virtuelles void-onregistercontentfortrackingandrevocationfailure (Konstante Std:: exception_ptr& Error, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung fehlschlägt
public virtual void onrevokecontentsuccess (Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Sperrung von erfolgreich war.
public virtual void onrevokecontentfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn der Widerruf von Inhalten fehlschlägt.
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess-function"></a>Ongettemplatessuccess-Funktion
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templatedescriptors**: ein Verweis auf die Liste der Vorlagen Deskriptoren 


* **context**: Der gleiche Kontext, der an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md) übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: gettemplatesasync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: ongettemplatessuccess oder Schutz Module:: Observer:: ongettemplatesfailure weitergeleitet
  
### <a name="ongettemplatesfailure-function"></a>Ongettemplatesfailure-Funktion
Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.

Parameter:  
* **Fehler**: Fehler beim Abrufen von Vorlagen. 


* **context**: Der gleiche Kontext, der an ProtectionEngine::GetTemplatesAsync übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an ProtectionEngine::GetTemplatesAsync übergeben. Derselbe Kontext wird dann an ProtectionEngine::Observer::OnGetTemplatesSuccess oder ProtectionEngine::Observer::OnGetTemplatesFailure weitergeleitet.
  
### <a name="ongetrightsforlabelidsuccess-function"></a>OnGetRightsForLabelIdSuccess-Funktion
Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.

Parameter:  
* **rights**: eine Referenz zu der Liste mit abgerufenen Rechten 


* **context**: derselbe Kontext, der an "Schutz Modul [:: GetRightsForLabelIdAsync](class_mip_protectionengine.md)" übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: GetRightsForLabelIdAsync" übergeben, und derselbe Kontext wird unverändert an "schutzengine:: Observer:: OnGetRightsForLabelIdSuccess" oder "schutzengine:: Observer:: OnGetRightsForLabelIdFailure" weitergeleitet.
  
### <a name="ongetrightsforlabelidfailure-function"></a>OnGetRightsForLabelIdFailure-Funktion
Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden

Parameter:  
* **Fehler**: Fehler beim Abrufen der Rechte. 


* **context**: derselbe Kontext, der an ProtectionEngine::GetRightsForLabelIdAsync übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an ProtectionEngine::GetRightsForLabelIdAsync übergeben. Derselbe Kontext wird dann an ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess oder ProtectionEngine::Observer::OnGetRightsForLabelIdFailure weitergeleitet.
  
### <a name="onloadusercertsuccess-function"></a>Onloadusercertsuccess-Funktion
Wird aufgerufen, wenn das Benutzerzertifikat erfolgreich geladen wurde.

Parameter:  
* **context**: derselbe Kontext, der an "schutzengine:: loadusercert" übermittelt wurde.


Eine Anwendung kann eine beliebige Art von Kontext (z. b. Std::p romise, Std:: function) an [schutzengine:: loadusercertasync übergeben, und derselbe Kontext wird unverändert an Schutz- [Engine:: Observer:: onloadusercertsuccess](class_mip_protectionengine_observer.md) oder [schutzengine:: Observer:: onloadusercertfailure](class_mip_protectionengine_observer.md) weitergeleitet.
  
### <a name="onloadusercertfailure-function"></a>Onloadusercertfailure-Funktion
Wird aufgerufen, wenn das Benutzerzertifikat geladen wurde.

Parameter:  
* **Fehler**: Fehler beim Abrufen der Rechte. 


* **Kontext**: der gleiche Kontext, der an die Schutz-Engine:: loadusercert übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. Std::p romise, Std:: function) an schutzengine:: loadusercertasync übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onloadusercertsuccess oder Schutzmodule:: Observer:: onloadusercertfailure weitergeleitet.
  
### <a name="onregistercontentfortrackingandrevocationsuccess-function"></a>Onregistercontentfortrackingandrevocationsuccess-Funktion
Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung erfolgreich war.

Parameter:  
* **context**: derselbe Kontext, der an "Schutz Modul:: registercontentfortrackingandrevocationasync" übermittelt wurde.


Eine Anwendung kann beliebige Kontext Typen übergeben (z. b. Std::p romise, Std:: function) zu schutzengine:: registercontentfortrackingandrevocationasync, und derselbe Kontext wird unverändert an Schutz- [Engine:: Observer:: onregistercontentfortrackingandrevocationsuccess](class_mip_protectionengine_observer.md) oder [schutzengine:: Observer:: onregistercontentfortrackingandrevocationfailure](class_mip_protectionengine_observer.md) weitergeleitet.
  
### <a name="onregistercontentfortrackingandrevocationfailure-function"></a>Onregistercontentfortrackingandrevocationfailure-Funktion
Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung fehlschlägt

Parameter:  
* **Fehler**: Fehler beim Registrieren von Inhalt. 


* **Kontext**: derselbe Kontext, der an "Schutz Modul:: registercontentfortrackingandrevocationasync" übermittelt wurde.


Eine Anwendung kann beliebige Kontext Typen übergeben (z. b. Std::p romise, Std:: function) zu schutzengine:: registercontentfortrackingandrevocationasync, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onregistercontentfortrackingandrevocationsuccess oder schutzengine:: Observer:: onregistercontentfortrackingandrevocationfailure weitergeleitet.
  
### <a name="onrevokecontentsuccess-function"></a>Onrevokecontentsuccess-Funktion
Wird aufgerufen, wenn die Sperrung von erfolgreich war.

Parameter:  
* **context**: derselbe Kontext, der an "schutzengine:: revokecontentasync" übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: revokecontentasync" übergeben, und derselbe Kontext wird unverändert an Schutz- [Engine:: Observer:: onrevokecontentsuccess](class_mip_protectionengine_observer.md) oder [schutzengine:: Observer:: onrevokecontentfailure](class_mip_protectionengine_observer.md) weitergeleitet.
  
### <a name="onrevokecontentfailure-function"></a>Onrevokecontentfailure-Funktion
Wird aufgerufen, wenn der Widerruf von Inhalten fehlschlägt.

Parameter:  
* **Fehler**: Fehler beim widerrufen von Inhalt. 


* **Kontext**: derselbe Kontext, der an "Schutz Modul:: revokecontentasync" übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: revokecontentasync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onrevokecontentsuccess oder schutzengine:: Observer:: onrevokecontentfailure weitergeleitet.