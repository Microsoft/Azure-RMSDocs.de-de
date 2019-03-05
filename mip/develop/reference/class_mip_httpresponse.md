---
title: class mip::HttpResponse
description: Dokumentiert die mip::httpresponse-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: f7b16658135e802776cde37fdef19c82f7c198e6
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57329810"
---
# <a name="class-miphttpresponse"></a>class mip::HttpResponse 
Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public int32_t GetStatusCode() const  |  Ruft den Antwortstatuscode ab.
public const std::string& GetBody() const  |  Ruft den Text der Anforderung ab.
public const std::map\<std::string, std::string, CaseInsensitiveComparator\>& GetHeaders() const  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="getstatuscode-function"></a>GetStatusCode-Funktion
Ruft den Antwortstatuscode ab.

  
**Gibt**: Statuscode
  
### <a name="getbody-function"></a>GetBody-Funktion
Ruft den Text der Anforderung ab.

  
**Gibt**: Anforderungstext
  
### <a name="getheaders-function"></a>GetHeaders-Funktion
Ruft Anforderungsheader ab.

  
**Gibt**: Anforderungsheader
