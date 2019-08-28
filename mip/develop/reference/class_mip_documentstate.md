---
title: MIP::D ocenumentstate-Klasse
description: Dokumentiert die MIP::d ocenumentstate-Klasse des Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: d76da1fa15027abbac56b9432ef67c8d1b0996d9
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70055157"
---
# <a name="class-mipdocumentstate"></a>MIP::D ocenumentstate-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetContentIdentifier() const  |  Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].
public virtual datastate getdatastate () Konstanten  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
Public Std:: Vector\<Std::p Air\<Std:: String, Std:: String\> \> getcontentmetadata (Konst Std:: Vector\<Std:: String\>& Names, Konstanten Std:: Vector\<Std:: String\>& nameprefixes) konstant  |  Ruft die Metadatenelemente aus dem Inhalt ab.
Public Std:: shared_ptr\<schutzdescriptor\> getschutzdescriptor () konstant  |  Ruft den Deskriptor für den Schutz ab
public ContentFormat GetContentFormat() const  |  Ruft das Inhaltsformat ab.
public virtual Std:: shared_ptr\<classificationresults\> getclassificationresults (Konst Std:: Vector\<Std:: shared_ptr\<classificationrequest\> \> &) konstant  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual Std:: map\<Std:: String, Std:: String\> getauditmetadata () Konstanten  |  Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.
  
## <a name="members"></a>Member
  
### <a name="getcontentidentifier-function"></a>Getcontentidentifier-Funktion
Ruft die Inhaltsbeschreibung ab, die das Dokument beschreibt. Beispiel für eine Datei: [Pfad\Dateiname] Beispiel für eine e-Mail: [Subject: Sender].

  
**Gibt Folgendes zurück**: Inhaltsbeschreibung, die auf den Inhalt angewendet werden soll.
Dieser Wert wird in Form einer lesbaren Inhaltsbeschreibung überwacht.
  
### <a name="getdatastate-function"></a>Getdatastate-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Gibt Folgendes zurück**: Zustand der Inhaltsdaten
  
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
  
### <a name="getclassificationresults-function"></a>Getclassificationresults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **classificationids**: eine Liste der Klassifizierungs-IDs. 



  
**Gibt Folgendes zurück**: Eine Liste der Klassifizierungs Ergebnisse. gibt nullptr zurück, wenn kein Klassifizierungs Durchlauf ausgeführt wird.
  
### <a name="getauditmetadata-function"></a>Getauditmetadata-Funktion
Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.

  
**Gibt Folgendes zurück**: Eine Liste von anwendungsspezifischen Überwachungs Metadaten registrierter Schlüssel: Wert Paare Absender: E-Mail-ID für die Absender Empfänger: Stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy dar: E-Mail-ID für den Benutzer, der den Inhalt LastModifiedDate zuletzt geändert hat: Datum, an dem der Inhalt zuletzt geändert wurde