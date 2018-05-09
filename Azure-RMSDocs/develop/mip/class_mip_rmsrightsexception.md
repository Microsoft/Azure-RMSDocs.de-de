# <a name="class-miprmsrightsexception"></a>mip::RMSRightsException-Klasse 
Ausnahme für RMS-Rechte
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSRightsException(const std::string& message)  |  [RMSRightsException](#classmip_1_1_r_m_s_rights_exception)-Konstruktor
public inline RMSRightsException(const char*const& message)  |  [RMSRightsException](#classmip_1_1_r_m_s_rights_exception)-Konstruktor
public inline virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
public inline virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
public inline virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsrightsexception"></a>RMSRightsException
[RMSRightsException](#classmip_1_1_r_m_s_rights_exception)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung
  
### <a name="rmsrightsexception"></a>RMSRightsException
[RMSRightsException](#classmip_1_1_r_m_s_rights_exception)-Konstruktor
  
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