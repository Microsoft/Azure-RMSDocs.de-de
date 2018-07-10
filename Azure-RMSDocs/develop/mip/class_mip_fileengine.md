# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Eine Schnittstelle für alle Engine-Funktionen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public virtual ~FileEngine()  | _Noch nicht dokumentiert._
 public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  Eine Liste der Vertraulichkeitsbezeichnungen
public void CreateFileHandlerAsync(const std::string& inputFilePath, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver, const std::shared_ptr<void>& context)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.
public void CreateFileHandlerAsync(const std::shared_ptr<Stream>& inputStream, const std::string& inputFileName, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver, const std::shared_ptr<void>& context)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.
 protected FileEngine()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="fileengine"></a>~FileEngine
_Noch nicht dokumentiert._

  
### <a name="settings"></a>Einstellung
Gibt die Engine-Einstellungen zurück.
  
### <a name="label"></a>Label
Eine Liste der Vertraulichkeitsbezeichnungen
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.

Parameter:  
* **Die zu öffnende Datei**. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **Eine Klasse**, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.

Parameter:  
* **Ein Datenstrom**, der die Datei darstellt. 


* **Der Pfad zur Datei**. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **Eine Klasse**, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
### <a name="fileengine"></a>FileEngine
_Noch nicht dokumentiert._
