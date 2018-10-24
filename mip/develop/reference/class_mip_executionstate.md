---
title: Die Klasse „mip::ExecutionState“
description: Referenz zur Klasse „mip::ExecutionState“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 976bca60f3f494a0fbf196e6512b00bdcdd63992
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446310"
---
# <a name="class-mipexecutionstate"></a>mip::ExecutionState-Klasse 
Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
Clients sollten die Methoden nur aufrufen, um den erforderlichen Status abzurufen. Daher sollten Clients diese Schnittstelle aus Effizienzgründen implementieren, damit der entsprechende Status dynamisch und nicht im Voraus berechnet wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public std::string GetNewLabelId() const  |  Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.
 public ActionSource GetNewLabelActionSource() const  |  Ruft die Quelle für eine neue Bezeichnungsaktion ab
 public std::string GetContentIdentifier() const  |  Ruft den Inhaltsbezeichner ab, der das Dokument beschreibt. Dateibeispiel: [Pfad], E-Mail-Beispiel: [Betreff:Sender]
 public ContentState GetContentState() const  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
public std::pair<bool, std::string> IsDowngradeJustified() const  |  Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.
 public AssignmentMethod GetNewLabelAssignmentMethod() const  |  Ruft die Zuweisungsmethode für die neue Bezeichnung ab.
public std::vector<std::pair<std::string, std::string>> GetNewLabelExtendedProperties() const  |  Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.
public std::vector<std::pair<std::string, std::string>> GetContentMetadata(const std::vector<std::string>& names, const std::vector<std::string>& namePrefixes) const  |  Ruft die Metadatenelemente aus dem Inhalt ab.
public std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor() const  |  Ruft den Deskriptor für den Schutz ab
 public ContentFormat GetContentFormat() const  |  Ruft das Inhaltsformat ab.
 public ActionType GetSupportedActions() const  |  Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt
public virtual std::map<std::string, std::shared_ptr<ClassificationResult>> GetClassificationResults(const std::vector<std::string> &) const  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
  
## <a name="members"></a>Member
  
### <a name="getnewlabelid"></a>GetNewLabelId
Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.

  
**Rückgabe**: Die ID der Vertraulichkeitsbezeichnung, die ggf. auf den Inhalt angewendet werden soll. Wenn kein Inhalt vorhanden ist, kann die Bezeichnung entfernt werden.
  
### <a name="getnewlabelactionsource"></a>GetNewLabelActionSource
Ruft die Quelle für eine neue Bezeichnungsaktion ab

  
**Rückgabe:** Aktionsquelle
  
### <a name="getcontentidentifier"></a>GetContentIdentifier
Ruft den Inhaltsbezeichner ab, der das Dokument beschreibt. Dateibeispiel: [Pfad], E-Mail-Beispiel: [Betreff:Sender]

  
**Rückgabe:** Inhaltsbezeichner, der auf den Inhalt angewendet werden soll.
Dieser Wert wird in Form einer lesbaren Inhaltsbeschreibung überwacht.
  
### <a name="getcontentstate"></a>GetContentState
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Rückgabe:** Status der Inhaltsdaten
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.

  
**Rückgabe:** TRUE, wenn das Herabstufen berechtigt ist und eine Nachricht mit einer Begründung bereitgestellt wird; andernfalls FALSE 
  
**Weitere Informationen finden Sie unter:** [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
Ruft die Zuweisungsmethode für die neue Bezeichnung ab.

  
**Rückgabe**: Zuweisungsmethode STANDARD, PRIVILEGED, AUTO. 
  
**Weitere Informationen finden Sie unter:** mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties"></a>GetNewLabelExtendedProperties
Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.

  
**Rückgabe:** die erweiterten Eigenschaften, die auf den Inhalt angewendet werden sollen
  
### <a name="getcontentmetadata"></a>GetContentMetadata
Ruft die Metadatenelemente aus dem Inhalt ab.

  
**Rückgabe:** die Metadaten, die auf den Inhalt angewendet werden sollen Jedes Metadatenelement setzt sich aus einem Name-Wert-Paar zusammen.
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Ruft den Deskriptor für den Schutz ab

  
**Rückgabe:** der Deskriptor für den Schutz
  
### <a name="getcontentformat"></a>GetContentFormat
Ruft das Inhaltsformat ab.

  
**Rückgabe**: DEFAULT, EMAIL 
  
**Weitere Informationen finden Sie unter:** mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt

  
**Rückgabe**: eine maskierte Enumeration, die alle unterstützten Aktionstypen beschreibt
ActionType::Justify muss unterstützt werden. Wenn eine Erklärung für die Änderung einer Richtlinie oder einer Bezeichnung verlangt wird, wird stets eine Aktion zur Erklärung zurückgegeben.
  
### <a name="classificationresult"></a>ClassificationResult
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **classificationId**: eine Liste mit Klassifizierungs-IDs 



  
**Rückgabe**: eine Liste mit dem Klassifizierungsergebnis