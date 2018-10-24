---
title: Die Klasse „mip::ProtectionProfile“
description: Referenz zur Klasse „mip::ProtectionProfile“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7dffb4a6b1490ef185eb9a5062f394f4509f00a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446684"
---
# <a name="class-mipprotectionprofile"></a>mip::ProtectionProfile-Klasse 
[ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
Bevor Schutzvorgänge durchgeführt werden können, muss eine Anwendung ein [ProtectionProfile](class_mip_protectionprofile.md) erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  Startet den Vorgang zum Auflisten von Engines
public std::vector<std::string> ListEngines()  |  Listet Engines auf
public void AddEngineAsync(const ProtectionEngine::Settings& settings, const std::shared_ptr<void>& context)  |  Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.
public std::shared_ptr<ProtectionEngine> AddEngine(const ProtectionEngine::Settings& settings)  |  Fügt eine neue Schutz-Engine zum Profil hinzu
public void DeleteEngineAsync(const std::string& engineId, const std::shared_ptr<void>& context)  |  Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.
 public void DeleteEngine(const std::string& engineId)  |  Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.

  
**Rückgabe**: [Einstellungen](class_mip_protectionprofile_settings.md), die von [ProtectionProfile](class_mip_protectionprofile.md) während der Initialisierung und der Lebensdauer verwendet werden
  
### <a name="listenginesasync"></a>ListEnginesAsync
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines"></a>ListEngines
Listet Engines auf

  
**Rückgabe:** zwischengespeicherte Engine-IDs
  
### <a name="addengineasync"></a>AddEngineAsync
Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: das [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Objekt, das die Einstellungen der Engine angibt 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="protectionengine"></a>ProtectionEngine
Fügt eine neue Schutz-Engine zum Profil hinzu

Parameter:  
* **settings**: das [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Objekt, das die Einstellungen der Engine angibt



  
**Rückgabe:** neu erstellte [ProtectionEngine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird.


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine"></a>DeleteEngine
Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID

