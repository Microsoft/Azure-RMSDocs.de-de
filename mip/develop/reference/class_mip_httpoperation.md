---
title: 'MIP:: httpoperation-Klasse'
description: 'Dokumentiert die MIP:: httpoperation-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: d0f72a60233b05eab2c9e4b9e9cec2bf8bcda495
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056031"
---
# <a name="class-miphttpoperation"></a>MIP:: httpoperation-Klasse 
Schnittstelle, die einen einzelnen http-Vorgang beschreibt, der von der Client-App beim Überschreiben von [httpdelegaten](class_mip_httpdelegate.md)
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Vorgangs-ID ab.
Public Std:: shared_ptr\<HttpResponse\> GetResponse ()  |  Get-Antwort, falls vorhanden.
public bool isabgeb Rochen ()  |  Gibt den Abbruch Status des Vorgangs an.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Vorgangs-ID ab.

  
**Gibt Folgendes zurück**: Vorgangs-ID die entsprechenden HttpRequest-und HttpResponse-Befehle verfügen über die gleiche ID.
  
### <a name="getresponse-function"></a>GetResponse-Funktion
Get-Antwort, falls vorhanden.

  
**Gibt Folgendes zurück**: Antwort
  
### <a name="iscancelled-function"></a>Isabgeb Rochen-Funktion
Gibt den Abbruch Status des Vorgangs an.

  
**Gibt Folgendes zurück**: Abbruch Status