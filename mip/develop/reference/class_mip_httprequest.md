---
title: class mip::HttpRequest
description: Dokumentiert die mip::httprequest-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 56c736d985e7c8bd258fcb7c1f7e42b5db3801fd
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256939"
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
