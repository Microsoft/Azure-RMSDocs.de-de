---
title: Klasse mip::ClassificationRequest
description: Dokumentiert die mip::classificationrequest-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: a7350961af4c2e5d63211840382ee7a0b701f1c4
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652029"
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