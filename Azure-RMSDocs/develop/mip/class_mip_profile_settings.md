# <a name="class-mipprofilesettings"></a>mip::Profile::Settings-Klasse 
[Einstellungen](class_mip_profile_settings.md), die während der Erstellung und Lebensdauer von [Profile](class_mip_profile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<Profile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  Eine Schnittstelle für die Konfiguration des Profils
 public const std::string& GetPath() const  |  Ruft den Pfad zum gespeicherten Status ab.
 public bool GetUseInMemoryStorage() const  |  Ruft das Flag „Arbeitsspeicher verwenden“ ab.
public const std::shared_ptr<AuthDelegate>& GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab.
public const std::shared_ptr<Profile::Observer>& GetObserver() const  |  Ruft den Ereignisbeobachter ab.
 public const ApplicationInfo GetApplicationInfo() const  |  Ruft die Anwendungsinformationen ab.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Verwenden Sie die Implementierung der externen Protokollierung.
 public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
 public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **path**: Pfad zu einem Verzeichnis, in dem das SDK den Profilstatus speichert. 


* **useInMemoryStorage**: Flag, das angibt, ob der Status auf dem Datenträger gespeichert werden soll. 


* **authDelegate**: Authentifizierungsdelegat, der vom SDK zum Abrufen von Authentifizierungstoken verwendet wird 


* **observer**: Klasse, die die Schnittstelle [Profile::Observer](class_mip_profile_observer.md) implementiert. Kann „nullptr“ lauten. 


* **applicationInfo**: Anwendungsbezeichner für den Dienstzugriff.


  
### <a name="getpath"></a>GetPath
Ruft den Pfad zum gespeicherten Status ab.

  
**Rückgabe**: Pfad zum gespeicherten Status.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Ruft das Flag „Arbeitsspeicher verwenden“ ab.

  
**Rückgabe**: TRUE, wenn In-Memory-Speicher-Verwendung festgelegt ist; andernfalls wird FALSE zurückgegeben.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Ruft den Authentifizierungsdelegaten ab.

  
**Rückgabe**: Authentifizierungsdelegat.
  
### <a name="profileobserver"></a>Profile::Observer
Ruft den Ereignisbeobachter ab.

  
**Rückgabe**: Ereignisbeobachter.
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft die Anwendungsinformationen ab.

  
**Rückgabe**: die Anwendungsinformationen.
  
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