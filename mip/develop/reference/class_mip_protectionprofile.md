---
title: mip::ProtectionProfile-Klasse
description: Dokumentiert die MIP::p rotectionprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: cc69e167a5b5a8dc46157443c13d70732ace62c0
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69883331"
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

