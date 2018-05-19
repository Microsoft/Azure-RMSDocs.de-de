# <a name="class-miprmsexception"></a>mip::RMSException-Klasse 
RMS-Basisausnahme
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSException(const ExceptionTypes type, const int error, const std::string& message)  |  [RMSException](class_mip_rmsexception.md)-Konstruktor
 public RMSException(const ExceptionTypes type, const int error, const char*const& message)  |  [RMSException](class_mip_rmsexception.md)-Konstruktor
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md)-Konstruktor

Parameter:  
* **type**: Ausnahmetyp 


* **error**: Fehlercode des Typs [Error](class_mip_error.md) 


* **message**: Ausnahmemeldung


  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md)-Konstruktor

Parameter:  
* **type**: Ausnahmetyp 


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