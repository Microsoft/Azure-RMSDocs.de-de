---
title: mip::ContentLabel-Klasse
description: 'Dokumentiert die MIP:: contentlabel-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: d608ca9229a9b8c4ef0bec3c0d2fe37b51b71f61
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651733"
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