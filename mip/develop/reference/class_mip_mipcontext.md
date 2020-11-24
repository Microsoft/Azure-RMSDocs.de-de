---
title: Class mipcontext
description: 'Dokumentiert die mipcontext:: undefinierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: c593ebc368b0717d32e873e6924f80af103325ea
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566761"
---
# <a name="class-mipcontext"></a>Class mipcontext 
Mipcontext stellt den Status dar, der von allen Profilen, Engines und Handlern gemeinsam genutzt wird.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void Herunterfahren ()  |  Beenden Sie MIP.
public bool isfeatureaktivierte (flightingfeature-Funktion) konstant  |  Ruft ab, ob eine Funktion aktiviert ist.
public const ApplicationInfo& GetApplicationInfo() const  |  Anwendungsbeschreibung erhalten.
Public Konstanten Std:: String& getmippath () Konstanten  |  Dateipfad für Protokolle, Caches usw. erhalten
public bool isofflineonly ()  |  Nur offline-Einstellung erhalten.
öffentliches LogLevel getmarkoldloglevel () konstant  |  Schwellenwert Protokollebene erhalten.
Public Std:: shared_ptr \<LoggerDelegate\> getloggerdelegat ()  |  Get Logger-Implementierung.
öffentliches loggerdelegat * getrawloggerdelegat ()  |  Get Logger-Implementierung.
Public Konstanten Std:: map \<FlightingFeature, bool\>& getflightingfeatures () Konstanten  |  Get-flighting-Funktions Satz.
  
## <a name="members"></a>Members
  
### <a name="shutdown-function"></a>Shutdown-Funktion
Beenden Sie MIP.
Diese Methode muss vor dem Herunterfahren von Prozess/dll aufgerufen werden.
  
### <a name="isfeatureenabled-function"></a>Isfeatureaktivierte Funktion
Ruft ab, ob eine Funktion aktiviert ist.

Parameter:  
* **Feature**: Funktion zum Aktivieren/Deaktivieren



  
**Gibt** Folgendes zurück: gibt an, ob eine Funktion aktiviert ist, wenn ein featureflightingdelegat nicht von einer Anwendung bereitgestellt wurde. Dies gibt immer "true" zurück.
  
### <a name="getapplicationinfo-function"></a>Getapplicationinfo-Funktion
Anwendungsbeschreibung erhalten.

  
**Gibt Folgendes zurück**: Anwendungsbeschreibung
  
### <a name="getmippath-function"></a>Getmippath-Funktion
Dateipfad für Protokolle, Caches usw. erhalten

  
**Gibt Folgendes zurück**: Dateipfad (mit "MIP"-Blatt Verzeichnis)
  
### <a name="isofflineonly-function"></a>Isofflineonly-Funktion
Nur offline-Einstellung erhalten.

  
**Gibt Folgendes zurück: gibt** an, ob die Anwendung im reinen Offline Modus ausgeführt wird.
  
### <a name="getthresholdloglevel-function"></a>Getder oldloglevel-Funktion
Schwellenwert Protokollebene erhalten.

  
**Gibt Folgendes zurück**: Schwellenwert Protokollebene
  
### <a name="getloggerdelegate-function"></a>Getloggerdelegatfunktion
Get Logger-Implementierung.

  
**Rückgabe**: Protokollierung
  
### <a name="getrawloggerdelegate-function"></a>Getrawloggerdelegatfunktion
Get Logger-Implementierung.

  
**Rückgabe**: Protokollierung
  
### <a name="getflightingfeatures-function"></a>Getflightingfeatures-Funktion
Get-flighting-Funktions Satz.

  
**Returns**: flighting Feature Map