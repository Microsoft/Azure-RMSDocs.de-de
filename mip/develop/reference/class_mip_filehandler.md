---
title: mip::FileHandler-Klasse
description: 'Dokumentiert die MIP:: fileHandler-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: a75187820cea8b806a65eebea937ed091f0c62e0
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884325"
---
# <a name="class-mipfilehandler"></a>mip::FileHandler-Klasse 
Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<contentlabel\> GetLabel ()  |  Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
Public Std:: shared_ptr\<schutzhandler\> getprotection ()  |  Startet das Abrufen der Schutzrichtlinie der Datei.
öffentliches void classifyasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Führt die Regeln im-Handler aus und gibt die Liste der auszuführenden Aktionen zurück.
public void inspectasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Erstellen Sie ein Datei Inspektor-Objekt, das zum Abrufen von Dateiinhalten aus kompatiblen Dateiformaten verwendet wird.
öffentliches void setlabel (Konstante Std:: shared_ptr\<Label\>& Bezeichnung, Konstanten labelingoptions & labelingoptions, Konstante Schutzeinstellungen & Schutzeinstellungen)  |  Legt die Vertraulichkeitsbezeichnung für die Datei fest.
public void DeleteLabel(const LabelingOptions& labelingOptions)  |  Löscht die Vertraulichkeitsbezeichnung aus der Datei.
öffentliches void setprotection (Konstante Std:: shared_ptr\<schutzdescriptor\>& schutzdescriptor, Konstanten Schutzeinstellungen & Schutzeinstellungen)  |  Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
public void RemoveProtection()  |  Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
öffentliches void commitasync (Konstante Std:: String & outputfilepath, Konst Std:: shared_ptr\<void\>& context) | Writes the changes to the file specified by the \|outputFilePath\ |  angegeben.
öffentliches void commitasync (Konst Std:: shared_ptr\<Stream\>& OutputStream, Konstante Std:: shared_ptr\<void\>& context) | Writes the changes to the stream specified by the \|outputStream\ |  angegeben.
öffentliches void getdecryptedtemporaryfileasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Gibt einen Pfad zu einer temporären Datei (die nach Möglichkeit gelöscht wird) zurück, die den entschlüsselten Inhalt darstellt.
öffentliches void getdecryptedtemporarystreamasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Gibt einen Stream zurück, der den entschlüsselten Inhalt darstellt.
öffentliches void notifycommiterfolgreich (Konstante Std:: String & actualfilepath)  |  Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.
public std::string GetOutputFileName()  |  Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
  
## <a name="members"></a>Member
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
  
### <a name="getprotection-function"></a>Getprotection-Funktion
Startet das Abrufen der Schutzrichtlinie der Datei.
  
### <a name="classifyasync-function"></a>Classifyasync-Funktion
Führt die Regeln im-Handler aus und gibt die Liste der auszuführenden Aktionen zurück.

  
**Gibt Folgendes zurück**: Liste der Aktionen, die auf den Inhalt angewendet werden sollen.
  
### <a name="inspectasync-function"></a>Inspectasync-Funktion
Erstellen Sie ein Datei Inspektor-Objekt, das zum Abrufen von Dateiinhalten aus kompatiblen Dateiformaten verwendet wird.

  
**Gibt Folgendes zurück**: Ein Datei Inspektor.
  
### <a name="setlabel-function"></a>Setlabel-Funktion
Legt die Vertraulichkeitsbezeichnung für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst [JustificationRequiredError](class_mip_justificationrequirederror.md) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="deletelabel-function"></a>Delta Label-Funktion
Löscht die Vertraulichkeitsbezeichnung aus der Datei.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst [JustificationRequiredError](class_mip_justificationrequirederror.md) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="setprotection-function"></a>Setprotection-Funktion
Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="removeprotection-function"></a>Removeprotection-Funktion
Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="commitasync-function"></a>Commitasync-Funktion
Schreibt die Änderungen in die Datei, die durch den Parameter |outputFilePath| angegeben werden.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="commitasync-function"></a>Commitasync-Funktion
Schreibt die Änderungen in den Datenstrom, der durch den Parameter |outputStream| angegeben wird.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="getdecryptedtemporaryfileasync-function"></a>Getdecryptedtemporaryfileasync-Funktion
Gibt einen Pfad zu einer temporären Datei (die nach Möglichkeit gelöscht wird) zurück, die den entschlüsselten Inhalt darstellt.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="getdecryptedtemporarystreamasync-function"></a>Getdecryptedtemporarystreamasync-Funktion
Gibt einen Stream zurück, der den entschlüsselten Inhalt darstellt.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="notifycommitsuccessful-function"></a>Notifycommiterfolgreiches-Funktion
Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.

Parameter:  
* **actualFilePath**: Der tatsächliche Dateipfad für die Ausgabedatei. 


Löst ein Überprüfungsereignis aus
  
### <a name="getoutputfilename-function"></a>Getoutputfilename-Funktion
Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.