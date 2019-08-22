---
title: class mip::HttpRequest
description: 'Dokumentiert die MIP:: HttpRequest-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 28584ffa19c2ceb00f4ab3839f945adf737bdb3b
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885577"
---
# <a name="class-miphttprequest"></a>class mip::HttpRequest 
Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Anforderungs-ID ab.
public HttpRequestType GetRequestType() const  |  Ruft den Anforderungstyp ab.
public const std::string& GetUrl() const  |  Ruft die Anforderungs-URL ab.
Public Konstanten Std:: Vector\<uint8_t\>& GetBody () Konstanten  |  Ruft den Text der Anforderung ab.
Public Konstanten Std:: map\<Std:: String, Std:: String, caseinsensitivecomparator\>& gezeige Aders () Konstanten  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Anforderungs-ID ab.

  
**Gibt Folgendes zurück**: Anforderungs-ID die entsprechende HttpResponse hat dieselbe ID.
  
### <a name="getrequesttype-function"></a>Getrequesttype-Funktion
Ruft den Anforderungstyp ab.

  
**Gibt Folgendes zurück**: Anforderungstyp
  
### <a name="geturl-function"></a>GetURL-Funktion
Ruft die Anforderungs-URL ab.

  
**Gibt Folgendes zurück**: Anforderungs-URL
  
### <a name="getbody-function"></a>GetBody-Funktion
Ruft den Text der Anforderung ab.

  
**Gibt Folgendes zurück**: Anforderungstext
  
### <a name="getheaders-function"></a>Gezeige Aders-Funktion
Ruft Anforderungsheader ab.

  
**Gibt Folgendes zurück**: Anforderungs Header