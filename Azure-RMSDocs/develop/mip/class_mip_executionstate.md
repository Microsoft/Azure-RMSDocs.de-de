# <a name="class-mipexecutionstate"></a>mip::ExecutionState-Klasse 
Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
Clients sollten die Methoden nur aufrufen, um den erforderlichen Status abzurufen. Daher sollten Clients diese Schnittstelle aus Effizienzgründen implementieren, damit der entsprechende Status dynamisch und nicht im Voraus berechnet wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public std::string GetNewLabelId() const  |  Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.
 public bool IsDowngradeJustified() const  |  Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.
 public AssignmentMethod GetNewLabelAssignmentMethod() const  |  Ruft die Zuweisungsmethode für die neue Bezeichnung ab.
public std::vector<std::pair<std::string, std::string>> GetContentMetadata(const std::vector<std::string>& names, const std::vector<std::string>& namePrefixes) const  |  Ruft die Metadatenelemente aus dem Inhalt ab.
 public std::string GetTemplateId() const  |  Ruft die Schutzvorlagen-ID für den Rights Management Service ab.
 public ContentFormat GetContentFormat() const  |  Ruft das Inhaltsformat ab.
 public const ActionType GetSupportedActions() const  |  Gibt eine Liste von Aktionen zurück, die von der Anwendung unterstützt werden. Sämtliche Aktionstypen werden unter [mip/upe/action.h](#action) aufgeführt.
  
## <a name="members"></a>Member
  
### <a name="getnewlabelid"></a>GetNewLabelId
Ruft die ID der Vertraulichkeitsbezeichnung ab, die auf das Dokument angewendet werden sollte.

  
**Rückgabe**: Die ID der Vertraulichkeitsbezeichnung, die auf den Inhalt angewendet werden soll, sofern vorhanden. Wenn der Inhalt leer ist, kann die Bezeichnung entfernt werden.
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Bei der Implementierung sollte übergeben werden, ob eine vorhandene Bezeichnung herabgestuft wurde.

  
**Rückgabe**: TRUE bei bereits erfolgter Ausrichtung; FALSE bei noch nicht erfolgter Ausrichtung. 
**Weitere Informationen finden Sie unter:** [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
Ruft die Zuweisungsmethode für die neue Bezeichnung ab.

  
**Rückgabe**: Zuweisungsmethode STANDARD, PRIVILEGED, AUTO. 
**Weitere Informationen finden Sie unter:** mip::AssignmentMethod
  
### <a name="getcontentmetadata"></a>GetContentMetadata
Ruft die Metadatenelemente aus dem Inhalt ab.

  
**Rückgabe**: Ein Vektor von Schlüssel-Wert-Paaren, die die auf den Inhalt angewendeten Metadaten darstellen. Jedes Metadatenelement setzt sich aus einem Name-Wert-Paar zusammen.
  
### <a name="gettemplateid"></a>GetTemplateId
Ruft die Schutzvorlagen-ID für den Rights Management Service ab.

  
**Rückgabe**: Die Schutzvorlagen-ID für den Rights Management Service, sofern vorhanden; andernfalls wird in einem GUID-Format ohne Klammern eine leere Zeichenfolge zurückgegeben.
  
### <a name="getcontentformat"></a>GetContentFormat
Ruft das Inhaltsformat ab.

  
**Rückgabe**: DEFAULT, EMAIL; **Weitere Informationen**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Gibt eine Liste von Aktionen zurück, die von der Anwendung unterstützt werden. Sämtliche Aktionstypen werden unter [mip/upe/action.h](#action) aufgeführt.