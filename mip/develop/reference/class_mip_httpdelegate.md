---
title: class mip::HttpDelegate
description: 'Dokumentiert die MIP:: httpdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: e629e15ed3a4754123f8ca71adee04d32bc3785f
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77488108"
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