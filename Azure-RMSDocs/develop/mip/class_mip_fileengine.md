# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Eine Schnittstelle für alle Engine-Funktionen
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline virtual  ~FileEngine | 
public const Settings & GetSettings | Gibt die Engine-Einstellungen zurück
public const std::vector< std::shared_ptr< Label > > & ListSensitivityLabels | Eine Liste der Vertraulichkeitsbezeichnungen
public std::shared_ptr< FileHandler > CreateFileHandlerFileHandler::Observer > & fileHandlerObserver) | Gibt den Dateihandle für den angegebenen Dateipfad zurück
public std::shared_ptr< FileHandler > CreateFileHandlerStream > & inputStream,const std::string & inputFileName,const std::shared_ptr< FileHandler::Observer > & fileHandlerObserver) | Gibt den Dateihandle für den angegebenen Dateidatenstrom zurück
protected inline  FileEngine | 
## <a name="members"></a>Member
### <a name="fileengine"></a>~FileEngine
### <a name="settings"></a>Einstellung
Gibt die Engine-Einstellungen zurück
### <a name="label"></a>Label
Eine Liste der Vertraulichkeitsbezeichnungen
### <a name="filehandler"></a>FileHandler
Gibt den Dateihandle für den angegebenen Dateipfad zurück
#### <a name="parameters"></a>Parameter
* Die zu öffnende Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 
* Eine Klasse, welche die [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer)-Schnittstelle implementiert.
### <a name="filehandler"></a>FileHandler
Gibt den Dateihandle für den angegebenen Dateidatenstrom zurück
#### <a name="parameters"></a>Parameter
* Ein Datenstrom, der die Datei darstellt. 
* Der Pfad zur Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 
* Eine Klasse, welche die [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer)-Schnittstelle implementiert.
### <a name="fileengine"></a>FileEngine