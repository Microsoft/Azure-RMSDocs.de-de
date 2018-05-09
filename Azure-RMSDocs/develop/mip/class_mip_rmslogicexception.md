# <a name="class-miprmslogicexception"></a>mip::RMSLogicException-Klasse 
Ausnahme für RMS-Logik.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSLogicException(const ErrorTypes error, const std::string& message)  |  [RMSLogicException](#classmip_1_1_r_m_s_logic_exception)-Konstruktor.
public inline RMSLogicException(const ErrorTypes error, const char*const& message)  |  [RMSLogicException](#classmip_1_1_r_m_s_logic_exception)-Konstruktor.
public inline virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
public inline virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
public inline virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](#classmip_1_1_r_m_s_logic_exception)-Konstruktor.
  
#### <a name="parameters"></a>Parameter
* error der Fehlercode des Typs [Error](#classmip_1_1_error) 
* message die Ausnahmemeldung
  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](#classmip_1_1_r_m_s_logic_exception)-Konstruktor.
  
#### <a name="parameters"></a>Parameter
* error der Fehlercode des Typs [Error](#classmip_1_1_error) 
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