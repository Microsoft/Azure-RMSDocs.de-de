---
title: 'MIP:: httpoperation-Klasse'
description: 'Dokumentiert die MIP:: httpoperation-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 6f0c3cc726d72d89a8682907ebc350270db5daee
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73558787"
---
# <a name="class-miphttpoperation"></a>MIP:: httpoperation-Klasse 
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

  
**Gibt Folgendes zurück**: Vorgangs-ID: die entsprechende HttpRequest und HttpResponse haben dieselbe ID.
  
### <a name="getresponse-function"></a>GetResponse-Funktion
Get-Antwort, falls vorhanden.

  
**Gibt Folgendes zurück**: Antwort
  
### <a name="iscancelled-function"></a>Isabgeb Rochen-Funktion
Gibt den Abbruch Status des Vorgangs an.

  
**Returns**: Abbruch Status