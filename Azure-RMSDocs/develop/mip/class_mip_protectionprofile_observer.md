# <a name="class-mipprotectionprofileobserver"></a>mip::ProtectionProfile::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](#classmip_1_1_protection_profile) empfängt.
Diese Schnittstelle muss von Anwendungen mithilfe des Schutz-SDK implementiert werden.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline virtual void OnLoadSuccessProtectionProfile > & profile,const std::shared_ptr< void > & context) | Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public inline virtual void OnLoadFailure | Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
## <a name="members"></a>Member
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
#### <a name="parameters"></a>Parameter
* profile Ein Verweis auf das neu erstellte [ProtectionProfile](#classmip_1_1_protection_profile)
* context Derselbe Kontext, der an [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) übergeben wurde. Eine Anwendung kann beliebige Kontexttypen (z.B. std::promise, std:: Function usw.) an [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) übergeben, und derselbe Kontext wird an [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) oder [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291) übergeben.
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
#### <a name="parameters"></a>Parameter
* error Ein Fehler des Typs [Error](#classmip_1_1_error), der während des Ladens aufgetreten ist 
* context Derselbe Kontext, der an [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) übergeben wurde. Eine Anwendung kann beliebige Kontexttypen (z.B. std::promise, std:: Function usw.) an [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) übergeben, und derselbe Kontext wird an [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) oder [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291) übergeben.