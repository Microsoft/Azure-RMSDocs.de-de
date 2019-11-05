---
title: mip::ProtectionHandler::Observer-Klasse
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 8b48d6e5aacacb6f678fc7d5aea2aee531da88fa
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560087"
---
# <a name="class-mipprotectionhandlerobserver"></a>mip::ProtectionHandler::Observer-Klasse 
Eine Schnittstelle, die Benachrichtigungen zum Schutz Handler empfängt.
Diese Schnittstelle muss von Anwendungen mit dem Schutz-SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onkreateschutzhandlersuccess (Konstante Std:: shared_ptr\<schutzhandler\>& schutzhandler, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn der Schutz Handler erfolgreich erstellt wurde.
public virtual void onkreateschutzhandlerfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die schützerstellung fehlgeschlagen ist.
  
## <a name="members"></a>Member
  
### <a name="oncreateprotectionhandlersuccess-function"></a>Onkreateschutzhandlersuccess-Funktion
Wird aufgerufen, wenn der Schutz Handler erfolgreich erstellt wurde.

Parameter:  
* Schutz **Handler**: der neu erstellte Schutz Handler


* **context**: derselbe Kontext, der an "Schutz Modul:: deateschutzhandlerfromdescriptor Async" oder "schutzengine:: deateschutzhandlerfrompublishinglicencasync" übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. Std::p romise, Std:: function) an "schutzengine:: deateschutzhandlerfromdescriptorasync" oder "schutzengine:: kreateschutzhandlerfrompublishinglicenseasync" und denselben Kontext übergeben. wird unverändert an Schutz-Engine:: Observer:: onkreateschutzhandlersuccess oder schutzengine:: Observer:: onkreateschutzhandlerfailure weitergeleitet.
  
### <a name="oncreateprotectionhandlerfailure-function"></a>Onkreateschutzhandlerfailure-Funktion
Wird aufgerufen, wenn die schützerstellung fehlgeschlagen ist.

Parameter:  
* **Fehler**: Beim Erstellen aufgetretener Fehler. 


* **context**: derselbe Kontext, der an "Schutz Modul:: deateschutzhandlerfromdescriptor Async" oder "schutzengine:: deateschutzhandlerfrompublishinglicencasync" übergeben wurde.


Eine Anwendung kann einen beliebigen Kontexttyp (z. b. Std::p romise, Std:: function) an "schutzengine:: deateschutzhandlerfromdescriptorasync" oder "schutzengine:: kreateschutzhandlerfrompublishinglicenseasync" und denselben Kontext übergeben. wird unverändert an Schutz-Engine:: Observer:: onkreateschutzhandlersuccess oder schutzengine:: Observer:: onkreateschutzhandlerfailure weitergeleitet.