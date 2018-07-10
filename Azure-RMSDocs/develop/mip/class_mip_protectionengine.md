# <a name="class-mipprotectionengine"></a>mip::ProtectionEngine-Klasse 
Führt schutzbezogene Aktionen aus, die sich auf eine bestimmte Identität beziehen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Ruft die Engine-Einstellungen ab.
public void GetTemplatesAsync(const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
public void CreateProtectionHandlerFromDescriptorAsync(const std::shared_ptr<ProtectionDescriptor>& descriptor, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
public void CreateProtectionHandlerFromPublishingLicenseAsync(const std::vector<uint8_t>& serializedPublishingLicense, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler aus seiner serialisierten Form.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft die Engine-Einstellungen ab.

  
**Rückgabe**: Engine-Einstellungen
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **observer**: Klasse, die die Schnittstelle [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) implementiert 


* **context**: Der gleiche Kontext wird an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure) weitergeleitet.


  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **descriptor**: ein [ProtectionDescriptor](class_mip_protectiondescriptor.md), der die Schutzkonfiguration beschreibt 


* **options**: Erstellungsoptionen 


* **observer**: eine Klasse, die die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)-Schnittstelle implementiert 


* **context**: Der gleiche Kontext wird an [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) oder „ProtectionHandler::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.


  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
Erstellt einen Schutzhandler aus seiner serialisierten Form.

Parameter:  
* **serializedPublishingLicense**: eine serialisierte Veröffentlichungslizenz 


* **options**: Erstellungsoptionen 


* **observer**: eine Klasse, die die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)-Schnittstelle implementiert 


* **context**: Der gleiche Kontext wird an [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) oder „ProtectionHandler::Observer::OnCreateProtectionHandlerFailure“ weitergeleitet.

