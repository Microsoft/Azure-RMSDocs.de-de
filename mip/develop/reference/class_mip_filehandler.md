---
title: Klassen-Datei Handler
description: 'Dokumentiert die fileHandler:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: bf3866fb1ec06156ebf40b2efed8c44f8af4a4ce
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566959"
---
# <a name="class-filehandler"></a>Klassen-Datei Handler 
Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr \<ContentLabel\> GetLabel ()  |  Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
Public Std:: Vector \<std::pair\<std::string, std::string\> \> GetProperties (uint32_t Version)  |  Ruft die Dateieigenschaften gemäß Version ab.
Public Std:: shared_ptr \<ProtectionHandler\> getprotection ()  |  Startet das Abrufen der Schutzrichtlinie der Datei.
Public Std:: shared_ptr \<AsyncControl\> registercontentfortrackingandrevocationasync (bool isownernotificationaktivierte, Konstante Std:: shared_ptr \<ProtectionEngine::Observer\>& Observer, Konst Std:: shared_ptr \<void\>& context)  |  # # # #-Parameter
Public Std:: shared_ptr \<AsyncControl\> revokecontentasync (Konst Std:: shared_ptr \<ProtectionEngine::Observer\>& Observer, Konstante Std:: shared_ptr \<void\>& context)  |  Führen Sie eine Sperre für den Inhalt aus.
öffentliches void classifyasync (Konst Std:: shared_ptr \<void\>& Kontext)  |  Führt die Regeln im-Handler aus und gibt die Liste der auszuführenden Aktionen zurück.
public void inspectasync (Konst Std:: shared_ptr \<void\>& context)  |  Erstellen Sie ein Datei Inspektor-Objekt, das zum Abrufen von Dateiinhalten aus kompatiblen Dateiformaten verwendet wird.
öffentliches void setlabel (Konstante Std:: shared_ptr \<Label\>& Bezeichnung, Konstanten labelingoptions& labelingoptions, Konstante Schutzeinstellungen& Schutzeinstellungen)  |  Legt die Vertraulichkeitsbezeichnung für die Datei fest.
public void DeleteLabel(const LabelingOptions& labelingOptions)  |  Löscht die Vertraulichkeitsbezeichnung aus der Datei.
öffentliches void setprotection (Konstante Std:: shared_ptr \<ProtectionDescriptor\>& schutzdescriptor, Konstante Schutzeinstellungen& Schutzeinstellungen)  |  Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
öffentliches void setprotection (Konstante Std:: shared_ptr \<ProtectionHandler\>& schutzhandler)  |  Legt den Schutz für ein Dokument mithilfe eines vorhandenen Schutz Handlers fest.
public void RemoveProtection()  |  Entfernt den Schutz von der Datei. Wenn das ursprüngliche Dateiformat die Bezeichnung nicht unterstützt, geht die Bezeichnung verloren, wenn der Schutz entfernt wird. Wenn das Native Format die Bezeichnung unterstützt, werden die Bezeichnungs Metadaten beibehalten.
public void CommitAsync(const std::string& outputFilePath, const std::shared_ptr\<void\>& context) | Writes the changes to the file specified by the \|outputFilePath\ |  .
public void CommitAsync(const std::shared_ptr\<Stream\>& outputStream, const std::shared_ptr\<void\>& context) | Writes the changes to the stream specified by the \|outputStream\ |  .
public bool IsModified ()  |  Überprüft, ob Änderungen an der Datei vorgenommen wurden.
öffentliches void getdecryptedtemporaryfileasync (Konst Std:: shared_ptr \<void\>& Kontext)  |  Gibt einen Pfad zu einer temporären Datei (die nach Möglichkeit gelöscht wird) zurück, die den entschlüsselten Inhalt darstellt.
öffentliches void getdecryptedtemporarystreamasync (Konst Std:: shared_ptr \<void\>& Kontext)  |  Gibt einen Stream zurück, der den entschlüsselten Inhalt darstellt.
öffentliches void notifycommiterfolgreich (Konstante Std:: String& actualfilepath)  |  Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.
public std::string GetOutputFileName()  |  Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
  
## <a name="members"></a>Members
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Ruft die Dateieigenschaften gemäß Version ab.
  
### <a name="getprotection-function"></a>Getprotection-Funktion
Startet das Abrufen der Schutzrichtlinie der Datei.
  
### <a name="registercontentfortrackingandrevocationasync-function"></a>Registercontentfortrackingandrevocationasync-Funktion

Parameter:  
* **isownernotificationaktivierte**: Legen Sie diese Einstellung auf "true" fest, um den Besitzer bei der Entschlüsselung des Dokuments per e-Mail zu benachrichtigen, oder "false", um die Benachrichtigung nicht zu senden. 


* **observer**: eine Klasse, die die ProtectionHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="revokecontentasync-function"></a>Revokecontentasync-Funktion
Führen Sie eine Sperre für den Inhalt aus.

Parameter:  
* **observer**: eine Klasse, die die ProtectionHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="classifyasync-function"></a>Classifyasync-Funktion
Führt die Regeln im-Handler aus und gibt die Liste der auszuführenden Aktionen zurück.

  
**Rückgabe**: Liste der Aktionen, die auf den Inhalt angewendet werden sollten.
  
### <a name="inspectasync-function"></a>Inspectasync-Funktion
Erstellen Sie ein Datei Inspektor-Objekt, das zum Abrufen von Dateiinhalten aus kompatiblen Dateiformaten verwendet wird.

  
**Gibt Folgendes zurück**: ein Datei Inspektor.
  
### <a name="setlabel-function"></a>Setlabel-Funktion
Legt die Vertraulichkeitsbezeichnung für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst JustificationRequiredError aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
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