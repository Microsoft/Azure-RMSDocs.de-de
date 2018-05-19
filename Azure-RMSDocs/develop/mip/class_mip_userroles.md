# <a name="class-mipuserroles"></a>mip::UserRoles-Klasse 
Stellt eine Gruppe von Benutzern und die ihr zugeordneten Rollen dar
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public MIP_EXPORT UserRoles(const UserList& users, const RoleList& roles)  |  [UserRoles](class_mip_userroles.md)-Konstruktor
 public const UserList& Users() const  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
 public const RoleList& Roles() const  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userroles"></a>UserRoles
[UserRoles](class_mip_userroles.md)-Konstruktor

Parameter:  
* **users**: Gruppe von Benutzern, in der allen Mitgliedern die gleichen Rollen zugeordnet sind 


* **roles**: [Rollen](class_mip_roles.md), die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="userlist"></a>UserList
Ruft Benutzer ab, denen Rollen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Rollen zugeordnet sind
  
### <a name="rolelist"></a>RoleList
Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: [Rollen](class_mip_roles.md), die einer Gruppe von Benutzern zugeordnet sind