---
title: mip::ProtectionProfile-Klasse
description: Dokumentiert die MIP::p rotectionprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: a6c78e7311f3af3920df19d7a3a6ca92bb09e819
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560055"
---
# <a name="class-mipprotectionprofile"></a>mip::ProtectionProfile-Klasse 
Schutzprofile ist die Stamm Klasse für die Durchführung von Schutz Vorgängen.
Eine Anwendung muss ein Schutzprofil erstellen, bevor Sie Schutz Vorgänge ausführen können.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft Einstellungen ab, die von Schutzprofile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.
öffentliches void listenginesasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector\<Std:: String\> listengines ()  |  Listet Engines auf
öffentliches void addengineasync (Konstante Schutz-Engine:: Settings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<schutzengine\> addengine (Konstante Schutz-Engine:: Settings & Settings)  |  Fügt eine neue Schutz-Engine zum Profil hinzu
öffentliches void deleteengineasync (Konstanten Std:: String & EngineID, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.
public static MIP_API void __CDECL MIP::P rotectionprofile:: LoadAsync | Von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendete Einstellungen
public static MIP_API Std:: shared_ptr&lt;Schutzprofile&gt; __CDECL MIP::P rotectionprofile:: Load | Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.
public static konstant MIP_API char * __CDECL MIP::P rotectionprofile:: GetVersion | Ruft die Bibliotheksversion ab.
public static MIP_API Std:: shared_ptr&lt;publishinglicenseingefo&gt; __CDECL MIP::P rotectionprofile:: getpublishinglicenseingefo | Erstellt einen Halter für Details einer Veröffentlichungs Lizenz und kann zum Erstellen eines Schutz Handlers verwendet werden. 

## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft Einstellungen ab, die von Schutzprofile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.

  
**Gibt Folgendes zurück**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.


Schutzprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines-function"></a>Listengines-Funktion
Listet Engines auf

  
**Rückgabe:** zwischengespeicherte Engine-IDs
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **Einstellungen**: das MIP::P rotectionengine:: Settings-Objekt, das die Einstellungen der Engine angibt. 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.


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


Schutzprofile:: Observer wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine-function"></a>Deleteengine-Funktion
Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID

### <a name="loadasync-function"></a>LoadAsync-Funktion
Von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendete Einstellungen 

[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.

Parameter:
* **Einstellungen**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.
* **Kontext**: dieser Kontext wird an Schutz profile:: Observer:: onloadsuccess oder Schutzprofile:: Observer:: onloadfailure unverändert weitergeleitet.

### <a name="load-function"></a>Load-Funktion
Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.

[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.

Parameter:
* **Einstellungen**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.

**Gibt Folgendes zurück**: neu erstelltes Profil.

### <a name="getversion-function"></a>GetVersion-Funktion
Ruft die Bibliotheksversion ab. 

**Gibt Folgendes zurück**: Bibliotheksversion.

### <a name="getpublishinglicenseinfo-function"></a>Getpublishinglicenseingefo-Funktion
Erstellt einen Halter für Details einer Veröffentlichungs Lizenz und kann zum Erstellen eines Schutz Handlers verwendet werden. 

Parameter:
* **serializedpublishinglicense**: die serialisierte Veröffentlichungs Lizenz.

**Gibt Folgendes zurück**: ein Inhaber für Details einer Veröffentlichungs Lizenz. 