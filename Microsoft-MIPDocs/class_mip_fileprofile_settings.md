# <a name="class-mipfileprofilesettings"></a>mip::FileProfile::Settings-Klasse 
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline  SettingsObserver > observer,const ApplicationInfo & applicationInfo) | Schnittstelle zur Konfiguration des Profils
public inline  ~Settings | 
public inline const std::string & GetPath | 
public inline bool GetUseInMemoryStorage | 
public inline std::shared_ptr< AuthDelegate > GetAuthDelegate | 
public inline std::shared_ptr< Observer > GetObserver | 
public inline const ApplicationInfo GetApplicationInfo | 
public inline bool GetSkipTelemetryInit | 
public inline void SetSkipTelemetryInit | 
public inline void SetSessionId | Legt die Profilsitzungs-ID fest
public inline const std::string & GetSessionId | Gibt die Profilsitzungs-ID zurück
## <a name="members"></a>Member
### <a name="settings"></a>Einstellung
Schnittstelle zur Konfiguration des Profils
#### <a name="parameters"></a>Parameter
* observer: Klasse, die die Schnittstelle [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) implementiert Der Wert kann nullptr sein.
### <a name="settings"></a>~Settings
### <a name="getpath"></a>GetPath
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
### <a name="getauthdelegate"></a>GetAuthDelegate
### <a name="observer"></a>Beobachter
### <a name="applicationinfo"></a>ApplicationInfo
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
### <a name="setsessionid"></a>SetSessionId
Legt die Profilsitzungs-ID fest
### <a name="getsessionid"></a>GetSessionId
Gibt die Profilsitzungs-ID zurück