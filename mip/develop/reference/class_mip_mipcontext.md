---
title: 'MIP:: mipcontext-Klasse'
description: 'Dokumentiert die MIP:: mipcontext-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 20ce55ec371582ee16c70f311e0fc38ffc79d2fc
ms.sourcegitcommit: 9cedac6569f3a33a22a721da27074a438b1a7882
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71070614"
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
Public Std:: shared_ptr\<\> loggerdelegat getloggerdelegat ()  |  Get Logger-Implementierung.
öffentliches loggerdelegat * getrawloggerdelegat ()  |  Get Logger-Implementierung.
public static MIP_API Std:: shared_ptr&lt;mipcontext&gt; __CDECL MIP:: mipcontext:: Create | Erstellen Sie eine neue mipcontext-Instanz, die beim Initialisieren von Profilen verwendet werden soll.
public static MIP_API Std:: shared_ptr&lt;mipcontext&gt; __CDECL MIP:: mipcontext:: up-withcustomfeaturesettings | Erstellen Sie eine neue mipcontext-Instanz mit benutzerdefinierten Funktionseinstellungen.

## <a name="members"></a>Member
  
### <a name="shutdown-function"></a>Shutdown-Funktion
Beenden Sie MIP.
Diese Methode muss vor dem Herunterfahren von Prozess/dll aufgerufen werden.
  
### <a name="isfeatureenabled-function"></a>Isfeatureaktivierte Funktion
Ruft ab, ob eine Funktion aktiviert ist.

Parameter:  
* **Feature**: Funktion zum Aktivieren/Deaktivieren



  
**Gibt Folgendes zurück**: Unabhängig davon, ob eine Funktion aktiviert ist, wenn ein featureflightingdelegat nicht von einer Anwendung bereitgestellt wurde, wird immer true zurückgegeben.
  
### <a name="getapplicationinfo-function"></a>Getapplicationinfo-Funktion
Anwendungsbeschreibung erhalten.

  
**Gibt Folgendes zurück**: Anwendungsbeschreibung
  
### <a name="getmippath-function"></a>Getmippath-Funktion
Dateipfad für Protokolle, Caches usw. erhalten

  
**Gibt Folgendes zurück**: Dateipfad (mit "MIP"-Blatt Verzeichnis)
  
### <a name="getloggerdelegate-function"></a>Getloggerdelegatfunktion
Get Logger-Implementierung.

  
**Gibt Folgendes zurück**: Protokollierung
  
### <a name="getrawloggerdelegate-function"></a>Getrawloggerdelegatfunktion
Get Logger-Implementierung.

**Gibt Folgendes zurück**: Protokollierung

### <a name="create-function"></a>Create-Funktion
Erstellen Sie eine neue mipcontext-Instanz, die beim Initialisieren von Profilen verwendet werden soll.

**Gibt Folgendes zurück**: Mipcontext-Instanz.

### <a name="createwithcustomfeaturesettings-function"></a>Funktion "kreatewithcustomfeaturesettings"
Erstellen Sie eine neue mipcontext-Instanz mit benutzerdefinierten Funktionseinstellungen.

**Gibt Folgendes zurück**: Mipcontext-Instanz.

