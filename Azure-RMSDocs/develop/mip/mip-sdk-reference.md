# <a name="mip-sdk-for-c-preview-reference"></a>Referenz zu MIP SDK für C++ (Vorschau)

Mit dem Microsoft Information Protection (MIP) SDK für C++ (Vorschau) können Entwickler Datenschutzrichtlinien für Daten und andere digitale Objekte verwalten und anwenden.  

Weitere Informationen hierzu finden Sie im [Blog für MIP-Entwickler](https://aka.ms/MIPDevelopers) und in den [MIP-Beispielen](https://aka.ms/mipsdksamples).

Das MIP SDK für C++ enthält die folgenden Klassen:

| Klassenname | Beschreibung |
| :----------|:------------|
[mip::Action](class_mip_action.md) | Die Basisklasse für alle Aktionen. |
[mip::AddContentFooterAction](class_mip_addcontentfooteraction.md) | Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt zum Dokument hinzugefügt wird.
[mip::AddContentFooterAction](class_mip_addcontentheaderaction.md) | Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
[mip::AddWatermarkAction](class_mip_addwatermarkaction.md) | Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
[mip::BadInputError](class_mip_badinputerror.md) | Fehler bei ungültiger Eingabe für die API.
[mip::CommonRights](class_mip_commonrights.md) | Allgemein unterstützte Rechte.
[mip::Consent](class_mip_consent.md) | Stellt die Zustimmung bzw. Ablehnung eines Benutzers zur Zulassung einer Aktion dar.
[mip::ConsentCallback](class_mip_consentcallback.md) | Eine Schnittstelle für Benachrichtigungen über Zustimmungsanforderungen.
[mip::ConsentResult](class_mip_consentresult.md) | Beschreibt das Ergebnis der Zustimmungsanforderung nach der Benutzerinteraktion
[mip::ContentLabel](class_mip_contentlabel.md) | Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
[mip::CustomAction](class_mip_customaction.md) | Eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst.
[mip::CustomProtectedStream](class_mip_customprotectedstream.md) | Umschließt einen Stream, um beim Lesen und Schreiben transparente Verschlüsselung und Entschlüsselung zu gewährleisten.
[mip::EditableDocumentRights](class_mip_editabledocumentrights.md) | Rechte, die für editierbare Dokumente gelten
[mip::EmailRights](class_mip_emailrights.md) | Für E-Mails geltende Berechtigungen.
[mip::Error](class_mip_error.md) | Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
[mip::ExecutionState](class_mip_executionstate.md) | Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
[mip::FileEngine](class_mip_fileengine.md) | Eine Schnittstelle für alle Engine-Funktionen.
[mip::FileEngine::Settings](class_mip_fileengine_settings.md) | 
[mip::FileHandler](class_mip_filehandler.md) | Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
[mip::FileHandler::Observer](class_mip_filehandler_observer.md) | Observer-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse im Zusammenhang mit dem Dateihandle.
[mip::FileIOError](class_mip_fileioerror.md) | Datei-E/A-Fehler.
[mip::FileProfile](class_mip_fileprofile.md) | Die Stammklasse für Microsoft Information Protection-Vorgänge.
[mip::FileProfile::Observer](class_mip_fileprofile_observer.md) | Observer-Schnittstelle für den Empfang von profilbezogenen Ereignisbenachrichtigungen.
[mip::FileProfile::Settings](class_mip_fileprofile_settings.md) | Eine Schnittstelle für die Verwaltung von Dateiprofileinstellungen.
[mip::GetUserPolicyResult](class_mip_getuserpolicyresult.md) | Beschreibt die Ergebnisse einer Anforderung zur Benutzerrichtlinienanschaffung.
[mip::InternalError](class_mip_internalerror.md) | Ein interner SDK-Fehler. Es kam zu einem unerwarteten Vorfall.
[mip::IStream](class_mip_istream.md) | Die Basisschnittstelle für geschützte Streams.
[mip::JustificationRequiredError](class_mip_justificationrequirederror.md) | Für die angeforderte Änderung ist eine Erklärung erforderlich.
[mip::JustifyAction](class_mip_justifyaction.md) | Die Anforderung erfordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Festlegen der Antwort im Ausführungsstatus.
[mip::Label](class_mip_label.md) | Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
[mip::LabelingOptions](class_mip_labelingoptions.md) | Eine Schnittstelle für die Konfiguration von Beschriftungsoptionen für die SetLabel-Methode.
[mip::MetadataAction](class_mip_metadataaction.md) | Eine Aktion, in der die zum Inhalt hinzuzufügenden Metadateninformationen angegeben werden.
[mip::NetworkError](class_mip_networkerror.md) | Ein Netzwerkfehler
[mip::NotSupportedError](class_mip_notsupportederror.md) | Fehler „Der Vorgang wird nicht unterstützt.“
[mip::PolicyDescriptor](class_mip_policydescriptor.md) | Stellt eine Ad-hoc-Richtlinie dar, die geschütztem Inhalt zugeordnet ist.
[mip::PolicyEngine](class_mip_policyengine.md) | Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) | Eine Instanz dieser Klasse mit den passenden Parametern sollte bereitgestellt werden, um eine Engine zu initiieren.
[mip::PrivilegedRequiredError](class_mip_privilegedrequirederror.md) | Die aktuelle Bezeichnung wurde von der Zuweisungsmethode für Berechtigungen festgelegt und kann nicht überschrieben werden.
[mip::Profile](class_mip_profile.md) | Die Stammklasse für Microsoft Information Protection-Vorgänge.
[mip::Profile::Observer](class_mip_profile_observer.md) | Eine Schnittstelle für den Empfang von profilbezogenen Ereignisbenachrichtigungen.
[mip::Profile::Settings](class_mip_profile_settings.md) | Konfiguriert die Profileinstellungen.
[mip::ProtectAdhocAction](class_mip_protectadhocaction.md) | Eine Aktionsklasse, mit der Ad-hoc-Schutz zum Dokument hinzugefügt wird.  
[mip::ProtectbyTemplateAction](class_mip_protectbytemplateaction.md) | Eine Aktionsklasse, die angibt, dass Schutz nach Vorlage zum Dokument hinzugefügt wird.
[mip::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md) | Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form einer Nichtweiterleitung hinzugefügt wird.
[mip::ProtectionProfile](class_mip_protectionprofile.md) | Basisklasse zur Durchführung von Schutzvorgängen.
[mip::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) | Wird für den Empfang von Benachrichtigungen für Schutzprofile verwendet.
[mip::ProtectionProfile::Observer](class_mip_protectionprofile_settings.md) | Einstellungen für Schutzprofile, die über die gesamte Nutzungsdauer der Instanz verwendet werden.
[mip::RemoveContentFooterAction](class_mip_removecontentfooteraction.md) | Eine Aktionsklasse, mit der angegeben wird,dass die Fußzeile mit Inhalt aus dem Dokument entfernt wird.
[mip::RemoveContentFooterAction](class_mip_removecontentheaderaction.md) | Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird
[mip::RemoveContentFooterAction](class_mip_removeprotectionaction.md) | Eine Aktionsklasse, mit der Schutz aus dem Dokument entfernt wird.
[mip::RemoveContentFooterAction](class_mip_removewatermarkaction.md) | Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt werden soll
[mip::RMSCryptographyException](class_mip_rmscryptographyexception.md) | RMS-Kryptografieausnahme
[mip::RMSException](class_mip_rmsexception.md) | RMS-Basisausnahme
[mip::RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md) | RMS-Ausnahme für ungültiges Argument
[mip::RMSException](class_mip_rmslogicexception.md) | Ausnahme für RMS-Logik.
[mip::RMSException](class_mip_rmsnetworkexception.md) | Ausnahme für ein RMS-Netzwerk.
[mip::RMSException](class_mip_rmsnotfoundexception.md) | Ausnahme: RMS wurde nicht gefunden.
[mip::RMSException](class_mip_rmsnullpointerexception.md) | Ausnahme: RMS-NULL-Zeiger.
[mip::RMSOfficeFileException](class_mip_rmsofficefileexception.md) | Ausnahme für RMS-Office-Datei.
[mip::RMSOfficeFileException](class_mip_rmspfileexception.md) | RMS-PFile-Ausnahme
[mip::RMSOfficeFileException](class_mip_rmsrightsexception.md) | Ausnahme für RMS-Rechte
[mip::RMSOfficeFileException](class_mip_rmsstreamexception.md) | Ausnahme für den RMS-Stream
[mip::Roles](class_mip_roles.md) | Definiert Rollen für den Schutz von Daten.
[mip::Stream](class_mip_stream.md) | Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
[mip::TemplateDescriptor](class_mip_templatedescriptor.md) | Beschreibt eine RMS-Vorlage.
[mip::UserPolicy](class_mip_userpolicy.md) | Stellt die geschützten Inhalten zugeordnete Richtlinie dar.
[mip::UserRights](class_mip_userrights.md) | Stellt eine Gruppe von Benutzern und die ihr zugeordneten Berechtigungen dar
[mip::UserRoles](class_mip_userroles.md) | Stellt eine Gruppe von Benutzern und die ihr zugeordneten Rollen dar
 
