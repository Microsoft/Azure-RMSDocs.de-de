---
title: mip::ProtectionEngine::Settings-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: a083d037fcfb48ae9eee5df67fb78d53fcb5490a
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70057593"
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
public const Identity& GetIdentity() const  |  Ruft die der Engine zugeordnete Benutzer [Identität](class_mip_identity.md) ab.
public void SetIdentity(const Identity& identity)  |  Legt die der Engine zugeordnete Benutzer [Identität](class_mip_identity.md) fest.
public const std::string& GetClientData() const  |  Ruft vom Client festgelegte benutzerdefinierte Daten ab.
public void SetClientData(const std::string& clientData)  |  Legt vom Client festgelegte benutzerdefinierte Daten fest.
public const std::string& GetLocale() const  |  Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& Wert)  |  Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () Konstanten  |  Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID der Engine ab.
public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt optional die Basis-URL für den Cloudendpunkt fest.
public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **Identität**: [Identität](class_mip_identity.md) , die Schutz- [Engine](class_mip_protectionengine.md) zugeordnet wird


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* Gebiets Schema: Die Engine-Ausgabe wird in diesem Gebiets Schema bereitgestellt.


  
### <a name="settings-function"></a>Settings-Funktion
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: Eindeutiger Bezeichner der Engine, die geladen wird 


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* Gebiets Schema: Die Engine-Ausgabe wird in diesem Gebiets Schema bereitgestellt.


  
### <a name="getengineid-function"></a>Getengineid-Funktion
Ruft die Engine-ID ab.

  
**Gibt Folgendes zurück**: Engine-ID
  
### <a name="setengineid-function"></a>Funktion "stengineid"
Legt die Engine-ID fest.

Parameter:  
* **engineId**: Engine-ID


  
### <a name="getidentity-function"></a>GetIdentity-Funktion
Ruft die der Engine zugeordnete Benutzer [Identität](class_mip_identity.md) ab.

  
**Gibt Folgendes zurück**: Der Engine zugeordnete Benutzer [Identität](class_mip_identity.md)
  
### <a name="setidentity-function"></a>Die Funktion "Funktion"
Legt die der Engine zugeordnete Benutzer [Identität](class_mip_identity.md) fest.

Parameter:  
* **Identität**: Der Engine zugeordnete Benutzer [Identität](class_mip_identity.md)


  
### <a name="getclientdata-function"></a>Getclientdata-Funktion
Ruft vom Client festgelegte benutzerdefinierte Daten ab.

  
**Gibt Folgendes zurück**: Vom Client angegebene benutzerdefinierte Daten
  
### <a name="setclientdata-function"></a>Setclientdata-Funktion
Legt vom Client festgelegte benutzerdefinierte Daten fest.

Parameter:  
* **Custom**: vom Client festgelegte Daten


  
### <a name="getlocale-function"></a>GetLocale-Funktion
Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.

  
**Gibt Folgendes zurück**: Das Gebiets Schema, in dem Engine-Daten geschrieben werden.
  
### <a name="setcustomsettings-function"></a>Setcustomsettings-Funktion
Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.

Parameter:  
* **CustomSettings**: Name/Wert-Paare, die für Tests und Experimente verwendet werden


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.

  
**Gibt Folgendes zurück**: Name/Wert-Paare, die für Tests und Experimente verwendet werden
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.

Parameter:  
* **sessionId**: Engine-Sitzungs-ID, die für die Korrelation von Protokollierung/Telemetrie verwendet wird


  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Ruft die Sitzungs-ID der Engine ab.

  
**Gibt Folgendes zurück**: Engine-Sitzungs-ID
  
### <a name="setcloudendpointbaseurl-function"></a>Setcloudendpointbaseurl-Funktion
Legt optional die Basis-URL für den Cloudendpunkt fest.

Parameter:  
* **cloudEndpointBaseUrl**: die Basis-URL, die von allen Service Requests verwendet wird (z.B. https://api.aadrm.com )


Wenn keine Basis-URL angegeben ist, wird diese über die DNS-Suche der Domäne der Engine-Identität bestimmt.
  
### <a name="getcloudendpointbaseurl-function"></a>Getcloudendpointbaseurl-Funktion
Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.

  
**Gibt Folgendes zurück**: Basis-URL