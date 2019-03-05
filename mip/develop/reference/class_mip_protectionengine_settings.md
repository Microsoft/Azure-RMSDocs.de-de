---
title: mip::ProtectionEngine::Settings-Klasse
description: Dokumentiert die mip::protectionengine-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: d874e57806ecf2ee98fa41eb3b655e9525ed8362
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333754"
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
public const Identity& GetIdentity() const  |  Ruft den Benutzer ab [Identität](class_mip_identity.md) die Engine zugeordnet.
public void SetIdentity(const Identity& identity)  |  Den Benutzer legt [Identität](class_mip_identity.md) die Engine zugeordnet.
public const std::string& GetClientData() const  |  Ruft vom Client festgelegte benutzerdefinierte Daten ab.
public void SetClientData(const std::string& clientData)  |  Legt vom Client festgelegte benutzerdefinierte Daten fest.
public const std::string& GetLocale() const  |  Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.
Öffentliche void SetCustomSettings (const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& Wert)  |  Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetCustomSettings() const  |  Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID der Engine ab.
public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt optional die Basis-URL für den Cloudendpunkt fest.
public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **identity**: [Identität](class_mip_identity.md) , die zugeordnet wird [ProtectionEngine](class_mip_protectionengine.md)


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt werden.


  
### <a name="settings-function"></a>Settings-Funktion
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: Eindeutiger Bezeichner des Datenbankmoduls, die geladen werden 


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt werden.


  
### <a name="getengineid-function"></a>GetEngineId-Funktion
Ruft die Engine-ID ab.

  
**Gibt**: Engine-ID
  
### <a name="setengineid-function"></a>SetEngineId-Funktion
Legt die Engine-ID fest.

Parameter:  
* **engineId**: Engine-ID


  
### <a name="getidentity-function"></a>"Getidentity"-Funktion
Ruft den Benutzer ab [Identität](class_mip_identity.md) die Engine zugeordnet.

  
**Gibt**: Benutzer [Identität](class_mip_identity.md) verknüpft ist, mit der Engine
  
### <a name="setidentity-function"></a>SetIdentity-Funktion
Den Benutzer legt [Identität](class_mip_identity.md) die Engine zugeordnet.

Parameter:  
* **identity**: Benutzer [Identität](class_mip_identity.md) verknüpft ist, mit der Engine


  
### <a name="getclientdata-function"></a>GetClientData-Funktion
Ruft vom Client festgelegte benutzerdefinierte Daten ab.

  
**Gibt**: Benutzerdefinierte Daten, die vom Client angegebene
  
### <a name="setclientdata-function"></a>SetClientData-Funktion
Legt vom Client festgelegte benutzerdefinierte Daten fest.

Parameter:  
* **Custom**: vom Client festgelegte Daten


  
### <a name="getlocale-function"></a>GetLocale-Funktion
Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.

  
**Gibt**: Gebietsschema in die Engine die Daten geschrieben werden
  
### <a name="setcustomsettings-function"></a>SetCustomSettings-Funktion
Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.

Parameter:  
* **customSettings**: Name/Wert-Paaren, die für Tests und Versuche verwendet werden.


  
### <a name="getcustomsettings-function"></a>GetCustomSettings-Funktion
Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.

  
**Gibt**: Name/Wert-Paaren, die für Tests und Versuche verwendet werden.
  
### <a name="setsessionid-function"></a>SetSessionId-Funktion
Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.

Parameter:  
* **sessionId**: Engine-Sitzungs-ID, für die Korrelation der Protokollierung bzw. der Telemetrie


  
### <a name="getsessionid-function"></a>GetSessionId-Funktion
Ruft die Sitzungs-ID der Engine ab.

  
**Gibt**: Engine-Sitzungs-ID
  
### <a name="setcloudendpointbaseurl-function"></a>SetCloudEndpointBaseUrl function
Legt optional die Basis-URL für den Cloudendpunkt fest.

Parameter:  
* **cloudEndpointBaseUrl**: die Basis-URL, die von allen Service Requests verwendet wird (z.B. https://api.aadrm.com)


Wenn keine Basis-URL angegeben ist, wird diese über die DNS-Suche der Domäne der Engine-Identität bestimmt.
  
### <a name="getcloudendpointbaseurl-function"></a>GetCloudEndpointBaseUrl function
Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.

  
**Gibt**: Basis-URL
