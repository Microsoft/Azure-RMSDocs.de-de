---
title: mip::ProtectionHandler::Observer-Klasse
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 0e1a1d039928e1244d6c279fe055330eac7f9577
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69883405"
---
# <a name="class-mipprotectionhandlerobserver"></a>mip::ProtectionHandler::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionHandler](class_mip_protectionhandler.md) empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onkreateschutzhandlersuccess (Konstante Std::\<shared_ptr schutzhandler\>& schutzhandler, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn [ProtectionHandler](class_mip_protectionhandler.md) erfolgreich erstellt wurde.
public virtual void onkreateschutzhandlerfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) nicht erfolgreich war.
  
## <a name="members"></a>Member
  
### <a name="oncreateprotectionhandlersuccess-function"></a>Onkreateschutzhandlersuccess-Funktion
Wird aufgerufen, wenn [ProtectionHandler](class_mip_protectionhandler.md) erfolgreich erstellt wurde.

Parameter:  
* **protectionHandler**: Der neu erstellte Schutz [Handler](class_mip_protectionhandler.md) .


* **Kontext**: Der gleiche Kontext, der an die Schutz- [Engine:: deateschutzhandlerfromdescriptor Async](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder schutzengine [:: kreateschutzhandlerfrompublishinglicencasync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function) übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function) übergeben, und der gleiche Kontext wird unverändert an „ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess“ oder „ProtectionEngine::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.
  
### <a name="oncreateprotectionhandlerfailure-function"></a>Onkreateschutzhandlerfailure-Funktion
Wird aufgerufen, wenn die Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) nicht erfolgreich war.

Parameter:  
* **Fehler**: Fehler, der während der Erstellung aufgetreten ist 


* **Kontext**: Der gleiche Kontext, der an die Schutz- [Engine:: deateschutzhandlerfromdescriptor Async](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder schutzengine [:: kreateschutzhandlerfrompublishinglicencasync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function) übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function) übergeben, und der gleiche Kontext wird unverändert an „ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess“ oder „ProtectionEngine::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.