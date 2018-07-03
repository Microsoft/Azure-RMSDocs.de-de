# <a name="class-mipremovewatermarkaction"></a>mip::RemoveWatermarkAction-Klasse 
Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt werden soll
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector<std::string>& GetUIElementNames()  |  Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementnames"></a>GetUIElementNames
Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte

  
**Rückgabe**: Eine Liste mit Namen der Benutzeroberflächenelemente.
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.