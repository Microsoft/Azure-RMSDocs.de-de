# <a name="class-mipinternalerror"></a>mip::InternalError-Klasse 
Ein interner SDK-Fehler. Etwas Unerwartetes ist vorgefallen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline char const* what() const  |  Ruft eine CString-Fehlermeldung ab
public std::shared_ptr<Error> Clone() const  |  Klont den Fehler
public inline virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
public inline virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
public inline virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
public inline virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="what"></a>what
Ruft eine CString-Fehlermeldung ab
  
#### <a name="returns"></a>Rückgabe
Eine CString-Fehlermeldung
  
### <a name="error"></a>Fehler
Klont den Fehler
  
#### <a name="returns"></a>Rückgabe
Ein Klon des Fehlers
  
### <a name="errortype"></a>ErrorType
Ruft den Fehlertyp ab
  
#### <a name="returns"></a>Rückgabe
Der Fehlertyp
  
### <a name="geterrorname"></a>GetErrorName
Ruft den Fehlernamen ab
  
#### <a name="returns"></a>Rückgabe
Der Fehlername
  
### <a name="getmessage"></a>GetMessage
Ruft die Fehlermeldung ab
  
#### <a name="returns"></a>Rückgabe
Die Fehlermeldung
  
### <a name="setmessage"></a>SetMessage
Legt die Fehlermeldung fest
  
#### <a name="parameters"></a>Parameter
* msg: die Fehlermeldung.