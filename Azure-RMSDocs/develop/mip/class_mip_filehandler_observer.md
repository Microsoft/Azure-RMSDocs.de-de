# <a name="class-mipfilehandlerobserver"></a>mip::FileHandler::Observer-Klasse 
Die [Observer](class_mip_filehandler_observer.md)-Schnittstelle für Clients, mit der Benachrichtigungen für verknüpfte Ereignisse im Zusammenhang mit dem Dateihandler abgerufen werden.
Wenn ein Fehlerereignis des Typen „*Error“ auftritt, enthält das Fehlerobjekt eine Instanz der Klasse [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public virtual ~Observer()  | _Noch nicht dokumentiert._
public void OnGetLabelSuccess(const std::shared_ptr<ContentLabel>& label, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Bezeichnung erfolgreich (aus der Datei) abgerufen wird
public void OnGetLabelFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Abrufen der Bezeichnung (aus der Datei) ein Fehler auftritt
public void OnGetProtectionSuccess(const std::shared_ptr<UserPolicy>& userPolicy, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Schutzrichtlinie erfolgreich (aus der Datei) abgerufen wird
public void OnGetProtectionFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Abrufen der Schutzrichtlinie (aus der Datei) ein Fehler auftritt
public void OnCommitSuccess(bool commited, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
public void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt und diese nicht in der Datei übernommen werden
 geschützte Observer()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="observer"></a>~Observer
_Noch nicht dokumentiert._

  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Wird aufgerufen, wenn die Bezeichnung erfolgreich (aus der Datei) abgerufen wird
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Wird aufgerufen, wenn beim Abrufen der Bezeichnung (aus der Datei) ein Fehler auftritt
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Wird aufgerufen, wenn die Schutzrichtlinie erfolgreich (aus der Datei) abgerufen wird
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Wird aufgerufen, wenn beim Abrufen der Schutzrichtlinie (aus der Datei) ein Fehler auftritt
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
  
### <a name="oncommitfailure"></a>OnCommitFailure
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt und diese nicht in der Datei übernommen werden
  
### <a name="observer"></a>Beobachter
_Noch nicht dokumentiert._
