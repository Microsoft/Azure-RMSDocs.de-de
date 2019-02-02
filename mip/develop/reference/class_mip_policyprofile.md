---
title: mip::PolicyProfile-Klasse
description: Dokumentiert die mip::policyprofile-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: c97f6335159f99c97ff68e233ed7d357242bedb3
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651155"
---
# <a name="class-mippolicyprofile"></a>mip::PolicyProfile-Klasse 
Die [PolicyProfile](class_mip_policyprofile.md)-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine [PolicyProfile](class_mip_policyprofile.md)-Klasse, kann bei Bedarf aber mehrere erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die auf dem Profil festgelegten Einstellungen ab.
public void ListEnginesAsync(const std::shared_ptr\<void\>& context)  |  Startet den Vorgang zum Auflisten von Engines
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
Öffentliche void AddEngineAsync (const PolicyEngine::Settings "und" Einstellungen "," const Std:: shared_ptr\<"void"\>& Kontext)  |  Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr\<void\>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die auf dem Profil festgelegten Einstellungen ab.

  
**Gibt**: Auf dem Profil festgelegten Einstellungen auf.
  
### <a name="listenginesasync-function"></a>ListEnginesAsync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync-function"></a>UnloadEngineAsync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync-function"></a>AddEngineAsync-Funktion
Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: Das [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)-Objekt, das die Engine-Einstellungen angibt. 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync-function"></a>DeleteEngineAsync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.