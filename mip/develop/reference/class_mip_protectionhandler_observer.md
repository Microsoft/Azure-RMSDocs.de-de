---
title: 'Class Protection Handler:: Observer'
description: 'Dokumentiert die schutzhandler:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 092448f4af5c27625b8a19f7cfea039e9bcd8071
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567139"
---
# <a name="class-protectionhandlerobserver"></a>Class Protection Handler:: Observer 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionHandler empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnCreateProtectionHandlerSuccess(const std::shared_ptr\<ProtectionHandler\>& protectionHandler, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn ProtectionHandler erfolgreich erstellt wurde.
public virtual void OnCreateProtectionHandlerFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Erstellung von ProtectionHandler nicht erfolgreich war.
  
## <a name="members"></a>Members
  
### <a name="oncreateprotectionhandlersuccess-function"></a>Onkreateschutzhandlersuccess-Funktion
Wird aufgerufen, wenn ProtectionHandler erfolgreich erstellt wurde.

Parameter:  
* **protectionHandler**: Die neu erstellte ProtectionHandler-Instanz.


* **context**: Der gleiche Kontext, der an ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync oder ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“ oder „std::function“) an ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync oder ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync übergeben, und der gleiche Kontext wird unverändert an „ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess“ oder „ProtectionEngine::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.
  
### <a name="oncreateprotectionhandlerfailure-function"></a>Onkreateschutzhandlerfailure-Funktion
Wird aufgerufen, wenn die Erstellung von ProtectionHandler nicht erfolgreich war.

Parameter:  
* **Fehler**: Beim Erstellen aufgetretener Fehler. 


* **context**: Der gleiche Kontext, der an ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync oder ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“ oder „std::function“) an ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync oder ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync übergeben, und der gleiche Kontext wird unverändert an „ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess“ oder „ProtectionEngine::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.