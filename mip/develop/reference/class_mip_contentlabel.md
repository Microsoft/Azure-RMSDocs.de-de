---
title: Microsoft Information Protection-Klasse „ContentLabel“
description: Referenz für die Microsoft Information Protection-Klasse „ContentLabel“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c105f620ed2cd3d6f1427f2543784ea66ce2c4d7
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446021"
---
# <a name="class-mipcontentlabel"></a>mip::ContentLabel-Klasse 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
Sie enthält auch die Eigenschaften für eine bestimmte angewendete Bezeichnungsinstanz.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetCreationTime() const  |  Ruft die Erstellungszeit der Bezeichnung ab
 public AssignmentMethod GetAssignmentMethod() const  |  Ruft die Zuweisungsmethode der Bezeichnung ab
public const std::vector<std::pair<std::string, std::string>>& GetExtendedProperties() const  |  Ruft erweiterte Eigenschaften ab.
 public bool IsProtectionAppliedFromLabel() const  |  Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.
public std::shared_ptr<Label> GetLabel() const  |  Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
  
## <a name="members"></a>Member
  
### <a name="getcreationtime"></a>GetCreationTime
Ruft die Erstellungszeit der Bezeichnung ab

  
**Rückgabe**: Erstellungszeit als GMT-Zeichenfolge.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
Ruft die Zuweisungsmethode der Bezeichnung ab

  
**Rückgabe**: AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
  
**Weitere Informationen finden Sie unter:** mip::AssignmentMethod
  
### <a name="getextendedproperties"></a>GetExtendedProperties
Ruft erweiterte Eigenschaften ab.

  
**Rückgabe**: Erweiterte Eigenschaften.
  
### <a name="isprotectionappliedfromlabel"></a>IsProtectionAppliedFromLabel
Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.

  
**Rückgabe**: TRUE, wenn Vorlagenschutz vorhanden ist und von dieser Bezeichnung bereitgestellt wird, andernfalls FALSE.
  
### <a name="label"></a>Label
Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird

  
**Rückgabe**: die Objektbezeichnung, die auf den Inhalt angewendet wird. 
  
**Weitere Informationen finden Sie unter:** [mip::Label](class_mip_label.md)