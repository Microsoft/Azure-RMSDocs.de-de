---
title: 'Class fileengine:: Settings'
description: 'Dokumentiert die fileengine:: Settings-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 56b4bf62af04b3b84c5ed291ce9ccb0fa0d3ee28
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215424"
---
# <a name="class-fileenginesettings"></a>Class fileengine:: Settings 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: String& EngineID, Konst Std:: shared_ptr \<AuthDelegate\>& authdelegat, Konstanten Std:: String& clientData, Konstante Std:: String& locale, bool loadsensitivitytypes)  |  Der FileEngine::Settings-Konstruktor zum Laden einer vorhandenen Engine
öffentliche Einstellungen (Konstante Identität& Identität, Konst Std:: shared_ptr \<AuthDelegate\>& authdelegat, Konstanten Std:: String& clientData, Konstante Std:: String& locale, bool loadsensitivitytypes)  |  Der FileProfile::Settings-Konstruktor für die Erstellung einer neuen Engine
public const std::string& GetEngineId() const  |  Gibt die Engine-ID zurück.
public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Gibt die Engine-Identität zurück.
public void SetIdentity(const Identity& identity)  |  Legt die Engine-Identität fest.
public const std::string& GetClientData() const  |  Gibt die Engine-Clientdaten zurück.
public const std::string& GetLocale() const  |  Gibt das Engine-Gebietsschema zurück.
öffentliches void setcustomsettings (Konstante Std:: Vector \<std::pair\<std::string, std::string\> \>& Wert)  |  Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  |  Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID für die Engine fest.
public const std::string& GetSessionId() const  |  Gibt die Sitzungs-ID für die Engine zurück.
öffentliches void setcloud (Cloud Cloud)  |  Legt optional die zielcloud fest.
öffentliche Cloud getcloud () konstant  |  Ruft die zielcloud ab, die von allen Service Requests verwendet wird.
public void SetProtectionCloudEndpointBaseUrl(const std::string& protectionCloudEndpointBaseUrl)  |  Legt die Basis-URL der Schutz-Cloud für die benutzerdefinierte Cloud fest.
public const std::string& GetProtectionCloudEndpointBaseUrl() const  |  Ruft die Basis-URL des Protection Cloud-Endpunkts ab
öffentliches void setpolicycloudendpointbaseurl (Konstanten Std:: String& policycloudendpointbaseurl)  |  Legt die Basis-URL der Richtlinien-Cloud für die benutzerdefinierte Cloud fest.
Public Konstanten Std:: String& getpolicycloudendpointbaseurl () Konstanten  |  Ruft die Basis-URL der richtliniencloud ab.
öffentliches void setschutzonlyengine (boolescher Schutz)  |  Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
public const bool IsProtectionOnlyEngine() const  |  Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
public bool isloadsensitivitytypesaktivierte () Konstante  |  Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.
öffentliches void-enablepfile (boolescher Wert)  |  Legt das Flag fest, das angibt, ob pfiles erzeugt.
Public Konstanten bool ispfileaktivierte ()  |  Rufen Sie das Flag ab, das angibt, ob pfiles erzeugt.
öffentliches void setdelegateduseremail (konstant Std:: String& delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String& getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
öffentliches void setlabelfilter (Konstante Std:: Vector \<LabelFilterType\>& depreseedlabelfilters)  |  Legt den Bezeichnungs Filter fest.
Public Konstanten Std:: Vector \<LabelFilterType\>& getlabelfilter () Konstanten  |  Ruft die Beschriftungs Filter ab, die über die veraltete Funktion setlabelfilter festgelegt wurden.
öffentliches void konfigurierte Funktionen (functionalityfiltertype functionalityfiltertype, bool aktiviert)  |  Aktiviert oder deaktiviert die-Funktionalität.
Public Konstanten Std:: map \<FunctionalityFilterType, bool\>& GetConfig redfunktion() Konstanten  |  Ruft die konfigurierte Funktionalität ab.
öffentliches void setauthdelegat (Konstanten Std:: shared_ptr \<AuthDelegate\>& authdelegat)  |  Legen Sie den Autorisierungs Delegaten für die Engine fest.
public std::shared_ptr\<AuthDelegate\> GetAuthDelegate() const  |  Holen Sie sich den Authentifizierungs Delegaten für die Engine.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Der FileEngine::Settings-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **EngineID**: Legen Sie diese auf die eindeutige Engine-ID fest, die von addengineasync generiert wurde. 


* **authdelegat**: der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird, überschreibt den policyprofile:: Settings:: authdelegaten, wenn beide bereitgestellt werden. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **loadsensitivitytypes**: ein optionales Flag, das anzeigt, wann die Engine geladen wird, sollte auch benutzerdefinierte Empfindlichkeits Typen laden, wenn true onpolicychange Observer im Profil für Aktualisierungen von benutzerdefinierten Sensitivitäts Typen und Richtlinien Änderungen aufgerufen wird. Wenn der Befehl "false listsensitivitytypes" aufruft, wird immer eine leere Liste zurückgegeben.


  
### <a name="settings-function"></a>Settings-Funktion
Der FileProfile::Settings-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **identity**: Informationen zur Identität des Benutzers, der der neuen Engine zugeordnet ist. 


* **authdelegat**: der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird, überschreibt den policyprofile:: Settings:: authdelegaten, wenn beide bereitgestellt werden. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **loadsensitivitytypes**: ein optionales Flag, das anzeigt, wann die Engine geladen wird, sollte auch benutzerdefinierte Empfindlichkeits Typen laden, wenn true onpolicychange Observer im Profil für Aktualisierungen von benutzerdefinierten Sensitivitäts Typen und Richtlinien Änderungen aufgerufen wird. Wenn der Befehl "false listsensitivitytypes" aufruft, wird immer eine leere Liste zurückgegeben.


  
### <a name="getengineid-function"></a>Getengineid-Funktion
Gibt die Engine-ID zurück.
  
### <a name="setengineid-function"></a>Funktion "stengineid"
Legt die Engine-ID fest.

Parameter:  
* **id**: Engine-ID.


  
### <a name="getidentity-function"></a>GetIdentity-Funktion
Gibt die Engine-Identität zurück.
  
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
  
### <a name="setcloud-function"></a>Setcloud-Funktion
Legt optional die zielcloud fest.

Parameter:  
* **Cloud**: Cloud


Wenn die Cloud nicht angegeben ist, wird standardmäßig die globale Cloud verwendet.
  
### <a name="getcloud-function"></a>Getcloud-Funktion
Ruft die zielcloud ab, die von allen Service Requests verwendet wird.

  
**Gibt Folgendes zurück**: Cloud
  
### <a name="setprotectioncloudendpointbaseurl-function"></a>Setschutzcloudendpointbaseurl-Funktion
Legt die Basis-URL der Schutz-Cloud für die benutzerdefinierte Cloud fest.

Parameter:  
* **protectionCloudEndpointBaseUrl**: mit Schutzendpunkten verknüpfte Basis-URL


Dieser Wert wird nur gelesen und muss für Cloud = Custom festgelegt werden.
  
### <a name="getprotectioncloudendpointbaseurl-function"></a>Getschutzcloudendpointbaseurl-Funktion
Ruft die Basis-URL des Protection Cloud-Endpunkts ab

  
**Gibt zurück**: Basis-URL, die mit Schutz Endpunkten verknüpft ist dieser Wert wird nur gelesen und muss für Cloud = Custom festgelegt werden.
  
### <a name="setpolicycloudendpointbaseurl-function"></a>Setpolicycloudendpointbaseurl-Funktion
Legt die Basis-URL der Richtlinien-Cloud für die benutzerdefinierte Cloud fest.

Parameter:  
* **policycloudendpointbaseurl**: Basis-URL, die Richtlinien Endpunkten zugeordnet ist


  
### <a name="getpolicycloudendpointbaseurl-function"></a>Getpolicycloudendpointbaseurl-Funktion
Ruft die Basis-URL der richtliniencloud ab.

  
**Gibt zurück**: Basis-URL, die Richtlinien Endpunkten zugeordnet ist.
  
### <a name="setprotectiononlyengine-function"></a>Setschutzonlyengine-Funktion
Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
  
### <a name="isprotectiononlyengine-function"></a>Isprotectiononlyengine-Funktion
Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
  
### <a name="isloadsensitivitytypesenabled-function"></a>Isloadsensitivitytypesaktivierte Funktion
Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.

  
**Gibt Folgendes zurück**: true, wenn aktiviert, andernfalls false.
  
### <a name="enablepfile-function"></a>Enablepfile-Funktion
Legt das Flag fest, das angibt, ob pfiles erzeugt.
  
### <a name="ispfileenabled-function"></a>Ispfileaktivierte-Funktion
Rufen Sie das Flag ab, das angibt, ob pfiles erzeugt.

  
**Gibt Folgendes zurück**: true, wenn aktiviert, andernfalls false.
  
### <a name="setdelegateduseremail-function"></a>Setdelegateduseremail-Funktion
Legt den Delegierten Benutzer fest.

Parameter:  
* **delegateduseremail**: die Delegierungs-e-Mail.


Ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="getdelegateduseremail-function"></a>Getdelegateduseremail-Funktion
Ruft den Delegierten Benutzer ab.

  
**Returns**: Delegierter Benutzer ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="setlabelfilter-function"></a>Setlabelfilter-Funktion
Legt den Bezeichnungs Filter fest.

Parameter:  
* **labelfilter**: der Bezeichnungs Filter.


Bezeichnungen werden standardmäßig für den Bereich gefiltert. diese API ermöglicht das Filtern nach möglichen Aktionen. Wenn nicht festgelegt, werden "hyokprotection" und "doublekeyprotection" gefiltert.
  
### <a name="getlabelfilter-function"></a>Getlabelfilter-Funktion
Ruft die Beschriftungs Filter ab, die über die veraltete Funktion setlabelfilter festgelegt wurden.

  
**Gibt Folgendes zurück**: der Bezeichnungs Filter.
Bezeichnungen werden standardmäßig für den Bereich gefiltert. diese API ermöglicht das Filtern nach möglichen Aktionen.
  
### <a name="configurefunctionality-function"></a>Funktion "konfigurier Funktion"
Aktiviert oder deaktiviert die-Funktionalität.

Parameter:  
* **functionalityfiltertype: der Funktionstyp**. 


* **aktiviert**: true zum Aktivieren, false zum Deaktivieren


Hyokprotection, doublekeyprotection, doublekeyuserdefinedprotection sind standardmäßig deaktiviert und müssen aktiviert werden.
  
### <a name="getconfiguredfunctionality-function"></a>Getkonfiguriredfunction-Funktion
Ruft die konfigurierte Funktionalität ab.

  
**Gibt Folgendes zurück**: eine Zuordnung der Typen zu einem booleschen Wert, der angibt, ob er aktiviert ist.
  
### <a name="setauthdelegate-function"></a>Setauthdelegatfunktion
Legen Sie den Autorisierungs Delegaten für die Engine fest.

Parameter:  
* **authdelegat**: der Authentifizierungs Delegat.


  
### <a name="getauthdelegate-function"></a>Getauthdelegatfunktion
Holen Sie sich den Authentifizierungs Delegaten für die Engine.

  
**Gibt Folgendes zurück**: der Engine auth-Delegat.