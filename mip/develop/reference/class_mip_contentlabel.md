---
title: mip::ContentLabel-Klasse
description: 'Dokumentiert die MIP:: contentlabel-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: a29ea5be05d928f25b9a4255416d93acedcb1c0b
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73558912"
---
# <a name="class-mipcontentlabel"></a>mip::ContentLabel-Klasse 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
Sie enthält auch die Eigenschaften für eine bestimmte angewendete Bezeichnungsinstanz.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getkreationtime () Konstanten  |  Ruft die Erstellungszeit der Bezeichnung ab
public AssignmentMethod GetAssignmentMethod() const  |  Ruft die Zuweisungsmethode der Bezeichnung ab
Public Konstante Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getextendecodproperties () Konstanten  |  Ruft erweiterte Eigenschaften ab.
public bool IsProtectionAppliedFromLabel() const  |  Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.
Public Std:: shared_ptr\<Bezeichnung\> GetLabel () Konstanten  |  Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
  
## <a name="members"></a>Member
  
### <a name="getcreationtime-function"></a>Getkreationtime-Funktion
Ruft die Erstellungszeit der Bezeichnung ab

  
**Gibt Folgendes zurück**: Erstellungszeit.
  
### <a name="getassignmentmethod-function"></a>Getaccessmentmethod-Funktion
Ruft die Zuweisungsmethode der Bezeichnung ab

  
**Rückgabe**: AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
  
**Siehe auch**: [MIP:: accessmentmethod](mip-enums-and-structs.md#assignmentmethod-enum)
  
### <a name="getextendedproperties-function"></a>Getextendecodproperties-Funktion
Ruft erweiterte Eigenschaften ab.

  
**Rückgabe**: Erweiterte Eigenschaften.
  
### <a name="isprotectionappliedfromlabel-function"></a>Isprotectionappliedfromlabel-Funktion
Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.

  
**Rückgabe**: TRUE, wenn Vorlagenschutz vorhanden ist und von dieser Bezeichnung bereitgestellt wird, andernfalls FALSE.
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird

  
**Rückgabe**: die Objektbezeichnung, die auf den Inhalt angewendet wird. 
  
**Siehe auch**: MIP:: Label