# <a name="class-mipprotectionprofile"></a>mip::ProtectionProfile-Klasse 
[ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
Bevor Schutzvorgänge durchgeführt werden können, muss eine Anwendung [ProtectionProfile](class_mip_protectionprofile.md) erstellen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.
 public void ClearCaches()  |  Löscht Caches (z.B. Datenbanken mit Zustimmungen usw.)
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft während der Initialisierung und der Lebensdauer die von [ProtectionProfile](class_mip_protectionprofile.md) verwendeten Einstellungen ab.

  
**Rückgabe**: [Einstellungen](class_mip_protectionprofile_settings.md), die von [ProtectionProfile](class_mip_protectionprofile.md) während der Initialisierung und der Lebensdauer verwendet werden
  
### <a name="clearcaches"></a>ClearCaches
Löscht Caches (z.B. Datenbanken mit Zustimmungen usw.) Nützlich für das Debuggen bzw. Testen