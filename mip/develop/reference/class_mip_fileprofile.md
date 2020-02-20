---
title: mip::FileProfile-Klasse
description: 'Dokumentiert die MIP:: File Profile-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 44d6024473555c0745ff3156ff5cd004f83b6f6b
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77488142"
---
# <a name="class-mipfileprofile"></a>mip::FileProfile-Klasse 
Die File Profile-Klasse ist die Stamm Klasse für die Verwendung der Microsoft Information Protection-Vorgänge.
Eine gewöhnliche Anwendung benötigt nur ein Profil.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Profileinstellungen zurück
Public Std:: shared_ptr\<AsyncControl\> listenginesasync (konstant Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: shared_ptr\<AsyncControl\> unloadengineasync (Konstanten Std:: String & ID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
Public Std:: shared_ptr\<AsyncControl\> addengineasync (Konstante fileengine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<AsyncControl\> deleteengineasync (konstant Std:: String & ID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Profileinstellungen zurück
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync-function"></a>Unloadengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.

  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.