# <a name="class-mipuserpolicy"></a>mip::UserPolicy-Klasse 
Stellt die geschützten Inhalten zugeordnete Richtlinie dar.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public bool AccessCheck(const std::string& right) const  |  Überprüft, ob die Richtlinie Benutzerzugriff auf das angegebene Recht gewährt
 public UserPolicyType GetType()  |  Ruft den Richtlinientyp ab
 public std::string GetName()  |  Ruft den Richtliniennamen ab
 public std::string GetDescription()  |  Ruft die Richtlinienbeschreibung ab
public std::shared_ptr<TemplateDescriptor> GetTemplateDescriptor()  |  Ruft [TemplateDescriptor](class_mip_templatedescriptor.md) für eine vorlagenbasierte [UserPolicy](class_mip_userpolicy.md) ab.
public std::shared_ptr<PolicyDescriptor> GetPolicyDescriptor()  |  Ruft [PolicyDescriptor](class_mip_policydescriptor.md) für eine Ad-hoc-[UserPolicy](class_mip_userpolicy.md) ab.
 public std::string GetOwner()  |  Ruft die E-Mail-Adresse des Inhaltsbesitzers ab
 public std::string GetIssuedTo()  |  Ruft den der Schutzrichtlinie zugeordneten Benutzer ab.
 public bool IsIssuedToOwner()  |  Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht.
 public std::string GetContentId()  |  Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.
 public const mip::AppDataHashMap GetEncryptedAppData()  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
 public const mip::AppDataHashMap GetSignedAppData()  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
public std::chrono::time_point<std::chrono::system_clock> GetContentValidUntil()  |  Ruft die Ablaufzeit der Richtlinie ab.
 public bool DoesUseDeprecatedAlgorithms()  |  Ruft ab, ob eine Richtlinie veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt.
 public bool IsAuditedExtractAllowed()  |  Ruft ab, ob eine Richtlinie dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht.
public const std::vector<unsigned char> GetSerializedPolicy()  |  Serialisiert die [UserPolicy](class_mip_userpolicy.md) in eine Veröffentlichungslizenz
public std::shared_ptr<rmscore::core::ProtectionPolicy> GetImpl()  |  Ruft die interne Implementierung der abgeleiteten Klasse der [UserPolicy](class_mip_userpolicy.md) ab.
  
## <a name="members"></a>Member
  
### <a name="accesscheck"></a>AccessCheck
Überprüft, ob die Richtlinie Benutzerzugriff auf das angegebene Recht gewährt

Parameter:  
* **right**: Zu prüfendes Recht



  
**Rückgabe**: Angabe, ob die Richtlinie Benutzerzugriff auf das angegebene Recht gewährt oder nicht
  
### <a name="userpolicytype"></a>UserPolicyType
Ruft den Richtlinientyp ab

  
**Rückgabe**: Richtlinientyp
  
### <a name="getname"></a>GetName
Ruft den Richtliniennamen ab

  
**Rückgabe**: Richtlinienname
  
### <a name="getdescription"></a>GetDescription
Ruft die Richtlinienbeschreibung ab

  
**Rückgabe**: Richtlinienbeschreibung
  
### <a name="templatedescriptor"></a>TemplateDescriptor
Ruft [TemplateDescriptor](class_mip_templatedescriptor.md) für eine vorlagenbasierte [UserPolicy](class_mip_userpolicy.md) ab.

  
**Rückgabe**: [TemplateDescriptor](class_mip_templatedescriptor.md), wenn [UserPolicy](class_mip_userpolicy.md) vorlagenbasiert ist, andernfalls „nullptr“
  
### <a name="policydescriptor"></a>PolicyDescriptor
Ruft [PolicyDescriptor](class_mip_policydescriptor.md) für eine Ad-hoc-[UserPolicy](class_mip_userpolicy.md) ab.

  
**Rückgabe**: [PolicyDescriptor](class_mip_policydescriptor.md), wenn [UserPolicy](class_mip_userpolicy.md) ad hoc ist, andernfalls „nullptr“
  
### <a name="getowner"></a>GetOwner
Ruft die E-Mail-Adresse des Inhaltsbesitzers ab

  
**Rückgabe**: E-Mail-Adresse des Inhaltsbesitzers
  
### <a name="getissuedto"></a>GetIssuedTo
Ruft den der Schutzrichtlinie zugeordneten Benutzer ab.

  
**Rückgabe**: Benutzer, der der Schutzrichtlinie zugeordnet ist
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht.

  
**Rückgabe**: Angabe, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht
  
### <a name="getcontentid"></a>GetContentId
Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.

  
**Rückgabe**: Eindeutiger Inhaltsbezeichner
  
### <a name="mipappdatahashmap"></a>mip::AppDataHashMap
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
Eine [UserPolicy](class_mip_userpolicy.md) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst verschlüsselt wurden. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [UserPolicy::GetSignedAppData](class_mip_userpolicy.md#getsignedappdata) zugänglich sind.
  
### <a name="mipappdatahashmap"></a>mip::AppDataHashMap
Ruft anwendungsspezifische Daten ab, die signiert waren.
Eine [UserPolicy](class_mip_userpolicy.md) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst signiert waren. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über [UserPolicy::GetEncryptedAppData](class_mip_userpolicy.md#getencryptedappdata) zugänglich sind.
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Ruft die Ablaufzeit der Richtlinie ab.

  
**Rückgabe**: Ablaufzeit der Richtlinie
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Ruft ab, ob eine Richtlinie veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt.

  
**Rückgabe**: Angabe, ob die Richtlinie veraltete Kryptografiealgorithmen nutzt oder nicht
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Ruft ab, ob eine Richtlinie dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht.

  
**Rückgabe**: Angabe, ob eine Richtlinie dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht
  
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serialisiert die [UserPolicy](class_mip_userpolicy.md) in eine Veröffentlichungslizenz

  
**Rückgabe**: Serialisierte [UserPolicy](class_mip_userpolicy.md)
  
### <a name="getimpl"></a>GetImpl
Ruft die interne Implementierung der abgeleiteten Klasse der [UserPolicy](class_mip_userpolicy.md) ab.

  
**Rückgabe**: Implementierung der abgeleiteten Klasse der [UserPolicy](class_mip_userpolicy.md) „Nur intern“