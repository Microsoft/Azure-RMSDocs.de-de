# <a name="class-miprmsnetworkexception"></a>mip::RMSNetworkException-Klasse 
Ausnahme für ein RMS-Netzwerk.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public RMSNetworkException(const std::string& message, Reason reason)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md)-Konstruktor
 public RMSNetworkException(const char*const& message, Reason reason)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md)-Konstruktor
 public virtual Reason reason() const  |  Ruft die Klassifizierung des Netzwerkfehlers ab
 public virtual const char* what() const  |  Ruft die Ausnahmemeldung ab
 public virtual ExceptionTypes type() const  |  Ruft den Ausnahmetyp ab
 public virtual int error() const  |  Ruft den Fehlercode ab
  
## <a name="members"></a>Member
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md)-Konstruktor

Parameter:  
* **message**: Ausnahmemeldung 


* **reason**: Netzwerkfehlerklassifizierung


  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md)-Konstruktor

Parameter:  
* **message**: Ausnahmemeldung 


* **reason**: Netzwerkfehlerklassifizierung


  
### <a name="reason"></a>Grund
Ruft die Klassifizierung des Netzwerkfehlers ab

  
**Rückgabe**: Netzwerkfehlerklassifizierung
  
### <a name="what"></a>what
Ruft die Ausnahmemeldung ab

  
**Rückgabe**: Ausnahmemeldung
  
### <a name="exceptiontypes"></a>ExceptionTypes
Ruft den Ausnahmetyp ab

  
**Rückgabe**: Ausnahmetyp
  
### <a name="error"></a>Fehler
Ruft den Fehlercode ab

  
**Rückgabe**: [Error](class_mip_error.md)-Code