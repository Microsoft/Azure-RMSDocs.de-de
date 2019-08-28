---
title: mip::LoggerDelegate-Klasse
description: 'Dokumentiert die MIP:: loggerdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 6339accaa94d00a95faf9ab047e148d61671422c
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054589"
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
  
### <a name="init-function"></a>Init-Funktion
Initialisiert die Protokollierung.

Parameter:  
* **storagePath**: Der Pfad zum Speicherort, an dem der persistente Status, einschließlich Protokollen, gespeichert werden kann. 


* **logLevel:** ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen sollte


  
### <a name="getloglevel-function"></a>Getloglevel-Funktion
Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslösen würde.

  
**Gibt Folgendes zurück**: Die niedrigste Protokollebene, die ein Protokollierungs Ereignis auslöst.
  
### <a name="flush-function"></a>Flush-Funktion
Leert die Protokolldaten.
  
### <a name="writetolog-function"></a>Funktion "Beschreib tetolog"
Schreibt eine Protokollanweisung in eine Protokolldatei.

Parameter:  
* **level**: die Protokollebene für die Protokollanweisung 


* **message**: die Nachricht an die Protokollanweisung 


* **function**: der Funktionsname für die Protokollanweisung 


* **file**: der Name der Datei, in der die Protokollanweisung generiert wurde 


* **line**: die Zeilennummer, in der die Protokollanweisung generiert wurde

