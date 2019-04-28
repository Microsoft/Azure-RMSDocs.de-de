---
title: class mip::HttpDelegate
description: Dokumentiert die mip::httpdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6dedd5e52b0599a58acabd85f7bd076169b3758e
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60174050"
---
# <a name="class-miphttpdelegate"></a>class mip::HttpDelegate 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<HttpOperation\> senden (const Std:: shared_ptr\<HttpRequest\>& Anforderung, const Std:: shared_ptr\<"void"\>& Kontext)  |  Sendet die HTTP-Anforderung.
Public Std:: shared_ptr\<HttpOperation\> SendAsync (const Std:: shared_ptr\<HttpRequest\>& Anforderung, const Std:: shared_ptr\<"void"\>& Kontext, const std:: Funktion\<"void" (Std:: shared_ptr\<HttpOperation\>)\>& Listenwerts)  |  Senden Sie HTTP-Anforderung asynchron.
Öffentliche void CancelOperation (const Std:: String & Anforderungs-ID)  |  Abbrechen eines bestimmten HTTP-Vorgangs an.
Öffentliche void CancelAllOperations()  |  Brechen Sie laufende HTTP-Anforderungen.
  
## <a name="members"></a>Member
  
### <a name="send-function"></a>Send-Funktion
Sendet die HTTP-Anforderung.

Parameter:  
* **request**: HTTP-Anforderung 


* **context**: Der gleiche-nicht transparent-Clientkontext, der an die API übergeben wurde, die diese HTTP-Anforderung geführt haben



  
**Gibt**: HTTP-Vorgang-container
  
### <a name="sendasync-function"></a>SendAsync-Funktion
Senden Sie HTTP-Anforderung asynchron.

Parameter:  
* **request**: HTTP-Anforderung 


* **context**: Der gleiche-nicht transparent-Clientkontext, der an die API übergeben wurde, die diese HTTP-Anforderung geführt haben 


* **callbackFn**: Funktion, die nach Abschluss ausgeführt wird



  
**Gibt**: HTTP-Vorgang-container
  
### <a name="canceloperation-function"></a>CancelOperation-Funktion
Abbrechen eines bestimmten HTTP-Vorgangs an.

Parameter:  
* **requestId**: ID der Anforderung zum Abbrechen


  
### <a name="cancelalloperations-function"></a>CancelAllOperations-Funktion
Brechen Sie laufende HTTP-Anforderungen.