---
title: Die Klasse „mip::LoggerDelegate“
description: Referenz zur Klasse „mip::LoggerDelegate“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b25cdb177735feccfa5c4d344613e4747d18b77f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445851"
---
# <a name="class-miploggerdelegate"></a>mip::LoggerDelegate-Klasse 
Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public void Init(const std::string& storagePath, LogLevel logLevel)  |  Initialisiert die Protokollierung.
 public LogLevel GetLogLevel() const  |  Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen würde.
 public void Flush()  |  Leert die Protokolldaten.
 public void WriteToLog(const LogLevel level, const std::string& message, const std::string& function, const std::string& file, const int32_t line)  |  Schreibt eine Protokollanweisung in eine Protokolldatei.
  
## <a name="members"></a>Member
  
### <a name="init"></a>Init
Initialisiert die Protokollierung.

Parameter:  
* **storagePath**: Der Pfad zum Speicherort, an dem der persistente Status, einschließlich Protokollen, gespeichert werden kann. 


* **logLevel:** ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen sollte


  
### <a name="loglevel"></a>LogLevel
Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen würde.

  
**Rückgabe:** ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen würde
  
### <a name="flush"></a>Leerung
Leert die Protokolldaten.
  
### <a name="writetolog"></a>WriteToLog
Schreibt eine Protokollanweisung in eine Protokolldatei.

Parameter:  
* **level**: die Protokollebene für die Protokollanweisung 


* **message**: die Nachricht an die Protokollanweisung 


* **function**: der Funktionsname für die Protokollanweisung 


* **file**: der Name der Datei, in der die Protokollanweisung generiert wurde 


* **line**: die Zeilennummer, in der die Protokollanweisung generiert wurde

