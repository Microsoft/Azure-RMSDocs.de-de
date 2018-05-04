# <a name="class-miprmsofficefileexception"></a>mip::RMSOfficeFileException-Klasse 
Ausnahme für RMS-Office-Datei.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSOfficeFileExceptionReason reason) public inline RMSOfficeFileExceptionReason reason) public inline virtual Reason reason | Ruft die Office-Dateifehlerklassifizierung ab.
public inline virtual const char * what | Ruft die Ausnahmemeldung ab
public inline virtual ExceptionTypes type | Ruft den Ausnahmetyp ab
public inline virtual int error | Ruft den Fehlercode ab
## <a name="members"></a>Member
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception)-Konstruktor.
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung 
* reason Office-Dateifehlerklassifizierung
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception)-Konstruktor.
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung 
* reason Office-Dateifehlerklassifizierung
### <a name="reason"></a>Grund
Ruft die Fehlerklassifizierung der Office-Datei ab.
#### <a name="returns"></a>Rückgabe
Die Fehlerklassifizierung der Office-Datei
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