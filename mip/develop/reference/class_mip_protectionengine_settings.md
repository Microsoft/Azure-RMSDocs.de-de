---
title: mip::ProtectionEngine::Settings-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 746309afc21637c85ec53dd9af7214151c5bb75a
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73557680"
---
# <a name="class-mipprotectionenginesettings"></a>mip::ProtectionEngine::Settings-Klasse 
Von der Schutz-Engine während ihrer Erstellung und während der gesamten Lebensdauer verwendete Einstellungen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  Protection Engine:: Settings-Konstruktor zum Erstellen einer neuen Engine.
public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  Der schutzengine:: Settings-Konstruktor zum Laden eines vorhandenen Moduls.
public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
public void SetEngineId(const std::string& engineId)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Ruft die Benutzeridentität ab, die der Engine zugeordnet ist.
public void SetIdentity(const Identity& identity)  |  Legt die Benutzeridentität fest, die der Engine zugeordnet ist.
public const std::string& GetClientData() const  |  Ruft vom Client festgelegte benutzerdefinierte Daten ab.
public void SetClientData(const std::string& clientData)  |  Legt vom Client festgelegte benutzerdefinierte Daten fest.
public const std::string& GetLocale() const  |  Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& Wert)  |  Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () konstant.  |  Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID der Engine ab.
public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt optional die Basis-URL für den Cloudendpunkt fest.
public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Protection Engine:: Settings-Konstruktor zum Erstellen einer neuen Engine.

Parameter:  
* **Identität**: die Identität, die der Schutz-Engine zugeordnet wird.


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt.


  
### <a name="settings-function"></a>Settings-Funktion
Der schutzengine:: Settings-Konstruktor zum Laden eines vorhandenen Moduls.

Parameter:  
* **engineId**: eindeutiger Bezeichner der Engine, der geladen wird 


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt.


  
### <a name="getengineid-function"></a>Getengineid-Funktion
Ruft die Engine-ID ab.

  
**Rückgabe**: Engine-ID
  
### <a name="setengineid-function"></a>Funktion "stengineid"
Legt die Engine-ID fest.

Parameter:  
* **engineId**: Engine-ID


  
### <a name="getidentity-function"></a>GetIdentity-Funktion
Ruft die Benutzeridentität ab, die der Engine zugeordnet ist.

  
**Rückgabe**: der Engine zugeordnete Benutzeridentität
  
### <a name="setidentity-function"></a>Die Funktion "Funktion"
Legt die Benutzeridentität fest, die der Engine zugeordnet ist.

Parameter:  
* **identity**: der Engine zugeordnete Benutzeridentität


  
### <a name="getclientdata-function"></a>Getclientdata-Funktion
Ruft vom Client festgelegte benutzerdefinierte Daten ab.

  
**Rückgabe**: vom Client festgelegte benutzerdefinierte Daten
  
### <a name="setclientdata-function"></a>Setclientdata-Funktion
Legt vom Client festgelegte benutzerdefinierte Daten fest.

Parameter:  
* **Custom**: vom Client festgelegte Daten


  
### <a name="getlocale-function"></a>GetLocale-Funktion
Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.

  
**Rückgabe**: Gebietsschema, in dem die Engine-Daten geschrieben werden
  
### <a name="setcustomsettings-function"></a>Setcustomsettings-Funktion
Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.

Parameter:  
* **customSettings**: Name-Wert-Paare, die für Tests und Versuche genutzt werden


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.

  
**Rückgabe**: Name-Wert-Paare, die für Tests und Versuche genutzt werden
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.

Parameter:  
* **sessionId**: Sitzungs-ID der Engine, die für die Korrelation von Protokollierung/Telemetrie verwendet wird


  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Ruft die Sitzungs-ID der Engine ab.

  
**Rückgabe**: Sitzungs-ID der Engine
  
### <a name="setcloudendpointbaseurl-function"></a>Setcloudendpointbaseurl-Funktion
Legt optional die Basis-URL für den Cloudendpunkt fest.

Parameter:  
* **cloudEndpointBaseUrl**: die Basis-URL, die von allen Service Requests verwendet wird (z.B. https://api.aadrm.com )


Wenn keine Basis-URL angegeben ist, wird diese über die DNS-Suche der Domäne der Engine-Identität bestimmt.
  
### <a name="getcloudendpointbaseurl-function"></a>Getcloudendpointbaseurl-Funktion
Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.

  
**Rückgabe:** Basis-URL