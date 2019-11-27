---
title: Versions Veröffentlichungs Verlauf und Unterstützungs Richtlinie für das Microsoft Information Protection (MIP) SDK
description: Verison-releaseverlauf und Änderungs Hinweise für das MIP SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 11/25/2019
ms.author: mbaldwin
manager: barbkess
ms.openlocfilehash: a678765835785dcb40aaf65e7f92e78fba67c73a
ms.sourcegitcommit: 487e681c9683b8adb7ae6fcfb374830bf0e5ad72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74479111"
---
# <a name="microsoft-information-protection-mip-sdk-version-release-history-and-support-policy"></a>Versions Veröffentlichungs Verlauf und Unterstützungs Richtlinie für das Microsoft Information Protection (MIP) SDK

## <a name="servicing"></a>Deten 

Jede allgemein verfügbare Version (General Availability, GA) wird sechs Monate lang unterstützt, nachdem die nächste GA-Version veröffentlicht wurde. In der Dokumentation sind möglicherweise keine Informationen zu nicht unterstützten Versionen enthalten. Korrekturen und neue Funktionen werden nur auf die neueste Version der allgemeinen Verfügbarkeit angewendet.

Vorschau Versionen sollten nicht in der Produktionsumgebung bereitgestellt werden. Verwenden Sie stattdessen die neueste Vorschauversion, um neue Funktionen oder Korrekturen zu testen, die in der nächsten GA-Version verfügbar sind. Nur die aktuelle Vorschauversion wird unterstützt.

## <a name="release-history"></a>Verlauf der Releases

Verwenden Sie die folgenden Informationen, um zu sehen, was für eine unterstützte Version neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. 

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn Sie also ein Problem mit dem SDK haben, sollten Sie überprüfen, ob es mit der neuesten Version der allgemeinen Verfügbarkeit behoben ist. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion.
>  
> Technische Unterstützung finden Sie im [Stack Overflow Microsoft Information Protection-Forum](https://stackoverflow.com/questions/tagged/microsoft-information-protection). 

## <a name="version-140"></a>Version 1.4.0 

**Veröffentlichungsdatum**: 6. November 2019

Mit dieser Version wird die Unterstützung für die Schutz-API im .net-Paket (Microsoft. informationprotection. File) eingeführt.

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
- Mip_telemetry. dll (zusammengeführt in mip_core. dll) wurde entfernt.

### <a name="file-api"></a>File-API

- RPMSG
  - Verschlüsselung
  - Unterstützung für die String8-Entschlüsselung hinzugefügt
- Konfigurierbares Pfile-Erweiterungs Verhalten (Standard, <EXT>. Pfile oder P<EXT>)
  - Schutz Settings:: setpfileextensionbehavior

### <a name="policy-api"></a>Policy-API

- Complete-C-API
- Konfigurieren der Filterung von mit dem Schutz verknüpften Bezeichnungen
  - Policyengine:: settigns:: setlabelfilter ()

### <a name="protection-api"></a>Protection-API

- Zuvor als veraltet markierte APIs entfernt
  - Entfernen von Schutz-Engine:: forateschutzhandlerfromdescriptor [Async] (Verwenden von schutzengine:: forateschutzhandlerforpublishing [Async])
  - Entfernen von Schutz-Engine:: forateschutzhandlerfrompublishinglicense [Async] (Verwenden von schutzengine:: forateschutzhandlerforverbrauch [Async])
- Complete C# API
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
- Die Überprüfung von Message. rpmsg-Dateien wird über `mip::FileInspector` und `mip::FileHandler::InspectAsync()`unterstützt.
- Der Cache auf dem Datenträger kann jetzt optional verschlüsselt werden.
- Die Schutz-API unterstützt jetzt China-Sovereign Cloud.
- Arm64-Unterstützung unter Android.
- Arm64e-Unterstützung unter IOS.
- Der Eul-Cache (End User License) kann jetzt deaktiviert werden.
- die Pfile-Verschlüsselung kann über `mip::FileEngine::EnablePFile` deaktiviert werden.
- Verbesserte Leistung für Schutz Vorgänge durch Reduzieren der Anzahl von HTTP-aufrufen
- Die Details der Delegierten Identität wurden aus `mip::Identity` entfernt, und stattdessen wurden `DelegatedUserEmail` zu `mip::FileEngine::Settings`, `mip::ProtectionSettings`, `mip::PolicyEngine::Settings`und `mip::ProtectionHandler``PublishingSettings` und `ConsumptionSettings`hinzugefügt.
- Funktionen, die zuvor LabelId zurückgegeben haben, geben nun ein `mip::Label` Objekt zurück.

### <a name="changes"></a>Änderungen

* In früheren Versionen war es erforderlich, dass Sie `mip::ReleaseAllResources`aufgerufen haben. Version 1,3 ersetzt dies durch `mip::MipContext::~MipContext` oder `mip::MipContext::Shutdown`.
* `ActionSource` aus `mip::LabelingOptions` entfernt und `mip::ExecutionState::GetNewLabelActionSource`
* `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptor` durch `mip::ProtectionEngine::CreateProtectionHandlerForPublishing`ersetzt.
* `mip::ProtectionEngine::CreateProtectionHandlerFromPublishingLicense` durch `mip::ProtectionEngine::CreateProtectionHandlerForConsumption`ersetzt.
* Umbenannte `mip::PublishingLicenseContext` in `mip::PublishingLicenseInfo` und aktualisiert, um umfangreiche Felder anstelle von unformatierten serialisierten Bytes zu enthalten.
* `mip::PublishingLicenseInfo` enthält die für MIP relevanten Daten nach dem Testen einer Veröffentlichungs Lizenz (PL).
* `mip::TemplateNotFoundError` und `mip::LabelNotFoundError` ausgelöst, wenn die Anwendung MIP eine Vorlagen-ID oder Bezeichnungs-ID übergibt, die nicht erkannt wird.
* Unterstützung für Bezeichnungs basierten bedingten Zugriff über den claims-Parameter von `AcquireToken()` und `mip::AuthDelegate::OAuth2Challenge()`hinzugefügt. Diese Funktionalität wurde noch nicht über das Security and Compliance Center-Portal verfügbar gemacht.


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

 - mip_common. dll wird in mip_core. dll und mip_telemetry. dll aufgeteilt.
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
    - MIP:: HttpRequest:: GetBody gibt Std:: Vector < uint8_t > anstelle von Std:: String zurück.
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
 - (Interface) MIP:: HttpResponse:: GetBody gibt Std:: Vector < uint8_t > anstelle von Std:: String zurück.
 - (Interface) MIP:: HttpResponse-Schnittstelle erfordert die Implementierung der GetId-Methode.
 - MIP:: contentlabel:: getkreationtime gibt Std:: Chrono:: time_point anstelle von Std:: String zurück.
 - MIP:: fileengine:: up filehandlerasync akzeptiert nicht mehr den Parameter "contentIdentifier".
 - MIP::P olicyhandler:: notifycommitedactions umbenannt in MIP::P olicyhandler:: notifycommittedactions


## <a name="version-110"></a>Version 1.1.0

**Veröffentlichungsdatum**: 15. Januar 2019

Mit dieser Version wird die Unterstützung für die folgenden Plattformen eingeführt:

  - .NET
  - IOS SDK (Richtlinien-API)
  - Android SDK (Richtlinien-API und Schutz-API)

### <a name="new-features"></a>Neue Funktionen

- ADRMS-Unterstützung
- Schutz-API-Vorgänge sind tatsächlich asynchron (auf Win32) und ermöglichen gleichzeitige, nicht blockierende Verschlüsselungs-/Entschlüsselungs Vorgänge.
  - Anwendungs Rückrufe (authdelegat, httpdelegat usw.) können jetzt für einen beliebigen Hintergrund Thread aufgerufen werden.
- Von IT-Administratoren festgelegte benutzerdefinierte Bezeichnungs Eigenschaften können jetzt über MIP:: Label:: getcustomsettings gelesen werden.
- Die serialisierte Veröffentlichungs Lizenz kann jetzt direkt aus einer Datei ohne http-Vorgänge über MIP:: fileHandler:: getserializedpublishinglicense abgerufen werden.
- Anwendungen werden benachrichtigt, ob ein HTTP-Vorgang erforderlich ist, um die Erstellung eines MIP:: fileengine/MIP::P olicyengine über MIP:: fileprofile:: Observer:: onaddpolicyenginestarting/MIP::P olicyprofile:: Observer:: onaddenginestarting abzuschließen.
- Die Erkennung, ob geschützte Inhalte ein Ablaufdatum aufweisen oder nicht, wurde mit der Hilfsmethode "MIP::P rotectiondescriptor::D oescontentexpire" vereinfacht.
- Ordnung
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
      - MIP:: fileengine
      - MIP:: fileHandler
      - mip::PolicyEngine
      - MIP::P rotectionhandler
  - MIP:: nopolicyerror wird ausgelöst, wenn der Mandant nicht für Bezeichnungen konfiguriert ist.
    - Gilt für die Erstellung von:
      - MIP:: fileengine
      - mip::PolicyEngine
  - MIP:: servicedisablederror wird ausgelöst, wenn der RMS-Dienst für einen bestimmten Benutzer/Gerät/Plattform/Mandanten deaktiviert ist.
    - Gilt für die Erstellung von:
      - MIP:: fileHandler
      - MIP::P rotectionhandler
  - MIP:: nopermissionserror wird ausgelöst, wenn ein Benutzer nicht über die Berechtigung zum Entschlüsseln eines Dokuments verfügt oder der Inhalt abgelaufen ist.
    - Gilt für die Erstellung von:
      - MIP:: fileHandler
      - MIP::P rotectionhandler

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu unterstützten Plattformen und mehr finden Sie unter [FAQs und Probleme im MIP SDK](faqs-known-issues.md) .
- Informationen zu den ersten Schritten mit dem MIP SDK finden Sie unter [MIP SDK-Setup und Konfiguration](setup-configure-mip.md) .
