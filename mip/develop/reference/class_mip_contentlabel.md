---
title: Klasse "contentlabel"
description: 'Dokumentiert die contentlabel:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: a60244b9db9b3087dde71cbdbcf63ba170cb06c3
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567196"
---
# <a name="class-contentlabel"></a>Klasse "contentlabel" 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
Sie enthält auch die Eigenschaften für eine bestimmte angewendete Bezeichnungsinstanz.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: Chrono:: time_point \<std::chrono::system_clock\> getkreationtime () Konstanten  |  Ruft die Erstellungszeit der Bezeichnung ab
public AssignmentMethod GetAssignmentMethod() const  |  Ruft die Zuweisungsmethode der Bezeichnung ab
Public Konstanten Std:: Vector \<MetadataEntry\>& getextendecodproperties () Konstanten  |  Ruft erweiterte Eigenschaften ab.
public bool IsProtectionAppliedFromLabel() const  |  Ruft ab, ob Schutz von der Bezeichnung angewendet wurde.
public std::shared_ptr\<Label\> GetLabel() const  |  Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
  
## <a name="members"></a>Members
  
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