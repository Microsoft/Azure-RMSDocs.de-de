---
title: mip::PolicyEngine::Settings-Klasse
description: Dokumentiert die MIP::p olicyengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 620775649ee0fa593f141b1a4f983ad8b52caafe
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77487615"
---
# <a name="class-mippolicyenginesettings"></a>mip::PolicyEngine::Settings-Klasse 
Definiert die einem policyengine zugeordneten Einstellungen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: String & EngineID, Konst Std:: String & clientData, Konstante Std:: String & locale, bool loadsensitivitytypes)  |  Policyengine:: Settings-Konstruktor zum Laden eines vorhandenen Moduls.
öffentliche Einstellungen (Konstante Identität & Identität, Konst Std:: String & clientData, Konstante Std:: String & locale, bool loadsensitivitytypes)  |  Policyengine:: Settings-Konstruktor zum Erstellen einer neuen Engine.
public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Ruft das Identity-Objekt ab.
public void SetIdentity(const Identity& identity)  |  Legt das Identity-Objekt fest.
public const std::string& GetClientData() const  |  Ruft die in den Einstellungen festgelegten Clientdaten ab.
public void SetClientData(const std::string& clientData)  |  Legt die Zeichenfolge der Clientdaten fest.
public const std::string& GetLocale() const  |  Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& CustomSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () konstant.  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.
public bool isloadsensitivitytypesaktivierte () Konstante  |  Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.
public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt optional die Basis-URL für den Cloudendpunkt fest.
public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft ggf. die Basis-URL für die Cloud ab, die von allen Service Requests verwendet wird.
öffentliches void setdelegateduseremail (konstant Std:: String & delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String & getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
öffentliches void setlabelfilter (Konstanten Std:: Vector\<labelfiltertype\>& labelfilter)  |  Legt den Bezeichnungs Filter fest.
Public Konstanten Std:: Vector\<labelfiltertype\>& getlabelfilter () konstant.  |  Ruft den Bezeichnungs Filter ab.
öffentliches void setvariabletextmarkingtype (variabletextmarkingtype variabletextmarkingtype)  |  Legt den Typ der Variablen Textmarkierung fest.
Public variabletextmarkingtype getvariabletextmarkingtype () Konstanten  |  Ruft den Typ der Variablen Textmarkierung ab.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Policyengine:: Settings-Konstruktor zum Laden eines vorhandenen Moduls.

Parameter:  
* **engineId**: Legen Sie diese auf die eindeutige, von AddEngineAsync erstellte oder auf eine selbst erstellte Engine-ID fest. Verwenden Sie beim Laden einer vorhandenen Engine die ID, andernfalls wird eine neue Engine erstellt. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **Optional**: das Flag, das anzeigt, wann die Engine geladen wird, sollte auch benutzerdefinierte Empfindlichkeits Typen laden, wenn true onpolicychange Observer im Profil für Aktualisierungen von benutzerdefinierten Empfindlichkeits Typen und Richtlinien Änderungen aufgerufen wird. Wenn der Befehl "false listsensitivitytypes" aufruft, wird immer eine leere Liste zurückgegeben.


  
### <a name="settings-function"></a>Settings-Funktion
Policyengine:: Settings-Konstruktor zum Erstellen einer neuen Engine.

Parameter:  
* **identity**: Informationen zur Identität des Benutzers, der der neuen Engine zugeordnet ist. 


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
* **identity**: Die eindeutige Identität eines Benutzers. 


  
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="getclientdata-function"></a>Getclientdata-Funktion
Ruft die in den Einstellungen festgelegten Clientdaten ab.

  
**Rückgabe**: Vom Client angegebene Datenzeichenfolge.
  
### <a name="setclientdata-function"></a>Setclientdata-Funktion
Legt die Zeichenfolge der Clientdaten fest.

Parameter:  
* **clientData**: Vom Benutzer angegebene Daten.


  
### <a name="getlocale-function"></a>GetLocale-Funktion
Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.

  
**Rückgabe**: Das Gebietsschema.
  
### <a name="setcustomsettings-function"></a>Setcustomsettings-Funktion
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.

Parameter:  
* **customSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Rückgabe**: Liste von Name-Wert-Paaren
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.

Parameter:  
* **sessionId**: Eine eindeutige Zeichenfolge, die Telemetrieereignisse verbindet.


  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.

  
**Rückgabe**: die Sitzungs-ID.
  
### <a name="isloadsensitivitytypesenabled-function"></a>Isloadsensitivitytypesaktivierte Funktion
Das Flag zum angeben, ob die Bezeichnungen für die Last Sensitivität aktiviert sind.

  
**Gibt Folgendes zurück**: true, wenn aktiviert, andernfalls false.
  
### <a name="setcloudendpointbaseurl-function"></a>Setcloudendpointbaseurl-Funktion
Legt optional die Basis-URL für den Cloudendpunkt fest.

Parameter:  
* **cloudEndpointBaseUrl**: die Basis-URL, die von allen Service Requests verwendet wird (z.B. https://dataservice.protection.outlook.com)


  
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


Bezeichnungen werden standardmäßig für den Bereich gefiltert. diese API ermöglicht das Filtern nach möglichen Aktionen.
  
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