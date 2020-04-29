---
title: 'Class policyengine:: Settings'
description: 'Dokumentiert die policyengine:: Settings-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 5e745dd011f9626e031cfcb9c9ae0466e91e2bfe
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81761072"
---
# <a name="class-policyenginesettings"></a>Class policyengine:: Settings 
Definiert die einer PolicyEngine-Klasse zugeordneten Einstellungen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: String& EngineID, Konst Std:: shared_ptr\<authdelegat\>& authdelegat, Konstanten Std:: String& clientData, Konstante Std:: String& locale, bool loadsensitivitytypes)  |  PolicyEngine::Settings-Konstruktor zum Laden einer vorhandenen Engine
öffentliche Einstellungen (Konstante Identität& Identität, Konst Std:: shared_ptr\<authdelegat\>& authdelegat, Konstanten Std:: String& clientData, Konstante Std:: String& locale, bool loadsensitivitytypes)  |  PolicyEngine::Settings-Konstruktor zum Erstellen einer neuen Engine
public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Ruft das Identity-Objekt ab.
public void SetIdentity(const Identity& identity)  |  Legt das Identity-Objekt fest.
public const std::string& GetClientData() const  |  Ruft die in den Einstellungen festgelegten Clientdaten ab.
public void SetClientData(const std::string& clientData)  |  Legt die Zeichenfolge der Clientdaten fest.
public const std::string& GetLocale() const  |  Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\> \>& CustomSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\> \>& getcustomsettings () Konstanten  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.
public bool isloadsensitivitytypesaktivierte () Konstante  |  Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.
öffentliches void setcloud (Cloud Cloud)  |  Legt optional die zielcloud fest.
öffentliche Cloud getcloud () konstant  |  Ruft die zielcloud ab, die von allen Service Requests verwendet wird.
public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt die Basis-URL für den cloudendpunkt für die benutzerdefinierte Cloud fest
public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.
öffentliches void setdelegateduseremail (konstant Std:: String& delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String& getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
öffentliches void setlabelfilter (Konstanten Std:: Vector\<labelfiltertype\>& labelfilter)  |  Legt den Bezeichnungs Filter fest.
Public Konstanten Std:: Vector\<labelfiltertype\>& getlabelfilter () Konstanten  |  Ruft den Bezeichnungs Filter ab.
öffentliches void setvariabletextmarkingtype (variabletextmarkingtype variabletextmarkingtype)  |  Legt den Typ der Variablen Textmarkierung fest.
Public variabletextmarkingtype getvariabletextmarkingtype () Konstanten  |  Ruft den Typ der Variablen Textmarkierung ab.
öffentliches void setauthdelegat (Konstanten Std:: shared_ptr\<authdelegat\>& authdelegat)  |  Legen Sie den Autorisierungs Delegaten für die Engine fest.
Public Std:: shared_ptr\<authdelegat\> getauthdelegat () Konstanten  |  Holen Sie sich den Authentifizierungs Delegaten für die Engine.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
PolicyEngine::Settings-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **EngineID**: Legen Sie diese auf die eindeutige Engine-ID fest, die von addengineasync oder einem selbst generierten generiert wurde. Verwenden Sie beim Laden einer vorhandenen Engine die ID, andernfalls wird eine neue Engine erstellt. 


* **authdelegat**: der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird, überschreibt den policyprofile:: Settings:: authdelegaten, wenn beide bereitgestellt werden. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **Optional**: das Flag, das anzeigt, wann die Engine geladen wird, sollte auch benutzerdefinierte Empfindlichkeits Typen laden, wenn true onpolicychange Observer im Profil für Aktualisierungen von benutzerdefinierten Empfindlichkeits Typen und Richtlinien Änderungen aufgerufen wird. Wenn der Befehl "false listsensitivitytypes" aufruft, wird immer eine leere Liste zurückgegeben.


  
### <a name="settings-function"></a>Settings-Funktion
PolicyEngine::Settings-Konstruktor zum Erstellen einer neuen Engine

Parameter:  
* **identity**: Informationen zur Identität des Benutzers, der der neuen Engine zugeordnet ist. 


* **authdelegat**: der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird, überschreibt den policyprofile:: Settings:: authdelegaten, wenn beide bereitgestellt werden. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **Optional**: das Flag, das anzeigt, wann die Engine geladen wird, sollte auch benutzerdefinierte Empfindlichkeits Typen laden, wenn true onpolicychange Observer im Profil für Aktualisierungen von benutzerdefinierten Empfindlichkeits Typen und Richtlinien Änderungen aufgerufen wird. Wenn der Befehl "false listsensitivitytypes" aufruft, wird immer eine leere Liste zurückgegeben.


  
### <a name="getengineid-function"></a>Getengineid-Funktion
Ruft die Engine-ID ab.

  
**Rückgabe**: Eindeutige Zeichenfolge, die die Engine identifiziert.
  
### <a name="setengineid-function"></a>Funktion "stengineid"
Legt die Engine-ID fest.

Parameter:  
* **id**: Engine-ID.


  
### <a name="getidentity-function"></a>GetIdentity-Funktion
Ruft das Identity-Objekt ab.

  
**Rückgabe**: Verweis auf die Identität im Einstellungsobjekt. 
  
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="setidentity-function"></a>Die Funktion "Funktion"
Legt das Identity-Objekt fest.

Parameter:  
* **Identität**: die eindeutige Identität eines Benutzers. 


  
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="getclientdata-function"></a>Getclientdata-Funktion
Ruft die in den Einstellungen festgelegten Clientdaten ab.

  
**Rückgabe**: Vom Client angegebene Datenzeichenfolge.
  
### <a name="setclientdata-function"></a>Setclientdata-Funktion
Legt die Zeichenfolge der Clientdaten fest.

Parameter:  
* **clientData**: benutzerdefinierte Daten.


  
### <a name="getlocale-function"></a>GetLocale-Funktion
Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.

  
**Rückgabe**: Das Gebietsschema.
  
### <a name="setcustomsettings-function"></a>Setcustomsettings-Funktion
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.

Parameter:  
* **CustomSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Rückgabe**: Liste von Name-Wert-Paaren
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.

Parameter:  
* **SessionID**: eine eindeutige Zeichenfolge, die telemetrieereignisse verbindet.


  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.

  
**Rückgabe**: die Sitzungs-ID.
  
### <a name="isloadsensitivitytypesenabled-function"></a>Isloadsensitivitytypesaktivierte Funktion
Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.

  
**Gibt Folgendes zurück**: true, wenn aktiviert, andernfalls false.
  
### <a name="setcloud-function"></a>Setcloud-Funktion
Legt optional die zielcloud fest.

Parameter:  
* **Cloud**: Cloud


Wenn Cloud nicht angegeben ist, wird standardmäßig die kommerzielle Cloud verwendet.
  
### <a name="getcloud-function"></a>Getcloud-Funktion
Ruft die zielcloud ab, die von allen Service Requests verwendet wird.

  
**Gibt Folgendes zurück**: Cloud
  
### <a name="setcloudendpointbaseurl-function"></a>Setcloudendpointbaseurl-Funktion
Legt die Basis-URL für den cloudendpunkt für die benutzerdefinierte Cloud fest

Parameter:  
* **cloudEndpointBaseUrl**: die Basis-URL, die von allen Service Requests verwendet wird (z.B. https://dataservice.protection.outlook.com)


Dieser Wert wird nur gelesen und muss für Cloud = Custom festgelegt werden.
  
### <a name="getcloudendpointbaseurl-function"></a>Getcloudendpointbaseurl-Funktion
Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.

  
**Rückgabe:** Basis-URL
  
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
Ruft den Bezeichnungs Filter ab.

  
**Gibt Folgendes zurück**: der Bezeichnungs Filter.
Bezeichnungen werden standardmäßig für den Bereich gefiltert. diese API ermöglicht das Filtern nach möglichen Aktionen.
  
### <a name="setvariabletextmarkingtype-function"></a>Setvariabletextmarkingtype-Funktion
Legt den Typ der Variablen Textmarkierung fest.

Parameter:  
* **variabletextmarkingtype**: der Typ der Variablen Textmarkierung.


  
### <a name="getvariabletextmarkingtype-function"></a>Getvariabletextmarkingtype-Funktion
Ruft den Typ der Variablen Textmarkierung ab.

  
**Gibt**folgenden Wert zurück: den Typ der Variablen Textmarkierung.
  
### <a name="setauthdelegate-function"></a>Setauthdelegatfunktion
Legen Sie den Autorisierungs Delegaten für die Engine fest.

Parameter:  
* **authdelegat**: der Authentifizierungs Delegat.


  
### <a name="getauthdelegate-function"></a>Getauthdelegatfunktion
Holen Sie sich den Authentifizierungs Delegaten für die Engine.

  
**Gibt Folgendes zurück**: der Engine auth-Delegat.