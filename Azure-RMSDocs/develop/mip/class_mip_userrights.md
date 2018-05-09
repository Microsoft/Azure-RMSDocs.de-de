# <a name="class-mipuserrights"></a>mip::UserRights-Klasse 
Stellt eine Gruppe von Benutzern und die ihr zugeordneten Berechtigungen dar
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline UserRights(const UserList& users, const RightList& rights)  |  [UserRights](#classmip_1_1_user_rights)-Konstruktor
public inline const UserList& Users() const  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
public inline const RightList& Rights() const  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userrights"></a>UserRights
[UserRights](#classmip_1_1_user_rights)-Konstruktor
  
#### <a name="parameters"></a>Parameter
* users Gruppe von Benutzern, die alle über die gleichen Berechtigungen verfügen 
* rights: Berechtigungen, die allen Benutzern einer Gruppe zugeordnet sind
  
### <a name="userlist"></a>UserList
Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
  
#### <a name="returns"></a>Rückgabe
Benutzer, denen Berechtigungen zugeordnet sind
  
### <a name="rightlist"></a>RightList
Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
#### <a name="returns"></a>Rückgabe
Die Berechtigungen, die einer Gruppe von Benutzern zugeordnet sind