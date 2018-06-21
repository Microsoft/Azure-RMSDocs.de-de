# <a name="class-mipaddcontentheaderaction"></a>mip::AddContentHeaderAction-Klasse 
Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetUIElementName()  |  Eine API, mit der das Inhaltsheaderelement markiert wird
 public const std::string& GetText() const  |  Ruft den Text ab, der im Inhaltsheader enthalten sein soll
 public const std::string& GetFontName() const  |  Ruft den Schriftartnamen ab, in der der Inhaltsheader angezeigt wird.
 public int GetFontSize() const  |  Ruft den Schriftgrad ab, in der der Inhaltsheader angezeigt wird.
 public const std::string& GetFontColor() const  |  Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.
 public ContentMarkAlignment GetAlignment() const  |  Ruft die Ausrichtung des Headers ab
 public int GetMargin() const  |  Ruft den Rand des Headers im unteren Bereich ab
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementname"></a>GetUIElementName
Eine API, mit der das Inhaltsheaderelement markiert wird

  
**Rückgabe**: Name, der für das UI-Element verwendet werden sollte, das den Kopfzeileninhalt enthält. Wenn der Inhaltsheader entfernt werden muss, wird derselbe Name in [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) zurückgegeben.
  
### <a name="gettext"></a>GetText
Ruft den Text ab, der im Inhaltsheader enthalten sein soll

  
**Rückgabe**: Text des Inhaltsheaders.
  
### <a name="getfontname"></a>GetFontName
Ruft den Schriftartnamen ab, in der der Inhaltsheader angezeigt wird.

  
**Rückgabe**: Schriftartname (Standardwert, wenn nicht Calibri von der Richtlinie festgelegt ist).
  
### <a name="getfontsize"></a>GetFontSize
Ruft den Schriftgrad ab, in der der Inhaltsheader angezeigt wird.

  
**Rückgabe**: Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor"></a>GetFontColor
Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.

  
**Rückgabe**: Schriftfarbe als Zeichenfolge (z.B. „#000000“).
  
### <a name="getalignment"></a>GetAlignment
Ruft die Ausrichtung des Headers ab

  
**Rückgabe**: Der ContentMarkAlignment-Enumerator, LEFT|RIGHT|CENTER. 
**Weitere Informationen finden Sie unter:** ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Ruft den Rand des Headers im unteren Bereich ab

  
**Rückgabe**: Ganze Zahl, die die Ränder im unteren Bereich des Dokuments angibt (z.B. 10 mm).
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.