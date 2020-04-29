---
title: class file profile
description: 'Dokumentiert die File profile:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: cf5950b37953dc32100e8ae2700b6111783cb612
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81762920"
---
# <a name="class-fileprofile"></a>class file profile 
Die FileProfile-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
Eine gewöhnliche Anwendung benötigt nur ein Profil.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Profileinstellungen zurück
Public Std:: shared_ptr\<AsyncControl\> listenginesasync (Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: shared_ptr\<AsyncControl\> unloadengineasync (Konstante Std:: String& ID, Konstanten Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
Public Std:: shared_ptr\<AsyncControl\> addengineasync (Konstante fileengine:: Settings& Settings, Konstanten Std:: shared_ptr\<void\>& context)  |  Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<AsyncControl\> deleteengineasync (Konstante Std:: String& ID, Konstanten Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
öffentliches void acquirepolicyauthtoken (Cloud Cloud, Konstanten Std:: shared_ptr\<authdelegat\>& authdelegat) konstant  |  Löst einen Authentifizierungs Rückruf für die Richtlinie aus.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Profileinstellungen zurück
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
FileProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync-function"></a>Unloadengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
FileProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
FileProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
FileProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="acquirepolicyauthtoken-function"></a>Acquirepolicyauthtoken-Funktion
Löst einen Authentifizierungs Rückruf für die Richtlinie aus.

Parameter:  
* **Cloud**: Azure-Cloud 


* **authdelegat**: Authentifizierungs Rückruf, der aufgerufen wird


MIP speichert oder führt keine weiteren Aktionen mit dem vom Authentifizierungs Delegaten zurückgegebenen Wert aus. Diese Funktion wird für Anwendungen empfohlen, die nicht "angemeldet" sind, bis MIP ein Authentifizierungs Token anfordert. Sie ermöglicht einer Anwendung das Abrufen eines Tokens, bevor MIP tatsächlich ein Token benötigt.