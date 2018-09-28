# <a name="class-mipconsent"></a>mip::Consent-Klasse 
Stellt die Zustimmung bzw. Ablehnung eines Benutzers zur Zulassung einer Aktion dar.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const mip::ConsentResult& Result() const  |  Ruft das Ergebnis einer Zustimmungsanforderung ab.
 public void Result(const ConsentResult& value)  |  Legt das Ergebnis einer Zustimmungsanforderung fest.
 public mip::ConsentType Type() const  |  Ruft den Typ der Zustimmung ab.
public const std::vector<std::string> Urls() const  |  Ruft die URLs der Zustimmungsanforderung ab.
 public const std::string User() const  |  Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wird.
 public const std::string Domain() const  |  Ruft die Domäne ab, die dem Benutzer zugeordnet ist, von dem eine Zustimmung angefordert wird.
  
## <a name="members"></a>Member
  
### <a name="mipconsentresult"></a>mip::ConsentResult
Ruft das Ergebnis einer Zustimmungsanforderung ab.

  
**Rückgabe**: Ergebnis der Zustimmungsanforderung
  
### <a name="result"></a>Result
Legt das Ergebnis einer Zustimmungsanforderung fest.

Parameter:  
* **value**: Ergebnis der Zustimmungsanforderung


  
### <a name="mipconsenttype"></a>mip::ConsentType
Ruft den Typ der Zustimmung ab.

  
**Rückgabe**: Typ der Zustimmung
  
### <a name="urls"></a>URLs
Ruft die URLs der Zustimmungsanforderung ab.

  
**Rückgabe**: URLs der Zustimmungsanforderung
  
### <a name="user"></a>Benutzer
Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wird.

  
**Rückgabe**: Benutzer, von dem eine Zustimmung angefordert wird
  
### <a name="domain"></a>Domain
Ruft die Domäne ab, die dem Benutzer zugeordnet ist, von dem eine Zustimmung angefordert wird.

  
**Rückgabe**: Domäne, die dem Benutzer zugeordnet ist, von dem eine Zustimmung angefordert wird