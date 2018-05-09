# <a name="class-miprmsinvalidargumentexception"></a>cmip::RMSInvalidArgumentException-Klasse 
RMS-Ausnahme für ungültiges Argument
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSInvalidArgumentException(const std::string& message)  |  [RMSInvalidArgumentException](#classmip_1_1_r_m_s_invalid_argument_exception)-Konstruktor
public inline RMSInvalidArgumentException(const char*const& message)  |  [RMSInvalidArgumentException](#classmip_1_1_r_m_s_invalid_argument_exception)-Konstruktor
public inline virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
public inline virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
public inline virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsinvalidargumentexception"></a>RMSInvalidArgumentException
[RMSInvalidArgumentException](#classmip_1_1_r_m_s_invalid_argument_exception)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung
  
### <a name="rmsinvalidargumentexception"></a>RMSInvalidArgumentException
[RMSInvalidArgumentException](#classmip_1_1_r_m_s_invalid_argument_exception)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung
  
### <a name="what"></a>what
Ruft die Ausnahmemeldung ab
  
#### <a name="returns"></a>Rückgabe
Ausnahmemeldung
  
### <a name="exceptiontypes"></a>ExceptionTypes
Ruft den Ausnahmetyp ab
  
#### <a name="returns"></a>Rückgabe
Ausnahmetyp
  
### <a name="error"></a>Fehler
Ruft den Fehlercode ab
  
#### <a name="returns"></a>Rückgabe
Fehlercode des Typs [Error](#classmip_1_1_error)