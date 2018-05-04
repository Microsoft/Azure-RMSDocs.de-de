# <a name="class-mipfileprofilesettings"></a>mip::FileProfile::Settings-Klasse 
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline  SettingsObserver > observer,const ApplicationInfo & applicationInfo) | Eine Schnittstelle für die Konfiguration des Profils
public inline  ~Settings | 
public inline const std::string & GetPath | 
public inline bool GetUseInMemoryStorage | 
public inline std::shared_ptr< AuthDelegate > GetAuthDelegate | 
public inline std::shared_ptr< Observer > GetObserver | 
public inline const ApplicationInfo GetApplicationInfo | 
public inline bool GetSkipTelemetryInit | 
public inline void SetSkipTelemetryInit | 
public inline void SetSessionId | Legt die Sitzungs-ID des Profils fest
public inline const std::string & GetSessionId | Gibt die Sitzungs-ID des Profils zurück
## <a name="members"></a>Member
### <a name="settings"></a>Einstellung
Eine Schnittstelle für die Konfiguration des Profils
#### <a name="parameters"></a>Parameter
* observer: Eine Klasse, die die [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer)-Schnittstelle implementiert. Kann „nullptr“ lauten.
### <a name="settings"></a>~Settings
### <a name="getpath"></a>GetPath
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
### <a name="getauthdelegate"></a>GetAuthDelegate
### <a name="observer"></a>Beobachter
### <a name="applicationinfo"></a>ApplicationInfo
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID des Profils fest
### <a name="getsessionid"></a>GetSessionId
Gibt die Sitzungs-ID des Profils zurück