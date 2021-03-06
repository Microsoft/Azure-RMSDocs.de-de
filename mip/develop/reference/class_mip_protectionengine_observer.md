---
title: 'Class schutzengine:: Observer'
description: 'Dokumentiert die schutzengine:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: b9243a1b7d9addaceaec907a368f7e651c99fbd5
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98214625"
---
# <a name="class-protectionengineobserver"></a>Class schutzengine:: Observer 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionEngine empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void ongettemplatessuccess (Konstante Std:: Vector \<std::shared_ptr\<TemplateDescriptor\> \>& templatedescriptors, Konstanten Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void OnGetTemplatesFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
public virtual void OnGetRightsForLabelIdSuccess (Konstante Std:: shared_ptr \<std::vector\<std::string\> \>& Rechte, Konstante Std:: shared_ptr \<void\>& Kontext)  |  Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.
public virtual void OnGetRightsForLabelIdFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden
public virtual void onloadusercertsuccess (Konstante Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn das Benutzerzertifikat erfolgreich geladen wurde.
public virtual void onloadusercertfailure (konstant Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr \<void\>& Kontext)  |  Wird aufgerufen, wenn das Benutzerzertifikat geladen wurde.
öffentliches virtuelles void-onregistercontentfortrackingandrevocationsuccess (Konstanten Std:: shared_ptr \<void\>&-Kontext)  |  Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung erfolgreich war.
public virtual void onregistercontentfortrackingandrevocationfailure (Konstante Std:: exception_ptr& Error, Konstante Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung fehlschlägt
öffentliches virtuelles void-onrevokecontentsuccess (Konstante Std:: shared_ptr \<void\>&-Kontext)  |  Wird aufgerufen, wenn die Sperrung von erfolgreich war.
public virtual void onrevokecontentfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn der Widerruf von Inhalten fehlschlägt.
public virtual void onkreatedelegatedlicensessuccess (Std:: Vector \<std::shared_ptr\<DelegationLicense\> \> delegatedlicenses, Konst Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn die CREATE Delegierte License erfolgreich ist.
public virtual void onkreatedelegatedlicensesfailure (konstant Std:: exception_ptr& Error, Konstante Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn die CREATE Delegierte License fehlschlägt.
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess-function"></a>Ongettemplatessuccess-Funktion
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templatedescriptors**: ein Verweis auf die Liste der Vorlagen Deskriptoren 


* **context**: Der gleiche Kontext, der an ProtectionEngine::GetTemplatesAsync übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an ProtectionEngine::GetTemplatesAsync übergeben. Derselbe Kontext wird dann an ProtectionEngine::Observer::OnGetTemplatesSuccess oder ProtectionEngine::Observer::OnGetTemplatesFailure weitergeleitet.
  
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


* **context**: derselbe Kontext, der an ProtectionEngine::GetRightsForLabelIdAsync übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an ProtectionEngine::GetRightsForLabelIdAsync übergeben. Derselbe Kontext wird dann an ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess oder ProtectionEngine::Observer::OnGetRightsForLabelIdFailure weitergeleitet.
  
### <a name="ongetrightsforlabelidfailure-function"></a>OnGetRightsForLabelIdFailure-Funktion
Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden

Parameter:  
* **Fehler**: Fehler beim Abrufen der Rechte. 


* **context**: derselbe Kontext, der an ProtectionEngine::GetRightsForLabelIdAsync übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an ProtectionEngine::GetRightsForLabelIdAsync übergeben. Derselbe Kontext wird dann an ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess oder ProtectionEngine::Observer::OnGetRightsForLabelIdFailure weitergeleitet.
  
### <a name="onloadusercertsuccess-function"></a>Onloadusercertsuccess-Funktion
Wird aufgerufen, wenn das Benutzerzertifikat erfolgreich geladen wurde.

Parameter:  
* **Kontext**: der gleiche Kontext, der an die Schutz-Engine:: loadusercert übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. Std::p romise, Std:: function) an schutzengine:: loadusercertasync übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onloadusercertsuccess oder Schutzmodule:: Observer:: onloadusercertfailure weitergeleitet.
  
### <a name="onloadusercertfailure-function"></a>Onloadusercertfailure-Funktion
Wird aufgerufen, wenn das Benutzerzertifikat geladen wurde.

Parameter:  
* **Fehler**: Fehler beim Abrufen der Rechte. 


* **Kontext**: der gleiche Kontext, der an die Schutz-Engine:: loadusercert übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. Std::p romise, Std:: function) an schutzengine:: loadusercertasync übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onloadusercertsuccess oder Schutzmodule:: Observer:: onloadusercertfailure weitergeleitet.
  
### <a name="onregistercontentfortrackingandrevocationsuccess-function"></a>Onregistercontentfortrackingandrevocationsuccess-Funktion
Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung erfolgreich war.

Parameter:  
* **Kontext**: derselbe Kontext, der an "Schutz Modul:: registercontentfortrackingandrevocationasync" übermittelt wurde.


Eine Anwendung kann beliebige Kontext Typen übergeben (z. b. Std::p romise, Std:: function) zu schutzengine:: registercontentfortrackingandrevocationasync, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onregistercontentfortrackingandrevocationsuccess oder schutzengine:: Observer:: onregistercontentfortrackingandrevocationfailure weitergeleitet.
  
### <a name="onregistercontentfortrackingandrevocationfailure-function"></a>Onregistercontentfortrackingandrevocationfailure-Funktion
Wird aufgerufen, wenn die Registrierung von Inhalten für die Nachverfolgung & Sperrung fehlschlägt

Parameter:  
* **Fehler**: Fehler beim Registrieren von Inhalt. 


* **Kontext**: derselbe Kontext, der an "Schutz Modul:: registercontentfortrackingandrevocationasync" übermittelt wurde.


Eine Anwendung kann beliebige Kontext Typen übergeben (z. b. Std::p romise, Std:: function) zu schutzengine:: registercontentfortrackingandrevocationasync, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onregistercontentfortrackingandrevocationsuccess oder schutzengine:: Observer:: onregistercontentfortrackingandrevocationfailure weitergeleitet.
  
### <a name="onrevokecontentsuccess-function"></a>Onrevokecontentsuccess-Funktion
Wird aufgerufen, wenn die Sperrung von erfolgreich war.

Parameter:  
* **Kontext**: derselbe Kontext, der an "Schutz Modul:: revokecontentasync" übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: revokecontentasync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onrevokecontentsuccess oder schutzengine:: Observer:: onrevokecontentfailure weitergeleitet.
  
### <a name="onrevokecontentfailure-function"></a>Onrevokecontentfailure-Funktion
Wird aufgerufen, wenn der Widerruf von Inhalten fehlschlägt.

Parameter:  
* **Fehler**: Fehler beim widerrufen von Inhalt. 


* **Kontext**: derselbe Kontext, der an "Schutz Modul:: revokecontentasync" übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: revokecontentasync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onrevokecontentsuccess oder schutzengine:: Observer:: onrevokecontentfailure weitergeleitet.
  
### <a name="oncreatedelegatedlicensessuccess-function"></a>Onkreatedelegatedlicensessuccess-Funktion
Wird aufgerufen, wenn die CREATE Delegierte License erfolgreich ist.

Parameter:  
* **context**: derselbe Kontext, der an "Schutz Modul:: deatedelegationlicensesasync" übergeben wurde.


Eine Anwendung kann beliebige Kontext Typen übergeben (z. b. Std::p romise, Std:: function) zu schutzengine:: builddelegationlicensesasync, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onkreatedelegatedlicensessuccess oder schutzengine:: Observer:: onkreatedelegatedlicensesfailure weitergeleitet.
  
### <a name="oncreatedelegatedlicensesfailure-function"></a>Onkreatedelegatedlicensesfailure-Funktion
Wird aufgerufen, wenn die CREATE Delegierte License fehlschlägt.

Parameter:  
* **Fehler**: aufgetretene Fehler 


* **Kontext**: derselbe Kontext, der an "Schutz Modul:: deatedelegationlicensesasync" übergeben wurde.


Eine Anwendung kann beliebige Kontext Typen übergeben (z. b. Std::p romise, Std:: function) zu schutzengine:: builddelegationlicensesasync, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onkreatedelegatedlicensessuccess oder schutzengine:: Observer:: onkreatedelegatedlicensesfailure weitergeleitet.