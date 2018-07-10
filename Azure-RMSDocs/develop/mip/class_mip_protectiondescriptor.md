# <a name="class-mipprotectiondescriptor"></a>mip::ProtectionDescriptor-Klasse 
Stellt eine Ad-hoc-Richtlinie dar, die geschütztem Inhalt zugeordnet ist.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public ProtectionType GetProtectionType() const  |  Ruft den Typ des Schutzes ab, unabhängig davon, ob er aus der Schutz-SDK-Vorlage stammt oder nicht.
 public const std::string& GetName() const  |  Ruft den Richtliniennamen ab
 public const std::string& GetDescription() const  |  Ruft die Richtlinienbeschreibung ab
 public const std::string& GetTemplateId() const  |  Ruft die Schutzvorlagen-ID ab.
public const std::vector<UserRights>& GetUserRights() const  |  Ruft die Auflistung von Benutzerrechtszuordnungen ab.
public const std::vector<UserRoles>& GetUserRoles() const  |  Ruft die Auflistung von Benutzerrollenzuordnungen ab.
public const std::chrono::time_point<std::chrono::system_clock>& GetContentValidUntil() const  |  Ruft die Ablaufzeit der Richtlinie ab.
 public bool DoesAllowOfflineAccess() const  |  Ruft die Information ab, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.
 public const std::string& GetReferrer() const  |  Ruft die Referreradresse der Richtlinie ab.
public const std::map<std::string, std::string>& GetEncryptedAppData() const  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
public const std::map<std::string, std::string>& GetSignedAppData() const  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
  
## <a name="members"></a>Member
  
### <a name="protectiontype"></a>ProtectionType
Ruft den Typ des Schutzes ab, unabhängig davon, ob er aus der Schutz-SDK-Vorlage stammt oder nicht.

  
**Rückgabe**: Typ des Schutzes
  
### <a name="getname"></a>GetName
Ruft den Richtliniennamen ab

  
**Rückgabe**: Richtlinienname
  
### <a name="getdescription"></a>GetDescription
Ruft die Richtlinienbeschreibung ab

  
**Rückgabe**: Richtlinienbeschreibung
  
### <a name="gettemplateid"></a>GetTemplateId
Ruft die Schutzvorlagen-ID ab.

  
**Rückgabe**: Vorlagen-ID
  
### <a name="userrights"></a>UserRights
Ruft die Auflistung von Benutzerrechtszuordnungen ab.

  
**Rückgabe**: Auflistung von Benutzerrechtszuordnungen: Der Wert der Eigenschaft [UserRights](class_mip_userrights.md) ist leer, wenn der aktuelle Benutzer keinen Zugriff auf die Benutzerrechtsinformationen hat (er also nicht der Besitzer ist und nicht über das Recht „VIEWRIGHTSDATA“ verfügt).
  
### <a name="userroles"></a>UserRoles
Ruft die Auflistung von Benutzerrollenzuordnungen ab.

  
**Rückgabe**: Auflistung von Benutzerrollenzuordnungen
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Ruft die Ablaufzeit der Richtlinie ab.

  
**Rückgabe**: Ablaufzeit der Richtlinie
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Ruft die Information ab, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht.

  
**Rückgabe**: Angabe, ob die Richtlinie den Zugang zu Offlineinhalten erlaubt oder nicht (Standard = TRUE)
  
### <a name="getreferrer"></a>GetReferrer
Ruft die Referreradresse der Richtlinie ab.

  
**Rückgabe**: Referreradresse der Richtlinie. Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Richtlinienbeschaffung fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.

  
**Rückgabe**: Anwendungsspezifische Daten. Ein [ProtectionHandler](class_mip_protectionhandler.md) kann ein vom Schutzdienst verschlüsseltes Wörterbuch mit anwendungsspezifischen Daten enthalten. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata) verfügbar sind.
  
### <a name="getsignedappdata"></a>GetSignedAppData
Ruft anwendungsspezifische Daten ab, die signiert waren.

  
**Rückgabe**: Anwendungsspezifische Daten. Ein [ProtectionHandler](class_mip_protectionhandler.md) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst signiert wurden. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata) zugänglich sind.