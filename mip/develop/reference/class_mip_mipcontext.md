---
title: 'MIP:: mipcontext-Klasse'
description: 'Dokumentiert die MIP:: mipcontext-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 9efbe9330014458a26f62e4dfac9ea24ad5d4475
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73561033"
---
# <a name="class-mipmipcontext"></a>MIP:: mipcontext-Klasse 
Mipcontext stellt den Status dar, der von allen Profilen, Engines und Handlern gemeinsam genutzt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches void Herunterfahren ()  |  Beenden Sie MIP.
public bool isfeatureaktivierte (flightingfeature-Funktion) konstant  |  Ruft ab, ob eine Funktion aktiviert ist.
public const ApplicationInfo& GetApplicationInfo() const  |  Anwendungsbeschreibung erhalten.
Public Konstanten Std:: String & getmippath () Konstanten  |  Dateipfad für Protokolle, Caches usw. erhalten
public bool isofflineonly ()  |  Nur offline-Einstellung erhalten.
Public Std:: shared_ptr\<loggerdelegat\> getloggerdelegat ()  |  Get Logger-Implementierung.
öffentliches loggerdelegat * getrawloggerdelegat ()  |  Get Logger-Implementierung.
public static MIP_API Std:: shared_ptr&lt;mipcontext&gt; __CDECL MIP:: mipcontext:: Create | Erstellen Sie eine neue mipcontext-Instanz, die beim Initialisieren von Profilen verwendet werden soll.
public static MIP_API Std:: shared_ptr&lt;mipcontext&gt; __CDECL MIP:: mipcontext:: kreatewithcustomfeaturesettings | Erstellen Sie eine neue mipcontext-Instanz mit benutzerdefinierten Funktionseinstellungen.

## <a name="members"></a>Member
  
### <a name="shutdown-function"></a>Shutdown-Funktion
Beenden Sie MIP.
Diese Methode muss vor dem Herunterfahren von Prozess/dll aufgerufen werden.
  
### <a name="isfeatureenabled-function"></a>Isfeatureaktivierte Funktion
Ruft ab, ob eine Funktion aktiviert ist.

Parameter:  
* **Feature**: Funktion zum Aktivieren/Deaktivieren



  
**Gibt**Folgendes zurück: gibt an, ob eine Funktion aktiviert ist, wenn ein featureflightingdelegat nicht von einer Anwendung bereitgestellt wurde. Dies gibt immer "true" zurück.
  
### <a name="getapplicationinfo-function"></a>Getapplicationinfo-Funktion
Anwendungsbeschreibung erhalten.

  
**Gibt Folgendes zurück**: Anwendungsbeschreibung
  
### <a name="getmippath-function"></a>Getmippath-Funktion
Dateipfad für Protokolle, Caches usw. erhalten

  
**Gibt Folgendes zurück**: Dateipfad (mit "MIP"-Blatt Verzeichnis)
  
### <a name="isofflineonly-function"></a>Isofflineonly-Funktion
Nur offline-Einstellung erhalten.

  
**Gibt Folgendes zurück: gibt**an, ob die Anwendung im reinen Offline Modus ausgeführt wird.
  
### <a name="getloggerdelegate-function"></a>Getloggerdelegatfunktion
Get Logger-Implementierung.

  
**Rückgabe**: Protokollierung.
  
### <a name="getrawloggerdelegate-function"></a>Getrawloggerdelegatfunktion
Get Logger-Implementierung.

  
**Rückgabe**: Protokollierung.

### <a name="create-function"></a>Create-Funktion
Erstellen Sie eine neue mipcontext-Instanz, die beim Initialisieren von Profilen verwendet werden soll.

**Gibt Folgendes zurück**: mipcontext-Instanz.

### <a name="createwithcustomfeaturesettings-function"></a>Funktion "kreatewithcustomfeaturesettings"
Erstellen Sie eine neue mipcontext-Instanz mit benutzerdefinierten Funktionseinstellungen.

**Gibt Folgendes zurück**: mipcontext-Instanz.