---
title: mip::ProtectionProfile-Klasse
description: 'Beschreibt die Klasse:: protectionprofile-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 4b7e5ecc3006ab44b1c5f55cd658a0e0b33748d3
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650951"
---
# <a name="class-mipprotectionprofile"></a>mip::ProtectionProfile-Klasse 
[ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
Bevor Schutzvorgänge durchgeführt werden können, muss eine Anwendung ein [ProtectionProfile](class_mip_protectionprofile.md) erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.
public void ListEnginesAsync(const std::shared_ptr\<void\>& context)  |  Startet den Vorgang zum Auflisten von Engines
Public Std:: vector\<Std:: String\> ListEngines()  |  Listet Engines auf
Öffentliche void AddEngineAsync (const ProtectionEngine::Settings "und" Einstellungen "," const Std:: shared_ptr\<"void"\>& Kontext)  |  Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.
Public Std:: shared_ptr\<ProtectionEngine\> AddEngine (const ProtectionEngine::Settings & Einstellungen)  |  Fügt eine neue Schutz-Engine zum Profil hinzu
public void DeleteEngineAsync(const std::string& engineId, const std::shared_ptr\<void\>& context)  |  Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.
public void DeleteEngine(const std::string& engineId)  |  Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.

  
**Gibt**: [Einstellungen](class_mip_protectionprofile_settings.md), die während der Initialisierung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden
  
### <a name="listenginesasync-function"></a>ListEnginesAsync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Clientkontext, der Clientkontext zurück an den Beobachter übergeben werden


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="listengines-function"></a>ListEngines-Funktion
Listet Engines auf

  
**Gibt**: Zwischengespeicherte-Engine-IDs
  
### <a name="addengineasync-function"></a>AddEngineAsync-Funktion
Beginnt damit, eine neue Schutz-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: das [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Objekt, das die Einstellungen der Engine angibt 


* **context**: Clientkontext, der Clientkontext zurück an den Beobachter übergeben werden


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengine-function"></a>AddEngine-Funktion
Fügt eine neue Schutz-Engine zum Profil hinzu

Parameter:  
* **settings**: das [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Objekt, das die Einstellungen der Engine angibt



  
**Gibt**: Neu erstellte [ProtectionEngine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync-function"></a>DeleteEngineAsync-Funktion
Beginnt damit, die Schutz-Engine mit der angegebenen ID zu löschen. Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Clientkontext, der Clientkontext zurück an den Beobachter übergeben werden


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengine-function"></a>DeleteEngine-Funktion
Löscht die Schutz-Engine mit der angegebenen ID Alle Daten für die angegebene Engine werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID

