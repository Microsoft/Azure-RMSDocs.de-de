# <a name="class-miprmsinvalidargumentexception"></a>cmip::RMSInvalidArgumentException-Klasse 
RMS-Ausnahme für ungültiges Argument
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSInvalidArgumentException(const std::string& message)  |  [RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md)-Konstruktor
 public RMSInvalidArgumentException(const char*const& message)  |  [RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md)-Konstruktor
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsinvalidargumentexception"></a>RMSInvalidArgumentException
[RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md)-Konstruktor

Parameter:  
* **message**: Ausnahmemeldung


  
### <a name="rmsinvalidargumentexception"></a>RMSInvalidArgumentException
[RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md)-Konstruktor

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