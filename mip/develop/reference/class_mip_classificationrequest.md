---
title: Klasse mip::ClassificationRequest
description: Dokumentiert die mip::classificationrequest-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 61846ef3b8273169e9cf38eaa173eac3ba18dae6
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330516"
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
