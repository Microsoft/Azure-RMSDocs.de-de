# <a name="class-mippolicyenginesettings"></a>mip::PolicyEngine::Settings-Klasse 
Eine Instanz dieser Klasse mit den passenden Parametern sollte bereitgestellt werden, um eine Engine zu initiieren.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
`public inline Settings(const std::string& id, const std::string& clientData, const std::string& locale)`  |  Konstruieren Sie eine Instanz mit den angegebenen Parametern. Verwenden Sie dies, um [Einstellungen](#classmip_1_1_policy_engine_1_1_settings) zum Aufruf von LoadEngineAsync zum Laden einer bereits vorhandenen Engine zu erstellen.
`public inline Settings(const Identity& identity, const std::string& clientData, const std::string& locale)`  |  Verwenden Sie dies, um [Einstellungen](#classmip_1_1_policy_engine_1_1_settings) zum Aufruf von AddEngineAsync zum Hinzufügen einer neuen Engine zu erstellen.
`public inline const std::string& GetId() const`  |  Ruft die Engine-ID ab.
`public inline void SetId(const std::string& id)`  |  Legt die Engine-ID fest.
`public inline const Identity& GetIdentity() const`  |  Ruft das Identity-Objekt ab.
`public inline void SetIdentity(const Identity& identity)`  |  Legt das Identity-Objekt fest.
`public inline const std::string& GetClientData() const`  |  Ruft die in den Einstellungen festgelegten Clientdaten ab.
`public inline void SetClientData(const std::string& clientData)`  |  Legt die Zeichenfolge der Clientdaten fest.
`public inline const std::string& GetLocale() const`  |  Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.
`public inline void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& customSettings)`  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
`public inline const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const`  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
`public inline void SetSessionId(const std::string& sessionId)`  |  Legt die Sitzungs-ID fest, wird für clientdefinierte Telemetrie verwendet.
`public inline const std::string& GetSessionId() const`  |  Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Konstruieren Sie eine Instanz mit den angegebenen Parametern. Verwenden Sie dies, um [Einstellungen](#classmip_1_1_policy_engine_1_1_settings) zum Aufruf von LoadEngineAsync zum Laden einer bereits vorhandenen Engine zu erstellen.
  
#### <a name="parameters"></a>Parameter
* id Stellen Sie diese auf die eindeutige, von AddEngineAsync erstellte oder auf eine selbst erstellte Engine-ID ein. Verwenden Sie beim Laden einer vorhandenen Engine die ID, andernfalls wird eine neue Engine erstellt. 
* clientData Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert werden, und sie können aus einer geladenen Engine abgerufen werden. 
* locale engine Lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt, die Standardeinstellung ist „en-US“.
  
### <a name="settings"></a>Einstellung
Verwenden Sie dies, um [Einstellungen](#classmip_1_1_policy_engine_1_1_settings) zum Aufruf von AddEngineAsync zum Hinzufügen einer neuen Engine zu erstellen.
  
#### <a name="parameters"></a>Parameter
* identity Eindeutiger Bezeichner für den Benutzer, für den die Engine hinzugefügt werden muss. 
* clientData Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert werden, und sie können aus einer geladenen Engine abgerufen werden. 
* locale engine Lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt, die Standardeinstellung ist `en-US`.
  
### <a name="getid"></a>GetId
Ruft die Engine-ID ab.
  
#### <a name="returns"></a>Rückgabe
Eindeutige Zeichenfolge, die die Engine identifiziert
  
### <a name="setid"></a>SetId
Legt die Engine-ID fest.
  
#### <a name="parameters"></a>Parameter
* id Engine-ID.
  
### <a name="getidentity"></a>GetIdentity
Ruft das Identity-Objekt ab.
  
#### <a name="returns"></a>Rückgabe
Verweis auf die Identität im Einstellungsobjekt. 
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Legt das Identity-Objekt fest.
  
#### <a name="parameters"></a>Parameter
* identity Die eindeutige Identität eines Benutzers. 
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Ruft die in den Einstellungen festgelegten Clientdaten ab.
  
#### <a name="returns"></a>Rückgabe
Vom Client angegebene Zeichenfolge.
  
### <a name="setclientdata"></a>SetClientData
Legt die Zeichenfolge der Clientdaten fest.
  
#### <a name="parameters"></a>Parameter
* clientData Vom Benutzer angegebene Daten.
  
### <a name="getlocale"></a>GetLocale
Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.
  
#### <a name="returns"></a>Rückgabe
Gebietsschema
  
### <a name="setcustomsettings"></a>SetCustomSettings
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
  
#### <a name="parameters"></a>Parameter
* customSettings Liste von Name-Wert-Paaren.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
  
#### <a name="parameters"></a>Parameter
* Liste von Name-Wert-Paaren.
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest, wird für clientdefinierte Telemetrie verwendet.
  
#### <a name="parameters"></a>Parameter
* sessionId Eine eindeutige Zeichenfolge, die Telemetrieereignisse verbindet.
  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.
  
#### <a name="returns"></a>Rückgabe
der Sitzungs-ID