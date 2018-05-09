# <a name="class-mipprofile"></a>mip::Profile-Klasse 
Die [Profile](#classmip_1_1_profile)-Klasse ist die Stammklasse für die Verwendung von Microsoft Information Protection-Vorgängen. Eine typische Anwendung benötigt nur ein [Profil](#classmip_1_1_profile), kann bei Bedarf aber mehrere erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die auf dem Profil festgelegten Einstellungen ab.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  Startet den Vorgang zum Auflisten von Engines
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
public void AddEngineAsync(const PolicyEngine::Settings& settings, const std::shared_ptr<void>& context)  |  Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden vollständig gelöscht.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft die auf dem Profil festgelegten Einstellungen ab.
  
#### <a name="returns"></a>Rückgabe
Die auf dem Profil festgelegten Einstellungen.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Startet den Vorgang zum Auflisten von Engines
  
#### <a name="parameters"></a>Parameter
* context Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.
  
#### <a name="parameters"></a>Parameter
* id Die eindeutige Engine-ID. 
* context Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync"></a>AddEngineAsync
Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.
  
#### <a name="parameters"></a>Parameter
* settings Das [mip::PolicyEngine::Settings](#classmip_1_1_policy_engine_1_1_settings)-Objekt, das die Engine-Parameter angibt. 
* context Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden vollständig gelöscht.
  
#### <a name="parameters"></a>Parameter
* id Die eindeutige Engine-ID. 
* context Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.