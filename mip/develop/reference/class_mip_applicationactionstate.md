---
title: 'MIP:: applicationaktionstate-Klasse'
description: 'Dokumentiert die MIP:: applicationaktionstate-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 308918e57cf5495e3da2102ee8caca910c11f670
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69893615"
---
# <a name="class-mipapplicationactionstate"></a>MIP:: applicationaktionstate-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches labelstate getnewlabelstate () Konstanten  |  Ruft den neuen Bezeichnungs Zustand ab.
Public Std:: shared_ptr\<Label\> getnewlabel () Konstanten  |  Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.
Public Std::p Air\<bool, Std:: String\> isdowngradebug () Konstanten  |  Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.
public AssignmentMethod GetNewLabelAssignmentMethod() const  |  Ruft die Zuweisungsmethode für die neue Bezeichnung ab.
public virtual Std:: Vector\<Std::p Air\<Std:: String, Std:: String\> \> getnewlabelextendedproperties () Konstanten  |  Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.
public ActionType GetSupportedActions() const  |  Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt
public bool IsRecommendationEnabled () konstant  |  Gibt einen booleschen Wert zurück, der die empfohlene Aktion zurückgibt. Standardmäßig sollte true lauten, sofern der Benutzer nicht else angibt.
  
## <a name="members"></a>Member
  
### <a name="getnewlabelstate-function"></a>Getnewlabelstate-Funktion
Ruft den neuen Bezeichnungs Zustand ab.

  
**Gibt Folgendes zurück**: Der neue Bezeichnungs Zustand. 
  
**Siehe auch**: MIP:: labelstate
  
### <a name="getnewlabel-function"></a>Getnewlabel-Funktion
Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.

  
**Gibt Folgendes zurück**: Die ID der Vertraulichkeits Bezeichnung, die auf den Inhalt angewendet werden soll, wenn vorhanden ist, wird die Bezeichnung entfernt.
  
### <a name="isdowngradejustified-function"></a>Isdowngradebug-Funktion
Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.

  
**Gibt Folgendes zurück**: True, wenn die Herabstufung rechtzeitig mit der Begründung messageelse false ist. 
  
**Weitere Informationen finden Sie unter:** [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod-function"></a>Getnewlabelaccessmentmethod-Funktion
Ruft die Zuweisungsmethode für die neue Bezeichnung ab.

  
**Gibt Folgendes zurück**: Die Zuweisungs Methode Standard, privilegiert, Auto. 
  
**Siehe auch**: [MIP:: accessmentmethod](mip-enums-and-structs.md#assignmentmethod-enum)
  
### <a name="getnewlabelextendedproperties-function"></a>Getnewlabelextendedproperties-Funktion
Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.

  
**Gibt Folgendes zurück**: Die erweiterten Eigenschaften, die auf den Inhalt angewendet werden.
  
### <a name="getsupportedactions-function"></a>Getsupportedactions-Funktion
Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt

  
**Gibt Folgendes zurück**: Eine maskierte Enumeration, die alle unterstützten Aktions Typen beschreibt.
ActionType::Justify muss unterstützt werden. Wenn eine Erklärung für die Änderung einer Richtlinie oder einer Bezeichnung verlangt wird, wird stets eine Aktion zur Erklärung zurückgegeben.
  
### <a name="isrecommendationenabled-function"></a>IsRecommendationEnabled-Funktion
Gibt einen booleschen Wert zurück, der die empfohlene Aktion zurückgibt. Standardmäßig sollte true lauten, sofern der Benutzer nicht else angibt.

  
**Gibt Folgendes zurück**: Ein boolescher Wert, der die empfohlene Aktion gekennzeichnet, wird zurückgegeben.
"Aktionstyp:: RecommendLabel" muss aktiviert sein, damit dieses Feld eine Auswirkung hat.