---
title: mip::ContentLabel-Klasse
description: 'Dokumentiert die MIP:: contentlabel-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 96f8cca48f385a21685e93eb5bc57abac571975c
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60184772"
---
# <a name="class-mipcontentlabel"></a>mip::ContentLabel-Klasse 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
Sie enthält auch die Eigenschaften für eine bestimmte angewendete Bezeichnungsinstanz.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::chrono::time_point\<std::chrono::system_clock\> GetCreationTime() const  |  Ruft die Erstellungszeit der Bezeichnung ab
public AssignmentMethod GetAssignmentMethod() const  |  Ruft die Zuweisungsmethode der Bezeichnung ab
public const std::vector\<std::pair\<std::string, std::string\>\>& GetExtendedProperties() const  |  Ruft erweiterte Eigenschaften ab.
public bool IsProtectionAppliedFromLabel() const  |  Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.
Public Std:: shared_ptr\<Bezeichnung\> GetLabel() const  |  Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
  
## <a name="members"></a>Member
  
### <a name="getcreationtime-function"></a>GetCreationTime-Funktion
Ruft die Erstellungszeit der Bezeichnung ab

  
**Gibt**: Zeitpunkt der Erstellung.
  
### <a name="getassignmentmethod-function"></a>GetAssignmentMethod-Funktion
Ruft die Zuweisungsmethode der Bezeichnung ab

  
**Gibt**: AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
  
**Siehe auch**: [MIP:: assignmentmethod](mip-enums-and-structs.md#assignmentmethod)
  
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