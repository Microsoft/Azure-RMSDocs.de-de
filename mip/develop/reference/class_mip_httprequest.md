---
title: class mip::HttpRequest
description: 'Dokumentiert die MIP:: HttpRequest-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 92cf2bc3840e3cb38210c42c1e1b2d43db1e8bd4
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054826"
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