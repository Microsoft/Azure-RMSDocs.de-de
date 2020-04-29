---
title: Klasse DocumentState
description: 'Dokumentiert die DocumentState:: nicht definierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 674e43b89a43fe90fa1fb38fb7c6d1d51a7326e0
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763318"
---
# <a name="class-documentstate"></a>Klasse DocumentState 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetContentIdentifier() const  |  Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].
public virtual datastate getdatastate () Konstanten  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
Public Std:: Vector\<MetadataEntry\> getcontentmetadata (Konst Std:: Vector\<Std:: String\>& Names, Konstanten Std:: Vector\<Std:: String\>& nameprefixes) Konstanten  |  Ruft die Metadatenelemente aus dem Inhalt ab.
Public Std:: shared_ptr\<schutzdescriptor\> getschutzdescriptor () konstant  |  Ruft den Deskriptor für den Schutz ab
public ContentFormat GetContentFormat() const  |  Ruft das Inhaltsformat ab.
public virtual Ganzzahl ohne Vorzeichen int GetContentMetadataVersion () konstant  |  Ruft die höchste Metadatenversion ab, die von der Anwendung für den Mandanten unterstützt wird.
public virtual Std:: shared_ptr\<classificationresults\> getclassificationresults (konstant Std::\<Vector Std:: shared_ptr\<classificationrequest\> \> &) konstant  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual Std:: map\<Std:: String, Std:: String\> getauditmetadata () Konstanten  |  Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.
public virtual Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getlastmodifiedtime () Konstanten  |  Rückgabe eines Zeitpunkts auf den Zeitpunkt der letzten Änderung des Dokuments.
  
## <a name="members"></a>Member
  
### <a name="getcontentidentifier-function"></a>Getcontentidentifier-Funktion
Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].

  
**Gibt Folgendes zurück**: Inhaltsbeschreibung, die auf den Inhalt angewendet werden soll.
Dieser Wert wird in Form einer lesbaren Inhaltsbeschreibung überwacht.
  
### <a name="getdatastate-function"></a>Getdatastate-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Rückgabe:** Status der Inhaltsdaten
  
### <a name="getcontentmetadata-function"></a>Getcontentmetadata-Funktion
Ruft die Metadatenelemente aus dem Inhalt ab.

  
**Rückgabe:** die Metadaten, die auf den Inhalt angewendet werden sollen 
  
**Siehe auch**: MIP:: MetadataEntry.
  
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
  
### <a name="getclassificationresults-function"></a>Getclassificationresults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **classificationids**: eine Liste der Klassifizierungs-IDs. 



  
**Returns**: eine Liste der Klassifizierungs Ergebnisse. gibt nullptr zurück, wenn kein Klassifizierungs Durchlauf ausgeführt wird.
  
### <a name="getauditmetadata-function"></a>Getauditmetadata-Funktion
Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.

  
**Gibt Folgendes zurück**: eine Liste von anwendungsspezifischen Überwachungs Metadaten registrierter Schlüssel: Wert Paare Absender: e-Mail-ID für Absender Empfänger: stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy: e-Mail-ID für den Benutzer dar, der den Inhalt zuletzt geändert hat: Datum, an dem der Inhalt zuletzt geändert wurde.
  
### <a name="getlastmodifiedtime-function"></a>Getlastmodifiedtime-Funktion
Rückgabe eines Zeitpunkts auf den Zeitpunkt der letzten Änderung des Dokuments.

  
**Gibt Folgendes zurück**: der Zeitpunkt der letzten Änderung des Dokument Zeitpunkts.