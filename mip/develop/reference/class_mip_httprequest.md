---
title: class mip::HttpRequest
description: Dokumentiert die mip::httprequest-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6e663d4083d9daa2fc744289708f4c127ffb29c2
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330694"
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
