# <a name="class-mipconsentresult"></a>mip::ConsentResult-Klasse 
Beschreibt das Ergebnis der Zustimmungsanforderung nach der Benutzerinteraktion.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public inline ConsentResult public inline bool Accepted | Ruft ab, ob der Benutzer der Aktion zugestimmt hat.
public inline bool ShowAgain | Ruft ab, ob für künftige Anforderungen eine explizite Zustimmung erforderlich ist.
public inline const std::string & UserId | Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wurde.
## <a name="members"></a>Member
### <a name="consentresult"></a>ConsentResult
[ConsentResult](#classmip_1_1_consent_result)-Konstruktor.
#### <a name="parameters"></a>Parameter
* accepted: Gibt an, ob der Benutzer der Aktion zugestimmt hat 
* showAgain: Gibt an, ob für künftige Aktionsanforderungen eine explizite Zustimmung erforderlich ist 
* userId: Benutzer (E-Mail-Adresse), von dem eine Zustimmung angefordert wurde
### <a name="accepted"></a>Accepted
Ruft ab, ob der Benutzer der Aktion zugestimmt hat.
#### <a name="returns"></a>Rückgabe
Ruft ab, ob der Benutzer der Aktion zugestimmt hat
### <a name="showagain"></a>ShowAgain
Ruft ab, ob für künftige Aktionsanforderungen eine explizite Zustimmung erforderlich ist.
#### <a name="returns"></a>Rückgabe
Unabhängig davon, ob für künftige Anforderungen eine explizite Zustimmung erforderlich ist: Wenn dies zutrifft, speichert das SDK das Ergebnis dieser Zustimmung und fordert die Clientanwendung in Zukunft nicht zur Zustimmung auf.
### <a name="userid"></a>UserId
Ruft den Benutzer (E-Mail-Adresse) ab, von dem eine Zustimmung angefordert wurde.
#### <a name="returns"></a>Rückgabe
Benutzer, von dem eine Zustimmung angefordert wurde