---
title: mip::FileHandler-Klasse
description: 'Dokumentiert die MIP:: fileHandler-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: b2a6e3cd6de886c3e3983442a1ec7185b688b662
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73558839"
---
# <a name="class-mipfilehandler"></a>mip::FileHandler-Klasse 
Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<contentlabel\> GetLabel ()  |  Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
Public Std:: shared_ptr\<schutzhandler\> getprotection ()  |  Startet das Abrufen der Schutzrichtlinie der Datei.
öffentliches void classifyasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Führt die Regeln im-Handler aus und gibt die Liste der auszuführenden Aktionen zurück.
public void inspectasync (Konstante Std:: shared_ptr\<void\>& Kontext)  |  Erstellen Sie ein Datei Inspektor-Objekt, das zum Abrufen von Dateiinhalten aus kompatiblen Dateiformaten verwendet wird.
öffentliches void setlabel (Konstante Std:: shared_ptr\<Bezeichnung\>& Bezeichnung, Konstanten labelingoptions & labelingoptions, Konstante Schutzeinstellungen & Schutzeinstellungen)  |  Legt die Vertraulichkeitsbezeichnung für die Datei fest.
public void DeleteLabel(const LabelingOptions& labelingOptions)  |  Löscht die Vertraulichkeitsbezeichnung aus der Datei.
öffentliches void setprotection (Konstante Std:: shared_ptr\<schutzdescriptor\>& Schutz Deskriptor, Konstanten Schutzeinstellungen & Schutzeinstellungen)  |  Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
öffentliches void setprotection (Konstante Std:: shared_ptr\<schutzhandler\>& Schutz Handler)  |  Legt den Schutz für ein Dokument mithilfe eines vorhandenen Schutz Handlers fest.
public void RemoveProtection()  |  Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
öffentliches void commitasync (Konst Std:: String & outputfilepath, Konstanten Std:: shared_ptr\<void\>& Kontext) | Writes the changes to the file specified by the \|outputFilePath\ |  übergeben.
öffentliches void commitasync (Konstanten Std:: shared_ptr\<Stream\>& OutputStream, Konstanten Std:: shared_ptr\<void\>& Kontext) | Writes the changes to the stream specified by the \|outputStream\ |  übergeben.
public bool IsModified ()  |  Überprüft, ob Änderungen an der Datei vorgenommen wurden.
öffentliches void getdecryptedtemporaryfileasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Gibt einen Pfad zu einer temporären Datei (die nach Möglichkeit gelöscht wird) zurück, die den entschlüsselten Inhalt darstellt.
öffentliches void getdecryptedtemporarystreamasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Gibt einen Stream zurück, der den entschlüsselten Inhalt darstellt.
öffentliches void notifycommiterfolgreich (Konstante Std:: String & actualfilepath)  |  Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.
public std::string GetOutputFileName()  |  Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
öffentliches statisches bool IsProtected (Konstante Std:: String & filePath, Konstanten Std:: shared_ptr<MipContext>& mipcontext) | Überprüft, ob eine Datei geschützt ist oder nicht.
public static FILE_API Std:: Vector&lt;uint8_t&gt; __CDECL MIP:: fileHandler:: getserializedpublishinglicense | Rückgabe der Veröffentlichungs Lizenz, wenn Sie in der Datei gespeichert ist

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
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die privilegierte und die Auto-Methode ermöglichen es der API, jede vorhandene Bezeichnung außer Kraft zu setzen, wenn Sie für das Festlegen der Bezeichnung "Recht cationrequirements derror" festlegen, dass der Vorgang (über den Parameter "labelingoptions")
  
### <a name="deletelabel-function"></a>Delta Label-Funktion
Löscht die Vertraulichkeitsbezeichnung aus der Datei.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die privilegierte und die Auto-Methode ermöglichen es der API, jede vorhandene Bezeichnung außer Kraft zu setzen, wenn Sie für das Festlegen der Bezeichnung "Recht cationrequirements derror" festlegen, dass der Vorgang (über den Parameter "labelingoptions")
  
### <a name="setprotection-function"></a>Setprotection-Funktion
Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="setprotection-function"></a>Setprotection-Funktion
Legt den Schutz für ein Dokument mithilfe eines vorhandenen Schutz Handlers fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="removeprotection-function"></a>Removeprotection-Funktion
Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="commitasync-function"></a>Commitasync-Funktion
Schreibt die Änderungen in die Datei, die durch den Parameter |outputFilePath| angegeben werden.
FileHandler:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="commitasync-function"></a>Commitasync-Funktion
Schreibt die Änderungen in den Datenstrom, der durch den Parameter |outputStream| angegeben wird.
FileHandler:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="ismodified-function"></a>IsModified-Funktion
Überprüft, ob Änderungen an der Datei vorgenommen wurden.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="getdecryptedtemporaryfileasync-function"></a>Getdecryptedtemporaryfileasync-Funktion
Gibt einen Pfad zu einer temporären Datei (die nach Möglichkeit gelöscht wird) zurück, die den entschlüsselten Inhalt darstellt.
FileHandler:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="getdecryptedtemporarystreamasync-function"></a>Getdecryptedtemporarystreamasync-Funktion
Gibt einen Stream zurück, der den entschlüsselten Inhalt darstellt.
FileHandler:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="notifycommitsuccessful-function"></a>Notifycommiterfolgreiches-Funktion
Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.

Parameter:  
* **actualfilepath**: der tatsächliche Dateipfad für die Ausgabedatei. 


Löst ein Überprüfungsereignis aus
  
### <a name="getoutputfilename-function"></a>Getoutputfilename-Funktion
Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.

### <a name="isprotected-function"></a>IsProtected-Funktion
Überprüft, ob eine Datei geschützt ist oder nicht.

### <a name="getserializedpublishinglicense-function"></a>Getserializedpublishinglicense-Funktion
Rückgabe der Veröffentlichungs Lizenz, wenn Sie in der Datei gespeichert ist