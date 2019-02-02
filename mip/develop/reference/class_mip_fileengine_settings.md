---
title: mip::FileEngine::Settings-Klasse
description: 'Beschreibt die Klasse:: fileengine-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: db189020c13340409d2aca2f0bdc054dfc961b09
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650764"
---
# <a name="class-mipfileenginesettings"></a>mip::FileEngine::Settings-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale, bool loadSensitivityTypes)  |  Der [FileEngine::Settings](class_mip_fileengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine
public Settings(const Identity& identity, const std::string& clientData, const std::string& locale, bool loadSensitivityTypes)  |  Der [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor für die Erstellung einer neuen Engine
public const std::string& GetEngineId() const  |  Gibt die Engine-ID zurück.
public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Gibt die Engine [Identität](class_mip_identity.md).
public void SetIdentity(const Identity& identity)  |  Legt die Engine-Identität fest.
public const std::string& GetClientData() const  |  Gibt die Engine-Clientdaten zurück.
public const std::string& GetLocale() const  |  Gibt das Engine-Gebietsschema zurück.
Öffentliche void SetCustomSettings (const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& Wert)  |  Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetCustomSettings() const  |  Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID für die Engine fest.
public const std::string& GetSessionId() const  |  Gibt die Sitzungs-ID für die Engine zurück.
public void SetProtectionCloudEndpointBaseUrl(const std::string& protectionCloudEndpointBaseUrl)  |  Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.
public const std::string& GetProtectionCloudEndpointBaseUrl() const  |  Ruft „cloudEndpointBaseUrl“ ab.
public void SetProtectionOnlyEngine(const bool protectionOnly)  |  Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
public const bool IsProtectionOnlyEngine() const  |  Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
public bool IsLoadSensitivityTypesEnabled() const  |  Abrufen der das Flag gibt an, ob Load vertraulichkeitsbezeichnungen aktiviert ist.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Der [FileEngine::Settings](class_mip_fileengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: Legen Sie sie an, auf die eindeutige Engine-ID generiert, von addengineasync erzeugt wurde. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **loadSensitivityTypes**: Optionale Kennzeichen, das angibt, wenn das Skriptmodul geladen ist sollte auch benutzerdefinierte Empfindlichkeit Typen laden, wenn "true" OnPolicyChange Beobachter für das Profil für Updates für benutzerdefinierte Empfindlichkeit-Typen sowie der Änderungen aufgerufen werden soll. Wenn "false" ListSensitivityTypes aufrufen, gibt immer eine leere Liste zurück.


  
### <a name="settings-function"></a>Settings-Funktion
Der [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **identity**: [Identität](class_mip_identity.md) Informationen des Benutzers, das neue Modul zugeordnet. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **loadSensitivityTypes**: Optionale Kennzeichen, das angibt, wenn das Skriptmodul geladen ist sollte auch benutzerdefinierte Empfindlichkeit Typen laden, wenn "true" OnPolicyChange Beobachter für das Profil für Updates für benutzerdefinierte Empfindlichkeit-Typen sowie der Änderungen aufgerufen werden soll. Wenn "false" ListSensitivityTypes aufrufen, gibt immer eine leere Liste zurück.


  
### <a name="getengineid-function"></a>GetEngineId-Funktion
Gibt die Engine-ID zurück.
  
### <a name="setengineid-function"></a>SetEngineId-Funktion
Legt die Engine-ID fest.

Parameter:  
* **id**: Engine-ID.


  
### <a name="getidentity-function"></a>"Getidentity"-Funktion
Gibt die Engine [Identität](class_mip_identity.md).
  
### <a name="setidentity-function"></a>SetIdentity-Funktion
Legt die Engine-Identität fest.
  
### <a name="getclientdata-function"></a>GetClientData-Funktion
Gibt die Engine-Clientdaten zurück.
  
### <a name="getlocale-function"></a>GetLocale-Funktion
Gibt das Engine-Gebietsschema zurück.
  
### <a name="setcustomsettings-function"></a>SetCustomSettings-Funktion
Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
  
### <a name="getcustomsettings-function"></a>GetCustomSettings-Funktion
Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
  
### <a name="setsessionid-function"></a>SetSessionId-Funktion
Legt die Sitzungs-ID für die Engine fest.
  
### <a name="getsessionid-function"></a>GetSessionId-Funktion
Gibt die Sitzungs-ID für die Engine zurück.
  
### <a name="setprotectioncloudendpointbaseurl-function"></a>SetProtectionCloudEndpointBaseUrl function
Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.

Parameter:  
* **protectionCloudEndpointBaseUrl**: Schutz von Endpunkten zugeordnet Basis-url


  
### <a name="getprotectioncloudendpointbaseurl-function"></a>GetProtectionCloudEndpointBaseUrl function
Ruft „cloudEndpointBaseUrl“ ab.

  
**Gibt**: Schutz von Endpunkten zugeordnet Basis-url
  
### <a name="setprotectiononlyengine-function"></a>SetProtectionOnlyEngine-Funktion
Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
  
### <a name="isprotectiononlyengine-function"></a>IsProtectionOnlyEngine function
Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
  
### <a name="isloadsensitivitytypesenabled-function"></a>IsLoadSensitivityTypesEnabled-Funktion
Abrufen der das Flag gibt an, ob Load vertraulichkeitsbezeichnungen aktiviert ist.

  
**Gibt**: True, wenn aktiviert, andernfalls False.