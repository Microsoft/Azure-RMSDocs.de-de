# <a name="class-miprmslogicexception"></a>mip::RMSLogicException-Klasse 
Ausnahme für RMS-Logik.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSLogicException(const ErrorTypes error, const std::string& message)  |  [RMSLogicException](class_mip_rmslogicexception.md)-Konstruktor.
 public RMSLogicException(const ErrorTypes error, const char*const& message)  |  [RMSLogicException](class_mip_rmslogicexception.md)-Konstruktor.
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](class_mip_rmslogicexception.md)-Konstruktor.

Parameter:  
* **error**: Fehlercode des Typs [Error](class_mip_error.md) 


* **message**: Ausnahmemeldung


  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](class_mip_rmslogicexception.md)-Konstruktor.

Parameter:  
* **error**: Fehlercode des Typs [Error](class_mip_error.md) 


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