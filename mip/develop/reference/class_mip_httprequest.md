---
title: class mip::HttpRequest
description: 'Dokumentiert die MIP:: HttpRequest-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: bfe55f09caaa20687750b055e10828f8cc6df2bd
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560174"
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
Public Konstanten Std:: Map\<Std:: String, Std:: String, caseinsensitivecomparator\>& gezeige Aders () konstant.  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Anforderungs-ID ab.

  
**Gibt Folgendes zurück**: Anforderungs-ID die entsprechende HttpResponse hat dieselbe ID.
  
### <a name="getrequesttype-function"></a>Getrequesttype-Funktion
Ruft den Anforderungstyp ab.

  
**Rückgabe**: Der Anforderungstyp.
  
### <a name="geturl-function"></a>GetURL-Funktion
Ruft die Anforderungs-URL ab.

  
**Rückgabe**: Die Anforderungs-URL.
  
### <a name="getbody-function"></a>GetBody-Funktion
Ruft den Text der Anforderung ab.

  
**Rückgabe**: Der Anforderungstext.
  
### <a name="getheaders-function"></a>Gezeige Aders-Funktion
Ruft Anforderungsheader ab.

  
**Rückgabe**: Anforderungsheader.