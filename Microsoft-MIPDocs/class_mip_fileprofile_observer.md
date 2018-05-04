# <a name="class-mipfileprofileobserver"></a>mip::FileProfile::Observer-Klasse 
[Beobachter](#classmip_1_1_file_profile_1_1_observer)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
Wenn ein *Fehlerereignis auftritt, enthält das Fehlerobjekt die Klasse [mip::Error](#classmip_1_1_error). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline virtual  ~Observer | 
public inline virtual void OnLoadSuccessmip::FileProfile > & profile,const std::shared_ptr< void > & context) | Wird aufgerufen, wenn das Profil erfolgreich geladen wurde.
public inline virtual void OnLoadFailure | Wird aufgerufen, wenn das Laden eines Profils einen Fehler verursacht hat.
public inline virtual void OnListEnginesSuccess | Wird aufgerufen, wenn die Liste der Engines erfolgreich generiert wurde.
public inline virtual void OnListEnginesError | Wird aufgerufen, wenn das Auflisten der Engines einen Fehler verursacht hat.
public inline virtual void OnUnloadEngineSuccess | Wird aufgerufen, wenn eine Engine erfolgreich entladen wurde.
public inline virtual void OnUnloadEngineError | Wird aufgerufen, wenn das Entladen einer Engine einen Fehler verursacht hat.
public inline virtual void OnAddEngineSuccessmip::FileEngine > & engine,const std::shared_ptr< void > & context) | Wird aufgerufen, wenn eine neue Engine erfolgreich hinzugefügt wurde.
public inline virtual void OnAddEngineError | Wird aufgerufen, wenn das Hinzufügen einer neuen Engine einen Fehler verursacht hat.
public inline virtual void OnDeleteEngineSuccess | Wird aufgerufen, wenn eine Engine erfolgreich gelöscht wurde.
public inline virtual void OnDeleteEngineError | Wird aufgerufen, wenn das Löschen einer Engine einen Fehler verursacht hat.
public inline virtual void OnPolicyChanged | Wird aufgerufen, wenn die Richtlinie für die Engine mit der angegebenen ID geändert wurde.
protected inline  Observer | 
## <a name="members"></a>Member
### <a name="observer"></a>~Observer
### <a name="onloadsuccess"></a>OnLoadSuccess
Wird aufgerufen, wenn das Profil erfolgreich geladen wurde.
### <a name="onloadfailure"></a>OnLoadFailure
Wird aufgerufen, wenn das Laden eines Profils einen Fehler verursacht hat.
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