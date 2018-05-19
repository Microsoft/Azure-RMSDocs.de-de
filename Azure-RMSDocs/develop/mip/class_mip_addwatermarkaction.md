# <a name="class-mipaddwatermarkaction"></a>mip::AddWatermarkAction-Klasse 
Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetUIElementName()  |  Eine zum Markieren des Wasserzeichenelements genutzte API.
 public WatermarkLayout GetLayout() const  |  Eine zum Abrufen des Wasserzeichenlayouts genutzte API.
 public const std::string& GetText() const  |  Ruft den Text ab, der im Inhaltsheader enthalten sein soll
 public const std::string& GetFontName() const  |  Ruft den Schriftartnamen ab, in der der Inhaltsheader angezeigt wird.
 public int GetFontSize() const  |  Ruft den Schriftgrad ab, in der der Inhaltsheader angezeigt wird.
 public const std::string& GetFontColor() const  |  Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementname"></a>GetUIElementName
Eine zum Markieren des Wasserzeichenelements genutzte API.

  
**Rückgabe**: Name, der für das UI-Element verwendet werden soll, welches das Wasserzeichen enthält. Der gleiche Name wird in RemoveWatermarkingAction zurückgegeben, falls das Wasserzeichen entfernt werden muss.
  
### <a name="getlayout"></a>GetLayout
Eine zum Abrufen des Wasserzeichenlayouts genutzte API.

  
**Rückgabe**: WatermarkLayout Das Wasserzeichenlayout in der Form einer Enumeration HORIZONTAL|DIAGONAL. ,
  
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
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.