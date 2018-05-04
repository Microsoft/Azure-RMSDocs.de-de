# <a name="class-mipuserpolicy"></a>mip::UserPolicy-Klasse 
Stellt die geschützten Inhalten zugeordnete Richtlinie dar.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public bool AccessCheck | Überprüft, ob die Richtlinie Benutzerzugriff auf das angegebene Recht gewährt
public UserPolicyType GetType | Ruft den Richtlinientyp ab
public std::string GetName | Ruft den Richtliniennamen ab
public std::string GetDescription | Ruft die Richtlinienbeschreibung ab
public std::shared_ptr< TemplateDescriptor > GetTemplateDescriptor public std::shared_ptr< PolicyDescriptor > GetPolicyDescriptor public std::string GetOwner | Ruft die E-Mail-Adresse des Inhaltsbesitzers ab.
public std::string GetIssuedTo | Ruft der Schutzrichtlinie zugeordnete Benutzer ab.
public bool IsIssuedToOwner | Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht.
public std::string GetContentId | Ruft einen eindeutigen Bezeichner für das Dokument/den Inhalt ab.
public const mip::AppDataHashMap GetEncryptedAppData | Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
public const mip::AppDataHashMap GetSignedAppData | Ruft anwendungsspezifische Daten ab, die signiert waren.
public std::chrono::time_point< std::chrono::system_clock > GetContentValidUntil | Ruft die Ablaufzeit der Richtlinie ab.
public bool DoesUseDeprecatedAlgorithms | Ruft ab, ob eine Richtlinie veraltete Kryptoalgorithmen (ECB) für die Abwärtskompatibilität nutzt oder nicht.
public bool IsAuditedExtractAllowed | Ruft ab, ob eine Richtlinie dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht.
public const std::vector< unsigned char > GetSerializedPolicy public std::shared_ptr< rmscore::core::ProtectionPolicy > GetImpl
## <a name="members"></a>Member
### <a name="accesscheck"></a>AccessCheck
Überprüft, ob die Richtlinie Benutzerzugriff auf das angegebene Recht gewährt
#### <a name="parameters"></a>Parameter
* right Zu prüfendes Recht
#### <a name="returns"></a>Rückgabe
Angabe, ob die Richtlinie Benutzerzugriff auf das angegebene Recht gewährt oder nicht
### <a name="userpolicytype"></a>UserPolicyType
Ruft den Richtlinientyp ab
#### <a name="returns"></a>Rückgabe
Richtlinientyp
### <a name="getname"></a>GetName
Ruft den Richtliniennamen ab
#### <a name="returns"></a>Rückgabe
Name der Richtlinie
### <a name="getdescription"></a>GetDescription
Ruft die Richtlinienbeschreibung ab
#### <a name="returns"></a>Rückgabe
Richtlinienbeschreibung
### <a name="templatedescriptor"></a>TemplateDescriptor
Ruft [TemplateDescriptor](#classmip_1_1_template_descriptor) für eine vorlagenbasierte [UserPolicy](#classmip_1_1_user_policy) ab.
#### <a name="returns"></a>Rückgabe
von [TemplateDescriptor](#classmip_1_1_template_descriptor), wenn [UserPolicy](#classmip_1_1_user_policy) vorlagenbasiert ist, andernfalls nullptr
### <a name="policydescriptor"></a>PolicyDescriptor
Ruft [PolicyDescriptor](#classmip_1_1_policy_descriptor) für eine Ad-hoc-[UserPolicy](#classmip_1_1_user_policy) ab.
#### <a name="returns"></a>Rückgabe
von [PolicyDescriptor](#classmip_1_1_policy_descriptor), wenn [UserPolicy](#classmip_1_1_user_policy) ad hoc ist, andernfalls nullptr
### <a name="getowner"></a>GetOwner
Ruft die E-Mail-Adresse des Inhaltsbesitzers ab.
#### <a name="returns"></a>Rückgabe
der E-Mail-Adresse des Inhaltsbesitzers
### <a name="getissuedto"></a>GetIssuedTo
Ruft die der Schutzrichtlinie zugeordneten Benutzer ab.
#### <a name="returns"></a>Rückgabe
der Benutzer, die der Schutzrichtlinie zugeordnet sind
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht.
#### <a name="returns"></a>Rückgabe
der Information, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht
### <a name="getcontentid"></a>GetContentId
Ruft den eindeutigen Bezeichner für das Dokument/den Inhalt ab.
#### <a name="returns"></a>Rückgabe
des eindeutigen Inhaltsbezeichners
### <a name="mipappdatahashmap"></a>mip::AppDataHashMap
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
Eine [UserPolicy](#classmip_1_1_user_policy) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst verschlüsselt waren. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [UserPolicy::GetSignedAppData](#classmip_1_1_user_policy_1a1c8a284d50adcac1a0a09316afa1d43e) zugänglich sind.
### <a name="mipappdatahashmap"></a>mip::AppDataHashMap
Ruft anwendungsspezifische Daten ab, die signiert waren.
Eine [UserPolicy](#classmip_1_1_user_policy) kann ein Wörterbuch mit anwendungsspezifischen Daten enthalten, die durch den RMS-Dienst signiert waren. Diese signierten Daten sind unabhängig den verschlüsselten Daten, die über [UserPolicy::GetEncryptedAppData](#classmip_1_1_user_policy_1a610fbc799284ab0ce4354c0611ece0e8) zugänglich sind.
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Ruft die Ablaufzeit der Richtlinie ab.
#### <a name="returns"></a>Rückgabe
der Ablaufzeit der Richtlinie
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Ruft ab, ob eine Richtlinie veraltete Kryptoalgorithmen (ECB) für die Abwärtskompatibilität nutzt.
#### <a name="returns"></a>Rückgabe
der Information, ob die Richtlinie veraltete Kryptoalgorithmen nutzt oder nicht
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Ruft ab, ob eine Richtlinie dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht.
#### <a name="returns"></a>Rückgabe
der Information, ob eine Richtlinie dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serialisiert die [UserPolicy](#classmip_1_1_user_policy) in eine Veröffentlichungslizenz (PL)
#### <a name="returns"></a>Rückgabe
der serialisierten [UserPolicy](#classmip_1_1_user_policy)
### <a name="getimpl"></a>GetImpl
Ruft interne Implementierung der abgeleiteten Klasse der [UserPolicy](#classmip_1_1_user_policy) ab.
#### <a name="returns"></a>Rückgabe
der Implementierung der abgeleiteten Klasse der [UserPolicy](#classmip_1_1_user_policy) Nur intern