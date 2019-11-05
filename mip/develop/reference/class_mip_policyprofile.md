---
title: mip::PolicyProfile-Klasse
description: Dokumentiert die MIP::p olicyprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 8feb0b93982a00c4843ea914f969ef27cf8e5ca2
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560913"
---
# <a name="class-mippolicyprofile"></a>mip::PolicyProfile-Klasse 
Die policyprofile-Klasse ist die Stamm Klasse für die Verwendung von Microsoft Information Protection-Vorgängen. Eine typische Anwendung benötigt nur ein policyprofile, aber Sie kann bei Bedarf mehrere Profile erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die auf dem Profil festgelegten Einstellungen ab.
öffentliches void listenginesasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector\<Std:: String\> listengines ()  |  Die Liste der Module.
öffentliches void unloadengineasync (Konstanten Std:: String & ID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
öffentliches void unloadengine (Konstante Std:: String & ID)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
öffentliches void addengineasync (Konstanten policyengine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<policyengine\> addengine (Konstanten policyengine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Fügen Sie dem Profil eine neue Richtlinien-Engine hinzu.
öffentliches void deleteengineasync (Konstante Std:: String & ID, Konst Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löschen Sie die Richtlinien-Engine mit der angegebenen ID. Alle Daten für die angegebene Engine werden gelöscht.
public static MIP_API void __CDECL MIP::P olicyprofile:: LoadAsync | Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.
public static konstant MIP_API char * __CDECL MIP::P olicyprofile:: GetVersion | Bibliotheksversion erhalten

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


* **context**: ein Parameter, der für den Observer-Funktionsumfang und optional httpdelegat als nicht verwendend angezeigt wird. 


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

### <a name="loadasync-function"></a>LoadAsync-Funktion
Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.

Parameter:  
* **Einstellungen**: die Profileinstellungen, mit denen das Profil Objekt geladen wird. </para>
* **context**: ein Kontext Parameter, der an die Observer-Funktionen übergeben wird.

### <a name="getversion-function"></a>GetVersion-Funktion
Bibliotheksversion erhalten

**Gibt Folgendes zurück**: eine Versions Zeichenfolge.