---
title: mip::ProtectionEngine::Observer-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 688bc59b992e885b2b9724111c19f69f860badd9
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489672"
---
# <a name="class-mipprotectionengineobserver"></a>mip::ProtectionEngine::Observer-Klasse 
Eine Schnittstelle, die mit der Schutz-Engine verbundene Benachrichtigungen empfängt.
Diese Schnittstelle muss von Anwendungen mit dem Schutz-SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void ongettemplatessuccess (Konstante Std:: Vector\<Std:: shared_ptr\<templateDescriptor\>\>& templatedescriptors, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void ongettemplatesfailure (Konstante Std:: exception_ptr & Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
public virtual void OnGetRightsForLabelIdSuccess (Konst Std:: shared_ptr\<Std:: Vector\<Std:: String\>\>& Rechte, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.
öffentliches virtuelles void-OnGetRightsForLabelIdFailure (konstant Std:: exception_ptr & Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden
public virtual void onloadusercertsuccess (Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Benutzerzertifikat erfolgreich geladen wurde.
public virtual void onloadusercertfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn das Benutzerzertifikat geladen wurde.
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess-function"></a>Ongettemplatessuccess-Funktion
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templatedescriptors**: ein Verweis auf die Liste der Vorlagen Deskriptoren 


* **Kontext**: derselbe Kontext, der an "Schutz Modul:: gettemplatesasync" übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: gettemplatesasync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: ongettemplatessuccess oder schutzengine:: O weitergeleitet. bServer:: ongettemplatesfailure
  
### <a name="ongettemplatesfailure-function"></a>Ongettemplatesfailure-Funktion
Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.

Parameter:  
* **Fehler**: Fehler beim Abrufen von Vorlagen. 


* **Kontext**: derselbe Kontext, der an "Schutz Modul:: gettemplatesasync" übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: gettemplatesasync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: ongettemplatessuccess oder schutzengine:: O weitergeleitet. bServer:: ongettemplatesfailure
  
### <a name="ongetrightsforlabelidsuccess-function"></a>OnGetRightsForLabelIdSuccess-Funktion
Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.

Parameter:  
* **rights**: eine Referenz zu der Liste mit abgerufenen Rechten 


* **Kontext**: derselbe Kontext, der an die Schutz-Engine:: GetRightsForLabelIdAsync


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: GetRightsForLabelIdAsync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: OnGetRightsForLabelIdSuccess oder weitergeleitet. Schutz-Engine:: Observer:: OnGetRightsForLabelIdFailure
  
### <a name="ongetrightsforlabelidfailure-function"></a>OnGetRightsForLabelIdFailure-Funktion
Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden

Parameter:  
* **Fehler**: Fehler beim Abrufen der Rechte. 


* **Kontext**: derselbe Kontext, der an die Schutz-Engine:: GetRightsForLabelIdAsync


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. "Std::p romise, Std:: function)" an "schutzengine:: GetRightsForLabelIdAsync" übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: OnGetRightsForLabelIdSuccess oder weitergeleitet. Schutz-Engine:: Observer:: OnGetRightsForLabelIdFailure
  
### <a name="onloadusercertsuccess-function"></a>Onloadusercertsuccess-Funktion
Wird aufgerufen, wenn das Benutzerzertifikat erfolgreich geladen wurde.

Parameter:  
* **Kontext**: der gleiche Kontext, der an die Schutz-Engine:: loadusercert übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. Std::p romise, Std:: function) an schutzengine:: loadusercertasync übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onloadusercertsuccess oder schutzengine:: O weitergeleitet. bServer:: onloadusercertfailure
  
### <a name="onloadusercertfailure-function"></a>Onloadusercertfailure-Funktion
Wird aufgerufen, wenn das Benutzerzertifikat geladen wurde.

Parameter:  
* **Fehler**: Fehler beim Abrufen der Rechte. 


* **Kontext**: der gleiche Kontext, der an die Schutz-Engine:: loadusercert übermittelt wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. Std::p romise, Std:: function) an schutzengine:: loadusercertasync übergeben, und derselbe Kontext wird unverändert an Schutz-Engine:: Observer:: onloadusercertsuccess oder schutzengine:: O weitergeleitet. bServer:: onloadusercertfailure