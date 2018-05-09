# <a name="class-mipprotectionprofile"></a>mip::ProtectionProfile-Klasse 
[ProtectionProfile](#classmip_1_1_protection_profile) ist die Stammklasse für Schutzvorgänge.
Bevor Schutzvorgänge durchgeführt werden können, muss eine Anwendung [ProtectionProfile](#classmip_1_1_protection_profile) erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](#classmip_1_1_protection_profile) verwendeten Einstellungen ab.
public void ClearCaches()  |  Löscht Caches (z.B. Datenbanken mit Zustimmungen usw.)
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](#classmip_1_1_protection_profile) verwendeten Einstellungen ab.
  
#### <a name="returns"></a>Rückgabe
[Einstellungen](#classmip_1_1_protection_profile_1_1_settings), die während der Initialisierung und Lebensdauer von [ProtectionProfile](#classmip_1_1_protection_profile) verwendet werden
  
### <a name="clearcaches"></a>ClearCaches
Löscht Caches (z.B. Datenbanken mit Zustimmungen usw.) Nützlich für das Debuggen bzw. Testen