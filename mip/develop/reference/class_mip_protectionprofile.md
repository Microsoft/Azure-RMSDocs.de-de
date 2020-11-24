---
title: Class Protection profile
description: 'Dokumentiert die Schutzprofile:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: a783a90b64d5829632e2104ff2706fd86a0d9e68
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567108"
---
# <a name="class-protectionprofile"></a>Class Protection profile 
ProtectionProfile ist die Stammklasse für Schutzvorgänge.
Bevor Schutzvorgänge durchgeführt werden können, muss eine Anwendung ein ProtectionProfile erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft während der Initialisierung und der Lebensdauer die von ProtectionProfile verwendeten Einstellungen ab.
Public Std:: shared_ptr \<AsyncControl\> listenginesasync (Konst Std:: shared_ptr \<void\>& context)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector \<std::string\> listengines ()  |  Listet Engines auf
Public Std:: shared_ptr \<AsyncControl\> addengineasync (Konstante Schutz-Engine:: Settings& Settings, Konstanten Std:: shared_ptr \<void\>& context)  |  Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.
public std::shared_ptr\<ProtectionEngine\> AddEngine(const ProtectionEngine::Settings& settings)  |  Fügt eine neue Schutz-Engine zum Profil hinzu
Public Std:: shared_ptr \<AsyncControl\> deleteengineasync (Konstante Std:: String& EngineID, Konstanten Std:: shared_ptr \<void\>& context)  |  Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.
  
## <a name="members"></a>Members
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft während der Initialisierung und der Lebensdauer die von ProtectionProfile verwendeten Einstellungen ab.

  
**Gibt Folgendes zurück**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
ProtectionProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
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

