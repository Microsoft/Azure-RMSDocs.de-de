# <a name="class-mipuserroles"></a>mip::UserRoles-Klasse 
Stellt eine Gruppe von Benutzern und die ihr zugeordneten Rollen dar
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public MIP_EXPORT UserRoles(const UserList& users, const RoleList& roles)  |  [UserRoles](#classmip_1_1_user_roles)-Konstruktor
public inline const UserList& Users() const  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
public inline const RoleList& Roles() const  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userroles"></a>UserRoles
[UserRoles](#classmip_1_1_user_roles)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* users Gruppe von Benutzern, in der allen Mitgliedern die gleichen Rollen zugeordnet sind 
* roles: [Rollen](#classmip_1_1_roles), die allen Benutzern einer Gruppe zugeordnet sind
  
### <a name="userlist"></a>UserList
Ruft Benutzer ab, denen Rollen zugeordnet sind
  
#### <a name="returns"></a>Rückgabe
Benutzer, denen Rollen zugeordnet sind
  
### <a name="rolelist"></a>RoleList
Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
#### <a name="returns"></a>Rückgabe
[Rollen](#classmip_1_1_roles), die einer Gruppe von Benutzern zugeordnet sind