---
title: mip::ExecutionState-Klasse
description: 'Beschreibt die Klasse:: executionstate-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 318b87405ad9e6d6291f82a0bec3da6031e04ccd
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574357"
---
# <a name="class-mipexecutionstate"></a>mip::ExecutionState-Klasse 
Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
Clients sollten die Methoden nur aufrufen, um den erforderlichen Status abzurufen. Daher sollten Clients diese Schnittstelle aus Effizienzgründen implementieren, damit der entsprechende Status dynamisch und nicht im Voraus berechnet wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetNewLabelId() const  |  Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.
public ActionSource GetNewLabelActionSource() const  |  Ruft die Quelle für eine neue Bezeichnungsaktion ab
public std::string GetContentIdentifier() const  |  Ruft die Beschreibung der Inhalte, die beschreibt, das Dokument ab. Beispiel für eine Datei: [' Pfad\Dateiname '] Beispiel für eine e-Mail: [Betreff: Absender].
public virtual DataState GetDataState() const  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
public std::pair\<bool, std::string\> IsDowngradeJustified() const  |  Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.
public AssignmentMethod GetNewLabelAssignmentMethod() const  |  Ruft die Zuweisungsmethode für die neue Bezeichnung ab.
public virtual std::vector\<std::pair\<std::string, std::string\>\> GetNewLabelExtendedProperties() const  |  Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.
Public Std:: vector\<Std:: Pair\<Std:: String, Std:: String\> \> GetContentMetadata (const Std:: vector\<Std:: String\>& Namen, const Std:: vector\<Std:: String\>& NamePrefixes) const  |  Ruft die Metadatenelemente aus dem Inhalt ab.
Public Std:: shared_ptr\<ProtectionDescriptor\> GetProtectionDescriptor() const  |  Ruft den Deskriptor für den Schutz ab
public ContentFormat GetContentFormat() const  |  Ruft das Inhaltsformat ab.
public ActionType GetSupportedActions() const  |  Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt
public virtual std::shared_ptr\<ClassificationResults\> GetClassificationResults(const std::vector\<std::shared_ptr\<ClassificationRequest\>\> &) const  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual std::map\<std::string, std::string\> GetAuditMetadata() const  |  Geben Sie eine Zuordnung der Anwendung spezifischen Überwachung Schlüssel-Wert-Paaren zurück.
  
## <a name="members"></a>Member
  
### <a name="getnewlabelid-function"></a>GetNewLabelId-Funktion
Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.

  
**Gibt**: ID der vertraulichkeitsbezeichnung, die auf den Inhalt angewendet werden, wenn vorhanden; andernfalls leer, um die Bezeichnung entfernen.
  
### <a name="getnewlabelactionsource-function"></a>GetNewLabelActionSource-Funktion
Ruft die Quelle für eine neue Bezeichnungsaktion ab

  
**Gibt**: Aktionsquelle.
  
### <a name="getcontentidentifier-function"></a>GetContentIdentifier-Funktion
Ruft die Beschreibung der Inhalte, die beschreibt, das Dokument ab. Beispiel für eine Datei: [' Pfad\Dateiname '] Beispiel für eine e-Mail: [Betreff: Absender].

  
**Gibt**: Beschreibung der Inhalte, die auf den Inhalt angewendet werden.
Dieser Wert wird in Form einer lesbaren Inhaltsbeschreibung überwacht.
  
### <a name="getdatastate-function"></a>GetDataState-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Gibt**: Status der Inhaltsdaten
  
### <a name="isdowngradejustified-function"></a>IsDowngradeJustified-Funktion
Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.

  
**Gibt**: True, wenn ein Downgrade Justifiedalong mit der Begründung Messageelse "false" ist 
  
**Weitere Informationen finden Sie unter:** [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod-function"></a>GetNewLabelAssignmentMethod-Funktion
Ruft die Zuweisungsmethode für die neue Bezeichnung ab.

  
**Gibt**: Die Zuweisungsmethode STANDARD, PRIVILEGED, AUTO. 
  
**Siehe auch**: [MIP:: assignmentmethod](mip-enums-and-structs.md#assignmentmethod)
  
### <a name="getnewlabelextendedproperties-function"></a>GetNewLabelExtendedProperties-Funktion
Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.

  
**Gibt**: Die erweiterten Eigenschaften, die auf den Inhalt angewendet wird.
  
### <a name="getcontentmetadata-function"></a>GetContentMetadata-Funktion
Ruft die Metadatenelemente aus dem Inhalt ab.

  
**Gibt**: Die Metadaten, die auf den Inhalt angewendet wird. Jedes Metadatenelement setzt sich aus einem Name-Wert-Paar zusammen.
  
### <a name="getprotectiondescriptor-function"></a>GetProtectionDescriptor-Funktion
Ruft den Deskriptor für den Schutz ab

  
**Gibt**: Der Deskriptor Schutz
  
### <a name="getcontentformat-function"></a>GetContentFormat-Funktion
Ruft das Inhaltsformat ab.

  
**Gibt**: STANDARD-E-MAIL 
  
**Siehe auch**: [MIP:: contentformat](mip-enums-and-structs.md#contentformat)
  
### <a name="getsupportedactions-function"></a>GetSupportedActions-Funktion
Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt

  
**Gibt**: Eine maskierte-Enumeration, die alle unterstützten Aktionstypen beschreibt.
ActionType::Justify muss unterstützt werden. Wenn eine Erklärung für die Änderung einer Richtlinie oder einer Bezeichnung verlangt wird, wird stets eine Aktion zur Erklärung zurückgegeben.
  
### <a name="getclassificationresults-function"></a>GetClassificationResults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **ClassificationIds**: eine Liste der IDs-Klassifizierung. 



  
**Gibt**: Eine Liste der Klassifizierungsergebnisse. Geben Sie "nullptr" zurück, wenn keine Klassifizierung Zyklus ausgeführt.
  
### <a name="getauditmetadata-function"></a>GetAuditMetadata-Funktion
Geben Sie eine Zuordnung der Anwendung spezifischen Überwachung Schlüssel-Wert-Paaren zurück.

  
**Gibt**: Eine Liste der Anwendung spezifischen Überwachung Metadaten registriert Schlüssel-Wert-Paare Absender: Für den Absender-Empfänger-e-Mail-Id: Stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy dar: E-Mail-Id für den Benutzer, der den Inhalt LastModifiedDate & lt; zuletzt geändert: Datum, an der letzten des Inhalts Änderung