---
title: Die Klasse „mip::FileHandler“
description: Referenz zur Klasse „mip::FileHandler“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: efae18bdc10f8878f255f35c608a50482a29887b
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446123"
---
# <a name="class-mipfilehandler"></a>mip::FileHandler-Klasse 
Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public void GetLabelAsync(const std::shared_ptr<void>& context)  |  Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
public void GetProtectionAsync(const std::shared_ptr<void>& context)  |  Startet das Abrufen der Schutzrichtlinie der Datei.
 public void SetLabel(const std::string& labelId, const LabelingOptions& labelingOptions)  |  Legt die Vertraulichkeitsbezeichnung für die Datei fest.
 public void DeleteLabel(const LabelingOptions& labelingOptions)  |  Löscht die Vertraulichkeitsbezeichnung aus der Datei.
public void SetProtection(const std::shared_ptr<ProtectionDescriptor>& protectionDescriptor)  |  Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
 public void RemoveProtection()  |  Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
public void CommitAsync(const std::string& outputFilePath, const std::shared_ptr<void>& context) | Writes the changes to the file specified by the \|outputFilePath\ |  übergeben.
public void CommitAsync(const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& context) | Writes the changes to the stream specified by the \|outputStream\ |  übergeben.
 public void NotifyCommitSuccessful(const std::string& contentIdentifier)  |  Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.
 public std::string GetOutputFileName()  |  Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
  
## <a name="members"></a>Member
  
### <a name="getlabelasync"></a>GetLabelAsync
Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.

Parameter:  
* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
### <a name="getprotectionasync"></a>GetProtectionAsync
Startet das Abrufen der Schutzrichtlinie der Datei.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.

Parameter:  
* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
### <a name="setlabel"></a>SetLabel
Legt die Vertraulichkeitsbezeichnung für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst [JustificationRequiredError](class_mip_justificationrequirederror.md) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="deletelabel"></a>DeleteLabel
Löscht die Vertraulichkeitsbezeichnung aus der Datei.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden „Privileged“ und „Auto“ ermöglichen es der API, bestehende Bezeichnungen außer Kraft zu setzen. Löst [JustificationRequiredError](class_mip_justificationrequirederror.md) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung (über den labelingOptions-Parameter) erfordert.
  
### <a name="setprotection"></a>SetProtection
Legt benutzerdefinierte oder vorlagenbasierte Berechtigungen (entsprechend „protectionDescriptor->GetProtectionType“) für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="removeprotection"></a>RemoveProtection
Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
  
### <a name="commitasync"></a>CommitAsync
Schreibt die Änderungen in die Datei, die durch den Parameter |outputFilePath| angegeben werden.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="commitasync"></a>CommitAsync
Schreibt die Änderungen in den Datenstrom, der durch den Parameter |outputStream| angegeben wird.
[FileHandler::Observer](class_mip_filehandler_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="notifycommitsuccessful"></a>NotifyCommitSuccessful
Soll aufgerufen werden, wenn die Änderungen auf den Datenträger committet wurden.

Parameter:  
* **contentIdentifier:** Dateibeispiel: „C:\mip-sdk-for-cpp\files\audit.docx“ [Pfad] E-Mail-Beispiel „RE: Überprüfung design:user1@contoso.com“ [Betreff:Sender] 


Löst ein Überprüfungsereignis aus
  
### <a name="getoutputfilename"></a>GetOutputFileName
Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.