---
title: Class classificationresult
description: 'Dokumentiert die classificationresult:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 4e64abc1cca11f11b19238282c9061dc26b29290
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567229"
---
# <a name="class-classificationresult"></a>Class classificationresult 
Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
public std::string GetName() const  |  Den Namen der Klassifizierungs Richtlinie erhalten.
public int GetCount() const  |  Ruft die Anzahl der Instanzen ab.
public int GetConfidenceLevel() const  |  Ruft die Zuverlässigkeit des Ergebnisses ab.
Public Std:: String getsensitiveinformationerkenctions () Konstanten  |  Die Erkennungen für sensible Informationen erhalten.
public virtual Std:: Vector \<std::shared_ptr\<mip::DetailedClassificationResult\> \> getdetailedclassificationattributs () konstant  |  Dient zum Ermitteln der spezifischen Erkennungs Bänder, wenn die klassifizierte Klassifizierung aktiviert ist.
  
## <a name="members"></a>Members
  
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