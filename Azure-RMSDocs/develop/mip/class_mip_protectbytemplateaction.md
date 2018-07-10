# <a name="class-mipprotectbytemplateaction"></a>mip::ProtectByTemplateAction-Klasse 
Eine Aktionsklasse, die angibt, dass Schutz nach Vorlage zum Dokument hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetTemplateId() const  |  Ruft die Schutzvorlagen-ID ab, die mit der Aktion verknüpft ist.
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="gettemplateid"></a>GetTemplateId
Ruft die Schutzvorlagen-ID ab, die mit der Aktion verknüpft ist.

  
**Rückgabe**: eine Zeichenfolge mit der Schutzvorlagen-ID
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.