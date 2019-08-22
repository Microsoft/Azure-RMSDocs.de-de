---
title: class mip::HttpResponse
description: 'Dokumentiert die MIP:: HttpResponse-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 4d7711f755f4ffde923eb7d913abdb5bd2a905db
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884128"
---
# <a name="class-miphttpresponse"></a>class mip::HttpResponse 
Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Antwort-ID ab.
public int32_t GetStatusCode() const  |  Ruft den Antwortstatuscode ab.
Public Konstanten Std:: Vector\<uint8_t\>& GetBody () Konstanten  |  Ruft den Text der Anforderung ab.
Public Konstanten Std:: map\<Std:: String, Std:: String, caseinsensitivecomparator\>& gezeige Aders () Konstanten  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Antwort-ID ab.

  
**Gibt Folgendes zurück**: Antwort-ID die entsprechende HttpRequest weist die gleiche ID auf.
  
### <a name="getstatuscode-function"></a>GetStatus Code-Funktion
Ruft den Antwortstatuscode ab.

  
**Gibt Folgendes zurück**: Statuscode
  
### <a name="getbody-function"></a>GetBody-Funktion
Ruft den Text der Anforderung ab.

  
**Gibt Folgendes zurück**: Anforderungstext
  
### <a name="getheaders-function"></a>Gezeige Aders-Funktion
Ruft Anforderungsheader ab.

  
**Gibt Folgendes zurück**: Anforderungs Header