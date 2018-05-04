# <a name="class-mippolicyengine"></a>mip::PolicyEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings & GetSettings public const std::vector< std::shared_ptr< Label > > & ListSensitivityLabels | Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.
public std::shared_ptr< ContentLabel > GetSensitivityLabelExecutionState & state) | Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.
public std::shared_ptr< Label > GetDefaultSensitivityLabel | Ruft die Standardvertraulichkeitsbezeichnung ab.
public std::vector< std::shared_ptr< Action > > ComputeActionsExecutionState & state) | Führt die Regeln in der Engine basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.
## <a name="members"></a>Member
### <a name="settings"></a>Einstellung
Ruft die [Einstellungen](#classmip_1_1_policy_engine_1_1_settings) der Richtlinien-Engine ab.
#### <a name="returns"></a>Rückgabe
Die Einstellungen der Richtlinien-Engine. 
**Weitere Informationen finden Sie unter:** [mip::PolicyEngine::Settings](#classmip_1_1_policy_engine_1_1_settings)
### <a name="label"></a>Label
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.
#### <a name="returns"></a>Rückgabe
Eine Liste der Vertraulichkeitsbezeichnungen.
### <a name="contentlabel"></a>ContentLabel
Ruft die Vertraulichkeitsbezeichnung aus dem vorhandenen Inhalt ab.
Erforderliche Informationen zum Abrufen der Bezeichnung werden mithilfe des angegebenen Ausführungsstatus abgerufen. 
#### <a name="parameters"></a>Parameter
* state 
#### <a name="returns"></a>Rückgabe
Ein Inhaltsbezeichnungsobjekt, das die Vertraulichkeitsbezeichnung sowie zusätzliche Informationen enthält. Wird bei Nichtvorhandensein leer zurückgegeben. 
**Weitere Informationen finden Sie unter:** [mip::ContentLabel](#classmip_1_1_content_label).
### <a name="label"></a>Label
Ruft die Standardvertraulichkeitsbezeichnung ab.
#### <a name="returns"></a>Rückgabe
Die Standardvertraulichkeitsbezeichnung, sofern vorhanden. Wenn keine Standardbezeichnung festgelegt ist, wird „nullptr“ zurückgegeben.
### <a name="action"></a>Aktion
Führt die Regeln in der Engine basierend auf dem angegebenen Status aus und gibt die Liste der auszuführenden Aktionen zurück.
#### <a name="parameters"></a>Parameter
* state: der aktuelle Ausführungsstatus des Inhalts, für den die Regeln ausgeführt werden. 
#### <a name="returns"></a>Rückgabe
Eine Liste der Aktionen, die auf den Inhalt angewendet werden sollten.