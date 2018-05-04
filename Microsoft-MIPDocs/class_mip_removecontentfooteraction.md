# <a name="class-mipremovecontentfooteraction"></a>mip::RemoveContentFooterAction-Klasse 
Eine Aktionsklasse, mit der die Fußzeile mit Inhalt aus dem Dokument entfernt wird.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector< std::string > & GetUIElementNames | Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte
public ActionType GetType
## <a name="members"></a>Member
### <a name="getuielementnames"></a>GetUIElementNames
Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte
#### <a name="returns"></a>Rückgabe
Eine Liste mit Namen der Benutzeroberflächenelemente
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](#classmip_1_1_action) ab
#### <a name="returns"></a>Rückgabe
ActionType: der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann