# <a name="class-miprmsstreamexception"></a>mip::RMSStreamException-Klasse 
Ausnahme für den RMS-Stream
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSStreamException(const std::string& message)  |  [RMSStreamException](class_mip_rmsstreamexception.md)-Konstruktor.
 public RMSStreamException(const char*const& message)  |  [RMSStreamException](class_mip_rmsstreamexception.md)-Konstruktor.
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstreamexception.md)-Konstruktor.

Parameter:  
* **message**: Ausnahmemeldung


  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstreamexception.md)-Konstruktor.

Parameter:  
* **message**: Ausnahmemeldung


  
### <a name="what"></a>what
Ruft die Ausnahmemeldung ab

  
**Rückgabe**: Ausnahmemeldung
  
### <a name="exceptiontypes"></a>ExceptionTypes
Ruft den Ausnahmetyp ab

  
**Rückgabe**: Ausnahmetyp
  
### <a name="error"></a>Fehler
Ruft den Fehlercode ab

  
**Rückgabe**: [Error](class_mip_error.md)-Code