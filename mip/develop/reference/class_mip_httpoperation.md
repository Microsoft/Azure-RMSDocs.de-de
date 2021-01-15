---
title: httpoperation-Klasse
description: 'Dokumentiert die httpoperation:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 7ceb76ff61ce13fd47b764fa336ffcf5e167608e
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98211514"
---
# <a name="class-httpoperation"></a>httpoperation-Klasse 
Schnittstelle, die einen einzelnen http-Vorgang beschreibt, der von der Client-App beim Überschreiben von httpdelegaten
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Vorgangs-ID ab.
Public Std:: shared_ptr \<HttpResponse\> GetResponse ()  |  Get-Antwort, falls vorhanden.
public bool isabgeb Rochen ()  |  Gibt den Abbruch Status des Vorgangs an.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Vorgangs-ID ab.

  
**Gibt Folgendes zurück**: Vorgangs-ID: die entsprechende HttpRequest und HttpResponse haben dieselbe ID.
  
### <a name="getresponse-function"></a>GetResponse-Funktion
Get-Antwort, falls vorhanden.

  
**Gibt Folgendes zurück**: Antwort
  
### <a name="iscancelled-function"></a>Isabgeb Rochen-Funktion
Gibt den Abbruch Status des Vorgangs an.

  
**Returns**: Abbruch Status