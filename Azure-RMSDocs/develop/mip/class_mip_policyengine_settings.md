# <a name="class-mippolicyenginesettings"></a>mip::PolicyEngine::Settings-Klasse 
Eine Instanz dieser Klasse mit den passenden Parametern sollte bereitgestellt werden, um eine Engine zu initiieren.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  Konstruieren Sie eine Instanz mit den angegebenen Parametern. Verwenden Sie dies, um [Einstellungen](class_mip_policyengine_settings.md) zum Aufruf von LoadEngineAsync zum Laden einer bereits vorhandenen Engine zu erstellen.
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  Verwenden Sie dies, um [Einstellungen](class_mip_policyengine_settings.md) zum Aufruf von AddEngineAsync zum Hinzufügen einer neuen Engine zu erstellen.
 public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
 public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
 public const Identity& GetIdentity() const  |  Ruft das Identity-Objekt ab.
 public void SetIdentity(const Identity& identity)  |  Legt das Identity-Objekt fest.
 public const std::string& GetClientData() const  |  Ruft die in den Einstellungen festgelegten Clientdaten ab.
 public void SetClientData(const std::string& clientData)  |  Legt die Zeichenfolge der Clientdaten fest.
 public const std::string& GetLocale() const  |  Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& customSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest, wird für clientdefinierte Telemetrie verwendet.
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Konstruieren Sie eine Instanz mit den angegebenen Parametern. Verwenden Sie dies, um [Einstellungen](class_mip_policyengine_settings.md) zum Aufruf von LoadEngineAsync zum Laden einer bereits vorhandenen Engine zu erstellen.

Parameter:  
* **engineId**: Stellen Sie diese auf die eindeutige, von AddEngineAsync erstellte oder auf eine selbst erstellte Engine-ID ein. Verwenden Sie beim Laden einer vorhandenen Engine die ID, andernfalls wird eine neue Engine erstellt. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert werden, und sie können aus einer geladenen Engine abgerufen werden. 


* **locale**: von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. Die Standardeinstellung ist „en-US“.


  
### <a name="settings"></a>Einstellung
Verwenden Sie dies, um [Einstellungen](class_mip_policyengine_settings.md) zum Aufruf von AddEngineAsync zum Hinzufügen einer neuen Engine zu erstellen.

Parameter:  
* **identity**: Eindeutiger Bezeichner für den Benutzer, für den die Engine hinzugefügt werden muss. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert werden, und sie können aus einer geladenen Engine abgerufen werden. 


* **locale**: von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. Die Standardeinstellung ist „en-US“.


  
### <a name="getengineid"></a>GetEngineId
Ruft die Engine-ID ab.

  
**Rückgabe**: Eindeutige Zeichenfolge, die die Engine identifiziert.
  
### <a name="setengineid"></a>SetEngineId
Legt die Engine-ID fest.

Parameter:  
* **id**: Engine-ID.


  
### <a name="getidentity"></a>GetIdentity
Ruft das Identity-Objekt ab.

  
**Rückgabe**: Verweis auf die Identität im Einstellungsobjekt. 
  
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Legt das Identity-Objekt fest.

Parameter:  
* **identity**: Die eindeutige Identität eines Benutzers. 


  
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Ruft die in den Einstellungen festgelegten Clientdaten ab.

  
**Rückgabe**: Vom Client angegebene Datenzeichenfolge.
  
### <a name="setclientdata"></a>SetClientData
Legt die Zeichenfolge der Clientdaten fest.

Parameter:  
* **clientData**: Vom Benutzer angegebene Daten.


  
### <a name="getlocale"></a>GetLocale
Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.

  
**Rückgabe**: Das Gebietsschema.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.

Parameter:  
* **customSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings"></a>GetCustomSettings
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Rückgabe**: Liste von Name-Wert-Paaren
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest, wird für clientdefinierte Telemetrie verwendet.

Parameter:  
* **sessionId**: Eine eindeutige Zeichenfolge, die Telemetrieereignisse verbindet.


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.

  
**Rückgabe**: Die Sitzungs-ID.