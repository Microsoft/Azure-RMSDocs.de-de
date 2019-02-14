---
title: mip::ContentLabel-Klasse
description: 'Dokumentiert die MIP:: contentlabel-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 6ef95a20be13123eec6ad17a9eef26f321e36cf8
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254661"
---
# <a name="class-mipcontentlabel"></a>mip::ContentLabel-Klasse 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
Sie enthält auch die Eigenschaften für eine bestimmte angewendete Bezeichnungsinstanz.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetCreationTime() const  |  Ruft die Erstellungszeit der Bezeichnung ab
public AssignmentMethod GetAssignmentMethod() const  |  Ruft die Zuweisungsmethode der Bezeichnung ab
public const std::vector\<std::pair\<std::string, std::string\>\>& GetExtendedProperties() const  |  Ruft erweiterte Eigenschaften ab.
public bool IsProtectionAppliedFromLabel() const  |  Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.
Public Std:: shared_ptr\<Bezeichnung\> GetLabel() const  |  Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
  
## <a name="members"></a>Member
  
### <a name="getcreationtime-function"></a>GetCreationTime-Funktion
Ruft die Erstellungszeit der Bezeichnung ab

  
**Gibt**: Die Erstellungszeit als GMT-Zeichenfolge.
  
### <a name="getassignmentmethod-function"></a>GetAssignmentMethod-Funktion
Ruft die Zuweisungsmethode der Bezeichnung ab

  
**Gibt**: AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
  
**Siehe auch**: [MIP:: assignmentmethod](mip-enums-and-structs.md#assignmentmethod-enum)
  
### <a name="getextendedproperties-function"></a>GetExtendedProperties-Funktion
Ruft erweiterte Eigenschaften ab.

  
**Gibt**: Erweiterte Eigenschaften.
  
### <a name="isprotectionappliedfromlabel-function"></a>IsProtectionAppliedFromLabel function
Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.

  
**Gibt**: True, wenn es des Schutzes von Vorlagen und es, indem Sie diese Bezeichnung enthalten ist, andernfalls "false war".
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird

  
**Gibt**: Das Label-Objekt, das auf den Inhalt angewendet. 
  
**Weitere Informationen finden Sie unter:** [mip::Label](class_mip_label.md)
