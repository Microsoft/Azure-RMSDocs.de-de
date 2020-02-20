---
title: mip::PolicyProfile-Klasse
description: Dokumentiert die MIP::p olicyprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 515f780c269025175e99caed72e8da381ef88104
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489774"
---
# <a name="class-mippolicyprofile"></a>mip::PolicyProfile-Klasse 
Die policyprofile-Klasse ist die Stamm Klasse für die Verwendung von Microsoft Information Protection-Vorgängen. Eine typische Anwendung benötigt nur ein policyprofile, aber Sie kann bei Bedarf mehrere Profile erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die auf dem Profil festgelegten Einstellungen ab.
Public Std:: shared_ptr\<AsyncControl\> listenginesasync (konstant Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector\<Std:: String\> listengines ()  |  Die Liste der Module.
Public Std:: shared_ptr\<AsyncControl\> unloadengineasync (Konstanten Std:: String & ID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
öffentliches void unloadengine (Konstante Std:: String & ID)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
Public Std:: shared_ptr\<AsyncControl\> addengineasync (konstant policyengine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<policyengine\> addengine (Konstanten policyengine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Fügen Sie dem Profil eine neue Richtlinien-Engine hinzu.
Public Std:: shared_ptr\<AsyncControl\> deleteengineasync (konstant Std:: String & ID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löschen Sie die Richtlinien-Engine mit der angegebenen ID. Alle Daten für die angegebene Engine werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die auf dem Profil festgelegten Einstellungen ab.

  
**Rückgabe**: Auf dem Profil festgelegte Einstellungen.
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


Policyprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines-function"></a>Listengines-Funktion
Die Liste der Module.

  
**Rückgabe:** zwischengespeicherte Engine-IDs
  
### <a name="unloadengineasync-function"></a>Unloadengineasync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


Policyprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengine-function"></a>Unloadengine-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **id**: die eindeutige Engine-ID


  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **Einstellungen**: das MIP::P olicyengine:: Settings-Objekt, das die Einstellungen der Engine angibt. 


* **context**: ein Parameter, der an die Observer-Funktionen und optional httpdelegat weitergeleitet wird. 


Policyprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengine-function"></a>Addengine-Funktion
Fügen Sie dem Profil eine neue Richtlinien-Engine hinzu.

Parameter:  
* **Einstellungen**: das MIP::P olicyengine:: Settings-Objekt, das die Einstellungen der Engine angibt. 


* **context**: ein Parameter, der verdeckt an den optionalen httpdelegaten weitergeleitet wird.



  
**Gibt Folgendes zurück**: neu erstellte policyengine
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


Policyprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine-function"></a>Deleteengine-Funktion
Löschen Sie die Richtlinien-Engine mit der angegebenen ID. Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID

