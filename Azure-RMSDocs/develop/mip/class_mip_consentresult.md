# <a name="class-mipconsentresult"></a>mip::ConsentResult-Klasse 
Beschreibt das Ergebnis der Zustimmungsanforderung nach der Benutzerinteraktion
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public ConsentResult(bool accepted, bool showAgain, const std::string& userId)  |  [ConsentResult](class_mip_consentresult.md)-Konstruktor
 public bool Accepted() const  |  Ruft ab, ob der Benutzer der Aktion zugestimmt hat
 public bool ShowAgain() const  |  Ruft ab, ob für künftige Aktionsanforderungen eine explizite Zustimmung erforderlich ist
 public const std::string& UserId() const  |  Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wurde
  
## <a name="members"></a>Member
  
### <a name="consentresult"></a>ConsentResult
[ConsentResult](class_mip_consentresult.md)-Konstruktor

Parameter:  
* **accepted**: Gibt an, ob der Benutzer der Aktion zugestimmt hat 


* **showAgain**: Gibt an, ob für künftige Aktionsanforderungen eine explizite Zustimmung erforderlich ist 


* **userId**: Benutzer (E-Mail-Adresse), von dem eine Zustimmung angefordert wurde


  
### <a name="accepted"></a>Accepted
Ruft ab, ob der Benutzer der Aktion zugestimmt hat

  
**Rückgabe**: Angabe, ob der Benutzer der Aktion zugestimmt hat
  
### <a name="showagain"></a>ShowAgain
Ruft ab, ob für künftige Aktionsanforderungen eine explizite Zustimmung erforderlich ist

  
**Rückgabe**: Unabhängig davon, ob für künftige Anforderungen eine explizite Zustimmung erforderlich ist: Wenn dies zutrifft, speichert das SDK das Ergebnis dieser Zustimmung und fordert die Clientanwendung in Zukunft nicht mehr zur Zustimmung auf.
  
### <a name="userid"></a>UserId
Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wurde

  
**Rückgabe**: Benutzer, von dem eine Zustimmung angefordert wurde