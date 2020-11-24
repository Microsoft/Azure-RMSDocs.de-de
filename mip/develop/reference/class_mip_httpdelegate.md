---
title: Klasse httpdelegat
description: 'Dokumentiert die httpdeleg:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: d52752538aae982f8f5b0138aaf26deefa0d98a3
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566887"
---
# <a name="class-httpdelegate"></a>Klasse httpdelegat 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr\<HttpOperation\> Send(const std::shared_ptr\<HttpRequest\>& request, const std::shared_ptr\<void\>& context)  |  Sendet die HTTP-Anforderung.
Public Std:: shared_ptr \<HttpOperation\> SendAsync (Konstante Std:: shared_ptr \<HttpRequest\>& Request, Konst Std:: shared_ptr \<void\>& context, Konstante Std:: Function \<void(std::shared_ptr\<HttpOperation\> )  |  HTTP-Anforderung asynchron senden.
öffentliches void CancelOperation (Konstante Std:: String& RequestId)  |  Abbrechen eines bestimmten http-Vorgangs.
öffentliches void cancelalloperations ()  |  Abbrechen fortlaufender HTTP-Anforderungen.
  
## <a name="members"></a>Members
  
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