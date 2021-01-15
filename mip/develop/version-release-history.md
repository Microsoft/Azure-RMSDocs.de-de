---
title: Versions Veröffentlichungs Verlauf und Unterstützungs Richtlinie für das Microsoft Information Protection (MIP) SDK
description: Versions Veröffentlichungs Verlauf und Änderungs Hinweise für das MIP SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/25/2019
ms.author: mbaldwin
ms.openlocfilehash: 3e3d32dd5e66ee6948567bc43ebd5ecfa16154b6
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215509"
---
# <a name="microsoft-information-protection-mip-software-development-kit-sdk-version-release-history-and-support-policy"></a>Versions Veröffentlichungs Verlauf und Support Richtlinie für Microsoft Information Protection (MIP) Software Development Kit (SDK)

## <a name="servicing"></a>Wird gewartet

Jede allgemein verfügbare Version (General Availability, GA) wird ein Jahr lang unterstützt, nachdem die nächste GA-Version veröffentlicht wurde. In der Dokumentation sind möglicherweise keine Informationen zu nicht unterstützten Versionen enthalten. Korrekturen und neue Funktionen werden nur auf die neueste Version der allgemeinen Verfügbarkeit angewendet.

Vorschau Versionen sollten nicht in der Produktionsumgebung bereitgestellt werden. Verwenden Sie stattdessen die neueste Vorschauversion, um neue Funktionen oder Korrekturen zu testen, die in der nächsten GA-Version verfügbar sind. Nur die aktuelle Vorschauversion wird unterstützt.

## <a name="release-history"></a>Releaseverlauf

Verwenden Sie die folgenden Informationen, um zu sehen, was für eine unterstützte Version neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt.

> [!NOTE]
> Kleinere Fehlerbehebungen sind nicht aufgeführt. Wenn Sie ein Problem mit dem SDK haben, sollten Sie überprüfen, ob es mit der neuesten GA-Version behoben wurde. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion.
>  
> Technische Unterstützung finden Sie im [Stack Overflow Microsoft Information Protection-Forum](https://stackoverflow.com/questions/tagged/microsoft-information-protection).

## <a name="version-1886"></a>Version 1.8.86

**Veröffentlichungsdatum:** 13. Januar 2021

### <a name="general-changes"></a>Allgemeine Änderungen

- Unterstützung für Mac auf Arm hinzugefügt.
- Alle dylib-Dateien für Mac signiert.
- Alle Clouds werden in allen drei sdert vollständig unterstützt.
- Benennen Sie `TelemetryConfiguration` in `DiagnosticConfiguration` um.
- Aktualisiert `MipContext` , um `DiagnosticConfiguration` anstelle von zu akzeptieren `TelemetryConfiguration` .
- Neue und verfügbar gemacht `TelemetryDelegate` `AuditDelegate` .
- Der Name mehrerer benutzerdefinierter Einstellungen wurde geändert und wird in Version 1,9 entfernt. Diese funktionieren weiterhin parallel zu ihren Update Namen in Version 1,8. 

| Neuer Name          | Alter Name                   |
| ----------------- | -------------------------- |
| is_debug_audit    | is_debug_telemetry         |
| is_audit_disabled | is_built_in_audit_disabled |

### <a name="file-sdk"></a>Datei-SDK

- Unterstützung für benutzerdefinierte Bezeichnungen mit doppelter Schlüssel Verschlüsselung hinzugefügt.
- Eine API wurde hinzugefügt, `MsgInspector.BodyType` um den Text Codierungstyp für Nachrichten Dateien verfügbar zu machen.
- Es wurden APIs zur Unterstützung der doppelten Schlüssel Verschlüsselung mit User-Defined Berechtigungen hinzugefügt.
- Flag für hinzugefügt `mip::FileHandler` , mit dem der Aufrufer das Senden von Überwachungs Ermittlungs Ereignissen deaktivieren kann. Dadurch wird ein Szenario korrigiert, bei dem die Verwendung der `ClassifyAsync()` API zu doppelten Ermittlungs Ereignissen führt.
- Fehler behoben: 
  - Fehler beim Festlegen des Schutzes für die XPS-Datei.
  - Eine Datei kann nach dem Hochladen/Herunterladen von SharePoint Online und dem Entfernen benutzerdefinierter Berechtigungen nicht geöffnet werden.
  - `RemoveProtection()` die Funktion akzeptiert eine Message. rpmsg-Eingabe. Akzeptiert jetzt nur msg-Dateien.
  - Ein Absturz, der beim Versuch aufgetreten ist, ungeschützte Dateien zu verfolgen oder aufzuheben.

### <a name="policy-sdk"></a>Richtlinien-SDK

- `ActionId`Aus den standardmetadateneigenschaften wurde entfernt, um die Konsistenz zwischen Microsoft Office und den in SharePoint
- Unterstützung für Azure purview-spezifische Bezeichnungen hinzugefügt.
- Die Möglichkeit, sowohl Telemetriedaten als auch überwachen über Delegaten für jede zu überschreiben
  - Der Audit-Delegat bietet die Möglichkeit, AIP-Überwachungs Ereignisse an ein anderes Ziel als AIP Analytics oder zusätzlich zu AIP Analytics zu senden.
- Das Flag für wurde hinzugefügt `mip::PolicyHandler` , mit dem der Aufrufer das Senden von Überwachungs Ermittlungs Ereignissen ermitteln kann. Dadurch wird ein Szenario korrigiert, bei dem die Verwendung der `ClassifyAsync()` API zu doppelten Ermittlungs Ereignissen führt.
- Es wurde ein Fehler behoben, bei dem die verschlüsselte Richtlinien Datenbank nicht in bestimmten Szenarien geöffnet werden konnte.
- Es wurde eine neue bereitgestellt `AuditDelegate` , mit der Entwickler die standardmäßige MIP SDK-Überwachungs Pipeline überschreiben und Ereignisse an Ihre eigene Infrastruktur senden können 
- `mip::ClassifierUniqueIdsAndContentFormats` und `GetContentFormat()` geben jetzt `std::string` anstelle von zurück `mip::ContentFormat` . Diese Änderung wird in .net-und Java-Wrapper repliziert. 
- `ContentFormat.Default` ist jetzt `ContentFormat.File` .

### <a name="protection-sdk"></a>Schutz-SDK

- Es wurde eine Eigenschaft hinzugefügt `ProtectionEngineSettings.SetAllowCloudServiceOnly` , die keine Verbindungen mit Active Directory Rights Management Services Clustern zulässt, wenn true. Es werden nur cloudumgebungen verwendet.
- Unterstützung für das Abrufen von Delegierungs Lizenzen hinzugefügt.
  - Delegierungen ermöglichen es Diensten, eine Lizenz für den Inhalt im Auftrag eines Benutzers abzurufen.
  - Dadurch kann der Dienst Rechte Daten anzeigen und im Auftrag des Benutzers entschlüsseln, ohne dass zusätzliche Aufrufe an den Dienst durchzuführen sind.  

### <a name="java-wrapper-public-preview"></a>Java-Wrapper (Public Preview)

- Unterstützung für das Nachverfolgen und widerrufen zum Java-Wrapper hinzugefügt
- Datenstrom Unterstützung zum Java-Wrapper hinzugefügt

### <a name="c-api"></a>C-API

- **MIP_FLIGHTING_FEATURE_KEEP_PDF_LINEARIZATION** Flag aus der C-API wurde entfernt.

## <a name="version-17147"></a>Version 1.7.147

### <a name="file-sdk"></a>Datei-SDK

- Kleinere Fehlerbehebung für das pbix-Dateiformat. 

## <a name="version-17145"></a>Version 1.7.145

**Veröffentlichungsdatum:** 13. November 2020

### <a name="general-changes"></a>Allgemeine Änderungen

- Das nuget-Paket wurde aktualisiert, um Abhängigkeiten nur beim Update und nicht immer zu kopieren.
- Die Debugkonfiguration unter .NET verwendet die Releaseversion nativer Bibliotheken. Wir haben festgestellt, dass Kunden, die .net-Lösungen im Debugmodus für Remote Server bereitstellen, die VC + + Debug-Laufzeit installieren müssen, was nicht trivial ist. Wenn Sie in systemeigene Bibliotheken Debuggen müssen, kopieren Sie die DLLs aus dem verteilbaren SDK in den Projektordner (https://ala.ms/mipsdkbins)
- Es wurde ein Fehler behoben, der Warnungen für .net Core-Projekte generierte.

## <a name="version-17133"></a>Version 1.7.133

**Veröffentlichungsdatum**: 23. September 2020

### <a name="general-sdk-changes"></a>Allgemeine SDK-Änderungen

- Public Preview für Java unter Windows und Ubuntu 18,04 verfügbar.
- .Net Core wird jetzt unter Windows unterstützt.
- Unterstützung für die öffentliche Vorschauversion von .net Core unter Ubuntu 18,04.
- Verbesserte lokale Protokollierung für Keystore, wenn der Speicher Cachetyp auf festgelegt ist `OnDiskEncrypted.`
- Aktivierte Feature-flighting für .net-Wrapper
- Das SDK-telemetrieverhalten wurde auf Pre-1,6 zurückgesetzt. Ein minimal Satz von Verwendungs Ereignissen wird jetzt gesendet, wenn nur minimale Telemetriedaten gewählt werden.

### <a name="file-sdk"></a>Datei-SDK

- Korrigieren der UTF-16/UTF-8-Text Konvertierung in `MSGInspector` .
- Legen Sie eine standardmäßige maximale Dateigrößen Beschränkung für Dateien fest, die vom Datei-SDK geschützt werden, auf 6 GB.
  - Änderungen, die aufgrund der Entschlüsselung von großen Dateien vorgenommen wurden *, die mindestens* die Dateigröße im verfügbaren Arbeitsspeicher erfordern.
  - Kann durch eine benutzerdefinierte Einstellung überschrieben werden `max_file_size_for_protection` .
- Unterstützung für linearisierte PDF-Informationen hinzugefügt.
- Es wurde ein Fehler behoben, bei dem LastModifiedDate beim Änderungs Ereignis nicht aktualisiert wurde.
- Es wurde ein Speicherfehler bei der geschützten PDF-Erstellung korrigiert.
- File SDK unterstützt das Sperren von nach verfolgten Dateien.
- `FileEngine::Settings::SetLabelFilter` ist veraltet, verwenden Sie `ConfigureFunctionality` stattdessen.

### <a name="policy-sdk"></a>Richtlinien-SDK

- Das Richtlinien-SDK unterstützt jetzt nur Bezeichnungs Aktionen verschlüsseln.
- Es wurde ein Fehler behoben, der `mip::Identity` nicht ordnungsgemäß aus zwischengespeicherten Engines geladen wurde
- Es wurde ein Fehler behoben, bei dem bei Klassifizierungs-GUID-vergleichen die Groß-/Kleinschreibung in der
- Erweiterte Überwachungs Ereignisse durch Hinzufügen neuer Felder.

### <a name="protection-sdk"></a>Schutz-SDK

- Es wurde ein Fehler behoben, der `mip::Identity` nicht ordnungsgemäß aus zwischengespeicherten Engines geladen wurde
- Implizite Registrierung für neu erstellte Veröffentlichungs Lizenzen hinzugefügt.
- Unterstützung für kryptografische Algorithmen, die zur Unterstützung von DKE in Office-Dateien verwendet werden.
- `documentId`Und `owner` Parameter sind optional.

### <a name="c-apis"></a>C-APIs

- Fehlende Identitäts-und DKE-APIs wurden hinzugefügt.
- Verschieben `AuthDelegate` von Profil zu Modul über alle sdche hinweg
- Veröffentlichungs Richtlinien-SDK-Beispiel für C
- `MIP_CC_CreateProtectionEngineSettingsWithIdentity` ist veraltet, verwenden Sie `MIP_CC_CreateProtectionEngineSettingsWithIdentityAndAuthCallback` stattdessen.
- `MIP_CC_CreateProtectionEngineSettingsWithEngineId` ist veraltet, verwenden Sie `MIP_CC_CreateProtectionEngineSettingsWithEngineIdAndAuthCallback` stattdessen.
- `MIP_CC_CreateProtectionProfileSettings` die Signatur wurde geändert.
- `MIP_CC_CreatePolicyEngineSettingsWithIdentity` ist veraltet, verwenden Sie `MIP_CC_CreatePolicyEngineSettingsWithIdentityAndAuthCallback` .
- `MIP_CC_CreatePolicyEngineSettingsWithEngineId` ist veraltet, verwenden Sie `MIP_CC_CreatePolicyEngineSettingsWithEngineIdAndAuthCallback` .
- `MIP_CC_PolicyEngineSettings_SetLabelFilter` ist veraltet, verwenden Sie `MIP_CC_PolicyEngineSettings_ConfigureFunctionality` .
- `MIP_CC_CreatePolicyProfileSettings` die Signatur wurde geändert.

### <a name="breaking-changes"></a>Aktuelle Änderungen

#### <a name="common"></a>Allgemein

- `TelemetryConfiguration::isTelemetryOptedOut` wurde in `isMinimalTelemetryEnabled` umbenannt. 

#### <a name="c-api"></a>C-API

- `mip_cc_document_state` wurde mit einem neuen Wert aktualisiert `mip_cc_metadata_version_format` contentMetadataVersionFormat

## <a name="version-16103"></a>Version 1.6.103

**Veröffentlichungsdatum**: 16. April 2020

### <a name="general-sdk-changes"></a>Allgemeine SDK-Änderungen

- TLS 1,2 wird für alle nicht-ADRMS-http-Kommunikationssysteme erzwungen.
- Migrierte IOS/macOS-http-Implementierung von NSURLConnection zu nsurlsession.
- Migrierte IOS-telemetriekomponente vom Aria SDK in das 1Ds SDK.
- Die telemetriekomponente verwendet nun den httpdelegaten von MIP unter IOS, macOs und Linux. (Bisher nur Win32).
- Verbesserte Typsicherheit für die C-API.
- Authdelegat wurde aus dem Profil in die Engine in den C++-, c#-und Java-APIs verschoben.
- Authdelegat wurde von Konstruktor von `Profile::Settings` in verschoben `Engine::Settings` .
- Kategorie zu nopolicyerror hinzugefügt, um weitere Informationen zur Ursache für die Fehler bei der Richtlinien Synchronisierung bereitzustellen
- Hinzugefügte `PolicyEngine::GetTenantId` Methode.
- Explizite Unterstützung für alle Clouds hinzugefügt.
  - Neue `Engine::Settings::SetCloud` Methode zum Festlegen der zielcloud (gcc High, 21-vianet usw.).
  - Ein vorhandener `Engine::Settings::SetCloudEndpointBaseUrl` Methoden aufrufbedarf ist für erkannte Clouds nicht mehr erforderlich.
- Aktivierter Bitcode für IOS-Binärdateien.

### <a name="file-sdk"></a>Datei-SDK

- `IFileHandler::InspectAsync`Zu c#-und Java-Wrapper hinzugefügt
- Neue Unterstützung `FileProfile::AcquirePolicyAuthToken` für das Auslösen der Richtlinien Token-Erfassung, damit eine Anwendung den Tokencache bereinigen kann.    
- `MsgInspector::GetAttachments` gibt `vector<shared_ptr<MsgAttachmentData>>` anstelle von zurück. `vector<unique_ptr<MsgAttachmentData>>`
- `TelemetryConfiguration::isOptedOut` durch die Einstellung wird die Telemetrie nun vollständig deaktiviert. Zuvor wurde ein Satz minimaler Telemetriedaten gesendet.

### <a name="policy-sdk"></a>Richtlinien-SDK

- Neue Unterstützung für das Auslösen der tokenübernahme, damit eine Anwendung den Tokencache über abrufen kann `PolicyProfile::AcquireAuthToken` .
- Hyok-Bezeichnungen werden standardmäßig gefiltert.
- Die den gelöschten Bezeichnungen zugeordneten Metadaten werden nun entfernt.
- Wenn eine zwischengespeicherte Bezeichnungs Richtlinie und vertraulichkeitsrichtlinie nicht übereinstimmen, wird der Richtlinien Cache nun gelöscht.
- Neue Unterstützung für Versionierte Metadaten:
  - Ein Dateiformat kann den Speicherort bzw. das Format seiner Bezeichnungs Metadaten aufweisen. In diesem Fall sollte eine Anwendung MIP mit allen Metadaten bereitstellen, und MIP bestimmt, welche Metadaten "true" sind.
  - `ContentLabel::GetExtendedProperties` gibt jetzt `vector<MetadataEntry>` anstelle von zurück `vector<pair<string, string>>` .
  - `MetadataAction::GetMetadataToAdd` gibt jetzt `vector<MetadataEntry>` anstelle von zurück `vector<pair<string, string>>` .
  - `ExecutionState::GetContentMetadata` sollte jetzt `vector<MetadataEntry>` anstelle von zurückgeben `vector<pair<string, string>>` .
  - `ExecutionState::GetContentMetadataVersion` Gibt die höchste Version der Metadaten zurück, die die Anwendung für das aktuelle Dateiformat erkennt (normalerweise 0).
  - `PolicyEngine::GetWxpMetadataVersion` Gibt die Metadatenversion für Office-Dokumente gemäß der Konfiguration durch den Mandanten Administrator zurück (0 = Standard, 1 = coauth-fähiges Format).
  - Äquivalente Änderungen in der C-API:
    - `MIP_CC_ContentLabel_GetExtendedProperties`
    - `MIP_CC_MetadataAction_GetMetadataToAdd`
    - `mip_cc_metadata_callback`
    - `mip_cc_document_state`
    - `MIP_CC_PolicyEngine_GetWxpMetadataVersion`
- `TelemetryConfiguration::isOptedOut` durch die Einstellung wird die Telemetrie nun vollständig deaktiviert. Zuvor wurde ein Satz minimaler Telemetriedaten gesendet. 

### <a name="protection-sdk"></a>Schutz-SDK

- Neue Unterstützung für Registrierung und Sperrung der doc-Nachverfolgung.
- Neue Unterstützung für das Erstellen einer vorab Lizenz beim veröffentlichen.
- Verfügbar gemachte öffentliches Microsoft TLS-Zertifikat, das von Protection Service verwendet wird.
   - `GetMsftCert` und `GetMsftCertPEM`
   - Wenn eine Anwendung die `HttpDelegate` Schnittstelle überschreibt, muss Sie von dieser Zertifizierungsstelle ausgegebene Server Zertifikate als vertrauenswürdig einstufen
   - Diese Anforderung wird voraussichtlich spät in 2020 entfernt.    

## <a name="version-15124"></a>Version 1.5.124

**Veröffentlichungsdatum**: 2. März 2020

### <a name="general-sdk-changes"></a>Allgemeine SDK-Änderungen

- Java-API (nur Windows)
- Abbruch von asynchronen MIP-Tasks
  - Alle Async-Aufrufe geben MIP:: AsyncControl-Objekt mit einer Cancel ()-Methode zurück.
- Verzögerte Laden abhängiger Binärdateien
- Wahlweise bestimmte Telemetrie-/Überwachungseigenschaften maskieren
   - Konfigurierbar über MIP:: telemetryconfiguration:: maskedproperties
- Verbesserte Ausnahmen:
  - Alle Fehler enthalten Handlungs abhängige Korrelations-IDs in der Beschreibungs Zeichen
  - Netzwerkfehler enthält Felder "Category", "BaseURL", "RequestId" und "Statuscode".
- Verbessertes Ergebnis/Fehlerdetails der C-API

### <a name="file-sdk"></a>Datei-SDK

- Netzwerkfreie Überprüfung, ob die Datei gekennzeichnet oder geschützt ist
  - MIP:: fileHandler:: islabeledorprotected ()
  - Geringfügige Gefahr von falsch positiven Ergebnissen (z. b. wenn die Datei Zombie-Bezeichnungs Metadaten enthält)
- Filtern von Bezeichnungen, die bestimmten Schutz Typen zugeordnet sind
  - Konfigurierbar über MIP:: fileengine:: Settings:: setlabelfilter ()
- Verfügbar machen von Richtlinien Daten für die Datei-API
  - MIP:: fileengine:: getpolicydataxml ()

### <a name="policy-sdk"></a>Richtlinien-SDK

- Markierung dynamischer Inhalte für Wasserzeichen/Kopfzeile/Footer-Aktionen:
  - Felder wie "$ {Item. Label}", "$ {Item.Name}", "$ {User.Name}", "$ {Event. DateTime}" werden automatisch durch MIP aufgefüllt.
  - MIP:: Identity kann mit einem benutzerfreundlichen Namensfeld erstellt werden, das von der Markierung dynamischer Inhalte verwendet wird.
  - Konfigurierbar über MIP::P olicyengine:: Settings:: setvariabletextmarkingtype ()
- Netzwerkfreie Überprüfung, wenn der Inhalt gekennzeichnet ist
  - MIP::P olicyhandler:: isbezeichnung ()
  - Geringes Risiko von falsch positiven Ergebnissen (z. b. wenn Inhalt Zombie-Bezeichnungs Metadaten enthält)
- Gültigkeitsdauer Cache-TTL
  - Standard: 30 Tage
  - Konfigurierbar über MIP::P olicyprofile:: setcustomsettings ()
- **Wichtige Änderung**
  - "Policyengine. Settings. labelfilter" wurde aus der Liste der Enumerationen in das Bitfeld "Werte zulässt" aktualisiert.

### <a name="protection-sdk"></a>Schutz-SDK

- Pre-License
  - Das vorhanden sein einer vorab Lizenz neben verschlüsseltem Inhalt ermöglicht die Offline Entschlüsselung von Inhalten, zusammen mit einem zuvor abgerufenen Benutzerzertifikat.
  - MIP::P rotectionhandler:: consumptionsettings kann mit einer Pre-License erstellt werden.
  - MIP::P rotectionengine:: loadusercert | Async () Ruft das Benutzerzertifikat ab, das gemäß MIP::P rotectionprofile-Cache Richtlinie gespeichert wird.
- Server spezifische Funktionsüberprüfung
  - Überprüft, ob der Mandant des Benutzers "nur verschlüsseln" (nur in Azure RMS verfügbar) unterstützt.
  - MIP::P rotectionengine:: isfeaturesupported ()
- Umfangreichere Details beim Abrufen von RMS-Vorlagen
- **Wichtige Änderungen**
  - `mip::ProtectionEngine::GetTemplates()``vector<shared_ptr<string>>`Rückgabewert ersetzt durch `vector<shared_ptr<mip::TemplateDescriptor>>` (C++)
  - `mip::ProtectionEngine::Observer::OnGetTemplatesSuccess()` Rückruf `shared_ptr<vector<string>>` Parameter ersetzt durch `vector<shared_ptr<mip::TemplateDescriptor>>` (C++)
  - Ischutzengine. gettemplates | Der async ()-Rückgabewert wurde durch `List<string>` ersetzt `List<TemplateDescriptor>` . (C#)
  - MIP_CC_ProtectionEngine_GetTemplates () mip_cc_guid * param ersetzt durch mip_cc_template_descriptor * (C-API)

### <a name="c-api"></a>C-API

- Wichtige **Änderungen**: die meisten Funktionen wurden aktualisiert, sodass Sie mip_cc_error *-Parameter enthalten, kann NULL sein.
  

### <a name="errorexception-updates"></a>Fehler-/Ausnahme-Updates

- Zusammenfassung der Fehlerbehandlung:
  - Accessdeniederror: dem Benutzer wurden keine Zugriffsrechte für den Inhalt erteilt.
      - Noauthtokenerror: die APP hat kein Authentifizierungs Token bereitgestellt.
      - Nopermissionserror: dem Benutzer wurden keine Rechte für bestimmte Inhalte erteilt, aber Referrer/owner ist verfügbar.
      - Servicedisablederror: der Dienst ist für Benutzer/Gerät/Plattform/Mandant deaktiviert.
  - Adhucschutzrequirements derror: Ad-hoc-Schutz muss festgelegt werden, bevor eine Bezeichnung festgelegt wird.
  - Badinputerror: Ungültige Eingabe von Benutzer/App
      - Insuffizientbuffererror: Ungültige Puffer Eingabe von Benutzer/App
      - Labeldisablederror: die Bezeichnungs-ID wurde erkannt, aber für die Verwendung deaktiviert.
      - Labelnotfounderror: Unbekannte Bezeichnungs-ID
      - Templatenotfounderror: Unbekannte Vorlagen-ID
  - Genehmideniederror: für einen Vorgang, der Zustimmung von Benutzer/App erforderte, wurde keine Zustimmung erteilt.
  - Deprecatedapierror: Diese API ist veraltet.
  - Fehler beim Lesen/Schreiben der Datei.
  - InternalError: Unerwarteter interner Fehler.
  - NetworkError
      - Proxyauthenticationerror: Proxy Authentifizierung ist erforderlich.
    - Category = badresponse: der Server hat eine nicht lesbare HTTP-Antwort zurückgegeben (Wiederholung ist möglicherweise erfolgreich)
    - Category = abgebrochen: Es konnte keine HTTP-Verbindung hergestellt werden, da der Vorgang vom Benutzer/der APP abgebrochen wurde (die Wiederholung ist wahrscheinlich erfolgreich).
    - Category = failureresponsecode: der Server hat eine generische Fehler Antwort zurückgegeben (Wiederholungsversuch ist möglicherweise erfolgreich).
    - Category = NOCONNECTION: Fehler beim Herstellen einer HTTP-Verbindung (Wiederholungsversuch ist möglicherweise erfolgreich)
    - Category = offline: Fehler beim Herstellen einer HTTP-Verbindung, weil sich die Anwendung im Offline Modus befindet (Wiederholung nicht erfolgreich).
    - Kategorie = Proxy: Fehler beim Herstellen einer HTTP-Verbindung aufgrund eines Proxy Problems (Wiederholungsversuch ist wahrscheinlich nicht erfolgreich).
    - Kategorie = SSL: Fehler beim Herstellen einer HTTP-Verbindung aufgrund eines SSL-Problems (Wiederholungsversuch ist wahrscheinlich nicht erfolgreich).
    - Category = Throttled: der Server hat die Antwort "gedrosselt" zurückgegeben (Backoff/Wiederholung wird wahrscheinlich erfolgreich ausgeführt).
    - Category = Timeout: Fehler beim Herstellen einer HTTP-Verbindung nach einem Timeout (die Wiederholung wird wahrscheinlich erfolgreich ausgeführt)
    - Category = unexpectedresponse: der Server hat unerwartete Daten zurückgegeben (Wiederholungsversuch ist möglicherweise erfolgreich).
  - Nopolicyerror: Mandant oder Benutzer ist nicht für Bezeichnungen konfiguriert.
  - Notsupportederror: Vorgang wird im aktuellen Zustand nicht unterstützt.
  - Operationcancellederror: der Vorgang wurde abgebrochen.
  - Privilegedrequirederror: Bezeichnung kann nur geändert werden, wenn die Zuweisungs Methode = privilegierter ist.
- Änderungen
  - Nicht verwendeter policysyncerror wurde entfernt. Ersetzt durch Network Error
  - Nicht verwendeter transientnetworkerror wurde entfernt. Ersetzt durch Network error-Kategorien

## <a name="version-140"></a>Version 1.4.0 

**Veröffentlichungsdatum**: 6. November 2019

Mit dieser Version wird die Unterstützung für das Schutz-SDK im .net-Paket (Microsoft. informationprotection. File) eingeführt.

### <a name="sdk-changes"></a>SDK-Änderungen
- Leistungsverbesserungen und Fehlerbehebungen
- Umbenannte StorageType-Aufzählung in cachestoragetype
- Android Links zu libc + + anstelle von gnustl
- Zuvor als veraltet markierte APIs entfernt
  - File/Policy/profile:: Settings muss mit einem mipcontext initialisiert werden.
  - Datei/Richtlinie/Profil:: Einstellungs Pfad, Anwendungsinformationen, Protokollierungs Delegat, Telemetrie und Protokollierungsebene: Getters/Setter wurden entfernt. Diese Eigenschaften werden von mipcontext verwaltet.
- Bessere Unterstützung statischer Bibliotheken auf Apple-Plattformen
  - Monolithische statische Bibliotheken
    - libmip_file_sdk_static. a
    - libmip_upe_sdk_static. a
    - libmip_protection_sdk_static. a
    - libmip_upe_and_protection_sdk_static. a
  - in separate Bibliotheken extrahierte Abhängigkeiten von Drittanbietern
    - libsqlite3. a
    - libssl. a
- Entfernte mip_telemetry.dll (zusammengeführt in mip_core.dll)

### <a name="file-sdk"></a>Datei-SDK

- RPMSG
  - Verschlüsselung
  - Unterstützung für die String8-Entschlüsselung hinzugefügt
- Konfigurierbares Pfile-Erweiterungs Verhalten (Standard, <EXT> . Pfile oder P <EXT> )
  - Schutz Settings:: setpfileextensionbehavior

### <a name="policy-sdk"></a>Richtlinien-SDK

- Complete-C-API
- Konfigurieren der Filterung von mit dem Schutz verknüpften Bezeichnungen
  - Policyengine:: settigns:: setlabelfilter ()

### <a name="protection-sdk"></a>Schutz-SDK

- Zuvor als veraltet markierte APIs entfernt
  - Entfernen von Schutz-Engine:: forateschutzhandlerfromdescriptor [Async] (Verwenden von schutzengine:: forateschutzhandlerforpublishing [Async])
  - Entfernen von Schutz-Engine:: forateschutzhandlerfrompublishinglicense [Async] (Verwenden von schutzengine:: forateschutzhandlerforverbrauch [Async])
- Vervollständigen der c#-API
- Complete-C-API
  - C-API-normalisierungs Änderungen von v 1.3 C API Preview:
    - Umbenannte mip_cc_storage_type in mip_cc_cache_storage_type
    - Umbenannte MIP_CC_AddProtectionProfileEngine in MIP_CC_ProtectionProfile_AddEngine
    - Umbenannte MIP_CC_CreateProtectionEngineSettingsForExistingEngine in MIP_CC_CreateProtectionEngineSettingsWithEng
    - Umbenannte MIP_CC_CreateProtectionEngineSettingsForNewEngine in MIP_CC_CreateProtectionEngineSettingsWithIdentity
    - Umbenannte MIP_CC_SetProtectionProfileSettingsHttpDelegate in MIP_CC_ProtectionProfileSettings_SetHttpDelegate
    - Umbenannte MIP_CC_CreateProtectionHandlerForConsumption in MIP_CC_ProtectionEngine_CreateProtectionHandlerForConsumption
    - Umbenannte MIP_CC_CreateProtectionHandlerForPublishing in MIP_CC_ProtectionEngine_CreateProtectionHandlerForPublishing
    - Umbenannte MIP_CC_GetProtectionEngineId in MIP_CC_ProtectionEngine_GetEngineId
    - Umbenannte MIP_CC_GetProtectionEngineTemplates in MIP_CC_ProtectionEngine_GetTemplates
    - Umbenannte MIP_CC_GetProtectionEngineTemplatesSize in MIP_CC_ProtectionEngine_GetTemplatesSize
    - Umbenannte MIP_CC_SetTelemetryConfigurationHttpDelegate in MIP_CC_TelemetryConfiguration_SetHttpDelegate
    - Umbenannte MIP_CC_SetTelemetryConfigurationHostName in MIP_CC_TelemetryConfiguration_SetHostName
    - Umbenannte MIP_CC_SetTelemetryConfigurationIsLocalCachingEnabled in MIP_CC_TelemetryConfiguration_SetIsLocalCachingEnabled
    - Umbenannte MIP_CC_SetTelemetryConfigurationIsNetworkDetectionEnabled in MIP_CC_TelemetryConfiguration_SetIsNetworkDetectionEnabled
    - Umbenannte MIP_CC_SetTelemetryConfigurationIsTelemetryOptedOut in MIP_CC_TelemetryConfiguration_SetIsTelemetryOptedOut
    - Umbenannte MIP_CC_SetTelemetryConfigurationLibraryName in MIP_CC_TelemetryConfiguration_SetLibraryName
    - MIP_CC_ProtectionEngine_GetRightsForLabelIdSize und aktualisierte MIP_CC_ProtectionEngine_GetRightsForLabelId zum Auffüllen eines mip_cc_string_list anstelle eines durch Trennzeichen getrennten Zeichen folgen Puffers entfernt
    - MIP_CC_ProtectionHandler_GetRightsSize und aktualisierte MIP_CC_ProtectionHandler_GetRights zum Auffüllen eines mip_cc_string_list anstelle eines durch Trennzeichen getrennten Zeichen folgen Puffers entfernt
    - Es wurden MIP_CC_ProtectionEngine_GetEngineIdSize und aktualisierte MIP_CC_ProtectionEngine_GetEngineId hinzugefügt, um einen Zeichen folgen Puffer anstelle eines-mip_cc_guid aufzufüllen.
    - MIP_CC_CreateProtectionDescriptorFromUserRights jetzt ' mip_cc_dictionary-' param anstelle von ' mip_cc_dictionary '.
    - MIP_CC_ProtectionEngineSettings_SetCustomSettings jetzt ' mip_cc_dictionary-' param anstelle von ' mip_cc_dictionary '.
    - MIP_CC_ProtectionProfileSettings_SetCustomSettings jetzt ' mip_cc_dictionary-' param anstelle von ' mip_cc_dictionary '.
    - MIP_CC_TelemetryConfiguration_SetCustomSettings jetzt ' mip_cc_dictionary-' param anstelle von ' mip_cc_dictionary '.
    - MIP_CC_CreateMipContext nimmt die Parameter ' isofflineonly ' und ' loggerdelegateoverride ' an.


## <a name="version-130"></a>Version 1.3.0

**Veröffentlichungsdatum**: 22. August 2019

### <a name="new-features"></a>Neue Funktionen

- `mip::MipContext` ist das neue Objekt der höchsten Ebene.
- Das Entschlüsseln geschützter Nachrichten Dateien wird jetzt unterstützt.
- Die Überprüfung von Message. rpmsg-Dateien wird über und unterstützt `mip::FileInspector` `mip::FileHandler::InspectAsync()` .
- Der Cache auf dem Datenträger kann jetzt optional verschlüsselt werden.
- Das Schutz-SDK unterstützt jetzt chinesische cloudkunden.
- Arm64-Unterstützung unter Android.
- Arm64e-Unterstützung unter IOS.
- Der Eul-Cache (Endbenutzer Lizenz) kann jetzt deaktiviert werden.
- die Pfile-Verschlüsselung kann über `mip::FileEngine::EnablePFile`
- Verbesserte Leistung für Schutz Vorgänge durch Reduzieren der Anzahl von HTTP-aufrufen
- Die Delegierten Identitäts Details wurden aus entfernt `mip::Identity` und stattdessen `DelegatedUserEmail` zu `mip::FileEngine::Settings` , `mip::ProtectionSettings` , `mip::PolicyEngine::Settings` und `mip::ProtectionHandler` `PublishingSettings` `ConsumptionSettings` hinzugefügt.
- Funktionen, die zuvor LabelId zurückgegeben haben, geben nun ein- `mip::Label` Objekt zurück

### <a name="changes"></a>Änderungen

* In früheren Versionen war es erforderlich, dass Sie aufgerufen haben `mip::ReleaseAllResources` . Version 1,3 ersetzt dies durch `mip::MipContext::~MipContext` oder `mip::MipContext::Shutdown` .
* `ActionSource`Aus `mip::LabelingOptions` und entfernt`mip::ExecutionState::GetNewLabelActionSource`
* Ersetzt `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptor` durch `mip::ProtectionEngine::CreateProtectionHandlerForPublishing` .
* Ersetzt `mip::ProtectionEngine::CreateProtectionHandlerFromPublishingLicense` durch `mip::ProtectionEngine::CreateProtectionHandlerForConsumption` .
* Wurde `mip::PublishingLicenseContext` in umbenannt `mip::PublishingLicenseInfo` und in aktualisiert, sodass Sie umfangreiche Felder anstelle von rohserialisierten Bytes enthalten.
* `mip::PublishingLicenseInfo` enthält die für MIP relevanten Daten nach dem Testen einer Veröffentlichungs Lizenz (PL).
* `mip::TemplateNotFoundError` und ausgelöst `mip::LabelNotFoundError` , wenn die Anwendung MIP eine Vorlagen-ID oder Bezeichnungs-ID übergibt, die nicht erkannt wird.
* Unterstützung für den Bezeichnungs basierten bedingten Zugriff über den claims-Parameter von und wurde hinzugefügt `AcquireToken()` `mip::AuthDelegate::OAuth2Challenge()` . Diese Funktionalität wurde noch nicht über das Security and Compliance Center-Portal verfügbar gemacht.


## <a name="version-120"></a>Version 1.2.0

**Veröffentlichungsdatum**: 15. April 2019

### <a name="new-features"></a>Neue Funktionen

 - Die telemetriekomponente verwendet jetzt denselben HTTP-Stapel wie der restliche MIP, auch wenn Sie von der Client Anwendung mit httpdelegaten überschrieben wurde.
 - Client Anwendungen können das Threading Verhalten von asynchronen Aufgaben steuern, indem Sie taskdispatcherdelegat in Profilen überschreiben.
 - Rpmsg-Verschlüsselung ist jetzt als Vorschau verfügbar.
 - Datei-/richtliniensdk-Ausnahme Behandlungs Verhalten mit Protection SDK ausrichten:
    - Proxyautherror wird von allen sDas ausgelöst, wenn ein Proxy so konfiguriert ist, dass eine Authentifizierung erforderlich ist.
    - Noauthtokenerror wird von allen SDKs ausgelöst, wenn ein leeres Authentifizierungs Token durch die Implementierung von MIP:: authdelegaten:: AcquireOAuth2Token der Anwendung bereitgestellt wird.
 - Verbessertes http-Caching für das Richtlinien-SDK reduziert die Anzahl der erforderlichen http-Aufrufe um die Hälfte.
 - Umfangreichere Protokolle/Überwachung/Telemetrie für verbesserte Fehlererkennung und-Debuggen.
 - Unterstützung für externe/fremde Bezeichnungen, um die Migration zu AIP-Bezeichnungen zu vereinfachen.
 - Unterstützung für Drittanbieter Anwendungen zum Herunterladen von Vertraulichkeits Typen von SCC.
 - Weitere telemetrieeinstellungen werden offengelegt und konfigurierbar (Caching/Threading Verhalten usw.).
 
### <a name="sdk-changes"></a>SDK-Änderungen

 - mip_common.dll in mip_core.dll und mip_telemetry.dll aufgeteilt.
 - In MIP:: contentstate in MIP::D atastate wurde umbenannt, um zu beschreiben, wie eine Anwendung auf hoher Ebene mit Daten interagiert.
 - MIP:: adhucschutzrequirements derror-Ausnahme wird von fileHandler:: setlabel ausgelöst, um eine Anwendung zu benachrichtigen, dass Sie zunächst Ad-hoc-Schutz anwenden muss, bevor eine Bezeichnung angewendet wird.
 - die MIP:: operationcancellederror-Ausnahme wird ausgelöst, wenn ein Vorgang abgebrochen wurde (z. b. aufgrund eines herunter Fahrens oder eines HTTP-Abbruchs).
 - Neue APIs:
    - MIP:: classificationresult:: getsensitiveinformationerkenctions
    - MIP:: fileengine:: getlastpolicyfetchtime
    - MIP:: fileengine:: getdefaultsensitivitylabel
    - MIP:: fileengine:: getpolicyid
    - MIP:: fileengine:: hasclassificationrules
    - MIP:: fileengine:: Settings:: setpolicycloudendpointbaseurl
    - MIP:: fileHandler:: getdecryptedtemporaryfileasync
    - MIP:: fileHandler:: Observer:: ongetdecryptedtemporaryfilefailure
    - MIP:: fileHandler:: Observer:: ongetdecryptedtemporaryfilesuccess
    - MIP:: File/Policy/Schutzprofile:: settaskdispatcherdelegat
    - MIP:: File/Policy/Schutzprofile:: settelemetryconfiguration
    - MIP:: HttpRequest:: GetBody gibt Std:: Vector<uint8_t> anstelle von Std:: String zurück.
    - MIP:: HttpRequest:: GetId
    - MIP::P olicyengine:: getlastpolicyfetchtime
    - MIP::P olicyengine:: getpolicyid
    - MIP::P olicyengine:: hasclassificationrules
    - MIP::P olicyengine:: Settings:: setcloudendpointbaseurl
    - MIP::P rotectiondescriptor:: getContentID
    - (Interface) MIP:: taskdispatcherdelegat
 
### <a name="new-requirements"></a>Neue Anforderungen
 - MIP:: ReleaseAllResources muss vor der Beendigung des Prozesses aufgerufen werden (nach dem Löschen von Verweisen auf alle Profile, Engines und Handler).
 - (Interface) MIP:: executionstate:: getclassificationresults-Rückgabetyp und classificationids-Parameter wurden geändert.
 - (Interface) MIP:: fileexecutionstate:: getauditmetadata kann von Anwendungen implementiert werden, um ausführliche Informationen anzugeben, die auf dem Überwachungs Dashboard eines Mandanten Administrators angezeigt werden sollen (z. b. Absender, Empfänger, zuletzt geändert usw.).
 - (Interface) MIP:: fileexecutionstate:: getclassificationresults-Rückgabetyp wurde geändert und erfordert nun einen fileHandler-Parameter.
 - (Interface) MIP:: fileexecutionstate:: getdatastate sollte von Anwendungen implementiert werden, um anzugeben, wie eine Anwendung mit contentIdentifier interagiert.
 - (Interface) MIP:: httpdelegorschnittstelle erfordert die Methoden "CancelOperation" und "cancelalloperations".
 - (Interface) MIP:: httpdelegatschnittstelle "Send" und "SendAsync" geben MIP:: httpoperation anstelle von "MIP:: HttpResponse" zurück.
 - (Interface) MIP:: HttpResponse:: GetBody gibt Std:: Vector<uint8_t> anstelle von Std:: String zurück.
 - (Interface) MIP:: HttpResponse-Schnittstelle erfordert die Implementierung der GetId-Methode.
 - MIP:: contentlabel:: getkreationtime gibt Std:: Chrono:: time_point anstelle von Std:: String zurück.
 - MIP:: fileengine:: up filehandlerasync akzeptiert nicht mehr den Parameter "contentIdentifier".
 - MIP::P olicyhandler:: notifycommitedactions umbenannt in MIP::P olicyhandler:: notifycommittedactions


## <a name="version-110"></a>Version 1.1.0 

**Veröffentlichungsdatum**: 15. Januar 2019

Mit dieser Version wird die Unterstützung für die folgenden Plattformen eingeführt:

  - .NET
  - IOS SDK (Policy SDK)
  - Android SDK (Richtlinien-SDK und Schutz-SDK)

### <a name="new-features"></a>Neue Funktionen

- ADRMS-Unterstützung
- Schutz-SDK-Vorgänge sind tatsächlich asynchron (auf Win32) und ermöglichen gleichzeitige, nicht blockierende Verschlüsselungs-/Entschlüsselungs Vorgänge.
  - Anwendungs Rückrufe (authdelegat, httpdelegat usw.) können jetzt für einen beliebigen Hintergrund Thread aufgerufen werden.
- Von IT-Administratoren festgelegte benutzerdefinierte Bezeichnungs Eigenschaften können jetzt über MIP:: Label:: getcustomsettings gelesen werden.
- Die serialisierte Veröffentlichungs Lizenz kann jetzt direkt aus einer Datei ohne http-Vorgänge über MIP:: fileHandler:: getserializedpublishinglicense abgerufen werden.
- Anwendungen werden benachrichtigt, ob ein HTTP-Vorgang erforderlich ist, um die Erstellung eines MIP:: fileengine/MIP::P olicyengine über MIP:: fileprofile:: Observer:: onaddpolicyenginestarting/MIP::P olicyprofile:: Observer:: onaddenginestarting abzuschließen.
- Die Erkennung, ob geschützte Inhalte ein Ablaufdatum aufweisen oder nicht, wurde mit der Hilfsmethode "MIP::P rotectiondescriptor::D oescontentexpire" vereinfacht.
- Klassifizierung:
  - Empfindlichkeits Typen (Regex-Ausdrücke für CC-, Passport # s usw.) können vom SCC-Dienst abgerufen werden.
    - Aktivieren Sie das Feature, indem Sie MIP:: fileengine:: Settings/MIP::P olicyengine:: Settings-Flag festlegen.
    - Lese Typen über MIP:: fileengine:: listsensitivitytypes/MIP::P olicyengine:: listsensitivitytypes
  - Klassifizierungs Ergebnisse aus externen Dokumentenscanner können per MIP an MIP weitergeleitet werden, um empfohlene/erforderliche Bezeichnungen basierend auf Dokument Inhalten zu steuern.
    - Ergebnisse an MIP über MIP:: fileexecutionstate:: getclassificationresults/MIP:: executionstate:: getclassificationresults übergeben
    - MIP:: applylabelaction und MIP:: RecommendLabelAction können von MIP::P olicyengine:: computeactions zurückgegeben werden, wenn Klassifizierungs Ergebnisse einer Richtlinien Regel entsprechen, die erforderliche/Empfohlene Bezeichnungen anzeigt.

### <a name="new-requirements"></a>Neue Anforderungen 

  - Erzwungene Auffüllung von ID/Name-/Versionsfeldern MIP:: ApplicationInfo beim Erstellen von MIP:: fileprofile, MIP::P olicyprofile und MIP::P rotectionprofile
  - Anwendungen müssen beim Erstellen von MIP:: filehandlers die neue MIP:: fileexecutionstate-Schnittstelle implementieren.
  
### <a name="new-exceptions"></a>Neue Ausnahmen 

  - MIP:: noauthtokenerror wird ausgelöst, wenn der authdelegat der Anwendung ein leeres Token zurückgibt (aufgrund eines Abbruchs).
    - Gilt für die Erstellung von:
      - mip::FileEngine
      - mip::FileHandler
      - mip::PolicyEngine
      - mip::ProtectionHandler
  - MIP:: nopolicyerror wird ausgelöst, wenn der Mandant nicht für Bezeichnungen konfiguriert ist.
    - Gilt für die Erstellung von:
      - mip::FileEngine
      - mip::PolicyEngine
  - MIP:: servicedisablederror wird ausgelöst, wenn der RMS-Dienst für einen bestimmten Benutzer/Gerät/Plattform/Mandanten deaktiviert ist.
    - Gilt für die Erstellung von:
      - mip::FileHandler
      - mip::ProtectionHandler
  - MIP:: nopermissionserror wird ausgelöst, wenn ein Benutzer nicht über die Berechtigung zum Entschlüsseln eines Dokuments verfügt oder der Inhalt abgelaufen ist.
    - Gilt für die Erstellung von:
      - mip::FileHandler
      - mip::ProtectionHandler

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu unterstützten Plattformen und mehr finden Sie unter [FAQs und Probleme im MIP SDK](faqs-known-issues.md) .
- Informationen zu den ersten Schritten mit dem MIP SDK finden Sie unter [MIP SDK-Setup und Konfiguration](setup-configure-mip.md) .
