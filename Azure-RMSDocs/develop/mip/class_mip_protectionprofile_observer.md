# <a name="class-mipprotectionprofileobserver"></a>mip::ProtectionProfile::Observer-Klasse 
Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md) empfängt.
Diese Schnittstelle muss von Anwendungen mithilfe des Schutz-SDK implementiert werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<ProtectionProfile>& profile, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void OnListEnginesError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.
public virtual void OnAddEngineSuccess(const std::shared_ptr<ProtectionEngine>& engine, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void OnAddEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void OnDeleteEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Ein Verweis auf das neu erstellte [ProtectionProfile](class_mip_protectionprofile.md)


* **context**: Der gleiche Kontext, der an „ProtectionProfile::LoadAsync“ übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“, „std::function“ usw.) an „ProtectionProfile::LoadAsync“ übergeben, und der gleiche Kontext wird unverändert an [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure) weitergeleitet.
  
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **error**: Ein [Fehler](class_mip_error.md), der während des Ladens aufgetreten ist 


* **context**: Der gleiche Kontext, der an „ProtectionProfile::LoadAsync“ übergeben wurde.


Eine Anwendung kann einen beliebigen Typ des Kontexts (z.B. „std::promise“, „std::function“ usw.) an „ProtectionProfile::LoadAsync“ übergeben, und der gleiche Kontext wird unverändert an [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) oder [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure) weitergeleitet.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onlistengineserror"></a>OnListEnginesError
Wird aufgerufen, wenn das Auflisten der Engines zu einem Fehler geführt hat.

Parameter:  
* **error**: Fehler, durch den das Auflisten der Engine nicht erfolgreich ist 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wird aufgerufen, wenn das Löschen einer Engine zu einem Fehler geführt hat.

Parameter:  
* **error**: Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.

