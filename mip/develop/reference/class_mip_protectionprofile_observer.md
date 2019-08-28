---
title: mip::ProtectionProfile::Observer-Klasse
description: Dokumentiert die MIP::p rotectionprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: e7e260f879fb1e48b19d43f13a451a3a91ee1a39
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70057467"
---
# <a name="class-mipprotectionprofileobserver"></a>mip::ProtectionProfile::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md) empfängt.
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onloadsuccess (Konstante Std::\<shared_ptr Schutzprofile\>& Profile, Konst Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void onloadfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void onlistenginessuccess (Konstante Std::\<Vector Std:: String\>& engineids, Konst Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void onlistenginesfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.
public virtual void onaddenginesuccess (Konstante Std::\<shared_ptr schutzengine\>& Engine, Konstante Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void onaddenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.
public virtual void ondeleteenginesuccess (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void ondeleteenginefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess-function"></a>Onloadsuccess-Funktion
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **Profil**: Ein Verweis auf das neu erstellte Schutz [Profil](class_mip_protectionprofile.md)


* **Kontext**: Derselbe Kontext, der an " [Schutzprofile:: LoadAsync](class_mip_protectionprofile.md#addengineasync-function) " übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess-function) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure-function) weitergeleitet.
  
### <a name="onloadfailure-function"></a>Onloadfailure-Funktion
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **Fehler**: Beim Laden ist ein [Fehler](class_mip_error.md) aufgetreten. 


* **Kontext**: Derselbe Kontext, der an " [Schutzprofile:: LoadAsync](class_mip_protectionprofile.md#addengineasync-function) " übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z.B. „std::promise“ oder „std::function“) an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync-function) übergeben. Derselbe Kontext wird dann an [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess-function) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure-function) weitergeleitet.
  
### <a name="onlistenginessuccess-function"></a>Onlistenginessuccess-Funktion
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs 


* **Kontext**: Derselbe Kontext, der an " [Schutzprofile:: listenginesasync](class_mip_protectionprofile.md#listenginesasync-function) " übermittelt wurde.


  
### <a name="onlistenginesfailure-function"></a>Onlistenginesfailure-Funktion
Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.

Parameter:  
* **error**: Fehler, durch den das Auflisten der Engines fehlgeschlagen ist 


* **Kontext**: Derselbe Kontext, der an " [Schutzprofile:: listenginesasync](class_mip_protectionprofile.md#listenginesasync-function) " übermittelt wurde.


  
### <a name="onaddenginesuccess-function"></a>Onaddenginesuccess-Funktion
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.

Parameter:  
* \- **Engine**: Neu erstelltes Modul 


* **Kontext**: Derselbe Kontext, der an " [Schutzprofile:: addengineasync](class_mip_protectionprofile.md#addengineasync-function) " übermittelt wurde.


  
### <a name="onaddenginefailure-function"></a>Onaddenginefailure-Funktion
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: der Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **Kontext**: Derselbe Kontext, der an " [Schutzprofile:: addengineasync](class_mip_protectionprofile.md#addengineasync-function) " übermittelt wurde.


  
### <a name="ondeleteenginesuccess-function"></a>Ondeleteenginesuccess-Funktion
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **Kontext**: Derselbe Kontext, der an das Schutzprofil übermittelt wurde [::D eleteengineasync](class_mip_protectionprofile.md#deleteengineasync-function)


  
### <a name="ondeleteenginefailure-function"></a>Ondeleteenginefailure-Funktion
Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: Der Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **Kontext**: Derselbe Kontext, der an das Schutzprofil übermittelt wurde [::D eleteengineasync](class_mip_protectionprofile.md#deleteengineasync-function)

