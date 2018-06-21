# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Eine Schnittstelle für alle Engine-Funktionen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public virtual ~FileEngine()  | _Noch nicht dokumentiert._
 public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  Eine Liste der Vertraulichkeitsbezeichnungen
public std::shared_ptr<FileHandler> CreateFileHandler(const std::string& inputFilePath, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver)  |  Gibt den Dateihandle für den angegebenen Dateipfad zurück
public std::shared_ptr<FileHandler> CreateFileHandler(const std::shared_ptr<Stream>& inputStream, const std::string& inputFileName, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver)  |  Gibt den Dateihandle für den angegebenen Dateidatenstrom zurück
 protected FileEngine()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="fileengine"></a>~FileEngine
_Noch nicht dokumentiert._

  
### <a name="settings"></a>Einstellung
Gibt die Engine-Einstellungen zurück.
  
### <a name="label"></a>Label
Eine Liste der Vertraulichkeitsbezeichnungen
  
### <a name="filehandler"></a>FileHandler
Gibt den Dateihandle für den angegebenen Dateipfad zurück

Parameter:  
* **Die zu öffnende Datei**. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **Eine Klasse**, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert.


  
### <a name="filehandler"></a>FileHandler
Gibt den Dateihandle für den angegebenen Dateidatenstrom zurück

Parameter:  
* **Ein Datenstrom**, der die Datei darstellt. 


* **Der Pfad zur Datei**. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **Eine Klasse**, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert.


  
### <a name="fileengine"></a>FileEngine
_Noch nicht dokumentiert._
