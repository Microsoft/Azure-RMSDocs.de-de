---
title: 'MIP:: mipcontext-Klasse'
description: 'Dokumentiert die MIP:: mipcontext-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: f6bc8d5a61ec259b85ae9e2479afeb9a2f00412f
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054582"
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