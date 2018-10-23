---
title: Microsoft Information Protection-Klasse „HttpDelegate“
description: Referenz für die Microsoft Information Protection-Klasse „HttpDelegate“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3e55f9aff5a9ebd97731ec21e408a33f22905648
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445369"
---
# <a name="class-miphttpdelegate"></a>class mip::HttpDelegate 
Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr<HttpResponse> Send(const std::shared_ptr<HttpRequest>& request, const std::shared_ptr<void>& context)  |  Sendet die HTTP-Anforderung.
  
## <a name="members"></a>Member
  
### <a name="httpresponse"></a>HttpResponse
Sendet die HTTP-Anforderung.

Parameter:  
* **request**: Die HTTP-Anforderung. 


* **context**: Der gleiche nicht transparente Clientkontext, der an die API übergeben wurde und zu dieser HTTP-Anforderung geführt habt.



  
**Rückgabe**: Die HTTP-Antwort.