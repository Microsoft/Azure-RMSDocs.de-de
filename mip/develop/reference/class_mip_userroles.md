# <a name="class-mipuserroles"></a>mip::UserRoles-Klasse 
Stellt eine Gruppe von Benutzern und die ihr zugeordneten Rollen dar
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public UserRoles(const std::vector<std::string>& users, const std::vector<std::string>& roles)  |  [UserRoles](class_mip_userroles.md)-Konstruktor
public const std::vector<std::string>& Users() const  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
public const std::vector<std::string>& Roles() const  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userroles"></a>UserRoles
[UserRoles](class_mip_userroles.md)-Konstruktor

Parameter:  
* **users**: Gruppe von Benutzern, in der allen Mitgliedern die gleichen Rollen zugeordnet sind 


* **roles**: Rollen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="users"></a>Users
Ruft Benutzer ab, denen Rollen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Rollen zugeordnet sind
  
### <a name="roles"></a>Rollen
Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Rollen, die einer Gruppe von Benutzern zugeordnet sind