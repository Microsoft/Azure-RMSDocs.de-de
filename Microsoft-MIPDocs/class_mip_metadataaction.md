# <a name="class-mipmetadataaction"></a>mip::MetadataAction-Klasse 
Ein [Aktion](#classmip_1_1_action) ist gemeint, die angibt, welche Metainformationen zu dem Inhalt hinzugefügt werden sollen.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector< std::string > & GetMetadataToRemove | Ruft die Liste der Namen der Metadaten ab, die vom Inhalt entfernt werden müssen.
public const std::vector< std::pair< std::string, std::string > > & GetMetadataToAdd | Ruft die Liste der Metadaten als Schlüssel-Wert-Paare ab. Die Metadaten müssen zu den Metadaten des Inhalts hinzugefügt werden.
public ActionType GetType
## <a name="members"></a>Member
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Ruft die Liste der Namen der Metadaten ab, die vom Inhalt entfernt werden müssen.
#### <a name="returns"></a>Rückgabe
eines Vektors von Zeichenfolgen, die entfernt werden müssen. der Information, dass das Entfernen der Metadaten vor dem Hinzufügen von Metadaten erfolgen sollte.
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Ruft die Liste der Metadaten als Schlüssel-Wert-Paare ab. Die Metadaten müssen zu den Metadaten des Inhalts hinzugefügt werden.
#### <a name="returns"></a>Rückgabe
const std::vector<std::pair<std::string, std::string>>& Das Entfernen von Metadaten sollte erfolgen, bevor Metadaten hinzugefügt werden.
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](#classmip_1_1_action) ab.
#### <a name="returns"></a>Rückgabe
von ActionType: der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.