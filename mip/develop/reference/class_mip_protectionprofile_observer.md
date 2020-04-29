---
title: 'Class Protection profile:: Observer'
description: 'Dokumentiert die Schutzprofile:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 8448f75a06bfe99debcf4c1c40ab2228c46690e6
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763928"
---
# <a name="class-protectionprofileobserver"></a>Class Protection profile:: Observer 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionProfile empfängt.
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onloadsuccess (Konstante Std::\<shared_ptr Schutzprofile\>& Profile, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void onloadfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void onlistenginessuccess (Konstante Std::\<Vector Std:: String\>& engineids, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void onlistenginesfailure (konstant Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.
public virtual void onaddenginesuccess (Konstante Std::\<shared_ptr schutzengine\>& Engine, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
öffentliches virtuelles void-onaddenginefailure (Konstante Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.
öffentliches virtuelles void ondeleteenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void ondeleteenginefailure (konstant Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess-function"></a>Onloadsuccess-Funktion
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Ein Verweis auf das neu erstellte ProtectionProfile


* **context**: derselbe Kontext, der an "Schutzprofile:: LoadAsync" übermittelt wurde.


Eine Anwendung kann einen beliebigen Typ von Kontext (z. b. Std::p romise, Std:: function) an Schutzprofile:: LoadAsync übergeben, und derselbe Kontext wird unverändert an Protection profile:: Observer:: onloadsuccess oder schützprofile:: Observer:: onloadfailure weitergeleitet.
  
### <a name="onloadfailure-function"></a>Onloadfailure-Funktion
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **Fehler**: Fehler beim Laden. 


* **context**: Der gleiche Kontext, der an ProtectionProfile::LoadAsync übergeben wurde


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an ProtectionProfile::LoadAsync übergeben. Derselbe Kontext wird dann an ProtectionProfile::Observer::OnLoadSuccess oder ProtectionProfile::Observer::OnLoadFailure weitergeleitet.
  
### <a name="onlistenginessuccess-function"></a>Onlistenginessuccess-Funktion
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs 


* **context**: derselbe Kontext, der an [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md) übergeben wurde


  
### <a name="onlistenginesfailure-function"></a>Onlistenginesfailure-Funktion
Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.

Parameter:  
* **error**: Fehler, durch den das Auflisten der Engines fehlgeschlagen ist 


* **context**: derselbe Kontext, der an ProtectionProfile::ListEnginesAsync übergeben wurde


  
### <a name="onaddenginesuccess-function"></a>Onaddenginesuccess-Funktion
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.

Parameter:  
* **engine**: neu erstellte Engine 


* **context**: derselbe Kontext, der an [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md) übergeben wurde


  
### <a name="onaddenginefailure-function"></a>Onaddenginefailure-Funktion
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: der Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **context**: derselbe Kontext, der an ProtectionProfile::AddEngineAsync übergeben wurde


  
### <a name="ondeleteenginesuccess-function"></a>Ondeleteenginesuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **context**: derselbe Kontext, der an [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md) übergeben wurde


  
### <a name="ondeleteenginefailure-function"></a>Ondeleteenginefailure-Funktion
Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: Der Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **context**: derselbe Kontext, der an ProtectionProfile::DeleteEngineAsync übergeben wurde

