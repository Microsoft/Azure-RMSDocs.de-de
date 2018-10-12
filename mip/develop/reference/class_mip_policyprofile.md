---
title: Microsoft Information Protection-Klasse „PolicyProfile“
description: Referenz für die Microsoft Information Protection-Klasse „PolicyProfile“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 387e28780cb0ef02d56050f534d4783fdebc286e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446861"
---
# <a name="class-mippolicyprofile"></a>mip::PolicyProfile-Klasse 
Die [PolicyProfile](class_mip_policyprofile.md)-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine [PolicyProfile](class_mip_policyprofile.md)-Klasse, kann bei Bedarf aber mehrere erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Ruft die auf dem Profil festgelegten Einstellungen ab.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  Startet den Vorgang zum Auflisten von Engines
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
public void AddEngineAsync(const PolicyEngine::Settings& settings, const std::shared_ptr<void>& context)  |  Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft die auf dem Profil festgelegten Einstellungen ab.

  
**Rückgabe**: Auf dem Profil festgelegte Einstellungen.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **id**: Die eindeutige Engine-ID. 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync"></a>AddEngineAsync
Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: Das [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)-Objekt, das die Engine-Einstellungen angibt. 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.

Parameter:  
* **id**: Die eindeutige Engine-ID. 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.