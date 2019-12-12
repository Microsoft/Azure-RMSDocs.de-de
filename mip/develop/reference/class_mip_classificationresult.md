---
title: mip::ClassificationResult-Klasse
description: 'Dokumentiert die MIP:: classificationresult-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 6f4b1147ef6831ca622d095c0cada67b9f0cf023
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73559397"
---
# <a name="class-mipclassificationresult"></a>mip::ClassificationResult-Klasse 
Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
public std::string GetName() const  |  Den Namen der Klassifizierungs Richtlinie erhalten.
public int GetCount() const  |  Ruft die Anzahl der Instanzen ab.
public int GetConfidenceLevel() const  |  Ruft die Zuverlässigkeit des Ergebnisses ab.
Public Std:: String getsensitiveinformationerkenctions () Konstanten  |  Die Erkennungen für sensible Informationen erhalten.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die ID der Klassifizierungsrichtlinie ab.

  
**Rückgabe**: ID der Klassifizierungsrichtlinie.
  
### <a name="getname-function"></a>GetName-Funktion
Den Namen der Klassifizierungs Richtlinie erhalten.

  
**Gibt Folgendes zurück**: Name der Klassifizierungs Richtlinie.
  
### <a name="getcount-function"></a>GetCount-Funktion
Ruft die Anzahl der Instanzen ab.

  
**Rückgabe**: Anzahl von Instanzen
  
### <a name="getconfidencelevel-function"></a>Getconficelevel-Funktion
Ruft die Zuverlässigkeit des Ergebnisses ab.
  
### <a name="getsensitiveinformationdetections-function"></a>Getsensitiveingeformationdetections-Funktion
Die Erkennungen für sensible Informationen erhalten.

  
**Gibt Folgendes zurück**: JSON-Zeichenfolge aller Erkennungen sensibler Informationen.