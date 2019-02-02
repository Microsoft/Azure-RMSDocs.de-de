---
title: class mip::HttpRequest
description: Dokumentiert die mip::httprequest-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 3c23d37836b241a416cbaf5ee5cd22f8c726794d
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650084"
---
# <a name="class-miphttprequest"></a>class mip::HttpRequest 
Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public HttpRequestType GetRequestType() const  |  Ruft den Anforderungstyp ab.
public const std::string& GetUrl() const  |  Ruft die Anforderungs-URL ab.
public const std::string& GetBody() const  |  Ruft den Text der Anforderung ab.
public const std::map\<std::string, std::string, CaseInsensitiveComparator\>& GetHeaders() const  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="getrequesttype-function"></a>GetRequestType-Funktion
Ruft den Anforderungstyp ab.

  
**Gibt**: Anforderungstyp
  
### <a name="geturl-function"></a>GetUrl-Funktion
Ruft die Anforderungs-URL ab.

  
**Gibt**: Anforderungs-url
  
### <a name="getbody-function"></a>GetBody-Funktion
Ruft den Text der Anforderung ab.

  
**Gibt**: Anforderungstext
  
### <a name="getheaders-function"></a>GetHeaders-Funktion
Ruft Anforderungsheader ab.

  
**Gibt**: Anforderungsheader