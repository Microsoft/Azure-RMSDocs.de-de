# <a name="class-mipprotectionprofileobserver"></a>mip::ProtectionProfile::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md) empfängt.
Diese Schnittstelle muss von Anwendungen mithilfe des Schutz-SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<ProtectionProfile>& profile, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Ein Verweis auf das neu erstellte [ProtectionProfile](class_mip_protectionprofile.md)


* **context**: Der gleiche Kontext, der an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) übergeben wurde


Eine Anwendung kann einen beliebigen Typ des Kontexts (z. B. „std::promise“, „std::function“ usw.) an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) übergeben und der gleiche Kontext wird [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure) übergeben
  
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **error**: Ein Fehler des Typs [Error](class_mip_error.md), der während des Ladens aufgetreten ist 


* **context**: Der gleiche Kontext, der an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) übergeben wurde


Eine Anwendung kann einen beliebigen Typ des Kontexts (z. B. „std::promise“, „std::function“ usw.) an [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) übergeben und der gleiche Kontext wird [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure) übergeben