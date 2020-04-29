---
title: Class classificationresult
description: 'Dokumentiert die classificationresult:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: b87db224bdd7a571c22de9e382ff9faf3ce656b8
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763526"
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