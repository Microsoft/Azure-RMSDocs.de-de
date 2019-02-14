---
title: class mip::HttpDelegate
description: Dokumentiert die mip::httpdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 8dd81508766c65d6232c278d56f3720a98aaa9eb
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256293"
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
