---
title: mip::ContentLabel-Klasse
description: 'Dokumentiert die MIP:: contentlabel-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 27f8adba3e65647a3804256e0b429e1457003085
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884398"
---
# <a name="class-mipcontentlabel"></a>mip::ContentLabel-Klasse 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
Sie enthält auch die Eigenschaften für eine bestimmte angewendete Bezeichnungsinstanz.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getkreationtime () Konstanten  |  Ruft die Erstellungszeit der Bezeichnung ab
public AssignmentMethod GetAssignmentMethod() const  |  Ruft die Zuweisungsmethode der Bezeichnung ab
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& getextendecodproperties () Konstanten  |  Ruft erweiterte Eigenschaften ab.
public bool IsProtectionAppliedFromLabel() const  |  Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.
Public Std:: shared_ptr\<Label\> GetLabel () Konstanten  |  Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
  
## <a name="members"></a>Member
  
### <a name="getcreationtime-function"></a>Getkreationtime-Funktion
Ruft die Erstellungszeit der Bezeichnung ab

  
**Gibt Folgendes zurück**: Erstellungszeit.
  
### <a name="getassignmentmethod-function"></a>Getaccessmentmethod-Funktion
Ruft die Zuweisungsmethode der Bezeichnung ab

  
**Gibt Folgendes zurück**: AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
  
**Siehe auch**: [MIP:: accessmentmethod](mip-enums-and-structs.md#assignmentmethod-enum)
  
### <a name="getextendedproperties-function"></a>Getextendecodproperties-Funktion
Ruft erweiterte Eigenschaften ab.

  
**Gibt Folgendes zurück**: Erweiterte Eigenschaften.
  
### <a name="isprotectionappliedfromlabel-function"></a>Isprotectionappliedfromlabel-Funktion
Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.

  
**Gibt Folgendes zurück**: "True", wenn Vorlagen Schutz vorhanden ist, andernfalls "false".
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird

  
**Gibt Folgendes zurück**: Das Bezeichnungs Objekt, das auf den Inhalt angewendet wird. 
  
**Weitere Informationen finden Sie unter:** [mip::Label](class_mip_label.md)