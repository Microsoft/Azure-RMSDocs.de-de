# <a name="class-mipprofileobserver"></a>mip::Profile::Observer-Klasse 
[Observer](class_mip_profile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Wenn ein Fehlerereignis des Typs „*Error“ auftritt, enthält das Fehlerobjekt die Klasse [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<Profile>& profile, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void OnListEnginesError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
public virtual void OnUnloadEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public virtual void OnUnloadEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public virtual void OnAddEngineSuccess(const std::shared_ptr<PolicyEngine>& engine, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void OnAddEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void OnDeleteEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
 public virtual void OnPolicyChanged(const std::string& engineId)  |  Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
  
## <a name="members"></a>Member
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde

Parameter:  
* **profile**: Das aktuelle Profil, über das der Vorgang gestartet wird. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist

Parameter:  
* **error**: Fehler, durch den der Ladevorgang fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.

Parameter:  
* **engineIds**: Liste der verfügbaren Engine-IDs. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onlistengineserror"></a>OnListEnginesError
Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.

Parameter:  
* **error**: Fehler, durch den das Auflisten der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.

Parameter:  
* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Fehler, durch den das Entladen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Fehler, durch den das Hinzufügen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.

Parameter:  
* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.

Parameter:  
* **error**: Fehler, durch den das Löschen der Engine fehlgeschlagen ist. 


* **context**: Der an den Vorgang übergebene Kontext.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.

Parameter:  
* **engineId**: Die Engine 


Zum Laden der neuen Richtlinie muss AddEngineAsync erneut mit der angegebenen Engine-ID aufgerufen werden.