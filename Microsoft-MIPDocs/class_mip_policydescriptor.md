# <a name="class-mippolicydescriptor"></a>mip::PolicyDescriptor-Klasse 
Stellt eine Ad-hoc-Richtlinie dar, die geschütztem Inhalt zugeordnet ist.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string & GetName | Ruft den Richtliniennamen ab
public void SetName | Legt den Richtliniennamen fest.
public const std::string & GetDescription | Ruft die Richtlinienbeschreibung ab
public void SetDescription | Legt die Richtlinienbeschreibung fest.
public const std::vector< UserRights > & GetUserRightsList | Ruft die Auflistung von Benutzerrechtszuordnungen ab.
public const std::vector< mip::UserRoles > & GetUserRolesList | Ruft die Auflistung von Benutzerrollenzuordnungen ab.
public const std::chrono::time_point< std::chrono::system_clock > & GetContentValidUntil | Ruft die Ablaufzeit der Richtlinie ab.
public void SetContentValidUntil | Legt die Ablaufzeit der Richtlinie fest.
public bool DoesAllowOfflineAccess | Ruft die Information ab, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.
public void SetAllowOfflineAccess | Legt fest, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.
public const std::string & GetReferrer | Ruft die Referreradresse der Richtlinie ab.
public void SetReferrer | Legt die Referreradresse der Richtlinie fest.
public const AppDataHashMap & GetEncryptedAppData | Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
public void SetEncryptedAppDataAppDataHashMap & value) | Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
public const AppDataHashMap & GetSignedAppData | Ruft anwendungsspezifische Daten ab, die signiert waren.
public void SetSignedAppDataAppDataHashMap & value) | Legt anwendungsspezifische Daten fest, die signiert werden sollten.
## <a name="members"></a>Member
### <a name="getname"></a>GetName
Ruft den Richtliniennamen ab
#### <a name="returns"></a>Rückgabe
Name der Richtlinie
### <a name="setname"></a>SetName
Legt den Richtliniennamen fest.
#### <a name="parameters"></a>Parameter
* value Policy name
### <a name="getdescription"></a>GetDescription
Ruft die Richtlinienbeschreibung ab
#### <a name="returns"></a>Rückgabe
Richtlinienbeschreibung
### <a name="setdescription"></a>SetDescription
Legt die Richtlinienbeschreibung fest.
#### <a name="parameters"></a>Parameter
* Legt die Richtlinienbeschreibung fest
### <a name="userrights"></a>UserRights
Ruft die Auflistung von Benutzerrechtszuordnungen ab.
#### <a name="returns"></a>Rückgabe
Auflistung von Benutzerrechtszuordnungen Der Wert der Eigenschaft UserRightsList wird leer, wenn der aktuelle Benutzer keinen Zugriff auf die Benutzerrechtsinformationen hat (er also nicht der Besitzer ist und nicht über das Recht VIEWRIGHTSDATA verfügt).
### <a name="mipuserroles"></a>mip::UserRoles
Ruft die Auflistung von Benutzerrollenzuordnungen ab.
#### <a name="returns"></a>Rückgabe
der Auflistung von Benutzerrollenzuordnungen
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Ruft die Ablaufzeit der Richtlinie ab.
#### <a name="returns"></a>Rückgabe
der Ablaufzeit der Richtlinie
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Legt die Ablaufzeit der Richtlinie fest.
#### <a name="parameters"></a>Parameter
* Wert Ablaufzeit der Richtlinie
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Ruft die Information ab, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.
#### <a name="returns"></a>Rückgabe
der Information, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht (Standard = TRUE)
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Legt fest, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.
#### <a name="parameters"></a>Parameter
* Wert Die Information, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht
### <a name="getreferrer"></a>GetReferrer
Ruft die Referreradresse der Richtlinie ab.
#### <a name="returns"></a>Rückgabe
Referreradresse der Richtlinie: Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Richtlinienbeschaffung fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
### <a name="setreferrer"></a>SetReferrer
Legt die Referreradresse der Richtlinie fest.
#### <a name="parameters"></a>Parameter
* uri Referreradresse der Richtlinie. Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Richtlinienbeschaffung fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
### <a name="appdatahashmap"></a>AppDataHashMap
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
#### <a name="returns"></a>Rückgabe
App-specific data Eine [UserPolicy](#classmip_1_1_user_policy) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst verschlüsselt waren. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [PolicyDescriptor::GetSignedAppData](#classmip_1_1_policy_descriptor_1ad523870efc92f9f81c82121a054d74d4) zugänglich sind
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
#### <a name="parameters"></a>Parameter
* Wert Anwendungsspezifische Daten Eine Anwendung kann ein Wörterbuch mit anwendungsspezifischen Daten angeben, die durch den RMS-Dienst verschlüsselt werden. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die von [PolicyDescriptor::SetSignedAppData](#classmip_1_1_policy_descriptor_1a00f35c0b91e48ccdcc6387466a61f362) festgelegt wurden.
### <a name="appdatahashmap"></a>AppDataHashMap
Ruft anwendungsspezifische Daten ab, die signiert waren.
#### <a name="returns"></a>Rückgabe
von anwendungsspezifischen Daten Eine [UserPolicy](#classmip_1_1_user_policy) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst signiert waren. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über [PolicyDescriptor::GetEncryptedAppData](#classmip_1_1_policy_descriptor_1a9a5bcf9d1bf7357de549429179197ab6) zugänglich sind
### <a name="setsignedappdata"></a>SetSignedAppData
Legt anwendungsspezifische Daten fest, die signiert werden sollten.
#### <a name="parameters"></a>Parameter
* Wert Anwendungsspezifische Daten Eine Anwendung kann ein Wörterbuch mit anwendungsspezifischen Daten angeben, die durch den RMS-Dienst signiert werden. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die von [PolicyDescriptor::SetEncryptedAppData](#classmip_1_1_policy_descriptor_1a5275224932dc17319092304497e59eb2) festgelegt wurden.