---
title: Klasse httpdelegat
description: 'Dokumentiert die httpdeleg:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 9240f0ed4eca43d7a6dcd5045c80f9724dc2a11b
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215254"
---
# <a name="class-httpdelegate"></a>Klasse httpdelegat 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr\<HttpOperation\> Send(const std::shared_ptr\<HttpRequest\>& request, const std::shared_ptr\<void\>& context)  |  Sendet die HTTP-Anforderung.
Public Std:: shared_ptr \<HttpOperation\> SendAsync (Konstante Std:: shared_ptr \<HttpRequest\>& Request, Konst Std:: shared_ptr \<void\>& context, Konstante Std:: Function \<void(std::shared_ptr\<HttpOperation\> )  |  HTTP-Anforderung asynchron senden.
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