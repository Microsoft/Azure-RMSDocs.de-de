---
title: mip::FileProfile-Klasse
description: 'Dokumentiert die MIP:: File Profile-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 9971ae734b17186bd9ba942ca7dc991ab3e4ef15
ms.sourcegitcommit: 9cedac6569f3a33a22a721da27074a438b1a7882
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71070607"
---
# <a name="class-mipfileprofile"></a>mip::FileProfile-Klasse 
Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
Eine gewöhnliche Anwendung benötigt nur ein Profil.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Profileinstellungen zurück
öffentliches void listenginesasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
öffentliches void unloadengineasync (Konstante Std:: String & ID, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
öffentliches void addengineasync (Konstante fileengine:: Settings & Settings, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
öffentliches void deleteengineasync (Konstante Std:: String & ID, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
public static FILE_API void __CDECL MIP:: fileprofile:: LoadAsync | Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.
public static konstant FILE_API char * __CDECL MIP:: fileprofile:: GetVersion | Ruft die Bibliotheksversion ab.


## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Profileinstellungen zurück
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync-function"></a>Unloadengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.

### <a name="loadasync-function"></a>LoadAsync-Funktion
Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.

[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.

### <a name="getversion-function"></a>GetVersion-Funktion
Ruft die Bibliotheksversion ab.
