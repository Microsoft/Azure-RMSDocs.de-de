---
title: mip::FileProfile-Klasse
description: 'Dokumentiert die MIP:: File Profile-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: a436024aefe58a73ea03747fce5c5f2f4b4fc4b1
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73558800"
---
# <a name="class-mipfileprofile"></a>mip::FileProfile-Klasse 
Die File Profile-Klasse ist die Stamm Klasse für die Verwendung der Microsoft Information Protection-Vorgänge.
Eine gewöhnliche Anwendung benötigt nur ein Profil.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Profileinstellungen zurück
öffentliches void listenginesasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
öffentliches void unloadengineasync (Konstanten Std:: String & ID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
öffentliches void addengineasync (Konstante fileengine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
öffentliches void deleteengineasync (Konstante Std:: String & ID, Konst Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
public static FILE_API void __CDECL MIP:: fileprofile:: LoadAsync | Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.
public static konstant FILE_API char * __CDECL MIP:: fileprofile:: GetVersion | Ruft die Bibliotheksversion ab.

## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Profileinstellungen zurück
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync-function"></a>Unloadengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
File profile:: Observer wird bei Erfolg oder Fehler aufgerufen.

### <a name="loadasync-function"></a>LoadAsync-Funktion
Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.

[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.

### <a name="getversion-function"></a>GetVersion-Funktion
Ruft die Bibliotheksversion ab.