# <a name="class-mipmetadataaction"></a>mip::MetadataAction-Klasse 
Eine [Aktion](#classmip_1_1_action), die angibt, welche Metainformationen dem Inhalt hinzugefügt werden sollen
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector<std::string>& GetMetadataToRemove() const  |  Ruft die Liste der Namen der Metadaten ab, die aus dem Inhalt entfernt werden müssen
public const std::vector<std::pair<std::string, std::string>>& GetMetadataToAdd() const  |  Ruft die Liste der Metadaten als Schlüssel-Wert-Paare ab. Die Metadaten müssen zu den Metadaten des Inhalts hinzugefügt werden.
public ActionType GetType() const  |  Ruft den Typ der [Aktion](#classmip_1_1_action) ab.
  
## <a name="members"></a>Member
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Ruft die Liste der Namen der Metadaten ab, die aus dem Inhalt entfernt werden müssen
  
#### <a name="returns"></a>Rückgabe
Ein Vektor von Zeichenfolgen, die entfernt werden sollen. Das Entfernen der Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Ruft die Liste der Metadaten als Schlüssel-Wert-Paare ab. Die Metadaten müssen zu den Metadaten des Inhalts hinzugefügt werden.
  
#### <a name="returns"></a>Rückgabe
const std::vector<std::pair<std::string, std::string>>& Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](#classmip_1_1_action) ab.
  
#### <a name="returns"></a>Rückgabe
ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.