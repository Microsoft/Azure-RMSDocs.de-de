---
title: Klassen-Datei Handler
description: 'Dokumentiert die fileHandler:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: fe04fd0303d5f5717690206760125932826f4708
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763171"
---
# <a name="class-filehandler"></a>Klassen-Datei Handler 
Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<contentlabel\> GetLabel ()  |  Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
Public Std:: shared_ptr\<schutzhandler\> getprotection ()  |  Startet das Abrufen der Schutzrichtlinie der Datei.
öffentliches void classifyasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Führt die Regeln im-Handler aus und gibt die Liste der auszuführenden Aktionen zurück.
öffentliches void inspectasync (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Erstellen Sie ein Datei Inspektor-Objekt, das zum Abrufen von Dateiinhalten aus kompatiblen Dateiformaten verwendet wird.
öffentliches void setlabel (Konstante Std:: shared_ptr\<Bezeichnung\>& Bezeichnung, Konstanten labelingoptions& labelingoptions, Konstante Schutzeinstellungen& Schutzeinstellungen)  |  Legt die Vertraulichkeitsbezeichnung für die Datei fest.
public void DeleteLabel(const LabelingOptions& labelingOptions)  |  Löscht die Vertraulichkeitsbezeichnung aus der Datei.
öffentliches void setprotection (Konstante Std:: shared_ptr\<schutzdescriptor\>& schutzdescriptor, Konstanten Schutzeinstellungen& Schutzeinstellungen)  |  Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
öffentliches void setprotection (Konstante Std:: shared_ptr\<Protection Handler\>& schutzhandler)  |  Legt den Schutz für ein Dokument mithilfe eines vorhandenen Schutz Handlers fest.
public void RemoveProtection()  |  Entfernt den Schutz von der Datei. Wenn das ursprüngliche Dateiformat die Bezeichnung nicht unterstützt, geht die Bezeichnung verloren, wenn der Schutz entfernt wird. Wenn das Native Format die Bezeichnung unterstützt, werden die Bezeichnungs Metadaten beibehalten.
öffentliches void commitasync (Konst Std:: String& outputfilepath, Konstante Std:: shared_ptr\<void\>& Kontext) | Writes the changes to the file specified by the \|outputFilePath\ |  .
öffentliches void commitasync (Konst Std:: shared_ptr\<Stream\>& OutputStream, Konstante Std:: shared_ptr\<void\>& Kontext) | Writes the changes to the stream specified by the \|outputStream\ |  .
public bool IsModified ()  |  Überprüft, ob Änderungen an der Datei vorgenommen wurden.
öffentliches void getdecryptedtemporaryfileasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Gibt einen Pfad zu einer temporären Datei (die nach Möglichkeit gelöscht wird) zurück, die den entschlüsselten Inhalt darstellt.
öffentliches void getdecryptedtemporarystreamasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Gibt einen Stream zurück, der den entschlüsselten Inhalt darstellt.
öffentliches void notifycommiterfolgreich (Konstante Std:: String& actualfilepath)  |  Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.
public std::string GetOutputFileName()  |  Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
  
## <a name="members"></a>Member
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
  
### <a name="getprotection-function"></a>Getprotection-Funktion
Startet das Abrufen der Schutzrichtlinie der Datei.
  
### <a name="classifyasync-function"></a>Classifyasync-Funktion
Führt die Regeln im-Handler aus und gibt die Liste der auszuführenden Aktionen zurück.

  
**Rückgabe**: Liste der Aktionen, die auf den Inhalt angewendet werden sollten.
  
### <a name="inspectasync-function"></a>Inspectasync-Funktion
Erstellen Sie ein Datei Inspektor-Objekt, das zum Abrufen von Dateiinhalten aus kompatiblen Dateiformaten verwendet wird.

  
**Gibt Folgendes zurück**: ein Datei Inspektor.
  
### <a name="setlabel-function"></a>Setlabel-Funktion
Legt die Vertraulichkeitsbezeichnung für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst [JustificationRequiredError](class_mip_justificationrequirederror.md) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="deletelabel-function"></a>Delta Label-Funktion
Löscht die Vertraulichkeitsbezeichnung aus der Datei.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst JustificationRequiredError aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="setprotection-function"></a>Setprotection-Funktion
Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="setprotection-function"></a>Setprotection-Funktion
Legt den Schutz für ein Dokument mithilfe eines vorhandenen Schutz Handlers fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="removeprotection-function"></a>Removeprotection-Funktion
Entfernt den Schutz von der Datei. Wenn das ursprüngliche Dateiformat die Bezeichnung nicht unterstützt, geht die Bezeichnung verloren, wenn der Schutz entfernt wird. Wenn das Native Format die Bezeichnung unterstützt, werden die Bezeichnungs Metadaten beibehalten.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="commitasync-function"></a>Commitasync-Funktion
Schreibt die Änderungen in die Datei, die durch den Parameter |outputFilePath| angegeben werden.
FileHandler::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="commitasync-function"></a>Commitasync-Funktion
Schreibt die Änderungen in den Datenstrom, der durch den Parameter |outputStream| angegeben wird.
FileHandler::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="ismodified-function"></a>IsModified-Funktion
Überprüft, ob Änderungen an der Datei vorgenommen wurden.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="getdecryptedtemporaryfileasync-function"></a>Getdecryptedtemporaryfileasync-Funktion
Gibt einen Pfad zu einer temporären Datei (die nach Möglichkeit gelöscht wird) zurück, die den entschlüsselten Inhalt darstellt.
FileHandler::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="getdecryptedtemporarystreamasync-function"></a>Getdecryptedtemporarystreamasync-Funktion
Gibt einen Stream zurück, der den entschlüsselten Inhalt darstellt.
FileHandler::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="notifycommitsuccessful-function"></a>Notifycommiterfolgreiches-Funktion
Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.

Parameter:  
* **actualfilepath**: der tatsächliche Dateipfad für die Ausgabedatei. 


Löst ein Überprüfungsereignis aus
  
### <a name="getoutputfilename-function"></a>Getoutputfilename-Funktion
Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.