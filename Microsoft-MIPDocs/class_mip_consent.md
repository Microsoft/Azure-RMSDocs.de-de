# <a name="class-mipconsent"></a>mip::Consent-Klasse 
Stellt die Zustimmung/Ablehnung eines Benutzers zur Zulassung einer Aktion dar.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const mip::ConsentResult & Result | Ruft das Ergebnis einer Zustimmungsanforderung ab.
public void ResultConsentResult & value) | Legt das Ergebnis einer Zustimmungsanforderung fest.
public mip::ConsentType Type | Ruft den Typ der Zustimmung ab.
public const std::vector< std::string > Urls | Ruft die URLs der Zustimmungsanforderung ab.
public const std::string User | Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wird.
public const std::string Domain | Ruft die Domäne ab, die dem Benutzer zugeordnet ist, von dem eine Zustimmung angefordert wird.
## <a name="members"></a>Member
### <a name="mipconsentresult"></a>mip::ConsentResult
Ruft das Ergebnis einer Zustimmungsanforderung ab.
#### <a name="returns"></a>Rückgabe
Das Ergebnis der Zustimmungsanforderung
### <a name="result"></a>Result
Legt das Ergebnis einer Zustimmungsanforderung fest.
#### <a name="parameters"></a>Parameter
* value: das Ergebnis der Zustimmungsanforderung
### <a name="mipconsenttype"></a>mip::ConsentType
Ruft den Typ der Zustimmung ab.
#### <a name="returns"></a>Rückgabe
Der Typ der Zustimmung
### <a name="urls"></a>URLs
Ruft die URLs der Zustimmungsanforderung ab.
#### <a name="returns"></a>Rückgabe
Die URLs der Zustimmungsanforderung
### <a name="user"></a>Benutzer
Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wird.
#### <a name="returns"></a>Rückgabe
Der Benutzer, von dem eine Zustimmung angefordert wurde
### <a name="domain"></a>Domain
Ruft die Domäne ab, die dem Benutzer zugeordnet ist, von dem eine Zustimmung angefordert wird.
#### <a name="returns"></a>Rückgabe
Die Domäne, die dem Benutzer zugeordnet ist, von dem eine Zustimmung angefordert wird