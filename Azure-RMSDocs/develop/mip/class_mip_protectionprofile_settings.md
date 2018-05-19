# <a name="class-mipprotectionprofilesettings"></a>mip::ProtectionProfile::Settings-Klasse 
[Einstellungen](class_mip_protectionprofile_settings.md), die während der Erstellung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, const std::shared_ptr<ProtectionProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor.
 public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.
public const std::shared_ptr<ProtectionProfile::Observer>& GetObserver() const  |  Ruft den Observer ab, der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören.
 public const ApplicationInfo& GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das SDK für den Schutz nutzt.
 public bool GetSkipTelemetryInit() const  |  Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden sollte.
 public void SetSkipTelemetryInit()  |  Deaktiviert die Initialisierung der Telemetrie.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest.
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor.

Parameter:  
* **path**: Dateipfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind 


* **observer**: Instanz von [Observer](class_mip_protectionprofile_observer.md), die Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören


* **applicationInfo**: Informationen zur Anwendung, die das SDK für den Schutz nutzt


  
### <a name="getpath"></a>GetPath
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.

  
**Rückgabe**: der Pfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Ruft den Observer ab, der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören.

  
**Rückgabe**: [Beobachter](class_mip_protectionprofile_observer.md), der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft Informationen zu der Anwendung ab, die das SDK für den Schutz nutzt.

  
**Rückgabe**: Informationen zu der Anwendung, die das SDK für den Schutz nutzt
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden sollte.

  
**Rückgabe**: ob eine Initialisierung der Telemetrie übersprungen werden sollte
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Deaktiviert die Initialisierung der Telemetrie.
Diese Einstellung sollte normalerweise nicht von Clientanwendungen aufgerufen werden. Sie wird stattdessen von File SDK verwendet (das die Telemetrie bereits initialisiert hat), um eine doppelte Initialisierung zu verhindern.
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest.

Parameter:  
* **sessionId**: die Sitzungs-ID zum Korrelieren von Protokollen bzw. der Telemetrie


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab.

  
**Rückgabe**: Sitzungs-ID zum Korrelieren von Protokollen bzw. der Telemetrie