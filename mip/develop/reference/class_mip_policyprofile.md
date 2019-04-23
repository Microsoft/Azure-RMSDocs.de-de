---
title: mip::PolicyProfile-Klasse
description: Dokumentiert die mip::policyprofile-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 45af1f4d072a1d8a690aa8f459950ae500df3db8
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60173336"
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