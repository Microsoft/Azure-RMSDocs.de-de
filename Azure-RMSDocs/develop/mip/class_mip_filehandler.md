# <a name="class-mipfilehandler"></a>mip::FileHandler-Klasse 
Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public void GetLabelAsync | Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
public void GetProtectionAsync | Startet das Abrufen der Schutzrichtlinie der Datei.
public void SetLabelLabelingOptions & labelingOptions) | Legt die Vertraulichkeitsbezeichnung für die Datei fest.
public void DeleteLabel | Löscht die Vertraulichkeitsbezeichnung aus der Datei.
public void SetCustomPermissionsPolicyDescriptor > & policyDescriptor) | Legt benutzerdefinierte Berechtigungen für die Datei fest.
public void RemoveProtection | Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
public void CommitAsync | Schreibt die Änderungen in die Datei, die durch den Parameter \|outputFilePath\| angegeben wird.
public void CommitAsyncStream > & outputStream,const std::shared_ptr< void > & context) | Schreibt die Änderungen in den Datenstrom, der durch den Parameter \|outputStream\| angegeben wird.
public std::string GetOutputFileName | Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
public inline virtual  ~FileHandler | 
protected inline  FileHandler | 
## <a name="members"></a>Member
### <a name="getlabelasync"></a>GetLabelAsync
Startet das Abrufen der Vertraulichkeitsbezeichnung der Datei.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.
#### <a name="parameters"></a>Parameter
* context Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.
### <a name="getprotectionasync"></a>GetProtectionAsync
Startet das Abrufen der Schutzrichtlinie der Datei.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.
#### <a name="parameters"></a>Parameter
* context Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.
### <a name="setlabel"></a>SetLabel
Legt die Vertraulichkeitsbezeichnung für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
Löst [JustificationRequiredError](#classmip_1_1_justification_required_error) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung erfordert und keine Legitimierungsnachricht über den Parameter labelingOptions ausgegeben wurde.
### <a name="deletelabel"></a>DeleteLabel
Löscht die Vertraulichkeitsbezeichnung aus der Datei.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird. Die Methoden Privilegd und Auto ermöglichen es der API, bestehende Bezeichnungen zu überschreiben. Löst [JustificationRequiredError](#classmip_1_1_justification_required_error) aus, wenn das Festlegen einer Bezeichnung eine Legitimierung erfordert und keine Legitimierungsnachricht über den Parameter justificationMessage ausgegeben wurde.
### <a name="setcustompermissions"></a>SetCustomPermissions
Legt benutzerdefinierte Berechtigungen für die Datei fest.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
### <a name="removeprotection"></a>RemoveProtection
Entfernt den Schutz von der Datei. Wenn der Datei eine Bezeichnung zugeordnet ist, geht diese verloren.
Änderungen werden erst in die Datei geschrieben, wenn CommitAsync aufgerufen wird.
### <a name="commitasync"></a>CommitAsync
Schreibt die Änderungen in die Datei, die durch den Parameter |outputFilePath| angegeben werden.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.
### <a name="commitasync"></a>CommitAsync
Schreibt die Änderungen in den Datenstrom, der durch den Parameter |outputStream| angegeben wird.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) wird bei Erfolg oder Fehler aufgerufen.
### <a name="getoutputfilename"></a>GetOutputFileName
Berechnet den Namen und die Erweiterung der Ausgabedatei auf Basis des ursprünglichen Dateinamens und der angefallenen Änderungen.
### <a name="filehandler"></a>~FileHandler
### <a name="filehandler"></a>FileHandler