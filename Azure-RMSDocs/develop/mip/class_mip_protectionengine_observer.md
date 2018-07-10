# <a name="class-mipprotectionengineobserver"></a>mip::ProtectionEngine::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionEngine](class_mip_protectionengine.md) empfängt.
Diese Schnittstelle muss von Anwendungen mithilfe des Schutz-SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnGetTemplatesSuccess(const std::shared_ptr<std::vector<std::string>>& templateIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.
public virtual void OnGetTemplatesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.
  
## <a name="members"></a>Member
  
### <a name="ongettemplatessuccess"></a>OnGetTemplatesSuccess
Wird aufgerufen, wenn Vorlagen erfolgreich abgerufen wurden.

Parameter:  
* **templateIds**: Verweis auf die Liste der abzurufenden Vorlagen 


* **context**: Der gleiche Kontext, der an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z. B. „std::promise“, „std::function“ usw.) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben, und der gleiche Kontext wird [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure) übergeben.
  
### <a name="ongettemplatesfailure"></a>OnGetTemplatesFailure
Wird aufgerufen, wenn beim Abrufen von Vorlagen ein Fehler aufgetreten ist.

Parameter:  
* **error**: Ein [Fehler](class_mip_error.md), der beim Abrufen von Vorlagen aufgetreten ist 


* **context**: Der gleiche Kontext, der an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z. B. „std::promise“, „std::function“ usw.) an [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) übergeben, und der gleiche Kontext wird [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure) übergeben.