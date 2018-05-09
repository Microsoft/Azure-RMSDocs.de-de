# <a name="class-miprmsexception"></a>mip::RMSException-Klasse 
RMS-Basisausnahme
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSException(const ExceptionTypes type, const int error, const std::string& message)  |  [RMSException](#classmip_1_1_r_m_s_exception)-Konstruktor
public inline RMSException(const ExceptionTypes type, const int error, const char*const& message)  |  [RMSException](#classmip_1_1_r_m_s_exception)-Konstruktor
public inline virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
public inline virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
public inline virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* type der Ausnahmetyp 
* error der Fehlercode des Typs [Error](#classmip_1_1_error) 
* message die Ausnahmemeldung
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* type der Ausnahmetyp 
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