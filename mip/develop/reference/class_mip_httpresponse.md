---
title: HttpResponse-Klasse
description: 'Dokumentiert die HttpResponse:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 0a08b2bea4834375a01897b3d657772112463b89
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566876"
---
# <a name="class-httpresponse"></a>HttpResponse-Klasse 
Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des HttpDelegate implementiert wird.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Antwort-ID ab.
public int32_t GetStatusCode() const  |  Ruft den Antwortstatuscode ab.
Public Konstanten Std:: Vector \<uint8_t\>& GetBody () Konstanten  |  Ruft den Text der Anforderung ab.
Public Konstanten Std:: map \<std::string, std::string, CaseInsensitiveComparator\>& gezeige Aders () Konstanten  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Members
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Antwort-ID ab.

  
**Returns**: Antwort-ID die entsprechende HttpRequest weist dieselbe ID auf.
  
### <a name="getstatuscode-function"></a>GetStatus Code-Funktion
Ruft den Antwortstatuscode ab.

  
**Rückgabe**: Der Statuscode.
  
### <a name="getbody-function"></a>GetBody-Funktion
Ruft den Text der Anforderung ab.

  
**Rückgabe**: Der Anforderungstext.
  
### <a name="getheaders-function"></a>Gezeige Aders-Funktion
Ruft Anforderungsheader ab.

  
**Rückgabe**: Anforderungsheader.