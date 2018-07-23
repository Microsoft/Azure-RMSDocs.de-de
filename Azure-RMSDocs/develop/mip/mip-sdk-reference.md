# <a name="mip-sdk-for-c-preview-reference"></a>Referenz zu MIP SDK für C++ (Vorschau)

Mit dem Microsoft Information Protection (MIP) SDK für C++ (Vorschau) können Entwickler Datenschutzrichtlinien für Daten und andere digitale Objekte verwalten und anwenden.  

Weitere Informationen hierzu finden Sie im [Blog für MIP-Entwickler](https://aka.ms/MIPDevelopers)<!-- and [MIP samples](https://aka.ms/mipsdksamples)-->.

Das MIP SDK für C++ enthält:

- [Enumerationen und Strukturen](mip-enums-and-structs.md)
- [Functions (Funktionen)](mip-functions.md)
- Die folgenden Klassen:

| Klassenname | Beschreibung |
| :----------|:------------|
[ConsentDelegate](class_consentdelegate.md)  |  Delegat für Vorgänge, die eine Zustimmung erfordern.
[mip::AccessDeniedError](class_mip_accessdeniederror.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen, z.B. der Zugriff wurde verweigert, der Inhalt wurde widerrufen usw.
[mip::Action](class_mip_action.md)  |  Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
[mip::AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  Eine Aktionsklasse, die Fußzeileninhalt angibt, der dem Dokument hinzugefügt werden soll.
[mip::AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
[mip::AddWatermarkAction](class_mip_addwatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
[mip::ApplyLabelAction](class_mip_applylabelaction.md)  |  Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
[mip::BadInputError](class_mip_badinputerror.md)  |  Fehler bei ungültiger Eingabe, der ausgegeben wird, sobald die Eingabe in ein SDK ungültig ist.
[mip::ClassificationResult](class_mip_classificationresult.md)  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
[mip::ContentLabel](class_mip_contentlabel.md)  |  Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
[mip::CustomAction](class_mip_customaction.md)  |  [CustomAction](class_mip_customaction.md) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
[mip::Error](class_mip_error.md)  |  Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
[mip::ExecutionState](class_mip_executionstate.md)  |  Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
[mip::FileEngine](class_mip_fileengine.md)  |  Eine Schnittstelle für alle Engine-Funktionen.
[mip::FileEngine::Settings](class_mip_fileengine::settings.md)  | _Noch nicht dokumentiert._
[mip::FileHandler](class_mip_filehandler.md)  |  Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
[mip::FileHandler::Observer](class_mip_filehandler::observer.md)  |  [Observer](class_mip_filehandler_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse im Zusammenhang mit dem Dateihandle.
[mip::FileIOError](class_mip_fileioerror.md)  |  Datei-E/A-Fehler.
[mip::FileProfile](class_mip_fileprofile.md)  |  Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
[mip::FileProfile::Observer](class_mip_fileprofile_observer.md)  |  [Observer](class_mip_fileprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
[mip::FileProfile::Settings](class_mip_fileprofile_settings.md)  |  [Einstellungen](class_mip_fileprofile_settings.md), die während der Erstellung und Lebensdauer von [FileProfile](class_mip_fileprofile.md) verwendet werden
[mip::InternalError](class_mip_internalerror.md)  |  Interner Fehler. Dieser Fehler tritt auf, wenn während der Ausführung etwas Unerwartetes passiert.
[mip::JustificationRequiredError](class_mip_justificationrequirederror.md)  | _Noch nicht dokumentiert._
[mip::JustifyAction](class_mip_justifyaction.md)  |  Diese [Aktion](class_mip_action.md) fordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Einstellen der Antwort im Ausführungsstatus an.
[mip::Label](class_mip_label.md)  |  Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
[mip::LabelingOptions](class_mip_labelingoptions.md)  |  Eine Schnittstelle für die Konfiguration von Beschriftungsoptionen für die SetLabel-Methode.
[mip::LoggerDelegate](class_mip_loggerdelegate.md)  |  Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
[mip::MetadataAction](class_mip_metadataaction.md)  |  Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
[mip::NetworkError](class_mip_networkerror.md)  |  Ein Netzwerkfehler Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
[mip::NotSupportedError](class_mip_notsupportederror.md)  |  Der von der Anwendung angeforderte Vorgang wird vom SDK nicht unterstützt.
[mip::PolicyEngine](class_mip_policyengine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  Eine Instanz dieser Klasse mit den passenden Parametern sollte bereitgestellt werden, um eine Engine zu initiieren.
[mip::PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  Die aktuelle Bezeichnung wurde als privilegierter Vorgang zugewiesen (das Äquivalent zu einem Administratorvorgang), daher kann sie nicht außer Kraft gesetzt werden.
[mip::Profile](class_mip_profile.md)  |  Die [Profile](class_mip_profile.md)-Klasse ist die Stammklasse für die Verwendung von Microsoft Information Protection-Vorgängen. Eine typische Anwendung benötigt nur ein [Profil](class_mip_profile.md), kann bei Bedarf aber mehrere erstellen.
[mip::Profile::Observer](class_mip_profile_observer.md)  |  [Observer](class_mip_profile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
[mip::Profile::Settings](class_mip_profile_settings.md)  |  [Einstellungen](class_mip_profile_settings.md), die während der Erstellung und Lebensdauer von [Profile](class_mip_profile.md) verwendet werden
[mip::ProtectAdhocAction](class_mip_protectadhocaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Ad-hoc-Schutz hinzugefügt wird.
[mip::ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  Eine Aktionsklasse, die angibt, dass Schutz nach Vorlage zum Dokument hinzugefügt wird.
[mip::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form einer Nichtweiterleitung hinzugefügt wird.
[mip::ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  Stellt eine Ad-hoc-Richtlinie dar, die geschütztem Inhalt zugeordnet ist.
[mip::ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  Stellt eine Ad-hoc-Richtlinie dar, die geschütztem Inhalt zugeordnet ist.
[mip::ProtectionEngine](class_mip_protectionengine.md)  |  Führt schutzbezogene Aktionen aus, die sich auf eine bestimmte Identität beziehen.
[mip::ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionEngine](class_mip_protectionengine.md) empfängt
[mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  [Einstellungen](class_mip_protectionengine_settings.md), die während der Erstellung und Lebensdauer von [ProtectionEngine](class_mip_protectionengine.md) verwendet werden
[mip::ProtectionHandler](class_mip_protectionhandler.md)  |  Führt schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration (d.h. Benutzer, Rechte, Rollen usw.) aus.
[mip::ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionHandler](class_mip_protectionhandler.md) empfängt
[mip::ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
[mip::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md) empfängt.
[mip::ProtectionProfile::Observer](class_mip_protectionprofile_settings.md)  |  [Einstellungen](class_mip_protectionprofile_settings.md), die während der Erstellung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden.
[mip::RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
[mip::RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  Eine Aktionsklasse, mit der angegeben wird,dass die Fußzeile mit Inhalt aus dem Dokument entfernt wird.
[mip::RemoveContentFooterAction](class_mip_removecontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird
[mip::RemoveContentFooterAction](class_mip_removeprotectionaction.md)  |  Eine Aktionsklasse, mit der Schutz aus dem Dokument entfernt wird.
[mip::RemoveContentFooterAction](class_mip_removewatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt werden soll
[mip::Stream](class_mip_stream.md)  |  Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
[mip::UserRights](class_mip_userrights.md)  |  Stellt eine Gruppe von Benutzern und die ihr zugeordneten Berechtigungen dar
[mip::UserRoles](class_mip_userroles.md)  |  Stellt eine Gruppe von Benutzern und die ihr zugeordneten Rollen dar

 
