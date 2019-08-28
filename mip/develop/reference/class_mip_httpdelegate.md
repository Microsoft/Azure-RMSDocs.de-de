---
title: class mip::HttpDelegate
description: 'Dokumentiert die MIP:: httpdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: f5f5bc13f3c01e40b0034d4fae1bd698da8426c5
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054881"
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