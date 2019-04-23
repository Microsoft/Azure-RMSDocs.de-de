---
title: class mip::HttpResponse
description: Dokumentiert die mip::httpresponse-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 06bc3f52bdecd85412dc0c35df46c7847167aa1b
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60173982"
---
# <a name="class-miphttpresponse"></a>class mip::HttpResponse 
Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Antwort-ID ab
public int32_t GetStatusCode() const  |  Ruft den Antwortstatuscode ab.
Public const Std:: vector\<uint8_t\>& GetBody() const  |  Ruft den Text der Anforderung ab.
public const std::map\<std::string, std::string, CaseInsensitiveComparator\>& GetHeaders() const  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Antwort-ID ab

  
**Gibt**: Antwort-ID der entsprechenden [HttpRequest](class_mip_httprequest.md) wird die gleiche ID hatten
  
### <a name="getstatuscode-function"></a>GetStatusCode-Funktion
Ruft den Antwortstatuscode ab.

  
**Gibt**: Statuscode
  
### <a name="getbody-function"></a>GetBody-Funktion
Ruft den Text der Anforderung ab.

  
**Gibt**: Anforderungstext
  
### <a name="getheaders-function"></a>GetHeaders-Funktion
Ruft Anforderungsheader ab.

  
**Gibt**: Anforderungsheader