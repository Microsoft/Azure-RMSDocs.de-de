# <a name="class-mipfileprofilesettings"></a>mip::FileProfile::Settings-Klasse 
[Einstellungen](class_mip_fileprofile_settings.md), die während der Erstellung und Lebensdauer von [FileProfile](class_mip_fileprofile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, bool isLicenseCachingEnabled, std::shared_ptr<AuthDelegate> authDelegate, std::shared_ptr<ConsentDelegate> consentDelegate, std::shared_ptr<Observer> observer, const ApplicationInfo& applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor
 public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.
 public bool GetUseInMemoryStorage() const  |  Ruft ab, ob alle Status im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen.
 public bool IsLicenseCachingEnabled() const  |  Ruft ab, ob das Zwischenspeichern von Lizenzen aktiviert ist.
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
public std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.
public std::shared_ptr<Observer> GetObserver() const  |  Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.
 public const ApplicationInfo GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das SDK nutzt.
 public bool GetSkipTelemetryInit() const  |  Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden sollte.
 public void SetSkipTelemetryInit()  |  Deaktiviert die Initialisierung der Telemetrie.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Verwenden Sie die Implementierung der externen Protokollierung.
 public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
 public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest.
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor

Parameter:  
* **path**: Pfad, in dem Protokollierung, Telemetrie und weitere persistente Status zum Schutz gespeichert sind 


* **useInMemoryStorage**: Information, ob alle Status im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen 


* **isLicenseCachingEnabled**: Aktiviert bzw. deaktiviert das Zwischenspeichern von Schutzlizenzen. 


* **authDelegate**: Authentifizierungsdelegat für die Beschaffung von Authentifizierungstoken 


* **observer**: [Beobachterinstanz](class_mip_fileprofile_observer.md), die Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören


* **applicationInfo**: Informationen zur Anwendung, die das SDK nutzt


  
### <a name="getpath"></a>GetPath
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.

  
**Rückgabe**: Pfad zum Speicherort für Protokollierung, Telemetrie und weitere persistente Status
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Ruft ab, ob alle Status im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen.

  
**Rückgabe**: Information, ob alle Status im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen
  
### <a name="islicensecachingenabled"></a>IsLicenseCachingEnabled
Ruft ab, ob das Zwischenspeichern von Lizenzen aktiviert ist.

  
**Rückgabe**: „TRUE“, wenn das Zwischenspeichern ausschließlich im Arbeitsspeicher erfolgt.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Rückgabe**: Authentifizierungsdelegat, der für die Beschaffung von Authentifizierungstoken verwendet wird
  
### <a name="consentdelegate"></a>ConsentDelegate
Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.

  
**Rückgabe**: Zustimmungsdelegat für die Anforderung der Zustimmung eines Benutzers
  
### <a name="observer"></a>Beobachter
Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.

  
**Rückgabe**: [Beobachter](class_mip_fileprofile_observer.md), der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft Informationen zu der Anwendung ab, die das SDK nutzt.

  
**Rückgabe**: Informationen zur Anwendung, die das SDK nutzt
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden sollte.

  
**Rückgabe**: ob eine Initialisierung der Telemetrie übersprungen werden sollte
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Deaktiviert die Initialisierung der Telemetrie.
Diese Einstellung sollte normalerweise nicht von Clientanwendungen aufgerufen werden. Sie wird stattdessen von File SDK verwendet (das die Telemetrie bereits initialisiert hat), um eine doppelte Initialisierung zu verhindern.
  
### <a name="loggerdelegate"></a>LoggerDelegate
Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).

  
**Rückgabe**: Protokollierungsdelegat, der für die Protokollierung verwendet wird
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Verwenden Sie die Implementierung der externen Protokollierung.
Dies sollte durch Clientanwendungen aufgerufen werden, wenn ihre eigene Implementierung für die Protokollierung verwendet werden soll.
  
### <a name="optouttelemetry"></a>OptOutTelemetry
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Rückgabe**: Information, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest.

Parameter:  
* **sessionId**: die Sitzungs-ID zum Korrelieren von Protokollen bzw. der Telemetrie


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab.

  
**Rückgabe**: Sitzungs-ID zum Korrelieren von Protokollen bzw. der Telemetrie