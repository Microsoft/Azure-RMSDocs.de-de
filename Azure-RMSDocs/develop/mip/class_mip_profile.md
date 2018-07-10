# <a name="class-mipprofile"></a>mip::Profile-Klasse 
Die [Profile](class_mip_profile.md)-Klasse ist die Stammklasse für die Verwendung von Microsoft Information Protection-Vorgängen. Eine typische Anwendung benötigt nur ein [Profil](class_mip_profile.md), kann bei Bedarf aber mehrere erstellen.
  
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

  
**Rückgabe**: Auf dem Profil festgelegte Einstellungen.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Startet den Vorgang zum Auflisten von Engines

Parameter:  
* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[Profile::Observer](class_mip_profile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu entladen.

Parameter:  
* **id**: Die eindeutige Engine-ID. 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[Profile::Observer](class_mip_profile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync"></a>AddEngineAsync
Beginnt damit, eine neue Richtlinien-Engine zu dem Profil hinzuzufügen.

Parameter:  
* **settings**: Das [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)-Objekt, das die Engine-Parameter angibt. 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[Profile::Observer](class_mip_profile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Beginnt damit, die Richtlinien-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden vollständig gelöscht.

Parameter:  
* **id**: Die eindeutige Engine-ID. 


* **context**: Ein Parameter, der an die Beobachterfunktionen weitergegeben wird. 


[Profile::Observer](class_mip_profile_observer.md) wird bei Erfolg oder Fehler aufgerufen.