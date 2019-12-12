---
title: mip::ProtectionEngine::Observer-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: e5196535dc474d2649c084b55c55a80c3af349b9
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73560762"
---
# <a name="class-mipprotectionengineobserver"></a>mip::ProtectionEngine::Observer-Klasse 
Eine Schnittstelle, die mit der Schutz-Engine verbundene Benachrichtigungen empfängt.
Diese Schnittstelle muss von Anwendungen mit dem Schutz-SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void ongettemplatessuccess (Konstante Std:: shared_ptr\<Std:: Vector\<Std:: String\>\>& templateids, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void ongettemplatesfailure (Konstante Std:: exception_ptr & Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
public virtual void OnGetRightsForLabelIdSuccess (Konst Std:: shared_ptr\<Std:: Vector\<Std:: String\>\>& Rechte, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Rechte erfolgreich abgerufen wurden.
öffentliches virtuelles void-OnGetRightsForLabelIdFailure (konstant Std:: exception_ptr & Fehler, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Rechte für eine Bezeichnungs-ID für den Benutzer abgerufen werden
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess-function"></a>Ongettemplatessuccess-Funktion
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templateIds**: Verweis auf die Liste der abzurufenden Vorlagen 


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