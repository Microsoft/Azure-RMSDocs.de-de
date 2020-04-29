---
title: HttpRequest-Klasse
description: 'Dokumentiert die HttpRequest:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: af302a760ee6b8f24b077b2c45bfe86ab0a80dac
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81762704"
---
# <a name="class-httprequest"></a>HttpRequest-Klasse 
Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Anforderungs-ID ab.
public HttpRequestType GetRequestType() const  |  Ruft den Anforderungstyp ab.
public const std::string& GetUrl() const  |  Ruft die Anforderungs-URL ab.
Public Konstanten Std:: Vector\<uint8_t\>& GetBody ()-Konstanten  |  Ruft den Text der Anforderung ab.
Public Konstanten Std:: map\<Std:: String, Std:: String, caseinsensitivecomparator\>& gezeige Aders () Konstanten  |  Ruft Anforderungsheader ab.
  
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