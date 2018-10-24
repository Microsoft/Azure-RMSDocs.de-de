---
title: Die Klasse „mip::FileEngines“
description: Referenz zur Klasse „ mip::FileEngine“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7342edf27b19f43881b2e8d378fa243d26f7056
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446072"
---
# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  Eine Liste der Vertraulichkeitsbezeichnungen
 public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
 public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.
public void CreateFileHandlerAsync(const std::string& inputFilePath, const ContentState contentState, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver, const std::shared_ptr<void>& context)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.
public void CreateFileHandlerAsync(const std::shared_ptr<Stream>& inputStream, const std::string& inputFilePath, const mip::ContentState contentState, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver, const std::shared_ptr<void>& context)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.
 public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Gibt die Engine-Einstellungen zurück.
  
### <a name="label"></a>Label
Eine Liste der Vertraulichkeitsbezeichnungen
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Rückgabe:** eine URL im Zeichenfolgenformat
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.

  
**Rückgabe:** TRUE, wenn eine Bezeichnung erforderlich ist; andernfalls FALSE.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.

Parameter:  
* **Die zu öffnende Datei**. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **contentState:** ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert 


* **Eine Klasse**, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.

Parameter:  
* **inputStream:** ein Stream, der die Dateidaten enthält 


* **inputFilePath:** der Dateipfad Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **contentState:** ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert 


* **fileHandlerObserver:** eine Klasse, die die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert 


* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **level:** Beschreibung der Protokollebene: Information/Fehler/Warnung 


* **eventType:** Beschreibung des Ereignistyps 


* **eventData:** dem Ereignis zugeordnete Daten

