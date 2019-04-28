---
title: mip::ClassificationResult-Klasse
description: Dokumentiert die mip::classificationresult-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6a048dd7902e8148e4f32f8cc9e62d63110b2b4a
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60174220"
---
# <a name="class-mipclassificationresult"></a>mip::ClassificationResult-Klasse 
Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
public int GetCount() const  |  Ruft die Anzahl der Instanzen ab.
public int GetConfidenceLevel() const  |  Ruft die Zuverlässigkeit des Ergebnisses ab.
public std::string GetSensitiveInformationDetections() const  |  Die Erkennung von vertraulichen Informationen zu erhalten.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die ID der Klassifizierungsrichtlinie ab.

  
**Gibt**: Die ID der Richtlinie Klassifizierung.
  
### <a name="getcount-function"></a>GetCount-Funktion
Ruft die Anzahl der Instanzen ab.

  
**Gibt**: Die Anzahl der Instanzen.
  
### <a name="getconfidencelevel-function"></a>GetConfidenceLevel-Funktion
Ruft die Zuverlässigkeit des Ergebnisses ab.
  
### <a name="getsensitiveinformationdetections-function"></a>GetSensitiveInformationDetections-Funktion
Die Erkennung von vertraulichen Informationen zu erhalten.

  
**Gibt**: Alle vertraulichen Informationen Erkennungen JSON-Zeichenfolge.