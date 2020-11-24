---
title: HttpRequest-Klasse
description: 'Dokumentiert die HttpRequest:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 9384976b01899f6d37b6ac55073014bb4a49e924
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566892"
---
# <a name="class-httprequest"></a>HttpRequest-Klasse 
Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Anforderungs-ID ab.
public HttpRequestType GetRequestType() const  |  Ruft den Anforderungstyp ab.
public const std::string& GetUrl() const  |  Ruft die Anforderungs-URL ab.
Public Konstanten Std:: Vector \<uint8_t\>& GetBody () Konstanten  |  Ruft den Text der Anforderung ab.
Public Konstanten Std:: map \<std::string, std::string, CaseInsensitiveComparator\>& gezeige Aders () Konstanten  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Members
  
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