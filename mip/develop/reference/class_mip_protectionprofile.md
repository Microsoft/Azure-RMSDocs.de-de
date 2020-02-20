---
title: mip::ProtectionProfile-Klasse
description: Dokumentiert die MIP::p rotectionprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 14d52de8ff87a75aaf2c777eb55c427bbde72a12
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77486731"
---
# <a name="class-mipprotectionprofile"></a>mip::ProtectionProfile-Klasse 
Schutzprofile ist die Stamm Klasse für die Durchführung von Schutz Vorgängen.
Eine Anwendung muss ein Schutzprofil erstellen, bevor Sie Schutz Vorgänge ausführen können.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft Einstellungen ab, die von Schutzprofile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.
Public Std:: shared_ptr\<AsyncControl\> listenginesasync (konstant Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector\<Std:: String\> listengines ()  |  Listet Engines auf
Public Std:: shared_ptr\<AsyncControl\> addengineasync (Konstante Schutz-Engine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<schutzengine\> addengine (Konstante Schutz-Engine:: Settings & Settings)  |  Fügt eine neue Schutz-Engine zum Profil hinzu
Public Std:: shared_ptr\<AsyncControl\> deleteengineasync (konstant Std:: String & EngineID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft Einstellungen ab, die von Schutzprofile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.

  
**Gibt Folgendes zurück**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
Schutzprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines-function"></a>Listengines-Funktion
Listet Engines auf

  
**Rückgabe:** zwischengespeicherte Engine-IDs
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **Einstellungen**: das MIP::P rotectionengine:: Settings-Objekt, das die Einstellungen der Engine angibt. 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
Schutzprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengine-function"></a>Addengine-Funktion
Fügt eine neue Schutz-Engine zum Profil hinzu

Parameter:  
* **Einstellungen**: das MIP::P rotectionengine:: Settings-Objekt, das die Einstellungen der Engine angibt.



  
**Gibt Folgendes zurück**: neu erstellte Schutz-Engine
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
Schutzprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine-function"></a>Deleteengine-Funktion
Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID

