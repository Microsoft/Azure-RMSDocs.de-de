# <a name="class-mipconsentcallback"></a>mip::ConsentCallback-Klasse 
Eine Schnittstelle für Benachrichtigungen über Zustimmungsanforderungen.
Dieser Rückruf wird von einer Clientanwendung implementiert, damit dem Benutzer zum richtigen Zeitpunkt eine Zustimmungsbenachrichtigung angezeigt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public ConsentList Consents(ConsentList& consents)  |  Wird aufgerufen, wenn für das SDK die Benutzerzustimmung zu einem Vorgang erforderlich ist
  
## <a name="members"></a>Member
  
### <a name="consentlist"></a>ConsentList
Wird aufgerufen, wenn für das SDK die Benutzerzustimmung zu einem Vorgang erforderlich ist

Parameter:  
* **consents**: Die Liste der Zustimmungen, die vom SDK angefordert werden



  
**Rückgabe**: [Consent](class_mip_consent.md)-Ergebnisse. Wenn Zustimmungen vom SDK angefordert werden, sollte die Clientanwendung die Zustimmung vom Benutzer erhalten. Die Ergebnisse der jeweiligen Zustimmung sollten über [Consent::Result(const ConsentResult&)](class_mip_consent.md#result) gespeichert werden. Außerdem sollte eine Liste der verarbeiteten Zustimmungen zurückgegeben werden.