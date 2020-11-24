---
title: Klasse executionstate
description: 'Dokumentiert die executionstate:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: f73c3e366f1be0647d2c9a7de78f37b6a9a95549
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566991"
---
# <a name="class-executionstate"></a>Klasse executionstate 
Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
Clients sollten die Methoden nur aufrufen, um den erforderlichen Status abzurufen. Daher sollten Clients diese Schnittstelle aus Effizienzgründen implementieren, damit der entsprechende Status dynamisch und nicht im Voraus berechnet wird.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr \<Label\> getnewlabel () Konstanten  |  Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.
public std::string GetContentIdentifier() const  |  Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].
public virtual datastate getdatastate () Konstanten  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
Public Std::p Air \<bool, std::string\> isdowngraabgerechtfer() konstant  |  Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.
public AssignmentMethod GetNewLabelAssignmentMethod() const  |  Ruft die Zuweisungsmethode für die neue Bezeichnung ab.
public virtual Std:: Vector \<std::pair\<std::string, std::string\> \> getnewlabelextendedproperties () Konstanten  |  Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.
Public Std:: Vector \<MetadataEntry\> getcontentmetadata (Konst Std:: Vector \<std::string\>& Names, Konstanten Std:: Vector \<std::string\>& nameprefixes) Konstanten  |  Ruft die Metadatenelemente aus dem Inhalt ab.
public std::shared_ptr\<ProtectionDescriptor\> GetProtectionDescriptor() const  |  Ruft den Deskriptor für den Schutz ab
public ContentFormat GetContentFormat() const  |  Ruft das Inhaltsformat ab.
public virtual MetadataVersion GetContentMetadataVersion () konstant  |  Ruft die höchste Metadatenversion ab, die von der Anwendung für den Mandanten unterstützt wird.
public ActionType GetSupportedActions() const  |  Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt
public virtual Std:: shared_ptr \<ClassificationResults\> getclassificationresults (Konstanten Std:: Vector \<std::shared_ptr\<ClassificationRequest\> \> &) konstant  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual Std:: map \<std::string, std::string\> getauditmetadata () Konstanten  |  Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.
  
## <a name="members"></a>Members
  
### <a name="getnewlabel-function"></a>Getnewlabel-Funktion
Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.

  
**Rückgabe**: Die ID der Vertraulichkeitsbezeichnung, die ggf. auf den Inhalt angewendet werden soll. Wenn kein Inhalt vorhanden ist, kann die Bezeichnung entfernt werden.
  
### <a name="getcontentidentifier-function"></a>Getcontentidentifier-Funktion
Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].

  
**Gibt Folgendes zurück**: Inhaltsbeschreibung, die auf den Inhalt angewendet werden soll.
Dieser Wert wird in Form einer lesbaren Inhaltsbeschreibung überwacht.
  
### <a name="getdatastate-function"></a>Getdatastate-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Rückgabe:** Status der Inhaltsdaten
  
### <a name="isdowngradejustified-function"></a>Isdowngradebug-Funktion
Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.

  
**Rückgabe:** TRUE, wenn das Herabstufen berechtigt ist und eine Nachricht mit einer Begründung bereitgestellt wird; andernfalls FALSE 
  
**Siehe auch**: MIP:: justifyaction
  
### <a name="getnewlabelassignmentmethod-function"></a>Getnewlabelaccessmentmethod-Funktion
Ruft die Zuweisungsmethode für die neue Bezeichnung ab.

  
**Rückgabe**: Zuweisungsmethode STANDARD, PRIVILEGED, AUTO. 
  
**Weitere Informationen finden Sie unter:** mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties-function"></a>Getnewlabelextendedproperties-Funktion
Gibt erweiterte Eigenschaften einer neuen Bezeichnung zurück.

  
**Rückgabe:** die erweiterten Eigenschaften, die auf den Inhalt angewendet werden sollen
  
### <a name="getcontentmetadata-function"></a>Getcontentmetadata-Funktion
Ruft die Metadatenelemente aus dem Inhalt ab.

  
**Rückgabe:** die Metadaten, die auf den Inhalt angewendet werden sollen Jedes Metadatenelement setzt sich aus einem Name-Wert-Paar zusammen.
  
### <a name="getprotectiondescriptor-function"></a>Getschutzdescriptor-Funktion
Ruft den Deskriptor für den Schutz ab

  
**Rückgabe:** der Deskriptor für den Schutz
  
### <a name="getcontentformat-function"></a>Getcontentformat-Funktion
Ruft das Inhaltsformat ab.

  
**Rückgabe**: DEFAULT, EMAIL 
  
**Weitere Informationen finden Sie unter:** mip::ContentFormat
  
### <a name="getcontentmetadataversion-function"></a>GetContentMetadataVersion-Funktion
Ruft die höchste Metadatenversion ab, die von der Anwendung für den Mandanten unterstützt wird.

  
**Gibt Folgendes zurück**: Content Metadata Version. Wenn der Wert 0 ist, werden die Metadaten nicht versioniert. Wenn ein Dateiformat mehrere Versionen von Metadaten unterstützt, ermöglicht MIP, alle Metadaten zu verstehen und detaillierte Metadatenänderungen auf der Grundlage der Versions Werte zu melden.
  
### <a name="getsupportedactions-function"></a>Getsupportedactions-Funktion
Ruft eine maskierte Enumeration ab, die alle unterstützten Aktionstypen beschreibt

  
**Rückgabe**: eine maskierte Enumeration, die alle unterstützten Aktionstypen beschreibt
ActionType::Justify muss unterstützt werden. Wenn eine Erklärung für die Änderung einer Richtlinie oder einer Bezeichnung verlangt wird, wird stets eine Aktion zur Erklärung zurückgegeben.
  
### <a name="getclassificationresults-function"></a>Getclassificationresults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **classificationids**: eine Liste der Klassifizierungs-IDs. 



  
**Returns**: eine Liste der Klassifizierungs Ergebnisse. gibt nullptr zurück, wenn kein Klassifizierungs Durchlauf ausgeführt wird.
  
### <a name="getauditmetadata-function"></a>Getauditmetadata-Funktion
Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.

  
**Gibt Folgendes zurück**: eine Liste von anwendungsspezifischen Überwachungs Metadaten registrierter Schlüssel: Wert Paare Absender: e-Mail-ID für Absender Empfänger: stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy: e-Mail-ID für den Benutzer dar, der den Inhalt zuletzt geändert hat: Datum, an dem der Inhalt zuletzt geändert wurde.