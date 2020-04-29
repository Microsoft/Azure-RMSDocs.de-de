---
title: HttpResponse-Klasse
description: 'Dokumentiert die HttpResponse:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 6e37613adce0397ed543c4df793a59e74795fb26
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81762470"
---
# <a name="class-httpresponse"></a>HttpResponse-Klasse 
Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des HttpDelegate implementiert wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Antwort-ID ab.
public int32_t GetStatusCode() const  |  Ruft den Antwortstatuscode ab.
Public Konstanten Std:: Vector\<uint8_t\>& GetBody ()-Konstanten  |  Ruft den Text der Anforderung ab.
Public Konstanten Std:: map\<Std:: String, Std:: String, caseinsensitivecomparator\>& gezeige Aders () Konstanten  |  Ruft Anforderungsheader ab.
  
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