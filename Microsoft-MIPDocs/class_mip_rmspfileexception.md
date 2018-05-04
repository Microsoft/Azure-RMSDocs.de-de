# <a name="class-miprmspfileexception"></a>mip::RMSPFileException-Klasse 
Ausnahme für RMS-PFile.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSPFileExceptionReason reason) public inline RMSPFileExceptionReason reason) public inline virtual Reason reason | Ruft die PFile-Fehlerklassifizierung ab.
public inline virtual const char * what | Ruft die Ausnahmemeldung ab.
public inline virtual ExceptionTypes type | Ruft den Ausnahmetyp ab
public inline virtual int error | Ruft den Fehlercode ab
## <a name="members"></a>Member
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception)-Konstruktor.
#### <a name="parameters"></a>Parameter
* message: die Ausnahmemeldung 
* reason: die PFile-Fehlerklassifizierung
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception)-Konstruktor.
#### <a name="parameters"></a>Parameter
* message: die Ausnahmemeldung 
* reason: die PFile-Fehlerklassifizierung
### <a name="reason"></a>Grund
Ruft die PFile-Fehlerklassifizierung ab.
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
Ruft den Fehlercode ab.
#### <a name="returns"></a>Rückgabe
[Fehlercode](#classmip_1_1_error)