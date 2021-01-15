---
title: 'Class Protection Handler:: Observer'
description: 'Dokumentiert die schutzhandler:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: bd7a2b24b5eb80b3b17c025c43b0e0b31589a00a
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98214540"
---
# <a name="class-protectionhandlerobserver"></a>Class Protection Handler:: Observer 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionHandler empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnCreateProtectionHandlerSuccess(const std::shared_ptr\<ProtectionHandler\>& protectionHandler, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn ProtectionHandler erfolgreich erstellt wurde.
public virtual void OnCreateProtectionHandlerFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Erstellung von ProtectionHandler nicht erfolgreich war.
  
## <a name="members"></a>Member
  
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