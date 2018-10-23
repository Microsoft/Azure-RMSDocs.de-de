---
title: Microsoft Information Protection-Klasse „HttpRequest“
description: Referenz für die Microsoft Information Protection-Klasse „HttpRequest“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e838eb247bc00d43da72db1de03304e89a1b1da5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445239"
---
# <a name="class-miphttprequest"></a>class mip::HttpRequest 
Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public HttpRequestType GetRequestType() const  |  Ruft den Anforderungstyp ab.
 public const std::string& GetUrl() const  |  Ruft die Anforderungs-URL ab.
 public const std::string& GetBody() const  |  Ruft den Text der Anforderung ab.
public const std::map<std::string, std::string, CaseInsensitiveComparator>& GetHeaders() const  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="httprequesttype"></a>HttpRequestType
Ruft den Anforderungstyp ab.

  
**Rückgabe**: Der Anforderungstyp.
  
### <a name="geturl"></a>GetUrl
Ruft die Anforderungs-URL ab.

  
**Rückgabe**: Die Anforderungs-URL.
  
### <a name="getbody"></a>GetBody
Ruft den Text der Anforderung ab.

  
**Rückgabe**: Der Anforderungstext.
  
### <a name="getheaders"></a>GetHeaders
Ruft Anforderungsheader ab.

  
**Rückgabe**: Anforderungsheader.