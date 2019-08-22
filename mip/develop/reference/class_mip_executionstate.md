---
title: mip::ExecutionState-Klasse
description: 'Dokumentiert die MIP:: executionstate-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 02e72dc55c12b3800ff76356da1fb7c3adf08fdd
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884354"
---
# <a name="class-mipexecutionstate"></a>mip::ExecutionState-Klasse 
Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
Clients sollten die Methoden nur aufrufen, um den erforderlichen Status abzurufen. Daher sollten Clients diese Schnittstelle aus Effizienzgründen implementieren, damit der entsprechende Status dynamisch und nicht im Voraus berechnet wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<Label\> getnewlabel () Konstanten  |  Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.
public std::string GetContentIdentifier() const  |  Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].
public virtual datastate getdatastate () Konstanten  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
Public Std::p Air\<bool, Std:: String\> isdowngradebug () Konstanten  |  Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.
public AssignmentMethod GetNewLabelAssignmentMethod() const  |  Ruft die Zuweisungsmethode für die neue Bezeichnung ab.
public virtual Std:: Vector\<Std::p Air\<Std:: String, Std:: String\> \> getnewlabelextendedproperties () Konstanten  |  Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.
Public Std:: Vector\<Std::p Air\<Std:: String, Std:: String\> \> getcontentmetadata (Konst Std:: Vector\<Std:: String\>& Names, Konstanten Std:: Vector\<Std:: String\>& nameprefixes) konstant  |  Ruft die Metadatenelemente aus dem Inhalt ab.
Public Std:: shared_ptr\<schutzdescriptor\> getschutzdescriptor () konstant  |  Ruft den Deskriptor für den Schutz ab
public ContentFormat GetContentFormat() const  |  Ruft das Inhaltsformat ab.
public ActionType GetSupportedActions() const  |  Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt
public virtual Std:: shared_ptr\<classificationresults\> getclassificationresults (Konst Std:: Vector\<Std:: shared_ptr\<classificationrequest\> \> &) konstant  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual Std:: map\<Std:: String, Std:: String\> getauditmetadata () Konstanten  |  Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.
  
## <a name="members"></a>Member
  
### <a name="getnewlabel-function"></a>Getnewlabel-Funktion
Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.

  
**Gibt Folgendes zurück**: Die ID der Vertraulichkeits Bezeichnung, die auf den Inhalt angewendet werden soll, wenn vorhanden ist, wird die Bezeichnung entfernt.
  
### <a name="getcontentidentifier-function"></a>Getcontentidentifier-Funktion
Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].

  
**Gibt Folgendes zurück**: Inhaltsbeschreibung, die auf den Inhalt angewendet werden soll.
Dieser Wert wird in Form einer lesbaren Inhaltsbeschreibung überwacht.
  
### <a name="getdatastate-function"></a>Getdatastate-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Gibt Folgendes zurück**: Zustand der Inhaltsdaten
  
### <a name="isdowngradejustified-function"></a>Isdowngradebug-Funktion
Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.

  
**Gibt Folgendes zurück**: True, wenn die Herabstufung rechtzeitig mit der Begründung messageelse false ist. 
  
**Weitere Informationen finden Sie unter:** [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod-function"></a>Getnewlabelaccessmentmethod-Funktion
Ruft die Zuweisungsmethode für die neue Bezeichnung ab.

  
**Gibt Folgendes zurück**: Die Zuweisungs Methode Standard, privilegiert, Auto. 
  
**Siehe auch**: [MIP:: accessmentmethod](mip-enums-and-structs.md#assignmentmethod-enum)
  
### <a name="getnewlabelextendedproperties-function"></a>Getnewlabelextendedproperties-Funktion
Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.

  
**Gibt Folgendes zurück**: Die erweiterten Eigenschaften, die auf den Inhalt angewendet werden.
  
### <a name="getcontentmetadata-function"></a>Getcontentmetadata-Funktion
Ruft die Metadatenelemente aus dem Inhalt ab.

  
**Gibt Folgendes zurück**: Die Metadaten, die auf den Inhalt angewendet werden. Jedes Metadatenelement setzt sich aus einem Name-Wert-Paar zusammen.
  
### <a name="getprotectiondescriptor-function"></a>Getschutzdescriptor-Funktion
Ruft den Deskriptor für den Schutz ab

  
**Gibt Folgendes zurück**: Der Schutz Deskriptor
  
### <a name="getcontentformat-function"></a>Getcontentformat-Funktion
Ruft das Inhaltsformat ab.

  
**Gibt Folgendes zurück**: STANDARD, E-MAIL 
  
**Siehe auch**: [MIP:: contentformat](mip-enums-and-structs.md#contentformat-enum)
  
### <a name="getsupportedactions-function"></a>Getsupportedactions-Funktion
Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt

  
**Gibt Folgendes zurück**: Eine maskierte Enumeration, die alle unterstützten Aktions Typen beschreibt.
ActionType::Justify muss unterstützt werden. Wenn eine Erklärung für die Änderung einer Richtlinie oder einer Bezeichnung verlangt wird, wird stets eine Aktion zur Erklärung zurückgegeben.
  
### <a name="getclassificationresults-function"></a>Getclassificationresults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **classificationids**: eine Liste der Klassifizierungs-IDs. 



  
**Gibt Folgendes zurück**: Eine Liste der Klassifizierungs Ergebnisse. gibt nullptr zurück, wenn kein Klassifizierungs Durchlauf ausgeführt wird.
  
### <a name="getauditmetadata-function"></a>Getauditmetadata-Funktion
Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.

  
**Gibt Folgendes zurück**: Eine Liste von anwendungsspezifischen Überwachungs Metadaten registrierter Schlüssel: Wert Paare Absender: E-Mail-ID für die Absender Empfänger: Stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy dar: E-Mail-ID für den Benutzer, der den Inhalt LastModifiedDate zuletzt geändert hat: Datum, an dem der Inhalt zuletzt geändert wurde