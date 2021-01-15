---
title: Class classificationresult
description: 'Dokumentiert die classificationresult:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: c1f4154bbc12613726aac8f56a322cb6cd4d5a53
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98211871"
---
# <a name="class-classificationresult"></a>Class classificationresult 
Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
public std::string GetName() const  |  Den Namen der Klassifizierungs Richtlinie erhalten.
public int GetCount() const  |  Ruft die Anzahl der Instanzen ab.
public int GetConfidenceLevel() const  |  Ruft die Zuverlässigkeit des Ergebnisses ab.
Public Std:: String getsensitiveinformationerkenctions () Konstanten  |  Die Erkennungen für sensible Informationen erhalten.
public virtual Std:: Vector \<std::shared_ptr\<mip::DetailedClassificationResult\> \> getdetailedclassificationattributs () konstant  |  Dient zum Ermitteln der spezifischen Erkennungs Bänder, wenn die klassifizierte Klassifizierung aktiviert ist.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die ID der Klassifizierungsrichtlinie ab.

  
**Gibt Folgendes zurück**: ID der Klassifizierungs Richtlinie.
  
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

  
**Gibt Folgendes zurück**: JSON-Zeichenfolge aller Erkennungen sensibler Informationen. Wenn nicht leer ist, muss ein gültiges JSON-Format vorliegen.
  
### <a name="getdetailedclassificationattributes-function"></a>Getdetailedclassificationattribute-Funktion
Dient zum Ermitteln der spezifischen Erkennungs Bänder, wenn die klassifizierte Klassifizierung aktiviert ist.

  
**Returns**: ein Vektor der Instanz wird mit unterschiedlichen Vertrauens Schwellenwerten gezählt.