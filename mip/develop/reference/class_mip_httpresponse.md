---
title: Microsoft Information Protection-Klasse „HttpResponse“
description: Referenz für die Microsoft Information Protection-Klasse „HttpResponse“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a19ea78b048cafe94501d452bb9c7409237f6ffd
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445353"
---
# <a name="class-miphttpresponse"></a>class mip::HttpResponse 
Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben von [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public int32_t GetStatusCode() const  |  Ruft den Antwortstatuscode ab.
 public const std::string& GetBody() const  |  Ruft den Text der Anforderung ab.
public const std::map<std::string, std::string, CaseInsensitiveComparator>& GetHeaders() const  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="getstatuscode"></a>GetStatusCode
Ruft den Antwortstatuscode ab.

  
**Rückgabe**: Der Statuscode.
  
### <a name="getbody"></a>GetBody
Ruft den Text der Anforderung ab.

  
**Rückgabe**: Der Anforderungstext.
  
### <a name="getheaders"></a>GetHeaders
Ruft Anforderungsheader ab.

  
**Rückgabe**: Anforderungsheader.