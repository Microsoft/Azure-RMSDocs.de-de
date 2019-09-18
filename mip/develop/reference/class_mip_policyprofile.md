---
title: mip::PolicyProfile-Klasse
description: Dokumentiert die MIP::p olicyprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 5abcca760f89b492f26ed5fa7b46e280e1bfc8ab
ms.sourcegitcommit: 9cedac6569f3a33a22a721da27074a438b1a7882
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71070530"
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
public static MIP_API void __CDECL MIP::P olicyprofile:: LoadAsync | Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.
public static konstant MIP_API char * __CDECL MIP::P olicyprofile:: GetVersion | Bibliotheksversion erhalten


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

### <a name="loadasync-function"></a>LoadAsync-Funktion
Startet das Laden eines Profils auf der Grundlage der bereitgestellten Einstellungen.

Parameter:  
* **Einstellungen**: die Profileinstellungen, mit denen das Profil Objekt geladen wird. </para>
* **context**: ein Kontext Parameter, der an die Observer-Funktionen übergeben wird.

### <a name="getversion-function"></a>GetVersion-Funktion
Bibliotheksversion erhalten

**Gibt Folgendes zurück**: Eine Versions Zeichenfolge.

