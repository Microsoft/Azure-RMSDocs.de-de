---
title: mip::LoggerDelegate-Klasse
description: 'Dokumentiert die MIP:: loggerdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: c9e4f4db31c12a84f888964694ffa4c88585c884
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77487734"
---
# <a name="class-miploggerdelegate"></a>mip::LoggerDelegate-Klasse 
Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public void Init(const std::string& storagePath)  |  Initialisiert die Protokollierung.
public void Flush()  |  Leert die Protokolldaten.
public void WriteToLog(const LogLevel level, const std::string& message, const std::string& function, const std::string& file, const int32_t line)  |  Schreibt eine Protokollanweisung in eine Protokolldatei.
  
## <a name="members"></a>Member
  
### <a name="init-function"></a>Init-Funktion
Initialisiert die Protokollierung.

Parameter:  
* **storagePath**: Der Pfad zum Speicherort, an dem der persistente Status, einschließlich Protokollen, gespeichert werden kann.


  
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

