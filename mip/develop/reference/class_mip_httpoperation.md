---
title: httpoperation-Klasse
description: 'Dokumentiert die httpoperation:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 09fac96f16bf18e72d6217842728d48244b9c412
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81762808"
---
# <a name="class-httpoperation"></a>httpoperation-Klasse 
Schnittstelle, die einen einzelnen http-Vorgang beschreibt, der von der Client-App beim Überschreiben von httpdelegaten
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Vorgangs-ID ab.
Public Std:: shared_ptr\<HttpResponse\> GetResponse ()  |  Get-Antwort, falls vorhanden.
public bool isabgeb Rochen ()  |  Gibt den Abbruch Status des Vorgangs an.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Vorgangs-ID ab.

  
**Gibt Folgendes zurück**: Vorgangs-ID: die entsprechende [HttpRequest](class_mip_httprequest.md) und [HttpResponse](class_mip_httpresponse.md) haben dieselbe ID.
  
### <a name="getresponse-function"></a>GetResponse-Funktion
Get-Antwort, falls vorhanden.

  
**Gibt Folgendes zurück**: Antwort
  
### <a name="iscancelled-function"></a>Isabgeb Rochen-Funktion
Gibt den Abbruch Status des Vorgangs an.

  
**Returns**: Abbruch Status