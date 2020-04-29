---
title: Class Protection profile
description: 'Dokumentiert die Schutzprofile:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: d3a2f02a0dab5bba9b74b264348bcfd7e073f783
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764406"
---
# <a name="class-protectionprofile"></a>Class Protection profile 
ProtectionProfile ist die Stammklasse für Schutzvorgänge.
Bevor Schutzvorgänge durchgeführt werden können, muss eine Anwendung ein ProtectionProfile erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft während der Initialisierung und der Lebensdauer die von ProtectionProfile verwendeten Einstellungen ab.
Public Std:: shared_ptr\<AsyncControl\> listenginesasync (Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector\<Std:: String\> listengines ()  |  Listet Engines auf
Public Std:: shared_ptr\<AsyncControl\> addengineasync (Konstante Schutz-Engine:: Settings& Settings, Konstanten Std:: shared_ptr\<void\>& context)  |  Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<schutzengine\> addengine (konstant Protection Engine:: Settings& Settings)  |  Fügt eine neue Schutz-Engine zum Profil hinzu
Public Std:: shared_ptr\<AsyncControl\> deleteengineasync (Konstanten Std:: String& EngineID, Konstante Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft während der Initialisierung und der Lebensdauer die von ProtectionProfile verwendeten Einstellungen ab.

  
**Gibt Folgendes zurück**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines-function"></a>Listengines-Funktion
Listet Engines auf

  
**Rückgabe:** zwischengespeicherte Engine-IDs
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: das mip::ProtectionEngine::Settings-Objekt, das die Einstellungen der Engine angibt 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
ProtectionProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengine-function"></a>Addengine-Funktion
Fügt eine neue Schutz-Engine zum Profil hinzu

Parameter:  
* **settings**: das mip::ProtectionEngine::Settings-Objekt, das die Einstellungen der Engine angibt



  
**Rückgabe:** neu erstellte ProtectionEngine
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **ID**: die eindeutige Engine-ID. 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
ProtectionProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine-function"></a>Deleteengine-Funktion
Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **ID**: die eindeutige Engine-ID.

