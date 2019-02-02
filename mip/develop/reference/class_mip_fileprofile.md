---
title: mip::FileProfile-Klasse
description: 'Beschreibt die Klasse:: fileprofile-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 0210bc6b3bdf9ffdbe3f34c2c606997773d16b31
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651087"
---
# <a name="class-mipfileprofile"></a>mip::FileProfile-Klasse 
Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
Eine gewöhnliche Anwendung benötigt nur ein Profil.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Profileinstellungen zurück
public void ListEnginesAsync(const std::shared_ptr\<void\>& context)  |  Startet den Vorgang zum Auflisten von Engines
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
Öffentliche void AddEngineAsync (const FileEngine::Settings "und" Einstellungen "," const Std:: shared_ptr\<"void"\>& Kontext)  |  Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Profileinstellungen zurück
  
### <a name="listenginesasync-function"></a>ListEnginesAsync-Funktion
Startet den Vorgang zum Auflisten von Engines
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync-function"></a>UnloadEngineAsync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync-function"></a>AddEngineAsync-Funktion
Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync-function"></a>DeleteEngineAsync-Funktion
Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.