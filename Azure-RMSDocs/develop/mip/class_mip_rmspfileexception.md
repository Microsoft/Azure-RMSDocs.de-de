# <a name="class-miprmspfileexception"></a>mip::RMSPFileException-Klasse 
RMS-PFile-Ausnahme
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSPFileException(const std::string& message, Reason reason)  |  [RMSPFileException](#classmip_1_1_r_m_s_p_file_exception)-Konstruktor.
public inline RMSPFileException(const char*const& message, Reason reason)  |  [RMSPFileException](#classmip_1_1_r_m_s_p_file_exception)-Konstruktor.
public inline virtual Reason reason() const  |  Ruft die PFile-Fehlerklassifizierung ab
public inline virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
public inline virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
public inline virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception)-Konstruktor.
  
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung 
* reason die PFile-Fehlerklassifizierung
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception)-Konstruktor.
  
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung 
* reason die PFile-Fehlerklassifizierung
  
### <a name="reason"></a>Grund
Ruft die PFile-Fehlerklassifizierung ab
  
#### <a name="returns"></a>Rückgabe
Die PFile-Fehlerklassifizierung
  
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