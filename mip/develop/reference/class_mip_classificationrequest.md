---
title: Klasse mip::ClassificationRequest
description: Dokumentiert die mip::classificationrequest-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 81e9a7276b78817f3d2f409cc403992284d23ceb
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259149"
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
