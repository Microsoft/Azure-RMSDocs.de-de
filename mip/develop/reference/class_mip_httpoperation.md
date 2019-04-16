---
title: Klasse mip::HttpOperation
description: Dokumentiert die mip::httpoperation-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: e3eaedbf508f116b19521286b686bc955d108efe
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574481"
---
# <a name="class-miphttpoperation"></a>Klasse mip::HttpOperation 
Schnittstelle, die einem HTTP-Vorgang, durch die Client-app implementiert werden, beim Überschreiben von beschreibt [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Vorgangs-ID.
Public Std:: shared_ptr\<HttpResponse\> von GetResponse() ab  |  Antwort zu erhalten, sofern vorhanden.
public Bool IsCancelled()  |  Ruft den Status der Abbruch des Vorgangs.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Vorgangs-ID.

  
**Gibt**: Vorgangs-ID der entsprechenden [HttpRequest](class_mip_httprequest.md) und [HttpResponse](class_mip_httpresponse.md) wird dieselbe ID haben
  
### <a name="getresponse-function"></a>GetResponse-Funktion
Antwort zu erhalten, sofern vorhanden.

  
**Gibt**: Antwort
  
### <a name="iscancelled-function"></a>IsCancelled-Funktion
Ruft den Status der Abbruch des Vorgangs.

  
**Gibt**: Abbruch-status