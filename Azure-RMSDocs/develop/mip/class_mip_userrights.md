# <a name="class-mipuserrights"></a>mip::UserRights-Klasse 
Stellt eine Gruppe von Benutzern und die ihr zugeordneten Berechtigungen dar
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public UserRights(const std::vector<std::string>& users, const std::vector<std::string>& rights)  |  [UserRights](class_mip_userrights.md)-Konstruktor
public const std::vector<std::string>& Users() const  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
public const std::vector<std::string>& Rights() const  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userrights"></a>UserRights
[UserRights](class_mip_userrights.md)-Konstruktor

Parameter:  
* **users**: Gruppe von Benutzern, die alle über die gleichen Berechtigungen verfügen 


* **rights**: Berechtigungen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="users"></a>Users
Ruft Benutzer ab, denen Berechtigungen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Berechtigungen zugeordnet sind
  
### <a name="rights"></a>Rechte
Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Berechtigungen, die einer Gruppe von Benutzern zugeordnet sind