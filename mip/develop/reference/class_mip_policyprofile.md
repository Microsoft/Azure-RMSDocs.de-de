---
title: Class policyprofile
description: 'Dokumentiert die policyprofile:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 89bac003d9a4924d5b854826b53eaa787f770a7c
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98213367"
---
# <a name="class-policyprofile"></a>Class policyprofile 
Die PolicyProfile-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine PolicyProfile-Klasse, kann bei Bedarf aber mehrere erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die auf dem Profil festgelegten Einstellungen ab.
Public Std:: shared_ptr \<AsyncControl\> listenginesasync (Konst Std:: shared_ptr \<void\>& context)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector \<std::string\> listengines ()  |  Die Liste der Module.
Public Std:: shared_ptr \<AsyncControl\> unloadengineasync (Konstante Std:: String& ID, Konstanten Std:: shared_ptr \<void\>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
öffentliches void unloadengine (Konstante Std:: String& ID)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
Public Std:: shared_ptr \<AsyncControl\> addengineasync (Konstanten policyengine:: Settings& Settings, Konstanten Std:: shared_ptr \<void\>& context)  |  Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr \<PolicyEngine\> addengine (Konstante policyengine:: Settings& Settings, Konst Std:: shared_ptr \<void\>& context)  |  Fügen Sie dem Profil eine neue Richtlinien-Engine hinzu.
Public Std:: shared_ptr \<AsyncControl\> deleteengineasync (Konstante Std:: String& ID, Konstanten Std:: shared_ptr \<void\>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löschen Sie die Richtlinien-Engine mit der angegebenen ID. Alle Daten für die angegebene Engine werden gelöscht.
öffentliches void acquireauthtoken (Cloud Cloud, Konstanten Std:: shared_ptr \<AuthDelegate\>& authdelegat) konstant  |  Löst einen Authentifizierungs Rückruf aus.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die auf dem Profil festgelegten Einstellungen ab.

  
**Rückgabe**: Auf dem Profil festgelegte Einstellungen.
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


PolicyProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines-function"></a>Listengines-Funktion
Die Liste der Module.

  
**Rückgabe:** zwischengespeicherte Engine-IDs
  
### <a name="unloadengineasync-function"></a>Unloadengineasync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **ID**: die eindeutige Engine-ID. 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


PolicyProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengine-function"></a>Unloadengine-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **ID**: die eindeutige Engine-ID.


  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: Das mip::PolicyEngine::Settings-Objekt, das die Engine-Einstellungen angibt. 


* **context**: ein Parameter, der an die Observer-Funktionen und optional httpdelegat weitergeleitet wird. 


PolicyProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengine-function"></a>Addengine-Funktion
Fügen Sie dem Profil eine neue Richtlinien-Engine hinzu.

Parameter:  
* **settings**: Das mip::PolicyEngine::Settings-Objekt, das die Engine-Einstellungen angibt. 


* **context**: ein Parameter, der verdeckt an den optionalen httpdelegaten weitergeleitet wird.



  
**Gibt Folgendes zurück**: neu erstellte policyengine
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.

Parameter:  
* **ID**: die eindeutige Engine-ID. 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


PolicyProfile::Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine-function"></a>Deleteengine-Funktion
Löschen Sie die Richtlinien-Engine mit der angegebenen ID. Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **ID**: die eindeutige Engine-ID.


  
### <a name="acquireauthtoken-function"></a>Acquireauthtoken-Funktion
Löst einen Authentifizierungs Rückruf aus.

Parameter:  
* **Cloud**: Azure-Cloud 


* **authdelegat**: Authentifizierungs Rückruf, der aufgerufen wird


MIP speichert oder führt keine weiteren Aktionen mit dem vom Authentifizierungs Delegaten zurückgegebenen Wert aus. Diese Funktion wird für Anwendungen empfohlen, die nicht "angemeldet" sind, bis MIP ein Authentifizierungs Token anfordert. Sie ermöglicht einer Anwendung das Abrufen eines Tokens, bevor MIP tatsächlich ein Token benötigt.