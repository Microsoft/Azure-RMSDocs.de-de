---
title: mip::ProtectionProfile::Observer-Klasse
description: Dokumentiert die MIP::p rotectionprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: a9138e497655dfa939a9ac9b15d7ed228331e9e0
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560700"
---
# <a name="class-mipprotectionprofileobserver"></a>mip::ProtectionProfile::Observer-Klasse 
Eine Schnittstelle, die mit dem Schutzprofil verbundene Benachrichtigungen empfängt.
Diese Schnittstelle muss von Anwendungen mit dem Schutz-SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onloadsuccess (Konstante Std:: shared_ptr\<Schutzprofile\>& Profile, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void onloadfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void onlistenginessuccess (Konstante Std:: Vector\<Std:: String\>& engineids, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void onlistenginesfailure (konstant Std:: exception_ptr & Error, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.
public virtual void onaddenginesuccess (Konstante Std:: shared_ptr\<schutzengine\>& Engine, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void onaddenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.
public virtual void ondeleteenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void ondeleteenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess-function"></a>Onloadsuccess-Funktion
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: ein Verweis auf das neu erstellte Schutzprofil


* **context**: Der gleiche Kontext, der an „ProtectionProfile::LoadAsync“ übergeben wurde.


Eine Anwendung kann beliebige Kontext Typen (z. b. Std::p romise, Std:: function) an Schutzprofile:: LoadAsync übergeben, und derselbe Kontext wird unverändert an Schutz profile:: Observer:: onloadsuccess oder schützprofile:: Observer:: O weitergeleitet. nloadfailure
  
### <a name="onloadfailure-function"></a>Onloadfailure-Funktion
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **Fehler**: Fehler beim Laden. 


* **context**: Der gleiche Kontext, der an „ProtectionProfile::LoadAsync“ übergeben wurde.


Eine Anwendung kann beliebige Kontext Typen (z. b. Std::p romise, Std:: function) an Schutzprofile:: LoadAsync übergeben, und derselbe Kontext wird unverändert an Schutz profile:: Observer:: onloadsuccess oder schützprofile:: Observer:: O weitergeleitet. nloadfailure
  
### <a name="onlistenginessuccess-function"></a>Onlistenginessuccess-Funktion
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs 


* **Kontext**: derselbe Kontext, der an "schützprofile:: listenginesasync" übermittelt wurde.


  
### <a name="onlistenginesfailure-function"></a>Onlistenginesfailure-Funktion
Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.

Parameter:  
* **error**: Fehler, durch den das Auflisten der Engines fehlgeschlagen ist 


* **Kontext**: derselbe Kontext, der an "schützprofile:: listenginesasync" übermittelt wurde.


  
### <a name="onaddenginesuccess-function"></a>Onaddenginesuccess-Funktion
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.

Parameter:  
* **engine**: neu erstellte Engine 


* **Kontext**: derselbe Kontext, der an "Schutzprofile:: addengineasync" übermittelt wurde.


  
### <a name="onaddenginefailure-function"></a>Onaddenginefailure-Funktion
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: der Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **Kontext**: derselbe Kontext, der an "Schutzprofile:: addengineasync" übermittelt wurde.


  
### <a name="ondeleteenginesuccess-function"></a>Ondeleteenginesuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **context**: derselbe Kontext, der an das Schutzprofil übermittelt wurde::D eleteengineasync


  
### <a name="ondeleteenginefailure-function"></a>Ondeleteenginefailure-Funktion
Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: Der Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **context**: derselbe Kontext, der an das Schutzprofil übermittelt wurde::D eleteengineasync

