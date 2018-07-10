# <a name="class-mipprotectionprofilesettings"></a>mip::ProtectionProfile::Settings-Klasse 
[Einstellungen](class_mip_protectionprofile_settings.md), die während der Erstellung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, bool isLicenseCachingEnabled, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const std::shared_ptr<ProtectionProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor.
 public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.
 public bool GetUseInMemoryStorage() const  |  Ruft ab, ob Caches nur im Arbeitsspeicher (und nicht auch auf Datenträgern) gespeichert werden.
 public bool IsLicenseCachingEnabled() const  |  Ruft ab, ob das Zwischenspeichern von Lizenzen aktiviert ist.
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
public std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.
public const std::shared_ptr<ProtectionProfile::Observer>& GetObserver() const  |  Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören.
 public const ApplicationInfo& GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das SDK für den Schutz nutzt.
 public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
 public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Verwenden Sie die Implementierung der externen Protokollierung.
 public bool GetSkipTelemetryInit() const  |  Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden sollte.
 public void SetSkipTelemetryInit()  |  Deaktiviert die Initialisierung der Telemetrie.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest.
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor.

Parameter:  
* **path**: Dateipfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind 


* **useInMemoryStorage**: Speichert jeden zwischengespeicherten Status im Arbeitsspeicher und nicht auf dem Datenträger. 


* **isLicenseCachingEnabled**: Aktiviert bzw. deaktiviert das Zwischenspeichern von Schutz-SDK-Lizenzen. 


* **authDelegate**: von der Clientanwendung implementiertes Rückrufobjekt zur Authentifizierung 


* **observer**: Instanz von [Observer](class_mip_protectionprofile_observer.md), die Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören


* **applicationInfo**: Informationen zur Anwendung, die das SDK für den Schutz nutzt


  
### <a name="getpath"></a>GetPath
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.

  
**Rückgabe**: der Pfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Ruft ab, ob Caches nur im Arbeitsspeicher (und nicht auch auf Datenträgern) gespeichert werden.

  
**Rückgabe**: „TRUE“, wenn das Zwischenspeichern ausschließlich im Arbeitsspeicher erfolgt.
  
### <a name="islicensecachingenabled"></a>IsLicenseCachingEnabled
Ruft ab, ob das Zwischenspeichern von Lizenzen aktiviert ist.

  
**Rückgabe**: „TRUE“, wenn das Zwischenspeichern der Schutz-SDK-Lizenz aktiviert ist.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Rückgabe**: Authentifizierungsdelegat, der für die Beschaffung von Authentifizierungstoken verwendet wird
  
### <a name="consentdelegate"></a>ConsentDelegate
Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.

  
**Rückgabe**: Zustimmungsdelegat, der für die Verbindung mit Diensten verwendet wird
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören.

  
**Rückgabe**: [Beobachter](class_mip_protectionprofile_observer.md), der Benachrichtigungen von Ereignissen empfängt, die zu [ProtectionProfile](class_mip_protectionprofile.md) gehören
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft Informationen zu der Anwendung ab, die das SDK für den Schutz nutzt.

  
**Rückgabe**: Informationen zu der Anwendung, die das SDK für den Schutz nutzt
  
### <a name="optouttelemetry"></a>OptOutTelemetry
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Rückgabe**: Information, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht
  
### <a name="loggerdelegate"></a>LoggerDelegate
Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).

  
**Rückgabe**: Protokollierungsdelegat, der für die Protokollierung verwendet wird
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Verwenden Sie die Implementierung der externen Protokollierung.
Dies sollte durch Clientanwendungen aufgerufen werden, wenn ihre eigene Implementierung für die Protokollierung verwendet werden soll.
  
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