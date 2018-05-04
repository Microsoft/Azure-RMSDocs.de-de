# <a name="class-miplabel"></a>mip::Label-Klasse 
Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string & GetId | Ruft die Bezeichnungs-ID ab.
public const std::string & GetName | Ruft den Bezeichnungsnamen ab.
public const std::string & GetDescription | Ruft die Beschreibung der Bezeichnung ab.
public const std::string & GetColor | Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll.
public const std::string & GetOrder | Ruft die Reihenfolge der Bezeichnung ab.
public const std::string & GetTooltip | Ruft die Beschreibung der QuickInfo für die Bezeichnung ab.
public bool IsActive | Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist.
public std::weak_ptr< Label > GetParent | Ruft die übergeordnete Bezeichnung ab.
public const std::vector< std::shared_ptr< Label > > & GetChildren | Ruft die untergeordneten Bezeichnungen der aktuelle Bezeichnung ab.
## <a name="members"></a>Member
### <a name="getid"></a>GetId
Ruft die Bezeichnungs-ID ab.
#### <a name="returns"></a>Rückgabe
Die Bezeichnungs-ID.
### <a name="getname"></a>GetName
Ruft den Bezeichnungsnamen ab.
#### <a name="returns"></a>Rückgabe
Der Bezeichnungsname.
### <a name="getdescription"></a>GetDescription
Ruft die Beschreibung der Bezeichnung ab.
#### <a name="returns"></a>Rückgabe
Die Beschreibung der Bezeichnung.
### <a name="getcolor"></a>GetColor
Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll.
#### <a name="returns"></a>Rückgabe
Der Farbwert der Zeichenfolge. „#RRGGBB“, wobei jedes RR, GG, BB ein Hexadezimalwert von 0 bis f ist.
### <a name="getorder"></a>GetOrder
Ruft die Reihenfolge der Bezeichnung ab.
#### <a name="returns"></a>Rückgabe
Ein numerischer, als Zeichenfolge zugeschriebener Wert.
### <a name="gettooltip"></a>GetTooltip
Ruft die Beschreibung der QuickInfo für die Bezeichnung ab.
#### <a name="returns"></a>Rückgabe
Eine QuickInfo-Zeichenfolge.
### <a name="isactive"></a>IsActive
Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist.
Nur aktive Bezeichnungen können angewendet werden. Inaktive Bezeichnungen können nicht angewendet werden und werden nur zu Anzeigezwecken verwendet. 
#### <a name="returns"></a>Rückgabe
TRUE, wenn die Bezeichnung aktiv ist; andernfalls wird FALSE zurückgegeben.
### <a name="label"></a>Label
Ruft die übergeordnete Bezeichnung ab.
#### <a name="returns"></a>Rückgabe
Ein schwacher Zeiger auf das übergeordnete Element, sofern vorhanden; andernfalls wird ein leerer Zeiger zurückgegeben.
### <a name="label"></a>Label
Ruft die untergeordneten Bezeichnungen der aktuelle Bezeichnung ab.
#### <a name="returns"></a>Rückgabe
Ein Vektor der freigegebenen Zeiger für Bezeichnungen.