---
title: mip::FileHandler-Klasse
description: 'Beschreibt die Klasse:: fileHandler-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 664478f074334196b78b5583867224e1a9f482d2
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56253066"
---
# <a name="class-mipfilehandler"></a>mip::FileHandler-Klasse 
Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<ContentLabel\> GetLabel()  |  Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
Public Std:: shared_ptr\<ProtectionHandler\> GetProtection()  |  Startet das Abrufen der Schutzrichtlinie der Datei.
Öffentliche void ClassifyAsync (const Std:: shared_ptr\<"void"\>& Kontext)  |  Führt die Regeln im Ereignishandler, und gibt die Liste der Aktionen, die ausgeführt werden.
public void SetLabel(const std::string& labelId, const LabelingOptions& labelingOptions)  |  Legt die Vertraulichkeitsbezeichnung für die Datei fest.
public void DeleteLabel(const LabelingOptions& labelingOptions)  |  Löscht die Vertraulichkeitsbezeichnung aus der Datei.
Öffentliche void SetProtection (const Std:: shared_ptr\<ProtectionDescriptor\>& ProtectionDescriptor)  |  Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
Öffentliche void SetProtection (const Std:: vector\<uint8_t\>& SerializedPublishingLicense, const Std:: vector\<uint8_t\>& SerializedProtectionInfo)  |  Benutzerdefinierte oder Template-basierten Berechtigungen (gemäß SerializedPublishingLicense und SerializedProtectionInfo) wird in der Datei festgelegt.
public void RemoveProtection()  |  Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
public void CommitAsync(const std::string& outputFilePath, const std::shared_ptr\<void\>& context) | Writes the changes to the file specified by the \|outputFilePath\ |  der Parameter.
Öffentliche void CommitAsync (const Std:: shared_ptr\<Stream\>& OutputStream, const Std:: shared_ptr\<"void"\>& Kontext) | Writes the changes to the stream specified by the \|outputStream\ |  der Parameter.
public void GetDecryptedTemporaryFileAsync(const std::shared_ptr\<void\>& context)  |  Gibt einen Pfad in eine temporäre Datei (die ggf. gelöscht werden) -, das den entschlüsselten Inhalt darstellt.
public void NotifyCommitSuccessful(const std::string& contentIdentifier)  |  Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.
public std::string GetOutputFileName()  |  Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
  
## <a name="members"></a>Member
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
  
### <a name="getprotection-function"></a>GetProtection-Funktion
Startet das Abrufen der Schutzrichtlinie der Datei.
  
### <a name="classifyasync-function"></a>ClassifyAsync-Funktion
Führt die Regeln im Ereignishandler, und gibt die Liste der Aktionen, die ausgeführt werden.

  
**Gibt**: Liste der Aktionen, die auf den Inhalt angewendet werden soll.
  
### <a name="setlabel-function"></a>SetLabel-Funktion
Legt die Vertraulichkeitsbezeichnung für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst [JustificationRequiredError](class_mip_justificationrequirederror.md) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="deletelabel-function"></a>DeleteLabel-Funktion
Löscht die Vertraulichkeitsbezeichnung aus der Datei.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst [JustificationRequiredError](class_mip_justificationrequirederror.md) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="setprotection-function"></a>SetProtection-Funktion
Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="setprotection-function"></a>SetProtection-Funktion
Benutzerdefinierte oder Template-basierten Berechtigungen (gemäß SerializedPublishingLicense und SerializedProtectionInfo) wird in der Datei festgelegt.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="removeprotection-function"></a>RemoveProtection-Funktion
Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="commitasync-function"></a>CommitAsync-Funktion
Schreibt die Änderungen in die Datei, die durch den Parameter |outputFilePath| angegeben werden.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="commitasync-function"></a>CommitAsync-Funktion
Schreibt die Änderungen in den Datenstrom, der durch den Parameter |outputStream| angegeben wird.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="getdecryptedtemporaryfileasync-function"></a>GetDecryptedTemporaryFileAsync-Funktion
Gibt einen Pfad in eine temporäre Datei (die ggf. gelöscht werden) -, das den entschlüsselten Inhalt darstellt.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="notifycommitsuccessful-function"></a>NotifyCommitSuccessful-Funktion
Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.

Parameter:  
* **ContentIdentifier**: Beispiel für eine Datei: 'C:\mip-sdk-for-cpp\files\audit.docx"[' Pfad\Dateiname'] Beispiel für eine e-Mail: "RE: Audit design:user1@contoso.com"[Betreff: Absender] 


Löst ein Überprüfungsereignis aus
  
### <a name="getoutputfilename-function"></a>GetOutputFileName-Funktion
Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
