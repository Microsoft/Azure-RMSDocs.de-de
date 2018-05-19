# <a name="class-mipfileprofilesettings"></a>mip::FileProfile::Settings-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, std::shared_ptr<AuthDelegate> authDelegate, std::shared_ptr<Observer> observer, const ApplicationInfo& applicationInfo)  |  Eine Schnittstelle für die Konfiguration des Profils
 public ~Settings()  | _Noch nicht dokumentiert._
 public const std::string& GetPath() const  | _Noch nicht dokumentiert._
 public bool GetUseInMemoryStorage() const  | _Noch nicht dokumentiert._
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  | _Noch nicht dokumentiert._
public std::shared_ptr<Observer> GetObserver() const  | _Noch nicht dokumentiert._
 public const ApplicationInfo GetApplicationInfo() const  | _Noch nicht dokumentiert._
 public bool GetSkipTelemetryInit() const  | _Noch nicht dokumentiert._
 public void SetSkipTelemetryInit()  | _Noch nicht dokumentiert._
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID des Profils fest
 public const std::string& GetSessionId() const  |  Gibt die Sitzungs-ID des Profils zurück
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **observer**: Eine Klasse, die die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. Kann „nullptr“ lauten.


  
### <a name="settings"></a>~Settings
_Noch nicht dokumentiert._

  
### <a name="getpath"></a>GetPath
_Noch nicht dokumentiert._

  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
_Noch nicht dokumentiert._

  
### <a name="getauthdelegate"></a>GetAuthDelegate
_Noch nicht dokumentiert._

  
### <a name="observer"></a>Beobachter
_Noch nicht dokumentiert._

  
### <a name="applicationinfo"></a>ApplicationInfo
_Noch nicht dokumentiert._

  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
_Noch nicht dokumentiert._

  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
_Noch nicht dokumentiert._

  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID des Profils fest
  
### <a name="getsessionid"></a>GetSessionId
Gibt die Sitzungs-ID des Profils zurück