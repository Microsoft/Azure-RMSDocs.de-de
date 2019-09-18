---
title: mip::ProtectionProfile-Klasse
description: Dokumentiert die MIP::p rotectionprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: dcd50c403f20486e479fc00016ed6c0ef8885efa
ms.sourcegitcommit: 9cedac6569f3a33a22a721da27074a438b1a7882
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71070500"
---
# <a name="class-mipprotectionprofile"></a>mip::ProtectionProfile-Klasse 
[ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
Bevor Schutzvorgänge durchgeführt werden können, muss eine Anwendung ein [ProtectionProfile](class_mip_protectionprofile.md) erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.
öffentliches void listenginesasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: Vector\<Std:: String\> listengines ()  |  Listet Engines auf
öffentliches void addengineasync (Konstante Schutz-Engine:: Settings & Settings, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<schutzengine\> addengine (konstant Protection Engine:: Settings & Settings)  |  Fügt eine neue Schutz-Engine zum Profil hinzu
öffentliches void deleteengineasync (Konstante Std:: String & EngineID, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.
public static MIP_API void __CDECL MIP::P rotectionprofile:: LoadAsync | Von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendete Einstellungen
public static MIP_API Std:: shared_ptr&lt;Schutzprofile&gt; __CDECL MIP::P rotectionprofile:: Load | Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.
public static konstant MIP_API char * __CDECL MIP::P rotectionprofile:: GetVersion | Ruft die Bibliotheksversion ab.
public static MIP_API Std:: shared_ptr&lt;publishinglicenseingefo&gt; __CDECL MIP::P rotectionprofile:: getpublishinglicenseingefo | Erstellt einen Halter für Details einer Veröffentlichungs Lizenz und kann zum Erstellen eines Schutz Handlers verwendet werden. 


## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.

  
**Gibt Folgendes zurück**: [Einstellungen](class_mip_protectionprofile_settings.md), die während der Initialisierung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **Kontext**: Client Kontext, der an Beobachter zurückgegeben wird


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines-function"></a>Listengines-Funktion
Listet Engines auf

  
**Gibt Folgendes zurück**: Zwischengespeicherte Engine-IDs
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: das [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Objekt, das die Einstellungen der Engine angibt 


* **Kontext**: Client Kontext, der an Beobachter zurückgegeben wird


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengine-function"></a>Addengine-Funktion
Fügt eine neue Schutz-Engine zum Profil hinzu

Parameter:  
* **settings**: das [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Objekt, das die Einstellungen der Engine angibt



  
**Gibt Folgendes zurück**: Neu erstellte Schutz- [Engine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **Kontext**: Client Kontext, der an Beobachter zurückgegeben wird


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine-function"></a>Deleteengine-Funktion
Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID

### <a name="loadasync-function"></a>LoadAsync-Funktion
Von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendete Einstellungen 

[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.

Parameter:
* **Einstellungen**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.
* **Kontext**: Derselbe Kontext wird an Schutz profile:: Observer:: onloadsuccess oder schützprofile:: Observer:: onloadfailure unverändert weitergeleitet.

### <a name="load-function"></a>Load-Funktion
Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.

[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.

Parameter:
* **Einstellungen**: Einstellungen, die von Protection Profile während der Initialisierung und während der gesamten Lebensdauer verwendet werden.

**Gibt Folgendes zurück**: Neu erstelltes Profil.

### <a name="getversion-function"></a>GetVersion-Funktion
Ruft die Bibliotheksversion ab. 

**Gibt Folgendes zurück**: Bibliotheksversion.

### <a name="getpublishinglicenseinfo-function"></a>Getpublishinglicenseingefo-Funktion
Erstellt einen Halter für Details einer Veröffentlichungs Lizenz und kann zum Erstellen eines Schutz Handlers verwendet werden. 

Parameter:
* **serializedPublishingLicense**: Die serialisierte Veröffentlichungs Lizenz.

**Gibt Folgendes zurück**: Ein Inhaber für Details einer Veröffentlichungs Lizenz. 
