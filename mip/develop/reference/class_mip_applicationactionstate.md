---
title: applicationaktionstate-Klasse
description: 'Dokumentiert die applicationaktionstate:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: ef62674d4586b967a822ccfb25612a491d157bf4
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212279"
---
# <a name="class-applicationactionstate"></a>applicationaktionstate-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches labelstate getnewlabelstate () Konstanten  |  Ruft den neuen Bezeichnungs Zustand ab.
Public Std:: shared_ptr \<Label\> getnewlabel () Konstanten  |  Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.
Public Std::p Air \<bool, std::string\> isdowngraabgerechtfer() konstant  |  Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.
public AssignmentMethod GetNewLabelAssignmentMethod() const  |  Ruft die Zuweisungsmethode für die neue Bezeichnung ab.
public virtual Std:: Vector \<std::pair\<std::string, std::string\> \> getnewlabelextendedproperties () Konstanten  |  Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.
public ActionType GetSupportedActions() const  |  Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt
public bool IsRecommendationEnabled () konstant  |  Gibt einen booleschen Wert zurück, der die empfohlene Aktion zurückgibt. Standardmäßig sollte true lauten, sofern der Benutzer nicht else angibt.
  
## <a name="members"></a>Member
  
### <a name="getnewlabelstate-function"></a>Getnewlabelstate-Funktion
Ruft den neuen Bezeichnungs Zustand ab.

  
**Gibt Folgendes zurück**: den neuen Bezeichnungs Zustand. 
  
**Siehe auch**: MIP:: labelstate
  
### <a name="getnewlabel-function"></a>Getnewlabel-Funktion
Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.

  
**Rückgabe**: Die ID der Vertraulichkeitsbezeichnung, die ggf. auf den Inhalt angewendet werden soll. Wenn kein Inhalt vorhanden ist, kann die Bezeichnung entfernt werden.
  
### <a name="isdowngradejustified-function"></a>Isdowngradebug-Funktion
Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.

  
**Rückgabe:** TRUE, wenn das Herabstufen berechtigt ist und eine Nachricht mit einer Begründung bereitgestellt wird; andernfalls FALSE 
  
**Siehe auch**: MIP:: justifyaction
  
### <a name="getnewlabelassignmentmethod-function"></a>Getnewlabelaccessmentmethod-Funktion
Ruft die Zuweisungsmethode für die neue Bezeichnung ab.

  
**Rückgabe**: Zuweisungsmethode STANDARD, PRIVILEGED, AUTO. 
  
**Weitere Informationen finden Sie unter:** mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties-function"></a>Getnewlabelextendedproperties-Funktion
Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.

  
**Rückgabe:** die erweiterten Eigenschaften, die auf den Inhalt angewendet werden sollen
  
### <a name="getsupportedactions-function"></a>Getsupportedactions-Funktion
Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt

  
**Rückgabe**: eine maskierte Enumeration, die alle unterstützten Aktionstypen beschreibt
ActionType::Justify muss unterstützt werden. Wenn eine Erklärung für die Änderung einer Richtlinie oder einer Bezeichnung verlangt wird, wird stets eine Aktion zur Erklärung zurückgegeben.
  
### <a name="isrecommendationenabled-function"></a>IsRecommendationEnabled-Funktion
Gibt einen booleschen Wert zurück, der die empfohlene Aktion zurückgibt. Standardmäßig sollte true lauten, sofern der Benutzer nicht else angibt.

  
**Returns**: ein boolescher Wert, der die empfohlene Aktion Kennzeichen, wird zurückgegeben.
"Aktionstyp:: RecommendLabel" muss aktiviert sein, damit dieses Feld eine Auswirkung hat.