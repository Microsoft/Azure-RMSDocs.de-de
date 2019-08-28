---
title: mip::ProtectionHandler::Observer-Klasse
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: a02e84a7be2071340a0ffef6310788823b768de3
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70057554"
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