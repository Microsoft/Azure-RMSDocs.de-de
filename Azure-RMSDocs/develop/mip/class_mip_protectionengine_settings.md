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
 public const std::string& GetLocale() const  |  Ruft das Gebietsschema ab, in dem die Engine-Daten geschrieben werden.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& value)  |  Legt Name-Wert-Paare fest, die für Tests und Versuche genutzt werden.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  Ruft Name-Wert-Paare ab, die für Tests und Versuche genutzt werden.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Engine-Sitzungs-ID fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.
 public const std::string& GetSessionId() const  |  Ruft die Engine-Sitzungs-ID ab.
 public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Legt die Basis-URL des Cloudendpunkts fest, durch die die Cloudgrenze festgelegt ist.
 public const std::string& GetCloudEndpointBaseUrl() const  |  Ruft „cloudEndpointBaseUrl“ ab.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor für die Erstellung einer neuen Engine

Parameter:  
* **identity**: Identität, die [ProtectionEngine](class_mip_protectionengine.md) zugeordnet wird


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt. Die Standardeinstellung ist „en-US“.


  
### <a name="settings"></a>Einstellung
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: eindeutiger Bezeichner der Engine, der geladen wird 


* **clientData**: anpassbare Clientdaten, die beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden können 


* **locale**: Die Engine-Ausgabe wird in diesem Gebietsschema bereitgestellt. Die Standardeinstellung ist „en-US“.


  
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
Legt die Engine-Sitzungs-ID fest, die für die Korrelation von Protokollierung/Telemetrie verwendet wird.

Parameter:  
* **sessionId**: Engine-Sitzungs-ID, die für die Korrelation von Protokollierung/Telemetrie verwendet wird


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Engine-Sitzungs-ID ab.

  
**Rückgabe**: Engine-Sitzungs-ID
  
### <a name="setcloudendpointbaseurl"></a>SetCloudEndpointBaseUrl
Legt die Basis-URL des Cloudendpunkts fest, durch die die Cloudgrenze festgelegt ist.

Parameter:  
* **cloudEndpointBaseUrl**: mit Schutzendpunkten verknüpfte Basis-URL


  
### <a name="getcloudendpointbaseurl"></a>GetCloudEndpointBaseUrl
Ruft „cloudEndpointBaseUrl“ ab.

  
**Rückgabe**: mit Schutzendpunkten verknüpfte Basis-URL