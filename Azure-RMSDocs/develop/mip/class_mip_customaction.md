# <a name="class-mipcustomaction"></a>mip::CustomAction-Klasse 
[CustomAction](#classmip_1_1_custom_action) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector< std::pair< std::string, std::string > > & GetProperties | Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
public ActionType GetType
## <a name="members"></a>Member
### <a name="getproperties"></a>GetProperties
Ruft die Schlüssel-Wert-Paar-Liste der Eigenschaften ab
#### <a name="returns"></a>Rückgabe
Eine Schlüssel-Wert-Paar-Liste
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](#classmip_1_1_action) ab.
#### <a name="returns"></a>Rückgabe
ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.