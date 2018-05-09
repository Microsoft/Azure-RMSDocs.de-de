# <a name="class-mipprotectionprofilesettings"></a>mip::ProtectionProfile::Settings-Klasse 
[Einstellungen](#classmip_1_1_protection_profile_1_1_settings), die während der Erstellung und Lebensdauer von [ProtectionProfile](#classmip_1_1_protection_profile) verwendet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline Settings(const std::string& path, const std::shared_ptr<ProtectionProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  [ProtectionProfile::Settings](#classmip_1_1_protection_profile_1_1_settings)-Konstruktor.
public inline const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.
public inline const std::shared_ptr<ProtectionProfile::Observer>& GetObserver() const  |  Ruft den Observer ab, der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](#classmip_1_1_protection_profile) gehören.
public inline const ApplicationInfo& GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das SDK für den Schutz nutzt.
public inline bool GetSkipTelemetryInit() const  |  Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden sollte.
public inline void SetSkipTelemetryInit()  |  Deaktiviert die Initialisierung der Telemetrie.
public inline void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest.
public inline const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[ProtectionProfile::Settings](#classmip_1_1_protection_profile_1_1_settings)-Konstruktor.
  
#### <a name="parameters"></a>Parameter
* path Dateipfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind 
* observer: Instanz von [Observer](#classmip_1_1_protection_profile_1_1_observer), die Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](#classmip_1_1_protection_profile) gehören
* applicationInfo Informationen zur Anwendung, die das SDK für den Schutz nutzt
  
### <a name="getpath"></a>GetPath
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.
  
#### <a name="returns"></a>Rückgabe
Der Pfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Ruft den Observer ab, der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](#classmip_1_1_protection_profile) gehören.
  
#### <a name="returns"></a>Rückgabe
Ein [Beobachter](#classmip_1_1_protection_profile_1_1_observer), der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](#classmip_1_1_protection_profile) gehören
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft Informationen zu der Anwendung ab, die das SDK für den Schutz nutzt.
  
#### <a name="returns"></a>Rückgabe
Informationen zu der Anwendung, die das SDK für den Schutz nutzt
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden sollte.
  
#### <a name="returns"></a>Rückgabe
Angabe, ob eine Initialisierung der Telemetrie übersprungen werden sollte
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Deaktiviert die Initialisierung der Telemetrie.
Diese Einstellung sollte normalerweise nicht von Clientanwendungen aufgerufen werden. Sie wird stattdessen von File SDK verwendet (das die Telemetrie bereits initialisiert hat), um eine doppelte Initialisierung zu verhindern.
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest.
  
#### <a name="parameters"></a>Parameter
* sessionId Die Sitzungs-ID zum Korrelieren von Protokollen bzw. der Telemetrie
  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab.
  
#### <a name="returns"></a>Rückgabe
Die Sitzungs-ID zum Korrelieren von Protokollen bzw. der Telemetrie