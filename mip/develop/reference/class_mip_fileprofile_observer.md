# <a name="class-mipfileprofileobserver"></a>mip::FileProfile::Observer-Klasse 
[Observer](class_mip_fileprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Wenn ein Fehlerereignis des Typs „*Error“ auftritt, enthält das Fehlerobjekt die Klasse [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public virtual ~Observer()  | _Noch nicht dokumentiert._
public virtual void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public virtual void OnListEnginesError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
public virtual void OnUnloadEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public virtual void OnUnloadEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public virtual void OnAddEngineSuccess(const std::shared_ptr<mip::FileEngine>& engine, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public virtual void OnAddEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public virtual void OnDeleteEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
 public virtual void OnPolicyChanged(const std::string& engineId)  |  Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
 geschützte Observer()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="observer"></a>~Observer
_Noch nicht dokumentiert._

  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde
  
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn beim Laden eines Profils ein Fehler aufgetreten ist
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
  
### <a name="onlistengineserror"></a>OnListEnginesError
Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
  
### <a name="observer"></a>Beobachter
_Noch nicht dokumentiert._
