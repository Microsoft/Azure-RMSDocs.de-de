---
title: mip::PolicyProfile-Klasse
description: Dokumentiert die MIP::p olicyprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 13d24afe87bc04f7a92dde8daf88c1ada38cedc2
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69883749"
---
# <a name="class-mippolicyprofile"></a>mip::PolicyProfile-Klasse 
Die [PolicyProfile](class_mip_policyprofile.md)-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine [PolicyProfile](class_mip_policyprofile.md)-Klasse, kann bei Bedarf aber mehrere erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die auf dem Profil festgelegten Einstellungen ab.
öffentliches void listenginesasync (Konst Std:: shared_ptr\<void\>& Kontext)  |  Startet den Vorgang zum Auflisten von Engines
öffentliches void unloadengineasync (Konstante Std:: String & ID, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
öffentliches void addengineasync (Konstante policyengine:: Settings & Settings, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
öffentliches void deleteengineasync (Konstante Std:: String & ID, Konst Std:: shared_ptr\<void\>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die auf dem Profil festgelegten Einstellungen ab.

  
**Gibt Folgendes zurück**: Einstellungen, die für das Profil festgelegt sind.
  
### <a name="listenginesasync-function"></a>Listenginesasync-Funktion
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync-function"></a>Unloadengineasync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync-function"></a>Addengineasync-Funktion
Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: Das [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)-Objekt, das die Engine-Einstellungen angibt. 


* **context**: Ein Parameter, der verdeckt an die Beobachterfunktionen weitergeleitet wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync-function"></a>Deleteengineasync-Funktion
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden gelöscht.

Parameter:  
* **id**: die eindeutige Engine-ID 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.