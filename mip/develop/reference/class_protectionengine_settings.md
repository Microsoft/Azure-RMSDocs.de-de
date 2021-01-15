---
title: 'Class schutzengine:: Settings'
description: 'Dokumentiert die schutzengine:: Settings-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 015c806c8830fd932354a1cc6afa33e15b9c1256
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98224947"
---
# <a name="class-protectionenginesettings"></a>Class schutzengine:: Settings 
Einstellungen, die während der Erstellung und Lebensdauer von ProtectionEngine verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Identität& Identität, Konstanten Std:: shared_ptr \<AuthDelegate\>& authdelegat, Konstanten Std:: String& clientData, Konstante Std:: String& locale)  |  ProtectionEngine::Settings-Konstruktor für die Erstellung einer neuen Engine
öffentliche Einstellungen (Konstante Std:: String& EngineID, Konstanten Std:: shared_ptr \<AuthDelegate\>& authdelegat, Konstanten Std:: String& clientData, Konstante Std:: String& locale)  |  ProtectionEngine::Settings-Konstruktor zum Laden einer vorhandenen Engine
public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
public void SetEngineId(const std::string& engineId)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Ruft die Benutzeridentität ab, die der Engine zugeordnet ist.
public void SetIdentity(const Identity& identity)  |  Legt die Benutzeridentität fest, die der Engine zugeordnet ist.
public const std::string& GetClientData() const  |  Ruft vom Client festgelegte benutzerdefinierte Daten ab.
public void SetClientData(const std::string& clientData)  |  Legt vom Client festgelegte benutzerdefinierte Daten fest.
public const std::string& GetLocale() const  |  Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.
öffentliches void setcustomsettings (Konstante Std:: Vector \<std::pair\<std::string, std::string\> \>& Wert)  |  Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  |  Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID der Engine fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID der Engine ab.
öffentliches void setcloud (Cloud Cloud)  |  Legt optional die zielcloud fest.
öffentliche Cloud getcloud () konstant  |  Ruft die zielcloud ab, die von allen Service Requests verwendet wird.
public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt die Basis-URL für den cloudendpunkt für die benutzerdefinierte Cloud fest
public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.
öffentliches void setauthdelegat (Konstanten Std:: shared_ptr \<AuthDelegate\>& authdelegat)  |  Legen Sie den Autorisierungs Delegaten für die Engine fest.
public std::shared_ptr\<AuthDelegate\> GetAuthDelegate() const  |  Holen Sie sich den Authentifizierungs Delegaten für die Engine.
Public Konstanten Std:: String& getunderlyingapplicationid () Konstanten  |  Ruft die zugrunde liegende Anwendungs-ID ab.
öffentliches void setunderlyingapplicationid (Konstanten Std:: String& underlyingapplicationid)  |  Legt die zugrunde liegende Anwendungs-ID fest.
public bool getallowcloudserviceonly () konstant  |  Ruft ab, ob nur der clouddienst zulässig ist.
öffentliches void "*", "*", allowcloudserviceonly)  |  Legt fest, ob nur der clouddienst zulässig ist.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
ProtectionEngine::Settings-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **identity**: Identität, die ProtectionEngine zugeordnet wird


* **authdelegat**: der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird, überschreibt den policyprofile:: Settings:: authdelegaten, wenn beide bereitgestellt werden. 


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt.


  
### <a name="settings-function"></a>Settings-Funktion
ProtectionEngine::Settings-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: eindeutiger Bezeichner der Engine, der geladen wird 


* **authdelegat**: der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird, überschreibt den policyprofile:: Settings:: authdelegaten, wenn beide bereitgestellt werden. 


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt.


  
### <a name="getengineid-function"></a>Getengineid-Funktion
Ruft die Engine-ID ab.

  
**Gibt Folgendes zurück**: Engine-ID
  
### <a name="setengineid-function"></a>Funktion "stengineid"
Legt die Engine-ID fest.

Parameter:  
* **EngineID**: Engine-ID.


  
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
* **SessionID**: Engine-Sitzungs-ID, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.


  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Ruft die Sitzungs-ID der Engine ab.

  
**Returns**: Engine-Sitzungs-ID
  
### <a name="setcloud-function"></a>Setcloud-Funktion
Legt optional die zielcloud fest.

Parameter:  
* **Cloud**: Cloud


Wenn die Cloud nicht angegeben ist, wird Sie nach Möglichkeit von der DNS-Suche nach der Identitäts Domäne der Engine bestimmt. andernfalls greifen Sie auf die globale Cloud zurück.
  
### <a name="getcloud-function"></a>Getcloud-Funktion
Ruft die zielcloud ab, die von allen Service Requests verwendet wird.

  
**Gibt Folgendes zurück**: Cloud
  
### <a name="setcloudendpointbaseurl-function"></a>Setcloudendpointbaseurl-Funktion
Legt die Basis-URL für den cloudendpunkt für die benutzerdefinierte Cloud fest

Parameter:  
* **cloudEndpointBaseUrl**: die Basis-URL, die von allen Service Requests verwendet wird (z.B. https://api.aadrm.com)


Dieser Wert wird nur gelesen und muss für Cloud = Custom festgelegt werden.
  
### <a name="getcloudendpointbaseurl-function"></a>Getcloudendpointbaseurl-Funktion
Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.

  
**Rückgabe:** Basis-URL
  
### <a name="setauthdelegate-function"></a>Setauthdelegatfunktion
Legen Sie den Autorisierungs Delegaten für die Engine fest.

Parameter:  
* **authdelegat**: der Authentifizierungs Delegat.


  
### <a name="getauthdelegate-function"></a>Getauthdelegatfunktion
Holen Sie sich den Authentifizierungs Delegaten für die Engine.

  
**Gibt Folgendes zurück**: der Engine auth-Delegat.
  
### <a name="getunderlyingapplicationid-function"></a>Getunderlyingapplicationid-Funktion
Ruft die zugrunde liegende Anwendungs-ID ab.

  
**Returns**: zugrunde liegende Anwendungs-ID
  
### <a name="setunderlyingapplicationid-function"></a>Setunderlyingapplicationid-Funktion
Legt die zugrunde liegende Anwendungs-ID fest.

Parameter:  
* **Underlyingapplicationid**: zugrunde liegende Anwendungs-ID.


  
### <a name="getallowcloudserviceonly-function"></a>Getallowcloudserviceonly-Funktion
Ruft ab, ob nur der clouddienst zulässig ist.

  
**Returns**: ein boolescher Wert, der angibt, ob nur der clouddienst zulässig ist.
  
### <a name="setallowcloudserviceonly-function"></a>Stallowcloudserviceonly-Funktion
Legt fest, ob nur der clouddienst zulässig ist.

Parameter:  
* **allowcloudserviceonly**: ein boolescher Wert, der angibt, ob nur der clouddienst zulässig ist.

