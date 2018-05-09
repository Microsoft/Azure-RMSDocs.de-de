# <a name="class-miprmsnetworkexception"></a>mip::RMSNetworkException-Klasse 
Ausnahme für ein RMS-Netzwerk.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline RMSNetworkException(const std::string& message, Reason reason)  |  [RMSNetworkException](#classmip_1_1_r_m_s_network_exception)-Konstruktor
public inline RMSNetworkException(const char*const& message, Reason reason)  |  [RMSNetworkException](#classmip_1_1_r_m_s_network_exception)-Konstruktor
public inline virtual Reason reason() const  |  Ruft die Klassifizierung des Netzwerkfehlers ab
public inline virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
public inline virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
public inline virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](#classmip_1_1_r_m_s_network_exception)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung 
* reason: Netzwerkfehlerklassifizierung
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](#classmip_1_1_r_m_s_network_exception)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* message die Ausnahmemeldung 
* reason: Netzwerkfehlerklassifizierung
  
### <a name="reason"></a>Grund
Ruft die Klassifizierung des Netzwerkfehlers ab
  
#### <a name="returns"></a>Rückgabe
Die Netzwerkfehlerklassifizierung
  
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