---
title: class mip::HttpResponse
description: 'Dokumentiert die MIP:: HttpResponse-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 3fe574665d6a51c03135cf863fcec9d2106e549d
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056020"
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