---
title: Klasse httpdelegat
description: 'Dokumentiert die httpdeleg:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: e1ddc8595e3cba2172228532a84ca68883cc0afd
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81762826"
---
# <a name="class-httpdelegate"></a>Klasse httpdelegat 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<httpoperation\> Send (Konstanten Std::\<shared_ptr HttpRequest\>& Request, Konstanten Std:: shared_ptr\<void\>& context)  |  Sendet die HTTP-Anforderung.
Public Std:: shared_ptr\<httpoperation\> \<SendAsync (Konstante Std:: shared_ptr HttpRequest\>& Request, Konst Std:: shared_ptr\<void\>& context, Konstanten Std:: Function\<void (Std:: shared_ptr\<httpoperation)\>  |  HTTP-Anforderung asynchron senden.
öffentliches void CancelOperation (Konstante Std:: String& RequestId)  |  Abbrechen eines bestimmten http-Vorgangs.
öffentliches void cancelalloperations ()  |  Abbrechen fortlaufender HTTP-Anforderungen.
  
## <a name="members"></a>Member
  
### <a name="send-function"></a>Send-Funktion
Sendet die HTTP-Anforderung.

Parameter:  
* **request**: Die HTTP-Anforderung. 


* **context**: Der gleiche nicht transparente Clientkontext, der an die API übergeben wurde und zu dieser HTTP-Anforderung geführt habt.



  
**Gibt Folgendes zurück**: http-Vorgangs Container
  
### <a name="sendasync-function"></a>SendAsync-Funktion
HTTP-Anforderung asynchron senden.

Parameter:  
* **request**: Die HTTP-Anforderung. 


* **context**: Der gleiche nicht transparente Clientkontext, der an die API übergeben wurde und zu dieser HTTP-Anforderung geführt habt. 


* **callbackfn**: Funktion, die nach Abschluss der Ausführung ausgeführt wird



  
**Gibt Folgendes zurück**: http-Vorgangs Container
  
### <a name="canceloperation-function"></a>CancelOperation-Funktion
Abbrechen eines bestimmten http-Vorgangs.

Parameter:  
* **RequestId**: ID der abzubrechenden Anforderung


  
### <a name="cancelalloperations-function"></a>Cancelalloperations-Funktion
Abbrechen fortlaufender HTTP-Anforderungen.