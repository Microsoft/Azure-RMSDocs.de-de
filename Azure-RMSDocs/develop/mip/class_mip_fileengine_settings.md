# <a name="class-mipfileenginesettings"></a>mip::FileEngine::Settings-Klasse 
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline  Settings | Erstellt eine Instanz mit den angegebenen Parametern.
public inline  Settings | Erstellt eine Instanz mit den angegebenen Parametern.
public inline const std::string & GetId | Gibt die Engine-ID zurück.
public inline const Identity & GetIdentity | Gibt die Engine-Identität zurück.
public inline void SetIdentity | Legt die Engine-Identität fest.
public inline const std::string & GetClientData | Gibt die Engine-Clientdaten zurück.
public inline const std::string & GetLocale | Gibt das Engine-Gebietsschema zurück.
public inline void SetCustomSettings | Legt eine Liste von Name-Wert-Paaren fest, die für Tests und Versuche genutzt werden.
public inline const std::vector< std::pair< std::string, std::string > > & GetCustomSettings | Ruft eine Liste von Name-Wert-Paaren ab, die für Tests und Versuche genutzt werden.
public inline void SetSessionId | Legt die Engine-Sitzungs-ID fest.
public inline const std::string & GetSessionId | Gibt die Engine-Sitzungs-ID zurück.
## <a name="members"></a>Member
### <a name="settings"></a>Einstellung
Erstellt eine Instanz mit den angegebenen Parametern.
Verwenden Sie dies, um [Einstellungen](#classmip_1_1_file_engine_1_1_settings) zum Aufruf von LoadEngineAsync zu erstellen, um eine vorhandene Engine zu laden (zuvor über AddEngineAsync hinzugefügt).
#### <a name="parameters"></a>Parameter
* id Stellen Sie diese auf die eindeutige Engine-ID ein, die von AddEngineAsync erzeugt wurde.
### <a name="settings"></a>Einstellung
Erstellt eine Instanz mit den angegebenen Parametern.
Verwenden Sie diese Instanz, um [Einstellungen](#classmip_1_1_file_engine_1_1_settings) zu erstellen, über die Sie AddEngineAsync aufrufen können, um eine neue Engine hinzuzufügen.
#### <a name="parameters"></a>Parameter
* identity Identitätsinformationen über den Benutzer, für den die Engine hinzugefügt werden muss.
### <a name="getid"></a>GetId
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
Legt eine Liste von Name-Wert-Paaren fest, die für Tests und Versuche genutzt werden.
### <a name="getcustomsettings"></a>GetCustomSettings
Ruft eine Liste von Name-Wert-Paaren ab, die für Tests und Versuche genutzt werden.
### <a name="setsessionid"></a>SetSessionId
Legt die Engine-Sitzungs-ID fest.
### <a name="getsessionid"></a>GetSessionId
Gibt die Engine-Sitzungs-ID zurück.