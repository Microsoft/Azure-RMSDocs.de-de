# <a name="class-mipfileprofile"></a>mip::FileProfile-Klasse 
Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
Eine typische Anwendung benötigt nur ein [Profil](class_mip_profile.md), kann bei Bedarf aber mehrere erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Gibt die Profileinstellungen zurück
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  Startet den Vorgang zum Auflisten von Engines
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen.
public void AddEngineAsync(const FileEngine::Settings& settings, const std::shared_ptr<void>& context)  |  Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden vollständig gelöscht.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Gibt die Profileinstellungen zurück
  
### <a name="listenginesasync"></a>ListEnginesAsync
Startet den Vorgang zum Auflisten von Engines
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Beginnt damit, die Datei-Engine mit der angegebenen ID zu entladen. [FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="addengineasync"></a>AddEngineAsync
Beginnt damit, eine neue Datei-Engine zu dem Profil hinzuzufügen.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Beginnt damit, die Datei-Engine mit der angegebenen ID zu löschen. Alle Daten für das angegebene Profil werden vollständig gelöscht.
[FileProfile::Observer](class_mip_fileprofile_observer.md) wird bei Erfolg oder Fehler aufgerufen.