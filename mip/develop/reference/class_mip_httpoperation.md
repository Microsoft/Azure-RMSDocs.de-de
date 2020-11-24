---
title: httpoperation-Klasse
description: 'Dokumentiert die httpoperation:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: ece0d76577747170e4328bc1d9bdabb0678e65a5
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566879"
---
# <a name="class-httpoperation"></a>httpoperation-Klasse 
Schnittstelle, die einen einzelnen http-Vorgang beschreibt, der von der Client-App beim Überschreiben von httpdelegaten
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Vorgangs-ID ab.
Public Std:: shared_ptr \<HttpResponse\> GetResponse ()  |  Get-Antwort, falls vorhanden.
public bool isabgeb Rochen ()  |  Gibt den Abbruch Status des Vorgangs an.
  
## <a name="members"></a>Members
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Vorgangs-ID ab.

  
**Gibt Folgendes zurück**: Vorgangs-ID: die entsprechende HttpRequest und HttpResponse haben dieselbe ID.
  
### <a name="getresponse-function"></a>GetResponse-Funktion
Get-Antwort, falls vorhanden.

  
**Gibt Folgendes zurück**: Antwort
  
### <a name="iscancelled-function"></a>Isabgeb Rochen-Funktion
Gibt den Abbruch Status des Vorgangs an.

  
**Returns**: Abbruch Status