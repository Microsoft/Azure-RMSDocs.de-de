# <a name="class-mipuserrights"></a>mip::UserRights-Klasse 
Stellt eine Gruppe von Benutzern und die ihr zugeordneten Berechtigungen dar
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public UserRights(const UserList& users, const RightList& rights)  |  [UserRights](class_mip_userrights.md)-Konstruktor
 public const UserList& Users() const  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
 public const RightList& Rights() const  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userrights"></a>UserRights
[UserRights](class_mip_userrights.md)-Konstruktor

Parameter:  
* **users**: Gruppe von Benutzern, die alle über die gleichen Berechtigungen verfügen 


* **rights**: Berechtigungen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="userlist"></a>UserList
Ruft Benutzer ab, denen Berechtigungen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Berechtigungen zugeordnet sind
  
### <a name="rightlist"></a>RightList
Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Berechtigungen, die einer Gruppe von Benutzern zugeordnet sind