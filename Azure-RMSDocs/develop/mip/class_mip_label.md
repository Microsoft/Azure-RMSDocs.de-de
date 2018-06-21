# <a name="class-miplabel"></a>mip::Label-Klasse 
Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetId() const  |  Ruft die Bezeichnungs-ID ab
 public const std::string& GetName() const  |  Ruft den Bezeichnungsnamen ab
 public const std::string& GetDescription() const  |  Ruft die Beschreibung der Bezeichnung ab
 public const std::string& GetColor() const  |  Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll
 public const std::string& GetOrder() const  |  Ruft die Reihenfolge der Bezeichnung ab
 public const std::string& GetTooltip() const  |  Ruft die QuickInfo-Beschreibung für die Bezeichnung ab
 public bool IsActive() const  |  Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist
public std::weak_ptr<Label> GetParent() const  |  Ruft die übergeordnete Bezeichnung ab
public const std::vector<std::shared_ptr<Label>>& GetChildren() const  |  Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab
  
## <a name="members"></a>Member
  
### <a name="getid"></a>GetId
Ruft die Bezeichnungs-ID ab

  
**Rückgabe**: die Bezeichnungs-ID.
  
### <a name="getname"></a>GetName
Ruft den Bezeichnungsnamen ab

  
**Rückgabe**: der Bezeichnungsname.
  
### <a name="getdescription"></a>GetDescription
Ruft die Beschreibung der Bezeichnung ab

  
**Rückgabe**: die Beschreibung der Bezeichnung.
  
### <a name="getcolor"></a>GetColor
Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll

  
**Rückgabe**: der Farbwert des Zeichenfolgenformats. „#RRGGBB“, wobei jedes RR, GG, BB ein Hexadezimalwert von 0 bis f ist
  
### <a name="getorder"></a>GetOrder
Ruft die Reihenfolge der Bezeichnung ab

  
**Rückgabe**: ein numerischer, als Zeichenfolge zugeschriebener Wert.
  
### <a name="gettooltip"></a>GetTooltip
Ruft die QuickInfo-Beschreibung für die Bezeichnung ab

  
**Rückgabe**: eine QuickInfo-Zeichenfolge.
  
### <a name="isactive"></a>IsActive
Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist
Es können nur aktive Bezeichnungen angewendet werden. Inaktive Bezeichnungen können nicht angewendet werden und werden nur zu Anzeigezwecken verwendet. 

  
**Rückgabe**: TRUE, wenn die Bezeichnung aktiv ist; andernfalls wird FALSE zurückgegeben.
  
### <a name="label"></a>Label
Ruft die übergeordnete Bezeichnung ab

  
**Rückgabe**: ein schwacher Zeiger auf das übergeordnete Element, sofern vorhanden; andernfalls wird ein leerer Zeiger zurückgegeben.
  
### <a name="label"></a>Label
Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab

  
**Rückgabe**: ein Vektor der freigegebenen Zeiger für Bezeichnungen.