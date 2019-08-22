---
title: class mip::HttpDelegate
description: 'Dokumentiert die MIP:: httpdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: d2b01c53b44d6884f47cf48c431ee7359f64b9c4
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885583"
---
# <a name="class-miphttpdelegate"></a>class mip::HttpDelegate 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<httpoperation\> Send (Konstante Std:: shared_ptr\<HttpRequest\>& Request, Konst Std:: shared_ptr\<void\>& context)  |  Sendet die HTTP-Anforderung.
Public Std:: shared_ptr\<httpoperation\> SendAsync (Konstante Std:: shared_ptr\<HttpRequest\>& Request, Konst Std:: shared_ptr\<void\>& context, Konstanten Std:: Function\<void (Std:: shared_ptr\<httpoperation\>)\>& callbackfn)  |  HTTP-Anforderung asynchron senden.
öffentliches void CancelOperation (Konstante Std:: String & RequestId)  |  Abbrechen eines bestimmten http-Vorgangs.
öffentliches void cancelalloperations ()  |  Abbrechen fortlaufender HTTP-Anforderungen.
  
## <a name="members"></a>Member
  
### <a name="send-function"></a>Send-Funktion
Sendet die HTTP-Anforderung.

Parameter:  
* **Anforderung**: HTTP-Anforderung 


* **Kontext**: Der gleiche nicht transparente Client Kontext, der an die API übermittelt wurde, die zu dieser HTTP-Anforderung geführt hat.



  
**Gibt Folgendes zurück**: HTTP-Vorgangs Container
  
### <a name="sendasync-function"></a>SendAsync-Funktion
HTTP-Anforderung asynchron senden.

Parameter:  
* **Anforderung**: HTTP-Anforderung 


* **Kontext**: Der gleiche nicht transparente Client Kontext, der an die API übermittelt wurde, die zu dieser HTTP-Anforderung geführt hat. 


* **callbackFn**: Funktion, die nach Abschluss ausgeführt wird



  
**Gibt Folgendes zurück**: HTTP-Vorgangs Container
  
### <a name="canceloperation-function"></a>CancelOperation-Funktion
Abbrechen eines bestimmten http-Vorgangs.

Parameter:  
* **requestId**: ID der abzubrechenden Anforderung


  
### <a name="cancelalloperations-function"></a>Cancelalloperations-Funktion
Abbrechen fortlaufender HTTP-Anforderungen.