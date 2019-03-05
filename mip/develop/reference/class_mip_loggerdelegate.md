---
title: mip::LoggerDelegate-Klasse
description: Dokumentiert die mip::loggerdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 511c8dabc8ff31c70c8343a80d423b76c43fa946
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330320"
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
  
### <a name="init-function"></a>"Init"-Funktion
Initialisiert die Protokollierung.

Parameter:  
* **storagePath**: Der Pfad zum Speicherort, an dem der persistente Status, einschließlich Protokollen, gespeichert werden kann. 


* **logLevel:** ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen sollte


  
### <a name="getloglevel-function"></a>GetLogLevel-Funktion
Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen würde.

  
**Gibt**: Die niedrigste Protokollebene, die ein Ereignis für die nachrichtenprotokollierung auslösen würde.
  
### <a name="flush-function"></a>Flush-Funktion
Leert die Protokolldaten.
  
### <a name="writetolog-function"></a>WriteToLog-Funktion
Schreibt eine Protokollanweisung in eine Protokolldatei.

Parameter:  
* **level**: die Protokollebene für die Protokollanweisung 


* **message**: die Nachricht an die Protokollanweisung 


* **function**: der Funktionsname für die Protokollanweisung 


* **file**: der Name der Datei, in der die Protokollanweisung generiert wurde 


* **line**: die Zeilennummer, in der die Protokollanweisung generiert wurde

