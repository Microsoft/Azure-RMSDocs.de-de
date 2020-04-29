---
title: Klasse "contentlabel"
description: 'Dokumentiert die contentlabel:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: e69a4a8146eb7e7251645ef83a8db0926d383166
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763399"
---
# <a name="class-contentlabel"></a>Klasse "contentlabel" 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
Sie enthält auch die Eigenschaften für eine bestimmte angewendete Bezeichnungsinstanz.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getkreationtime () Konstanten  |  Ruft die Erstellungszeit der Bezeichnung ab
public AssignmentMethod GetAssignmentMethod() const  |  Ruft die Zuweisungsmethode der Bezeichnung ab
Public Konstante Std:: Vector\<MetadataEntry\>& getextendecodproperties () Konstanten  |  Ruft erweiterte Eigenschaften ab.
public bool IsProtectionAppliedFromLabel() const  |  Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.
Public Std:: shared_ptr\<Bezeichnung\> GetLabel () Konstanten  |  Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
  
## <a name="members"></a>Member
  
### <a name="getcreationtime-function"></a>Getkreationtime-Funktion
Ruft die Erstellungszeit der Bezeichnung ab

  
**Gibt Folgendes zurück**: Erstellungszeit.
  
### <a name="getassignmentmethod-function"></a>Getaccessmentmethod-Funktion
Ruft die Zuweisungsmethode der Bezeichnung ab

  
**Rückgabe**: AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
  
**Weitere Informationen finden Sie unter:** mip::AssignmentMethod
  
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