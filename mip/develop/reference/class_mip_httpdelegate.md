---
title: class mip::HttpDelegate
description: Dokumentiert die mip::httpdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 18425a807fcddc1bc1db19a35534036a6552255c
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57329844"
---
# <a name="class-miphttpdelegate"></a>class mip::HttpDelegate 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<HttpResponse\> senden (const Std:: shared_ptr\<HttpRequest\>& Anforderung, const Std:: shared_ptr\<"void"\>& Kontext)  |  Sendet die HTTP-Anforderung.
public void SendAsync(const std::shared_ptr\<HttpRequest\>& request, const std::shared_ptr\<void\>& context, const std::function\<void(std::shared_ptr\<HttpResponse\>)\>& fnCallback)  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="send-function"></a>Send-Funktion
Sendet die HTTP-Anforderung.

Parameter:  
* **request**: HTTP-Anforderung 


* **context**: Der gleiche-nicht transparent-Clientkontext, der an die API übergeben wurde, die diese HTTP-Anforderung geführt haben



  
**Gibt**: HTTP-Antwort
  
### <a name="sendasync-function"></a>SendAsync-Funktion
_Noch nicht dokumentiert._
