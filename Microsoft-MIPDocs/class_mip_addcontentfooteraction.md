# <a name="class-mipaddcontentfooteraction"></a>mip::AddContentFooterAction-Klasse 
Eine Aktionsklasse, mit der Fußzeileninhalt zum Dokument hinzugefügt wird.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string & GetUIElementName | Eine API, mit der das Element des Fußzeileninhalts markiert wird.
public const std::string & GetText | Ruft den Text ab, der im Fußzeileninhalt enthalten sein soll.
public const std::string & GetFontName | Ruft den Namen der Schriftart ab, in der der Fußzeileninhalt angezeigt werden soll.
public int GetFontSize | Ruft den Schriftgrad ab, in dem der Fußzeileninhalt angezeigt werden soll.
public const std::string & GetFontColor | Ruft die Schriftfarbe ab, in der der Fußzeileninhalt angezeigt werden soll.
public ContentMarkAlignment GetAlignment | Ruft die Ausrichtung der Fußzeile ab.
public int GetMargin | Ruft den Rand der Fußzeile im unteren Bereich ab.
public ActionType GetType
## <a name="members"></a>Member
### <a name="getuielementname"></a>GetUIElementName
Eine API, mit der das Element des Fußzeileninhalts markiert wird.
#### <a name="returns"></a>Rückgabe
Der Name, der für das UI-Element verwendet werden sollte, das den Fußzeileninhalt enthält. Wenn der Fußzeileninhalt entfernt werden muss, wird der gleiche Name in [RemoveContentFooterAction](#classmip_1_1_remove_content_footer_action) zurückgegeben.
### <a name="gettext"></a>GetText
Ruft den Text ab, der im Fußzeileninhalt enthalten sein soll.
#### <a name="returns"></a>Rückgabe
Der Inhalt des Fußzeilentexts.
### <a name="getfontname"></a>GetFontName
Ruft den Namen der Schriftart ab, in der der Fußzeileninhalt angezeigt werden soll.
#### <a name="returns"></a>Rückgabe
Der Schriftartname (Standardwert, wenn nicht Calibri von der Richtlinie festgelegt ist).
### <a name="getfontsize"></a>GetFontSize
Ruft den Schriftgrad ab, in dem der Fußzeileninhalt angezeigt werden soll.
#### <a name="returns"></a>Rückgabe
Der Schriftgrad als ganze Zahl.
### <a name="getfontcolor"></a>GetFontColor
Ruft die Schriftfarbe ab, in der der Fußzeileninhalt angezeigt werden soll.
#### <a name="returns"></a>Rückgabe
Die Schriftfarbe als Zeichenfolge (z.B. „#000000“).
### <a name="getalignment"></a>GetAlignment
Ruft die Ausrichtung der Fußzeile ab.
#### <a name="returns"></a>Rückgabe
Der ContentMarkAlignment-Enumerator, LEFT|RIGHT|CENTER. 
**Weitere Informationen finden Sie unter:** ContentMarkAlignment
### <a name="getmargin"></a>GetMargin
Ruft den Rand der Fußzeile im unteren Bereich ab.
#### <a name="returns"></a>Rückgabe
Eine ganze Zahl, die die Ränder im unteren Bereich des Dokuments angibt (z.B. 10 mm).
### <a name="actiontype"></a>ActionType
Ruft den [Aktionstyp](#classmip_1_1_action) ab.
#### <a name="returns"></a>Rückgabe
ActionType: Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.