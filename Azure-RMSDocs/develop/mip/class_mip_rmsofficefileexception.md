# <a name="class-miprmsofficefileexception"></a>mip::RMSOfficeFileException-Klasse 
Ausnahme für RMS-Office-Datei.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSOfficeFileException(const std::string& message, Reason reason)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md)-Konstruktor.
 public RMSOfficeFileException(const char*const& message, Reason reason)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md)-Konstruktor.
 public virtual Reason reason() const  |  Ruft die Fehlerklassifizierung der Office-Datei ab.
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md)-Konstruktor.

Parameter:  
* **message**: Ausnahmemeldung 


* **reason**: Office-Dateifehlerklassifizierung


  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md)-Konstruktor.

Parameter:  
* **message**: Ausnahmemeldung 


* **reason**: Office-Dateifehlerklassifizierung


  
### <a name="reason"></a>Grund
Ruft die Fehlerklassifizierung der Office-Datei ab.

  
**Rückgabe**: Office-Dateifehlerklassifizierung
  
### <a name="what"></a>what
Ruft die Ausnahmemeldung ab

  
**Rückgabe**: Ausnahmemeldung
  
### <a name="exceptiontypes"></a>ExceptionTypes
Ruft den Ausnahmetyp ab

  
**Rückgabe**: Ausnahmetyp
  
### <a name="error"></a>Fehler
Ruft den Fehlercode ab

  
**Rückgabe**: [Error](class_mip_error.md)-Code