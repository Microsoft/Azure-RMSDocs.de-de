# <a name="class-mipgetuserpolicyresult"></a>mip::GetUserPolicyResult-Klasse 
Beschreibt die Ergebnisse einer Anforderung zur Benutzerrichtlinienanschaffung.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public GetUserPolicyResultStatus GetResultStatus | Ruft den Status einer Anforderung zur Richtlinienanschaffung ab.
public std::shared_ptr< std::string > GetReferrer | Ruft die Referreradresse der Richtlinie ab.
public std::shared_ptr< UserPolicy > GetPolicy
## <a name="members"></a>Member
### <a name="getuserpolicyresultstatus"></a>GetUserPolicyResultStatus
Ruft den Status einer Anforderung zur Richtlinienanschaffung ab.
#### <a name="returns"></a>Rückgabe
Status der Anforderung zur Richtlinienanschaffung
### <a name="getreferrer"></a>GetReferrer
Ruft die Referreradresse der Richtlinie ab.
#### <a name="returns"></a>Rückgabe
Referreradresse der Richtlinie: Der Referrer ist ein URI, der dem Benutzer angezeigt werden kann, nachdem die Richtlinienanschaffung fehlgeschlagen ist. Er enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
### <a name="userpolicy"></a>UserPolicy
Ruft eine [UserPolicy](#classmip_1_1_user_policy)-Instanz ab.
#### <a name="returns"></a>Rückgabe
Eine [UserPolicy](#classmip_1_1_user_policy)-Instanz, wenn die Anschaffung erfolgreich war; andernfalls wird „nullptr“ zurückgegeben