# <a name="class-mippolicydescriptor"></a>mip::PolicyDescriptor-Klasse 
Stellt eine Ad-hoc-Richtlinie dar, die geschütztem Inhalt zugeordnet ist.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetName()  |  Ruft den Richtliniennamen ab
 public void SetName(const std::string& value)  |  Legt den Richtliniennamen fest.
 public const std::string& GetDescription()  |  Ruft die Richtlinienbeschreibung ab
 public void SetDescription(const std::string& value)  |  Legt die Richtlinienbeschreibung fest.
public const std::vector<UserRights>& GetUserRightsList() const  |  Ruft die Auflistung von Benutzerrechtszuordnungen ab.
public const std::vector<mip::UserRoles>& GetUserRolesList()  |  Ruft die Auflistung von Benutzerrollenzuordnungen ab.
public const std::chrono::time_point<std::chrono::system_clock>& GetContentValidUntil()  |  Ruft die Ablaufzeit der Richtlinie ab.
public void SetContentValidUntil(const std::chrono::time_point<std::chrono::system_clock>& value)  |  Legt die Ablaufzeit der Richtlinie fest.
 public bool DoesAllowOfflineAccess()  |  Ruft die Information ab, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.
 public void SetAllowOfflineAccess(bool value)  |  Legt fest, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.
 public const std::string& GetReferrer() const  |  Ruft die Referreradresse der Richtlinie ab.
 public void SetReferrer(const std::string& uri)  |  Legt die Referreradresse der Richtlinie fest.
 public const AppDataHashMap& GetEncryptedAppData()  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
 public void SetEncryptedAppData(const AppDataHashMap& value)  |  Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
 public const AppDataHashMap& GetSignedAppData()  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
 public void SetSignedAppData(const AppDataHashMap& value)  |  Legt anwendungsspezifische Daten fest, die signiert werden sollten.
  
## <a name="members"></a>Member
  
### <a name="getname"></a>GetName
Ruft den Richtliniennamen ab

  
**Rückgabe**: Richtlinienname
  
### <a name="setname"></a>SetName
Legt den Richtliniennamen fest.

Parameter:  
* **value**: Richtlinienname


  
### <a name="getdescription"></a>GetDescription
Ruft die Richtlinienbeschreibung ab

  
**Rückgabe**: Richtlinienbeschreibung
  
### <a name="setdescription"></a>SetDescription
Legt die Richtlinienbeschreibung fest.

Parameter:  
* **value**: Richtlinienbeschreibung


  
### <a name="userrights"></a>UserRights
Ruft die Auflistung von Benutzerrechtszuordnungen ab.

  
**Rückgabe**: Auflistung von Benutzerrechtszuordnungen: Der Wert der Eigenschaft UserRightsList ist leer, wenn der aktuelle Benutzer keinen Zugriff auf die Benutzerrechtsinformationen hat (er also nicht der Besitzer ist und nicht über das Recht VIEWRIGHTSDATA verfügt).
  
### <a name="mipuserroles"></a>mip::UserRoles
Ruft die Auflistung von Benutzerrollenzuordnungen ab.

  
**Rückgabe**: Auflistung von Benutzerrollenzuordnungen
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Ruft die Ablaufzeit der Richtlinie ab.

  
**Rückgabe**: Ablaufzeit der Richtlinie
  
### <a name="setcontentvaliduntil"></a>GetContentValidUntil
Legt die Ablaufzeit der Richtlinie fest.

Parameter:  
* **value**: Ablaufzeit der Richtlinie


  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Ruft die Information ab, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.

  
**Rückgabe**: Angabe, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht (Standard = TRUE)
  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Legt fest, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.

Parameter:  
* **value**: Angabe, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt


  
### <a name="getreferrer"></a>GetReferrer
Ruft die Referreradresse der Richtlinie ab.

  
**Rückgabe**: Referreradresse der Richtlinie. Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Richtlinienbeschaffung fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
  
### <a name="setreferrer"></a>SetReferrer
Legt die Referreradresse der Richtlinie fest.

Parameter:  
* **uri**: Referreradresse der Richtlinie


Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Richtlinienbeschaffung fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
  
### <a name="appdatahashmap"></a>AppDataHashMap
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.

  
**Rückgabe**: Anwendungsspezifische Daten: Eine [UserPolicy](class_mip_userpolicy.md) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst verschlüsselt waren. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [PolicyDescriptor::GetSignedAppData](class_mip_policydescriptor.md#getsignedappdata) zugänglich sind
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.

Parameter:  
* **value**: Anwendungsspezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom RMS-Dienst verschlüsselt wird. Diese verschlüsselten Daten sind durch [PolicyDescriptor::SetSignedAppData](class_mip_policydescriptor.md#setsignedappdata) unabhängig von dem signierten Dataset.
  
### <a name="appdatahashmap"></a>AppDataHashMap
Ruft anwendungsspezifische Daten ab, die signiert waren.

  
**Rückgabe**: Anwendungsspezifische Daten: Eine [UserPolicy](class_mip_userpolicy.md) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst signiert waren. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über [PolicyDescriptor::GetEncryptedAppData](class_mip_policydescriptor.md#getencryptedappdata) zugänglich sind.
  
### <a name="setsignedappdata"></a>SetSignedAppData
Legt anwendungsspezifische Daten fest, die signiert werden sollten.

Parameter:  
* **value**: Anwendungsspezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom RMS-Dienst signiert wird. Diese signierten Daten sind durch [PolicyDescriptor::SetEncryptedAppData](class_mip_policydescriptor.md#setencryptedappdata) unabhängig von dem verschlüsselten Dataset.