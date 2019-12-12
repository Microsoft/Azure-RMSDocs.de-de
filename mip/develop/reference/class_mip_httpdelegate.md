---
title: class mip::HttpDelegate
description: 'Dokumentiert die MIP:: httpdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: a29673c71aaa0357ebb52bc4cab3b3fef74a21d1
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73560202"
---
# <a name="class-miphttpdelegate"></a>class mip::HttpDelegate 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<httpoperation\> Send (Konstanten Std:: shared_ptr\<HttpRequest\>& Request, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Sendet die HTTP-Anforderung.
Public Std:: shared_ptr\<httpoperation\> SendAsync (Konstante Std:: shared_ptr\<HttpRequest\>& Request, Konstanten Std:: shared_ptr\<void\>& context, Konstanten Std:: function\<void (Std:: shared_ptr\<httpoperation\>)  |  HTTP-Anforderung asynchron senden.
öffentliches void CancelOperation (Konstante Std:: String & RequestId)  |  Abbrechen eines bestimmten http-Vorgangs.
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