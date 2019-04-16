---
title: Klasse mip::ClassificationRequest
description: Dokumentiert die mip::classificationrequest-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 3fddd870b6aebb9f5209fc43160c32d87b1d7129
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573734"
---
# <a name="class-mipclassificationrequest"></a>Klasse mip::ClassificationRequest 
Klasse, die die Anforderung eines Aufrufs der Klassifizierung für den Ausführungsstatus enthält.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String GetClassificationId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
public std::string GetRulePackageId() const  |  Ruft die ID des Pakets Regel.
  
## <a name="members"></a>Member
  
### <a name="getclassificationid-function"></a>GetClassificationId-Funktion
Ruft die ID der Klassifizierungsrichtlinie ab.

  
**Gibt**: Die ID der Richtlinie Klassifizierung.
  
### <a name="getrulepackageid-function"></a>GetRulePackageId-Funktion
Ruft die ID des Pakets Regel.

  
**Gibt**: Die ID des Pakets Regel. vordefinierte Klassifizierungen werden auf leere Guid festgelegt werden.