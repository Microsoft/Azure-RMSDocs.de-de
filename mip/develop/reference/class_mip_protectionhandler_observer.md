---
title: mip::ProtectionHandler::Observer-Klasse
description: Dokumentiert die mip::protectionhandler-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: f6d71bc4f4c04ba305b59b4dcb3b5850f858716b
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60184449"
---
# <a name="class-mipprotectionhandlerobserver"></a>mip::ProtectionHandler::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionHandler](class_mip_protectionhandler.md) empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche virtuelle "void" OnCreateProtectionHandlerSuccess (const Std:: shared_ptr\<ProtectionHandler\>& ProtectionHandler, const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn [ProtectionHandler](class_mip_protectionhandler.md) erfolgreich erstellt wurde.
public virtual void OnCreateProtectionHandlerFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) nicht erfolgreich war.
  
## <a name="members"></a>Member
  
### <a name="oncreateprotectionhandlersuccess-function"></a>OnCreateProtectionHandlerSuccess-Funktion
Wird aufgerufen, wenn [ProtectionHandler](class_mip_protectionhandler.md) erfolgreich erstellt wurde.

Parameter:  
* **protectionHandler**: Die neu erstellte [ProtectionHandler](class_mip_protectionhandler.md)


* **context**: Der gleiche Kontext, der übergeben wurde [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function)


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function) übergeben, und der gleiche Kontext wird unverändert an „ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess“ oder „ProtectionEngine::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.
  
### <a name="oncreateprotectionhandlerfailure-function"></a>OnCreateProtectionHandlerFailure function
Wird aufgerufen, wenn die Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) nicht erfolgreich war.

Parameter:  
* **error**: Fehler, die während der Erstellung aufgetreten sind. 


* **context**: Der gleiche Kontext, der übergeben wurde [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function)


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“ oder „std::function“) an [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) oder [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function) übergeben, und der gleiche Kontext wird unverändert an „ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess“ oder „ProtectionEngine::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.