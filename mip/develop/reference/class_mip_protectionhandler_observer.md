---
title: 'Class Protection Handler:: Observer'
description: 'Dokumentiert die schutzhandler:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 66453d343505cc57427e177eac258b83a2663eb0
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764441"
---
# <a name="class-protectionhandlerobserver"></a>Class Protection Handler:: Observer 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionHandler empfängt
Diese Schnittstelle muss von Anwendungen mit dem Protection SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onkreateschutzhandlersuccess (Konstante Std::\<shared_ptr schutzhandler\>& schutzhandler, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn ProtectionHandler erfolgreich erstellt wurde.
public virtual void onkreateschutzhandlerfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Erstellung von ProtectionHandler nicht erfolgreich war.
  
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