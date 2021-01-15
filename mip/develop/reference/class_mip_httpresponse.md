---
title: HttpResponse-Klasse
description: 'Dokumentiert die HttpResponse:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 8e4a8c392c6e18197e3b9b376482f3145d1ecd3f
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98211395"
---
# <a name="class-httpresponse"></a>HttpResponse-Klasse 
Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des HttpDelegate implementiert wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Antwort-ID ab.
public int32_t GetStatusCode() const  |  Ruft den Antwortstatuscode ab.
Public Konstanten Std:: Vector \<uint8_t\>& GetBody () Konstanten  |  Ruft den Text der Anforderung ab.
Public Konstanten Std:: map \<std::string, std::string, CaseInsensitiveComparator\>& gezeige Aders () Konstanten  |  Ruft Anforderungsheader ab.
  
## <a name="members"></a>Member
  
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