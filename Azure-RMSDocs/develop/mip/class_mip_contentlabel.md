# <a name="class-mipcontentlabel"></a>mip::ContentLabel-Klasse 
Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts gilt, in der Regel für ein Dokument.
Außerdem enthält sie Eigenschaften für eine bestimmte angewendete Bezeichnung.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string & GetCreationTime | Ruft die Erstellungszeit der Bezeichnung ab
public AssignmentMethod GetAssignmentMethod | Ruft die Zuweisungsmethode der Bezeichnung ab
public std::shared_ptr< Label > GetLabel | Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
## <a name="members"></a>Member
### <a name="getcreationtime"></a>GetCreationTime
Ruft die Erstellungszeit der Bezeichnung ab
#### <a name="returns"></a>Rückgabe
Die Erstellungszeit als GMT-Zeichenfolge
### <a name="getassignmentmethod"></a>GetAssignmentMethod
Ruft die Zuweisungsmethode der Bezeichnung ab
#### <a name="returns"></a>Rückgabe
AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
**Siehe auch:** mip::AssignmentMethod
### <a name="label"></a>Label
Ruft die tatsächliche Objektbezeichnung ab, die auf den Inhalt angewendet wird
#### <a name="returns"></a>Rückgabe
Die Objektbezeichnung, die auf den Inhalt angewendet wird. 
**Weitere Informationen finden Sie unter:** [mip::Label](#classmip_1_1_label)