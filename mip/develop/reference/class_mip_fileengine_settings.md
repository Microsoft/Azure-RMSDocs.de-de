---
title: Die Klasse „mip::FileEngine::Settings“
description: Referenz zur Klasse „mip::FileEngine::Settings“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 656ad1cf21a2d761dfb4c857b278b7421ee2b790
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446480"
---
# <a name="class-mipfileenginesettings"></a>mip::FileEngine::Settings-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  Der [FileEngine::Settings](class_mip_fileengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  Der [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor für die Erstellung einer neuen Engine
 public const std::string& GetEngineId() const  |  Gibt die Engine-ID zurück.
 public const Identity& GetIdentity() const  |  Gibt die Engine-Identität zurück.
 public void SetIdentity(const Identity& identity)  |  Legt die Engine-Identität fest.
 public const std::string& GetClientData() const  |  Gibt die Engine-Clientdaten zurück.
 public const std::string& GetLocale() const  |  Gibt das Engine-Gebietsschema zurück.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& value)  |  Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID für die Engine fest.
 public const std::string& GetSessionId() const  |  Gibt die Sitzungs-ID für die Engine zurück.
 public void SetProtectionCloudEndpointBaseUrl(const std::string& protectionCloudEndpointBaseUrl)  |  Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.
 public const std::string& GetProtectionCloudEndpointBaseUrl() const  |  Ruft „cloudEndpointBaseUrl“ ab.
 public void SetProtectionOnlyEngine(const bool protectionOnly)  |  Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
 public const bool IsProtectionOnlyEngine() const  |  Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Der [FileEngine::Settings](class_mip_fileengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: Legen Sie diese auf die eindeutige Engine-ID fest, die von AddEngineAsync erzeugt wurde. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt.


  
### <a name="settings"></a>Einstellung
Der [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **identity**: Informationen zur Identität des Benutzers, der der neuen Engine zugeordnet ist. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt.


  
### <a name="getengineid"></a>GetEngineId
Gibt die Engine-ID zurück.
  
### <a name="getidentity"></a>GetIdentity
Gibt die Engine-Identität zurück.
  
### <a name="setidentity"></a>SetIdentity
Legt die Engine-Identität fest.
  
### <a name="getclientdata"></a>GetClientData
Gibt die Engine-Clientdaten zurück.
  
### <a name="getlocale"></a>GetLocale
Gibt das Engine-Gebietsschema zurück.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID für die Engine fest.
  
### <a name="getsessionid"></a>GetSessionId
Gibt die Sitzungs-ID für die Engine zurück.
  
### <a name="setprotectioncloudendpointbaseurl"></a>SetProtectionCloudEndpointBaseUrl
Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.

Parameter:  
* **protectionCloudEndpointBaseUrl**: mit Schutzendpunkten verknüpfte Basis-URL


  
### <a name="getprotectioncloudendpointbaseurl"></a>GetProtectionCloudEndpointBaseUrl
Ruft „cloudEndpointBaseUrl“ ab.

  
**Rückgabe**: mit Schutzendpunkten verknüpfte Basis-URL
  
### <a name="setprotectiononlyengine"></a>SetProtectionOnlyEngine
Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
  
### <a name="isprotectiononlyengine"></a>IsProtectionOnlyEngine
Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.