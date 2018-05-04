# <a name="class-mipaddcontentheaderaction"></a>mip::AddContentHeaderAction-Klasse 
Eine Aktionsklasse, mit der ein Inhaltsheader hinzugefügt wird.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string & GetUIElementName | Eine API, mit der das Element des Inhaltsheaders markiert wird.
public const std::string & GetText | Ruft den Text ab, der im Inhaltsheader enthalten sein soll
public const std::string & GetFontName | Ruft den Schriftartnamen ab, in der der Inhaltsheader angezeigt wird.
public int GetFontSize | Ruft den Schriftgrad ab, in der der Inhaltsheader angezeigt wird.
public const std::string & GetFontColor | Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.
public ContentMarkAlignment GetAlignment | Ruft die Ausrichtung des Headers ab.
public int GetMargin | Ruft den Rand des Headers im unteren Bereich ab.
public ActionType GetType
## <a name="members"></a>Member
### <a name="getuielementname"></a>GetUIElementName
Eine API, mit der das Element des Inhaltsheaders markiert wird.
#### <a name="returns"></a>Rückgabe
Der Name, der für das UI-Element verwendet werden sollte, das den Inhaltsheader enthält. Wenn der Inhaltsheader entfernt werden muss, wird der gleiche Name in [RemoveContentHeaderAction](#classmip_1_1_remove_content_header_action) zurückgegeben.
### <a name="gettext"></a>GetText
Ruft den Text ab, der im Inhaltsheader enthalten sein soll
#### <a name="returns"></a>Rückgabe
Der Text des Inhaltsheaders.
### <a name="getfontname"></a>GetFontName
Ruft den Schriftartnamen ab, in der der Inhaltsheader angezeigt wird.
#### <a name="returns"></a>Rückgabe
Der Schriftartname (Standardwert, wenn nicht Calibri von der Richtlinie festgelegt ist).
### <a name="getfontsize"></a>GetFontSize
Ruft den Schriftgrad ab, in der der Inhaltsheader angezeigt wird.
#### <a name="returns"></a>Rückgabe
Der Schriftgrad als ganze Zahl.
### <a name="getfontcolor"></a>GetFontColor
Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.
#### <a name="returns"></a>Rückgabe
Die Schriftfarbe als Zeichenfolge (z.B. „#000000“).
### <a name="getalignment"></a>GetAlignment
Ruft die Ausrichtung des Headers ab.
#### <a name="returns"></a>Rückgabe
Der ContentMarkAlignment-Enumerator, LEFT|RIGHT|CENTER. 
**Weitere Informationen finden Sie unter:** ContentMarkAlignment
### <a name="getmargin"></a>GetMargin
Ruft den Rand des Headers im unteren Bereich ab.
#### <a name="returns"></a>Rückgabe
Eine ganze Zahl, die die Ränder im unteren Bereich des Dokuments angibt (z.B. 10 mm).
### <a name="actiontype"></a>ActionType
Ruft den [Aktionstyp](#classmip_1_1_action) ab.
#### <a name="returns"></a>Rückgabe
ActionType: Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.