# <a name="class-miprmscryptographyexception"></a>mip::RMSCryptographyException-Klasse 
RMS-Kryptografieausnahme
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSCryptographyException(const std::string& message)  |  [RMSCryptographyException](class_mip_rmscryptographyexception.md)-Konstruktor.
 public RMSCryptographyException(const char*const& message)  |  [RMSCryptographyException](class_mip_rmscryptographyexception.md)-Konstruktor.
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmscryptographyexception"></a>RMSCryptographyException
[RMSCryptographyException](class_mip_rmscryptographyexception.md)-Konstruktor.

Parameter:  
* **message**: Ausnahmemeldung


  
### <a name="rmscryptographyexception"></a>RMSCryptographyException
[RMSCryptographyException](class_mip_rmscryptographyexception.md)-Konstruktor.

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