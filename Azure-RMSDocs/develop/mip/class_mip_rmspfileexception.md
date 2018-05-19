# <a name="class-miprmspfileexception"></a>mip::RMSPFileException-Klasse 
RMS-PFile-Ausnahme
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSPFileException(const std::string& message, Reason reason)  |  [RMSPFileException](class_mip_rmspfileexception.md)-Konstruktor.
 public RMSPFileException(const char*const& message, Reason reason)  |  [RMSPFileException](class_mip_rmspfileexception.md)-Konstruktor.
 public virtual Reason reason() const  |  Ruft die PFile-Fehlerklassifizierung ab
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](class_mip_rmspfileexception.md)-Konstruktor.

Parameter:  
* **message**: Ausnahmemeldung 


* **reason**: PFile-Fehlerklassifizierung


  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](class_mip_rmspfileexception.md)-Konstruktor.

Parameter:  
* **message**: Ausnahmemeldung 


* **reason**: PFile-Fehlerklassifizierung


  
### <a name="reason"></a>Grund
Ruft die PFile-Fehlerklassifizierung ab

  
**Rückgabe**: PFile-Fehlerklassifizierung
  
### <a name="what"></a>what
Ruft die Ausnahmemeldung ab

  
**Rückgabe**: Ausnahmemeldung
  
### <a name="exceptiontypes"></a>ExceptionTypes
Ruft den Ausnahmetyp ab

  
**Rückgabe**: Ausnahmetyp
  
### <a name="error"></a>Fehler
Ruft den Fehlercode ab

  
**Rückgabe**: [Error](class_mip_error.md)-Code