---
title: mip::ClassificationResult-Klasse
description: Dokumentiert die mip::classificationresult-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 716bc18031b5b67b080281b76c42df296f3d72fa
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57332513"
---
# <a name="class-mipclassificationresult"></a>mip::ClassificationResult-Klasse 
Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
public int GetCount() const  |  Ruft die Anzahl der Instanzen ab.
public int GetConfidenceLevel() const  |  Ruft die Zuverlässigkeit des Ergebnisses ab.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die ID der Klassifizierungsrichtlinie ab.

  
**Gibt**: Die ID der Richtlinie Klassifizierung.
  
### <a name="getcount-function"></a>GetCount-Funktion
Ruft die Anzahl der Instanzen ab.

  
**Gibt**: Die Anzahl der Instanzen.
  
### <a name="getconfidencelevel-function"></a>GetConfidenceLevel-Funktion
Ruft die Zuverlässigkeit des Ergebnisses ab.
