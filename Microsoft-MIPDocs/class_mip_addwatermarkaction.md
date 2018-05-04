# <a name="class-mipaddwatermarkaction"></a>mip::AddWatermarkAction-Klasse 
Eine Aktionsklasse, die das Hinzufügen eines Wasserzeichens angibt.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string & GetUIElementName | Eine zum Markieren des Wasserzeichenelements genutzte API.
public WatermarkLayout GetLayout | Eine zum Abrufen des Wasserzeichenlayouts genutzte API.
public const std::string & GetText | Ruft den Text ab, der im Inhaltsheader enthalten sein soll
public const std::string & GetFontName | Ruft den Namen der Schriftart ab, in welcher der Inhaltsheader angezeigt wird.
public int GetFontSize | Ruft den Schriftgrad ab, in welchem der Inhaltsheader angezeigt wird.
public const std::string & GetFontColor | Ruft die Schriftfarbe ab, in welcher der Inhaltsheader angezeigt wird.
public ActionType GetType
## <a name="members"></a>Member
### <a name="getuielementname"></a>GetUIElementName
Eine zum Markieren des Wasserzeichenelements genutzte API.
#### <a name="returns"></a>Rückgabe
der Namen, der für das UI-Element verwendet werden soll, welches das Wasserzeichen enthält. Der gleiche Name wird in RemoveWatermarkingAction zurückgegeben, falls das Wasserzeichen entfernt werden muss.
### <a name="getlayout"></a>GetLayout
Eine zum Abrufen des Wasserzeichenlayouts genutzte API.
#### <a name="returns"></a>Rückgabe
WatermarkLayout Das Wasserzeichenlayout in der Form einer Enumeration HORIZONTAL|DIAGONAL. ,
### <a name="gettext"></a>GetText
Ruft den Text ab, der im Inhaltsheader enthalten sein soll
#### <a name="returns"></a>Rückgabe
des Texts des Inhaltsheaders.
### <a name="getfontname"></a>GetFontName
Ruft den Namen der Schriftart ab, in welcher der Inhaltsheader angezeigt wird.
#### <a name="returns"></a>Rückgabe
Schriftartname; Standardwert ist Calibri, wenn nicht anders von der Richtlinie festgelegt.
### <a name="getfontsize"></a>GetFontSize
Ruft den Schriftgrad ab, in welchem der Inhaltsheader angezeigt wird.
#### <a name="returns"></a>Rückgabe
des Schriftgrads als ganze Zahl.
### <a name="getfontcolor"></a>GetFontColor
Ruft die Schriftfarbe ab, in welcher der Inhaltsheader angezeigt wird.
#### <a name="returns"></a>Rückgabe
der Schriftfarbe als Zeichenfolge (z.B. „#000000“).
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](#classmip_1_1_action) ab.
#### <a name="returns"></a>Rückgabe
von ActionType: der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.