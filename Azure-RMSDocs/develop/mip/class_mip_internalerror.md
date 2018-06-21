# <a name="class-mipinternalerror"></a>mip::InternalError-Klasse 
Ein interner SDK-Fehler. Etwas Unerwartetes ist vorgefallen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public char const* what() const  |  Ruft eine CString-Fehlermeldung ab
public std::shared_ptr<Error> Clone() const  |  Klont den Fehler
 public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
 public virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
 public virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
 public virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="what"></a>what
Ruft eine CString-Fehlermeldung ab

  
**Rückgabe**: eine CString-Fehlermeldung
  
### <a name="error"></a>Fehler
Klont den Fehler

  
**Rückgabe**: ein Klon des Fehlers.
  
### <a name="errortype"></a>ErrorType
Ruft den Fehlertyp ab

  
**Rückgabe**: der Fehlertyp.
  
### <a name="geterrorname"></a>GetErrorName
Ruft den Fehlernamen ab

  
**Rückgabe**: der Fehlername.
  
### <a name="getmessage"></a>GetMessage
Ruft die Fehlermeldung ab

  
**Rückgabe**: die Fehlermeldung.
  
### <a name="setmessage"></a>SetMessage
Legt die Fehlermeldung fest

Parameter:  
* **msg**: die Fehlermeldung.

