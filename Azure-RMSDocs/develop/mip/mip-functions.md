# <a name="functions"></a>Funktionen

 Funktionen (Bereich)                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetCustomSettingExportPolicyFileName()       |  Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.
public const std::string& GetCustomSettingPolicyDataFile()       |  Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.
public const std::string& GetCustomSettingPolicyDataName()       |  Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.
**mip-Funktionen** |
public std::shared_ptr<mip::Stream> CreateStreamFromBuffer(uint8_t* buffer, const int64_t size)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::iostream>& stdIOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::istream>& stdIStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::ostream>& stdOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.
**mip::Rights functions**|
public std::string AuditedExtract()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.
public std::string Comment()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.
public std::vector<std::string> CommonRights()       |  Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.
public std::string Edit()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.
public std::vector<std::string> EditableDocumentRights()       |  Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.
public std::vector<std::string> EmailRights()       |  Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.
public std::string Export()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.
public std::string Extract()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.
public std::string Forward()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.
public std::string Owner()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.
public std::string Print()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.
public std::string Reply()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.
public std::string ReplyAll()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.
public std::string View()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.
**mip::Roles functions**|
public std::string Author()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.
public std::string CoOwner()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.
public std::string Reviewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.
public std::string Viewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

  
## <a name="enumeration-details"></a>Details zu Enumerationen
  
## <a name="functions-common"></a>Funktionen (allgemein)

### <a name="getcustomsettingpolicydataname"></a>GetCustomSettingPolicyDataName
Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingexportpolicyfilename"></a>GetCustomSettingExportPolicyFileName
Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingpolicydatafile"></a>GetCustomSettingPolicyDataFile
Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel

## <a name="functions-mip"></a>Funktionen (mip)

### <a name="mipstream-istream"></a>mip::Stream (istream)

Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.

Parameter:  

* **stdIStream**: Schützt std::istream
  
**Rückgabe**: ein [Stream](class_mip_stream.md), der einen std::istream umschließt
  
### <a name="mipstream-ostream"></a>mip::Stream (ostream)

Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.

Parameter:  
* **stdOStream**: Schützt std::ostream

  
**Rückgabe**: ein [Stream](class_mip_stream.md), der einen std::ostream umschließt
  
### <a name="mipstream-iostream"></a>mip::Stream (iostream)

Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.

Parameter:  
* **stdIOStream**: Schützt std::iostream
  
**Rückgabe**: ein [Stream](class_mip_stream.md), der einen std::iostream umschließt
  
### <a name="mipstream-buffer"></a>mip::Stream (buffer)

Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.

Parameter:  
* **buffer**: Zeiger auf einen Puffer

**Rückgabe**: Größe des Puffers
  
## <a name="functions-miprights"></a>Funktionen (mip::rights)

### <a name="auditedextract"></a>AuditedExtract
Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „audited extract“
  
### <a name="comment"></a>Anmerkungen
Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „comment“
  
### <a name="commonrights"></a>CommonRights
Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für alle Szenarien gelten

### <a name="edit"></a>Bearbeiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „edit“
  
### <a name="editabledocumentrights"></a>EditableDocumentRights
Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für Dokumente gelten
  
### <a name="emailrights"></a>EmailRights
Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für E-Mails gelten
  
### <a name="export"></a>Exportieren
Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „export“
  
### <a name="extract"></a>Extrahieren
Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „extract“
  

### <a name="forward"></a>Weiterleiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „forward“
  
### <a name="owner"></a>Besitzer
Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „owner“
  
### <a name="print"></a>Drucken
Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „print“
  
### <a name="reply"></a>Antworten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply“
  
### <a name="replyall"></a>Allen antworten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply all“
  
### <a name="view"></a>Anzeigen
Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „view“
  
## <a name="functions-miproles"></a>Funktionen (mip::roles)

### <a name="author"></a>Autor
Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „author“. Ein Autor kann Inhalte anzeigen, bearbeiten, kopieren und drucken.
  
### <a name="coowner"></a>CoOwner
Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „Mitbesitzer“. Ein Mitbesitzer verfügt über alle Berechtigungen.

### <a name="reviewer"></a>Prüfer
Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „reviewer“. Ein Prüfer kann Inhalte anzeigen und bearbeiten. Ein Prüfer kann die Inhalte nicht kopieren oder drucken.

### <a name="viewer"></a>Anzeigen
Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „viewer“. Benutzer mit der Rolle „viewer“ können Inhalte nur anzeigen. Sie können die Inhalte nicht bearbeiten, kopieren oder drucken.
  
  
