# <a name="class-mipaddcontentheaderaction"></a>mip::AddContentHeaderAction-Klasse 
Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string & GetUIElementName | Eine API, mit der das Inhaltsheaderelement markiert wird
public const std::string & GetText | Ruft den Text ab, der im Inhaltsheader enthalten sein soll
public const std::string & GetFontName | Ruft den Namen der Schriftart ab, in der der Inhaltsheader angezeigt wird
public int GetFontSize | Ruft den Schriftgrad ab, in dem der Inhaltsheader angezeigt wird
public const std::string & GetFontColor | Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird
public ContentMarkAlignment GetAlignment | Ruft die Ausrichtung des Headers ab
public int GetMargin | Ruft den Rand des Headers im unteren Bereich ab
public ActionType GetType
## <a name="members"></a>Member
### <a name="getuielementname"></a>GetUIElementName
Eine API, mit der das Inhaltsheaderelement markiert wird
#### <a name="returns"></a>Rückgabe
Der Name, der für das UI-Element verwendet werden sollte, das den Inhaltsheader enthält. Wenn der Inhaltsheader entfernt werden muss, wird derselbe Name in [RemoveContentHeaderAction](#classmip_1_1_remove_content_header_action) zurückgegeben.
### <a name="gettext"></a>GetText
Ruft den Text ab, der im Inhaltsheader enthalten sein soll
#### <a name="returns"></a>Rückgabe
Text des Inhaltsheaders
### <a name="getfontname"></a>GetFontName
Ruft den Namen der Schriftart ab, in der der Inhaltsheader angezeigt wird
#### <a name="returns"></a>Rückgabe
Schriftartname, Standardwert, wenn nicht Calibri von der Richtlinie festgelegt ist
### <a name="getfontsize"></a>GetFontSize
Ruft den Schriftgrad ab, in dem der Inhaltsheader angezeigt wird
#### <a name="returns"></a>Rückgabe
Schriftgrad als Integer
### <a name="getfontcolor"></a>GetFontColor
Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird
#### <a name="returns"></a>Rückgabe
Schriftfarbe als Zeichenfolge (z.B. „#000000“)
### <a name="getalignment"></a>GetAlignment
Ruft die Ausrichtung des Headers ab
#### <a name="returns"></a>Rückgabe
Der ContentMarkAlignment-Enumerator, LEFT|RIGHT|CENTER. 
**Weitere Informationen finden Sie unter:** ContentMarkAlignment
### <a name="getmargin"></a>GetMargin
Ruft den Rand des Headers im unteren Bereich ab
#### <a name="returns"></a>Rückgabe
Eine ganze Zahl, die die Ränder im unteren Bereich des Dokuments angibt (z.B. 10 mm)
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](#classmip_1_1_action) ab.
#### <a name="returns"></a>Rückgabe
ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.