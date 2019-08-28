---
title: mip::FileEngine::Settings-Klasse
description: 'Dokumentiert die MIP:: fileengine-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 7d0845c2bf7516a4fc0a85b690fa94059253cde8
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70055036"
---
# <a name="class-mipfileenginesettings"></a>mip::FileEngine::Settings-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: String & EngineID, Konst Std:: String & clientData, Konstante Std:: String & locale, bool loadsensitivitytypes)  |  Der [FileEngine::Settings](class_mip_fileengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine
öffentliche Einstellungen (Konstante Identität & Identität, Konst Std:: String & clientData, Konstante Std:: String & locale, bool loadsensitivitytypes)  |  Der [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor für die Erstellung einer neuen Engine
public const std::string& GetEngineId() const  |  Gibt die Engine-ID zurück.
public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Gibt die Engine- [Identität](class_mip_identity.md)zurück.
public void SetIdentity(const Identity& identity)  |  Legt die Engine-Identität fest.
public const std::string& GetClientData() const  |  Gibt die Engine-Clientdaten zurück.
public const std::string& GetLocale() const  |  Gibt das Engine-Gebietsschema zurück.
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& Wert)  |  Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () Konstanten  |  Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID für die Engine fest.
public const std::string& GetSessionId() const  |  Gibt die Sitzungs-ID für die Engine zurück.
public void SetProtectionCloudEndpointBaseUrl(const std::string& protectionCloudEndpointBaseUrl)  |  Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.
public const std::string& GetProtectionCloudEndpointBaseUrl() const  |  Ruft die Basis-URL des Protection Cloud-Endpunkts ab
öffentliches void setpolicycloudendpointbaseurl (Konstanten Std:: String & policycloudendpointbaseurl)  |  Legt die Basis-URL der richtliniencloud fest, die zum Angeben der cloudgrenze verwendet wird
Public Konstanten Std:: String & getpolicycloudendpointbaseurl () Konstanten  |  Ruft die Basis-URL der richtliniencloud ab.
öffentliches void setschutzonlyengine (boolescher Schutz)  |  Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
public const bool IsProtectionOnlyEngine() const  |  Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
public bool isloadsensitivitytypesaktivierte () Konstante  |  Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.
öffentliches void-enablepfile (boolescher Wert)  |  Legt das Flag fest, das angibt, ob pfiles erzeugt.
Public Konstanten bool ispfileaktivierte ()  |  Rufen Sie das Flag ab, das angibt, ob pfiles erzeugt.
öffentliches void setdelegateduseremail (konstant Std:: String & delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String & getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Der [FileEngine::Settings](class_mip_fileengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: Legen Sie Sie auf die eindeutige Engine-ID fest, die von addengineasync generiert wurde. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **loadSensitivityTypes**: Optionales Flag, das anzeigt, wann die Engine geladen wird, sollte auch benutzerdefinierte Empfindlichkeits Typen laden, wenn true onpolicychange Observer im Profil für Aktualisierungen von benutzerdefinierten Empfindlichkeits Typen sowie Richtlinien Änderungen aufgerufen wird. Wenn der Befehl "false listsensitivitytypes" aufruft, wird immer eine leere Liste zurückgegeben.


  
### <a name="settings-function"></a>Settings-Funktion
Der [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **Identität**: [Identitäts](class_mip_identity.md) Informationen des Benutzers, der der neuen Engine zugeordnet ist. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **loadSensitivityTypes**: Optionales Flag, das anzeigt, wann die Engine geladen wird, sollte auch benutzerdefinierte Empfindlichkeits Typen laden, wenn true onpolicychange Observer im Profil für Aktualisierungen von benutzerdefinierten Empfindlichkeits Typen sowie Richtlinien Änderungen aufgerufen wird. Wenn der Befehl "false listsensitivitytypes" aufruft, wird immer eine leere Liste zurückgegeben.


  
### <a name="getengineid-function"></a>Getengineid-Funktion
Gibt die Engine-ID zurück.
  
### <a name="setengineid-function"></a>Funktion "stengineid"
Legt die Engine-ID fest.

Parameter:  
* **id**: Engine-ID.


  
### <a name="getidentity-function"></a>GetIdentity-Funktion
Gibt die Engine- [Identität](class_mip_identity.md)zurück.
  
### <a name="setidentity-function"></a>Die Funktion "Funktion"
Legt die Engine-Identität fest.
  
### <a name="getclientdata-function"></a>Getclientdata-Funktion
Gibt die Engine-Clientdaten zurück.
  
### <a name="getlocale-function"></a>GetLocale-Funktion
Gibt das Engine-Gebietsschema zurück.
  
### <a name="setcustomsettings-function"></a>Setcustomsettings-Funktion
Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
Legt die Sitzungs-ID für die Engine fest.
  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Gibt die Sitzungs-ID für die Engine zurück.
  
### <a name="setprotectioncloudendpointbaseurl-function"></a>Setschutzcloudendpointbaseurl-Funktion
Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.

Parameter:  
* **protectionCloudEndpointBaseUrl**: Basis-URL, die Schutz Endpunkten zugeordnet ist


  
### <a name="getprotectioncloudendpointbaseurl-function"></a>Getschutzcloudendpointbaseurl-Funktion
Ruft die Basis-URL des Protection Cloud-Endpunkts ab

  
**Gibt Folgendes zurück**: Basis-URL, die Schutz Endpunkten zugeordnet ist
  
### <a name="setpolicycloudendpointbaseurl-function"></a>Setpolicycloudendpointbaseurl-Funktion
Legt die Basis-URL der richtliniencloud fest, die zum Angeben der cloudgrenze verwendet wird

Parameter:  
* **policyCloudEndpointBaseUrl**: Basis-URL, die Richtlinien Endpunkten zugeordnet ist


  
### <a name="getpolicycloudendpointbaseurl-function"></a>Getpolicycloudendpointbaseurl-Funktion
Ruft die Basis-URL der richtliniencloud ab.

  
**Gibt Folgendes zurück**: Basis-URL, die Richtlinien Endpunkten zugeordnet ist
  
### <a name="setprotectiononlyengine-function"></a>Setschutzonlyengine-Funktion
Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
  
### <a name="isprotectiononlyengine-function"></a>Isprotectiononlyengine-Funktion
Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
  
### <a name="isloadsensitivitytypesenabled-function"></a>Isloadsensitivitytypesaktivierte Funktion
Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.

  
**Gibt Folgendes zurück**: True, wenn aktiviert, andernfalls false.
  
### <a name="enablepfile-function"></a>Enablepfile-Funktion
Legt das Flag fest, das angibt, ob pfiles erzeugt.
  
### <a name="ispfileenabled-function"></a>Ispfileaktivierte-Funktion
Rufen Sie das Flag ab, das angibt, ob pfiles erzeugt.

  
**Gibt Folgendes zurück**: True, wenn aktiviert, andernfalls false.
  
### <a name="setdelegateduseremail-function"></a>Setdelegateduseremail-Funktion
Legt den Delegierten Benutzer fest.

Parameter:  
* **delegateduseremail**: die Delegierungs-e-Mail.


Ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="getdelegateduseremail-function"></a>Getdelegateduseremail-Funktion
Ruft den Delegierten Benutzer ab.

  
**Gibt Folgendes zurück**: Delegierter Benutzer ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.