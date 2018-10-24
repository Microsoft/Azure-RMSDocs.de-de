---
title: Die Klasse „mip::ProtectionEngine::Settings“
description: Referenz zur Klasse „mip::ProtectionEngine::Settings“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f61e86a87ecfea21bc9d02f4e55f3fbe663e9b80
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446701"
---
# <a name="class-mipprotectionenginesettings"></a>mip::ProtectionEngine::Settings-Klasse 
[Einstellungen](class_mip_protectionengine_settings.md), die während der Erstellung und Lebensdauer von [ProtectionEngine](class_mip_protectionengine.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor für die Erstellung einer neuen Engine
 public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine
 public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
 public void SetEngineId(const std::string& engineId)  |  Legt die Engine-ID fest.
 public const Identity& GetIdentity() const  |  Ruft die Benutzeridentität ab, die der Engine zugeordnet ist.
 public void SetIdentity(const Identity& identity)  |  Legt die Benutzeridentität fest, die der Engine zugeordnet ist.
 public const std::string& GetClientData() const  |  Ruft vom Client festgelegte benutzerdefinierte Daten ab.
 public void SetClientData(const std::string& clientData)  |  Legt vom Client festgelegte benutzerdefinierte Daten fest.
 public const std::string& GetLocale() const  |  Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& value)  |  Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID der Engine ab.
 public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt optional die Basis-URL für den Cloudendpunkt fest.
 public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **identity**: Identität, die [ProtectionEngine](class_mip_protectionengine.md) zugeordnet wird


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt.


  
### <a name="settings"></a>Einstellung
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: eindeutiger Bezeichner der Engine, der geladen wird 


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt.


  
### <a name="getengineid"></a>GetEngineId
Ruft die Engine-ID ab.

  
**Rückgabe**: Engine-ID
  
### <a name="setengineid"></a>SetEngineId
Legt die Engine-ID fest.

Parameter:  
* **engineId**: Engine-ID


  
### <a name="getidentity"></a>GetIdentity
Ruft die Benutzeridentität ab, die der Engine zugeordnet ist.

  
**Rückgabe**: der Engine zugeordnete Benutzeridentität
  
### <a name="setidentity"></a>SetIdentity
Legt die Benutzeridentität fest, die der Engine zugeordnet ist.

Parameter:  
* **identity**: der Engine zugeordnete Benutzeridentität


  
### <a name="getclientdata"></a>GetClientData
Ruft vom Client festgelegte benutzerdefinierte Daten ab.

  
**Rückgabe**: vom Client festgelegte benutzerdefinierte Daten
  
### <a name="setclientdata"></a>SetClientData
Legt vom Client festgelegte benutzerdefinierte Daten fest.

Parameter:  
* **Custom**: vom Client festgelegte Daten


  
### <a name="getlocale"></a>GetLocale
Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.

  
**Rückgabe**: Gebietsschema, in dem die Engine-Daten geschrieben werden
  
### <a name="setcustomsettings"></a>SetCustomSettings
Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.

Parameter:  
* **customSettings**: Name-Wert-Paare, die für Tests und Versuche genutzt werden


  
### <a name="getcustomsettings"></a>GetCustomSettings
Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.

  
**Rückgabe**: Name-Wert-Paare, die für Tests und Versuche genutzt werden
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.

Parameter:  
* **sessionId**: Sitzungs-ID der Engine, die für die Korrelation von Protokollierung/Telemetrie verwendet wird


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID der Engine ab.

  
**Rückgabe**: Sitzungs-ID der Engine
  
### <a name="setcloudendpointbaseurl"></a>SetCloudEndpointBaseUrl
Legt optional die Basis-URL für den Cloudendpunkt fest.

Parameter:  
* **cloudEndpointBaseUrl**: die Basis-URL, die von allen Service Requests verwendet wird (z.B. https://api.aadrm.com)


Wenn keine Basis-URL angegeben ist, wird diese über die DNS-Suche der Domäne der Engine-Identität bestimmt.
  
### <a name="getcloudendpointbaseurl"></a>GetCloudEndpointBaseUrl
Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.

  
**Rückgabe:** Basis-URL