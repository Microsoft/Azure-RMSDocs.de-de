# <a name="class-miprmsrightsexception"></a>mip::RMSRightsException-Klasse 
Ausnahme für RMS-Rechte
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSRightsException(const std::string& message)  |  [RMSRightsException](class_mip_rmsrightsexception.md)-Konstruktor
 public RMSRightsException(const char*const& message)  |  [RMSRightsException](class_mip_rmsrightsexception.md)-Konstruktor
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsrightsexception"></a>RMSRightsException
[RMSRightsException](class_mip_rmsrightsexception.md)-Konstruktor

Parameter:  
* **message**: Ausnahmemeldung


  
### <a name="rmsrightsexception"></a>RMSRightsException
[RMSRightsException](class_mip_rmsrightsexception.md)-Konstruktor

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