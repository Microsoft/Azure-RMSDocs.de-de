---
title: mip::FileProfile-Klasse
description: 'Dokumentiert die MIP:: File Profile-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 1e7ca538a0add485fe285240fdcbde0d9ac5ce54
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056089"
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