# <a name="class-mipprofilesettings"></a>mip::Profile::Settings-Klasse 
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline  SettingsProfile::Observer > & observer,const ApplicationInfo & applicationInfo) | Eine Schnittstelle für die Konfiguration des Profils
public inline const std::string & GetPath | Ruft den Pfad zum gespeicherten Status ab.
public inline bool GetUseInMemoryStorage | Ruft das Flag „Arbeitsspeicher verwenden“ ab.
public inline const std::shared_ptr< AuthDelegate > & GetAuthDelegate | Ruft den Authentifizierungsdelegaten ab.
public inline const std::shared_ptr< Profile::Observer > & GetObserver | Ruft den Ereignisbeobachter ab.
public inline const ApplicationInfo GetApplicationInfo | Ruft die Anwendungsinformationen ab.
## <a name="members"></a>Member
### <a name="settings"></a>Einstellung
Eine Schnittstelle für die Konfiguration des Profils
#### <a name="parameters"></a>Parameter
* path Der Pfad zu einem Verzeichnis, in dem das SDK den Profilstatus speichert. 
* useInMemoryStorage Ein Flag, das angibt, ob der Status auf dem Datenträger gespeichert werden soll. 
* authDelegate Der Authentifizierungsdelegat, der vom SDK zum Abrufen von Authentifizierungstoken verwendet wird. 
* observer Eine Klasse, die die Schnittstelle [Profile::Observer](#classmip_1_1_profile_1_1_observer) implementiert. Kann „nullptr“ lauten. 
* applicationInfo Der Anwendungsbezeichner für den Dienstzugriff.
### <a name="getpath"></a>GetPath
Ruft den Pfad zum gespeicherten Status ab.
#### <a name="returns"></a>Rückgabe
Der Pfad zum gespeicherten Status.
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Ruft das Flag „Arbeitsspeicher verwenden“ ab.
#### <a name="returns"></a>Rückgabe
TRUE, wenn die interne Speicherverwendung festgelegt ist; andernfalls wird FALSE zurückgegeben.
### <a name="getauthdelegate"></a>GetAuthDelegate
Ruft den Authentifizierungsdelegaten ab.
#### <a name="returns"></a>Rückgabe
Der Authentifizierungsdelegat.
### <a name="profileobserver"></a>Profile::Observer
Ruft den Ereignisbeobachter ab.
#### <a name="returns"></a>Rückgabe
Der Ereignisbeobachter.
### <a name="applicationinfo"></a>ApplicationInfo
Ruft die Anwendungsinformationen ab.
#### <a name="returns"></a>Rückgabe
Die Anwendungsinformationen.