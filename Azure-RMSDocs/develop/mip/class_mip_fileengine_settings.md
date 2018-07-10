# <a name="class-mipfileenginesettings"></a>mip::FileEngine::Settings-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  Erstellt eine Instanz mit den angegebenen Parametern.
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  Erstellt eine Instanz mit den angegebenen Parametern.
 public const std::string& GetEngineId() const  |  Gibt die Engine-ID zurück.
 public const Identity& GetIdentity() const  |  Gibt die Engine-Identität zurück.
 public void SetIdentity(const Identity& identity)  |  Legt die Engine-Identität fest.
 public const std::string& GetClientData() const  |  Gibt die Engine-Clientdaten zurück.
 public const std::string& GetLocale() const  |  Gibt das Engine-Gebietsschema zurück.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& value)  |  Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Engine-Sitzungs-ID fest.
 public const std::string& GetSessionId() const  |  Gibt die Engine-Sitzungs-ID zurück.
 public void SetProtectionCloudEndpointBaseUrl(const std::string& protectionCloudEndpointBaseUrl)  |  Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.
 public const std::string& GetProtectionCloudEndpointBaseUrl() const  |  Ruft „cloudEndpointBaseUrl“ ab.
 public void SetProtectionOnlyEngine(const bool protectionOnly)  |  Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
 public const bool IsProtectionOnlyEngine() const  |  Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Erstellt eine Instanz mit den angegebenen Parametern.
Verwenden Sie dies, um [Einstellungen](class_mip_fileengine_settings.md) zum Aufruf von LoadEngineAsync zu erstellen, um eine vorhandene Engine zu laden (zuvor über AddEngineAsync hinzugefügt).

Parameter:  
* **engineId**: Legen Sie diese auf die eindeutige Engine-ID fest, die von AddEngineAsync erzeugt wurde.


  
### <a name="settings"></a>Einstellung
Erstellt eine Instanz mit den angegebenen Parametern.
Verwenden Sie dies, um [Einstellungen](class_mip_fileengine_settings.md) zum Aufruf von AddEngineAsync zum Hinzufügen einer neuen Engine zu erstellen.

Parameter:  
* **identity**: Identitätsinformationen über den Benutzer, für den die Engine hinzugefügt werden muss.


  
### <a name="getengineid"></a>GetEngineId
Gibt die Engine-ID zurück.
  
### <a name="getidentity"></a>GetIdentity
Gibt die Engine-Identität zurück.
  
### <a name="setidentity"></a>SetIdentity
Legt die Engine-Identität fest.
  
### <a name="getclientdata"></a>GetClientData
Gibt die Engine-Clientdaten zurück.
  
### <a name="getlocale"></a>GetLocale
Gibt das Engine-Gebietsschema zurück.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Legt eine Liste von Name/Wert-Paaren fest, die für Tests und Versuche genutzt werden.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Ruft eine Liste von Name/Wert-Paaren ab, die für Tests und Versuche genutzt werden.
  
### <a name="setsessionid"></a>SetSessionId
Legt die Engine-Sitzungs-ID fest.
  
### <a name="getsessionid"></a>GetSessionId
Gibt die Engine-Sitzungs-ID zurück.
  
### <a name="setprotectioncloudendpointbaseurl"></a>SetProtectionCloudEndpointBaseUrl
Legt die Basis-URL des Endpunkts der Schutzcloud fest, durch die die Cloudgrenze festgelegt ist.

Parameter:  
* **protectionCloudEndpointBaseUrl**: mit Schutzendpunkten verknüpfte Basis-URL


  
### <a name="getprotectioncloudendpointbaseurl"></a>GetProtectionCloudEndpointBaseUrl
Ruft „cloudEndpointBaseUrl“ ab.

  
**Rückgabe**: mit Schutzendpunkten verknüpfte Basis-URL
  
### <a name="setprotectiononlyengine"></a>SetProtectionOnlyEngine
Legt nur den Engine-Indikator für den Schutz fest – keine Richtlinie/Bezeichnung.
  
### <a name="isprotectiononlyengine"></a>IsProtectionOnlyEngine
Gibt nur den Engine-Indikator für den Schutz zurück – keine Richtlinie/Bezeichnung.