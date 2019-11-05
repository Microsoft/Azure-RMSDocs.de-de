---
title: MIP SDK für C-Referenz
description: MIP SDK für C-Referenz
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 11/4/2019
ms.openlocfilehash: 0187739b1f37a23051dbf6c3ddde8e992757f088
ms.sourcegitcommit: 7a8eef5eb9d6440c6e2300cb3f264da31061b00d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73592120"
---
# <a name="mip-sdk-for-c-reference"></a>MIP SDK für C-Referenz

Das Microsoft Information Protection (MIP) SDK für C ermöglicht Entwicklern das Verwalten und Anwenden von Datenschutzrichtlinien auf Daten und andere digitale Ressourcen.

Das MIP SDK für C umfasst

- [Enumerationen](enumerations.md)
- [Structures (Strukturen)](structures.md)
- Die folgenden Funktionen:

Funktion | Kurze Beschreibung |
|---|---|
| [mip_cc_auth_callback](functions.md#mip_cc_auth_callback) | Rückruf Funktionsdefinition zum Abrufen des OAuth2-Tokens |
| [mip_cc_consent_callback](functions.md#mip_cc_consent_callback) | Definition der Rückruffunktion für Zustimmung vom Benutzer für den Zugriff auf einen externen Dienst Endpunkt |
| [MIP_CC_CreateDictionary](functions.md#mip_cc_createdictionary) | Erstellen eines Wörterbuchs mit Zeichen folgen Schlüsseln/-Werten |
| [MIP_CC_Dictionary_GetEntries](functions.md#mip_cc_dictionary_getentries) | Schlüssel-Wert-Paare zum Verfassen eines Wörterbuchs erhalten |
| [MIP_CC_ReleaseDictionary](functions.md#mip_cc_releasedictionary) | Freigeben von Ressourcen, die einem Wörterbuch zugeordnet sind |
| [mip_cc_http_send_callback_fn](functions.md#mip_cc_http_send_callback_fn) | Rückruf Funktionsdefinition zum Ausgeben einer HTTP-Anforderung |
| [mip_cc_http_cancel_callback_fn](functions.md#mip_cc_http_cancel_callback_fn) | Rückruf Funktionsdefinition für das Abbrechen einer HTTP-Anforderung |
| [MIP_CC_CreateHttpDelegate](functions.md#mip_cc_createhttpdelegate) | Erstellt einen HTTP-Delegaten, der zum Überschreiben des HTTP-Standard Stapels verwendet werden kann. |
| [MIP_CC_NotifyHttpDelegateResponse](functions.md#mip_cc_notifyhttpdelegateresponse) | Benachrichtigt einen HTTP-Delegaten, dass eine HTTP-Antwort bereit ist. |
| [MIP_CC_ReleaseHttpDelegate](functions.md#mip_cc_releasehttpdelegate) | Freigabe Ressourcen, die einem http-delegathandle zugeordnet sind |
| [mip_cc_logger_init_callback_fn](functions.md#mip_cc_logger_init_callback_fn) | Rückruf Funktionsdefinition für die Initialisierung der Protokollierung |
| [mip_cc_logger_write_callback_fn](functions.md#mip_cc_logger_write_callback_fn) | Rückruf Funktionsdefinition zum Schreiben einer Log-Anweisung |
| [MIP_CC_CreateLoggerDelegate](functions.md#mip_cc_createloggerdelegate) | Erstellt einen Logger-Delegaten, der zum Überschreiben der Standard Protokollierung von MIP verwendet werden kann |
| [MIP_CC_ReleaseLoggerDelegate](functions.md#mip_cc_releaseloggerdelegate) | Freigabe Ressourcen, die einem Protokollierungs delegathandle zugeordnet sind |
| [MIP_CC_CreateMipContext](functions.md#mip_cc_createmipcontext) | Erstellen eines MIP-Kontexts zum Verwalten des Zustands, der für alle Profil Instanzen verwendet wird |
| [MIP_CC_CreateMipContextWithCustomFeatureSettings](functions.md#mip_cc_createmipcontextwithcustomfeaturesettings) | Erstellen eines MIP-Kontexts zum Verwalten des Zustands, der für alle Profil Instanzen verwendet wird |
| [MIP_CC_ReleaseMipContext](functions.md#mip_cc_releasemipcontext) | Freigeben von Ressourcen, die einem MIP-Kontext zugeordnet sind |
| [MIP_CC_ProtectionDescriptor_GetProtectionType](functions.md#mip_cc_protectiondescriptor_getprotectiontype) | Ruft den Typ des Schutzes ab, unabhängig davon, ob er durch eine RMS-Vorlage definiert ist. |
| [MIP_CC_ProtectionDescriptor_GetOwnerSize](functions.md#mip_cc_protectiondescriptor_getownersize) | Ruft die Größe des zum Speichern des Besitzers erforderlichen Puffers ab |
| [MIP_CC_ProtectionDescriptor_GetOwner](functions.md#mip_cc_protectiondescriptor_getowner) | Ruft den Schutz Besitzer ab |
| [MIP_CC_ProtectionDescriptor_GetNameSize](functions.md#mip_cc_protectiondescriptor_getnamesize) | Ruft die Größe des zum Speichern des Namens erforderlichen Puffers ab |
| [MIP_CC_ProtectionDescriptor_GetName](functions.md#mip_cc_protectiondescriptor_getname) | Ruft den Schutz Namen ab |
| [MIP_CC_ProtectionDescriptor_GetDescriptionSize](functions.md#mip_cc_protectiondescriptor_getdescriptionsize) | Ruft die Größe des Puffers zum Speichern der Beschreibung ab. |
| [MIP_CC_ProtectionDescriptor_GetDescription](functions.md#mip_cc_protectiondescriptor_getdescription) | Ruft die Schutz Beschreibung ab |
| [MIP_CC_ProtectionDescriptor_GetTemplateId](functions.md#mip_cc_protectiondescriptor_gettemplateid) | Ruft Vorlagen-ID ab |
| [MIP_CC_ProtectionDescriptor_GetLabelId](functions.md#mip_cc_protectiondescriptor_getlabelid) | Bezeichnungs-ID abrufen |
| [MIP_CC_ProtectionDescriptor_GetContentId](functions.md#mip_cc_protectiondescriptor_getcontentid) | Ruft Inhalts-ID ab |
| [MIP_CC_ProtectionDescriptor_DoesContentExpire](functions.md#mip_cc_protectiondescriptor_doescontentexpire) | Ruft ab, ob der Inhalt eine Ablaufzeit aufweist oder nicht. |
| [MIP_CC_ProtectionDescriptor_GetContentValidUntil](functions.md#mip_cc_protectiondescriptor_getcontentvaliduntil) | Ruft die Ablaufzeit des Schutzes ab (in Sekunden seit der Epoche). |
| [MIP_CC_ProtectionDescriptor_DoesAllowOfflineAccess](functions.md#mip_cc_protectiondescriptor_doesallowofflineaccess) | Ruft ab, ob der Offline Zugriff zulässig ist. |
| [MIP_CC_ProtectionDescriptor_GetReferrerSize](functions.md#mip_cc_protectiondescriptor_getreferrersize) | Ruft die Größe des für die Speicher Verweise erforderlichen Puffers ab. |
| [MIP_CC_ProtectionDescriptor_GetReferrer](functions.md#mip_cc_protectiondescriptor_getreferrer) | Ruft Schutz Verweise ab. |
| [MIP_CC_ReleaseProtectionDescriptor](functions.md#mip_cc_releaseprotectiondescriptor) | Freigeben von Ressourcen, die einer Schutz Beschreibung zugeordnet sind |
| [MIP_CC_CreateStringList](functions.md#mip_cc_createstringlist) | Zeichen folgen Liste erstellen |
| [MIP_CC_StringList_GetStrings](functions.md#mip_cc_stringlist_getstrings) | Zeichen folgen, die eine Zeichen folgen Liste bilden, erhalten |
| [MIP_CC_ReleaseStringList](functions.md#mip_cc_releasestringlist) | Freigeben von Ressourcen, die einer Zeichen folgen Liste zugeordnet sind |
| [mip_cc_dispatch_task_callback_fn](functions.md#mip_cc_dispatch_task_callback_fn) | Rückruf Funktionsdefinition für das Senden einer asynchronen Aufgabe |
| [mip_cc_cancel_task_callback_fn](functions.md#mip_cc_cancel_task_callback_fn) | Rückruffunktion zum Abbrechen von Hintergrundaufgaben |
| [MIP_CC_CreateTaskDispatcherDelegate](functions.md#mip_cc_createtaskdispatcherdelegate) | Erstellt einen Aufgaben Verteiler Delegaten, der zum Überschreiben der standardmäßigen asynchronen Task Verarbeitung von MIP verwendet werden kann. |
| [MIP_CC_ExecuteDispatchedTask](functions.md#mip_cc_executedispatchedtask) | Benachrichtigt einen taskdispatcher-Delegaten, dass eine Aufgabe jetzt für die Ausführung im aktuellen Thread geplant ist. |
| [MIP_CC_ReleaseTaskDispatcherDelegate](functions.md#mip_cc_releasetaskdispatcherdelegate) | Freigeben von Ressourcen, die einem Aufgaben Verteiler-delegathandle zugeordnet sind |
| [MIP_CC_TelemetryConfiguration_SetHostName](functions.md#mip_cc_telemetryconfiguration_sethostname) | Festlegen eines telemetriehostnamens, der interne telemetrieeinstellungen außer Kraft setzt |
| [MIP_CC_TelemetryConfiguration_SetLibraryName](functions.md#mip_cc_telemetryconfiguration_setlibraryname) | Überschreiben einer freigegebenen telemetriebibliothek festlegen |
| [MIP_CC_TelemetryConfiguration_SetHttpDelegate](functions.md#mip_cc_telemetryconfiguration_sethttpdelegate) | Standard-Telemetrie-HTTP-Stapel mit eigenem Client überschreiben |
| [MIP_CC_TelemetryConfiguration_SetIsNetworkDetectionEnabled](functions.md#mip_cc_telemetryconfiguration_setisnetworkdetectionenabled) | Legt fest, ob für die telemetriekomponente ein Ping-Netzwerkstatus in einem Hintergrund Thread zulässig ist. |
| [MIP_CC_TelemetryConfiguration_SetIsLocalCachingEnabled](functions.md#mip_cc_telemetryconfiguration_setislocalcachingenabled) | Legt fest, ob die telemetriekomponente Caches auf den Datenträger schreiben darf. |
| [MIP_CC_TelemetryConfiguration_SetIsTraceLoggingEnabled](functions.md#mip_cc_telemetryconfiguration_setistraceloggingenabled) | Legt fest, ob die telemetriekomponente Protokolle auf den Datenträger schreiben darf. |
| [MIP_CC_TelemetryConfiguration_SetIsTelemetryOptedOut](functions.md#mip_cc_telemetryconfiguration_setistelemetryoptedout) | Legt fest, ob eine Anwendung bzw. ein Benutzer die optionale Telemetrie deaktiviert hat. |
| [MIP_CC_TelemetryConfiguration_SetCustomSettings](functions.md#mip_cc_telemetryconfiguration_setcustomsettings) | Legt benutzerdefinierte telemetrieeinstellungen fest |
| [MIP_CC_ReleaseTelemetryConfiguration](functions.md#mip_cc_releasetelemetryconfiguration) | Freigeben von Ressourcen, die mit einer Schutzprofil Einstellung verknüpft sind |
| [MIP_CC_ReleaseProtectionEngine](functions.md#mip_cc_releaseprotectionengine) | Freigeben von Ressourcen, die einer Schutz-Engine zugeordnet sind |
| [MIP_CC_ProtectionEngine_CreateProtectionHandlerForPublishing](functions.md#mip_cc_protectionengine_createprotectionhandlerforpublishing) | Erstellt einen Schutz Handler zum Veröffentlichen von neuem Inhalt. |
| [MIP_CC_ProtectionEngine_CreateProtectionHandlerForConsumption](functions.md#mip_cc_protectionengine_createprotectionhandlerforconsumption) | Erstellt einen Schutz Handler für die Verwendung von vorhandenem Inhalt. |
| [MIP_CC_ProtectionEngine_GetEngineIdSize](functions.md#mip_cc_protectionengine_getengineidsize) | Ruft die Größe des für Engine-ID erforderlichen Puffers ab |
| [MIP_CC_ProtectionEngine_GetEngineId](functions.md#mip_cc_protectionengine_getengineid) | Ruft Engine-ID ab |
| [MIP_CC_ProtectionEngine_GetTemplatesSize](functions.md#mip_cc_protectionengine_gettemplatessize) | Ruft die Anzahl von RMS-Vorlagen ab, die einer Schutz-Engine zugeordnet sind |
| [MIP_CC_ProtectionEngine_GetTemplates](functions.md#mip_cc_protectionengine_gettemplates) | Sammlung von Vorlagen für Benutzer verfügbar machen |
| [MIP_CC_ProtectionEngine_GetRightsForLabelId](functions.md#mip_cc_protectionengine_getrightsforlabelid) | Liste der Rechte, die einem Benutzer für eine Bezeichnungs-ID erteilt werden |
| [MIP_CC_ProtectionEngine_GetClientDataSize](functions.md#mip_cc_protectionengine_getclientdatasize) | Ruft die Größe der Client Daten ab, die einer Schutz-Engine zugeordnet sind. |
| [MIP_CC_ProtectionEngine_GetClientData](functions.md#mip_cc_protectionengine_getclientdata) | Client Daten erhalten, die einer Schutz-Engine zugeordnet sind |
| [MIP_CC_CreateProtectionEngineSettingsWithIdentity](functions.md#mip_cc_createprotectionenginesettingswithidentity) | Erstellen Sie ein Einstellungs Objekt, das zum Erstellen einer neuen Schutz-Engine verwendet wird. |
| [MIP_CC_ProtectionEngineSettings_SetClientData](functions.md#mip_cc_protectionenginesettings_setclientdata) | Legt die Client Daten fest, die mit dieser Engine verdeckt gespeichert werden und Sitzungs übergreifend beibehalten werden |
| [MIP_CC_ProtectionEngineSettings_SetCustomSettings](functions.md#mip_cc_protectionenginesettings_setcustomsettings) | Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden. |
| [MIP_CC_ProtectionEngineSettings_SetSessionId](functions.md#mip_cc_protectionenginesettings_setsessionid) | Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann. |
| [MIP_CC_ProtectionEngineSettings_SetCloudEndpointBaseUrl](functions.md#mip_cc_protectionenginesettings_setcloudendpointbaseurl) | Legt die Basis-URL für alle Service Requests fest. |
| [MIP_CC_ReleaseProtectionEngineSettings](functions.md#mip_cc_releaseprotectionenginesettings) | Freigeben von Ressourcen, die den Einstellungen der Schutz-Engine zugeordnet |
| [MIP_CC_CreateProtectionHandlerPublishingSettings](functions.md#mip_cc_createprotectionhandlerpublishingsettings) | Erstellen Sie ein Einstellungs Objekt, das zum Erstellen eines Schutz Handlers zum Veröffentlichen neuer Inhalte verwendet wird. |
| [MIP_CC_ProtectionHandlerPublishingSettings_SetIsDeprecatedAlgorithmPreferred](functions.md#mip_cc_protectionhandlerpublishingsettings_setisdeprecatedalgorithmpreferred) | Legt fest, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird. |
| [MIP_CC_ProtectionHandlerPublishingSettings_SetIsAuditedExtractionAllowed](functions.md#mip_cc_protectionhandlerpublishingsettings_setisauditedextractionallowed) | Legt fest, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht. |
| [MIP_CC_ProtectionHandlerPublishingSettings_SetIsPublishingFormatJson](functions.md#mip_cc_protectionhandlerpublishingsettings_setispublishingformatjson) | Legt fest, ob pl im JSON-Format vorliegt (Standardwert ist XML). |
| [MIP_CC_ProtectionHandlerPublishingSettings_SetDelegatedUserEmail](functions.md#mip_cc_protectionhandlerpublishingsettings_setdelegateduseremail) | Legt Delegierten Benutzer fest. |
| [MIP_CC_CreateProtectionHandlerConsumptionSettings](functions.md#mip_cc_createprotectionhandlerconsumptionsettings) | Erstellen eines Einstellungs Objekts, das zum Erstellen eines Schutz Handlers zum Verarbeiten vorhandener Inhalte verwendet wird |
| [MIP_CC_ProtectionHandlerConsumptionSettings_SetIsOfflineOnly](functions.md#mip_cc_protectionhandlerconsumptionsettings_setisofflineonly) | Legt fest, ob die Erstellung von Schutz Handlern Online-http-Vorgänge zulässt |
| [MIP_CC_ProtectionHandlerConsumptionSettings_SetDelegatedUserEmail](functions.md#mip_cc_protectionhandlerconsumptionsettings_setdelegateduseremail) | Legt Delegierten Benutzer fest. |
| [MIP_CC_ProtectionHandler_GetSerializedPublishingLicenseSize](functions.md#mip_cc_protectionhandler_getserializedpublishinglicensesize) | Ruft die Größe der Veröffentlichungs Lizenz ab (in Bytes). |
| [MIP_CC_ProtectionHandler_GetSerializedPublishingLicense](functions.md#mip_cc_protectionhandler_getserializedpublishinglicense) | Ruft die Veröffentlichungs Lizenz ab |
| [MIP_CC_ProtectionHandler_GetProtectionDescriptor](functions.md#mip_cc_protectionhandler_getprotectiondescriptor) | Ruft den Schutz Deskriptor ab. |
| [MIP_CC_ProtectionHandler_GetRights](functions.md#mip_cc_protectionhandler_getrights) | Ruft eine Liste der dem Benutzer gewährten Rechte ab. |
| [MIP_CC_ProtectionHandler_GetProtectedContentSize](functions.md#mip_cc_protectionhandler_getprotectedcontentsize) | Berechnet die Größe geschützter Inhalte, Factoring in Auffüll Zeichen usw. |
| [MIP_CC_ProtectionHandler_GetBlockSize](functions.md#mip_cc_protectionhandler_getblocksize) | Ruft die Blockgröße (in Bytes) für den Verschlüsselungs Modus ab, der von einem Schutz Handler verwendet wird. |
| [MIP_CC_ProtectionHandler_GetIssuedUserSize](functions.md#mip_cc_protectionhandler_getissuedusersize) | Ruft die Größe des Puffers ab, der zum Speichern des Benutzers benötigt wird, dem Zugriff auf geschützte Inhalte gewährt wurde |
| [MIP_CC_ProtectionHandler_GetIssuedUser](functions.md#mip_cc_protectionhandler_getissueduser) | Ruft den Benutzer ab, dem Zugriff auf geschützte Inhalte gewährt wurde. |
| [MIP_CC_ProtectionHandler_GetOwnerSize](functions.md#mip_cc_protectionhandler_getownersize) | Ruft die Größe des Puffers ab, der zum Speichern des Besitzers geschützter Inhalte benötigt wird. |
| [MIP_CC_ProtectionHandler_GetOwner](functions.md#mip_cc_protectionhandler_getowner) | Ruft den Besitzer geschützter Inhalte ab. |
| [MIP_CC_ProtectionHandler_GetContentId](functions.md#mip_cc_protectionhandler_getcontentid) | Ruft den Inhalt des geschützten Inhalts ab. |
| [MIP_CC_ProtectionHandler_DoesUseDeprecatedAlgorithm](functions.md#mip_cc_protectionhandler_doesusedeprecatedalgorithm) | Ruft ab, ob der Schutz Handler den veralteten Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität verwendet. |
| [MIP_CC_ProtectionHandler_DecryptBuffer](functions.md#mip_cc_protectionhandler_decryptbuffer) | Entschlüsseln eines Puffers |
| [MIP_CC_ReleaseProtectionHandlerPublishingSettings](functions.md#mip_cc_releaseprotectionhandlerpublishingsettings) | Freigeben von Ressourcen, die den Einstellungen eines Schutz Handlers zugeordnet |
| [MIP_CC_ReleaseProtectionHandlerConsumptionSettings](functions.md#mip_cc_releaseprotectionhandlerconsumptionsettings) | Freigeben von Ressourcen, die den Einstellungen eines Schutz Handlers zugeordnet |
| [MIP_CC_ReleaseProtectionHandler](functions.md#mip_cc_releaseprotectionhandler) | Freigeben von Ressourcen, die einem Schutz Handler zugeordnet sind |
| [MIP_CC_LoadProtectionProfile](functions.md#mip_cc_loadprotectionprofile) | Profil laden |
| [MIP_CC_ReleaseProtectionProfile](functions.md#mip_cc_releaseprotectionprofile) | Freigeben von Ressourcen, die einem Schutzprofil zugeordnet sind |
| [MIP_CC_ProtectionProfileSettings_SetSessionId](functions.md#mip_cc_protectionprofilesettings_setsessionid) | Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann. |
| [MIP_CC_ProtectionProfileSettings_SetCanCacheLicenses](functions.md#mip_cc_protectionprofilesettings_setcancachelicenses) | Hiermit wird konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden. |
| [MIP_CC_ProtectionProfileSettings_SetHttpDelegate](functions.md#mip_cc_protectionprofilesettings_sethttpdelegate) | Standard-HTTP-Stapel mit eigenem Client überschreiben |
| [MIP_CC_ProtectionProfileSettings_SetTaskDispatcherDelegate](functions.md#mip_cc_protectionprofilesettings_settaskdispatcherdelegate) | Standardmäßiger asynchroner Aufgaben Verteiler mit eigenem Client überschreiben |
| [MIP_CC_ProtectionProfileSettings_SetCustomSettings](functions.md#mip_cc_protectionprofilesettings_setcustomsettings) | Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden. |
| [MIP_CC_ReleaseProtectionProfileSettings](functions.md#mip_cc_releaseprotectionprofilesettings) | Freigeben von Ressourcen, die mit einer Schutzprofil Einstellung verknüpft sind |
| [MIP_CC_Action_GetType](functions.md#mip_cc_action_gettype) | Ruft den Typ der Aktion ab. |
| [MIP_CC_Action_GetId](functions.md#mip_cc_action_getid) | Ruft die ID einer Aktion ab. |
| [MIP_CC_ActionResult_GetActions](functions.md#mip_cc_actionresult_getactions) | Aktionen zum Erstellen eines Aktions Ergebnisses |
| [MIP_CC_ReleaseActionResult](functions.md#mip_cc_releaseactionresult) | Freigeben von Ressourcen, die einem Aktions Ergebnis zugeordnet sind |
| [MIP_CC_AddContentFooterAction_GetUIElementNameSize](functions.md#mip_cc_addcontentfooteraction_getuielementnamesize) | Ruft die Größe des Puffers ab, der zum Speichern des Benutzeroberflächen-Element namens für die Aktion "Content Footer" erforderlich ist |
| [MIP_CC_AddContentFooterAction_GetUIElementName](functions.md#mip_cc_addcontentfooteraction_getuielementname) | Ruft den Benutzeroberflächen Elementnamen der Aktion "Content Footer hinzufügen" ab. |
| [MIP_CC_AddContentFooterAction_GetTextSize](functions.md#mip_cc_addcontentfooteraction_gettextsize) | Ruft die Größe des Puffers ab, der zum Speichern des Aktions Texts "Content Footer hinzufügen" erforderlich ist. |
| [MIP_CC_AddContentFooterAction_GetText](functions.md#mip_cc_addcontentfooteraction_gettext) | Ruft den Text der Aktion "Content Footer hinzufügen" ab. |
| [MIP_CC_AddContentFooterAction_GetFontNameSize](functions.md#mip_cc_addcontentfooteraction_getfontnamesize) | Ruft die Größe des Puffers ab, der zum Speichern des Schriftart namens der Aktion "Content Footer" hinzugefügt wird. |
| [MIP_CC_AddContentFooterAction_GetFontName](functions.md#mip_cc_addcontentfooteraction_getfontname) | Ruft den Schriftart Namen der Aktion "Content Footer hinzufügen" ab. |
| [MIP_CC_AddContentFooterAction_GetFontSize](functions.md#mip_cc_addcontentfooteraction_getfontsize) | Ruft den Schrift Grad der ganzen Zahl ab |
| [MIP_CC_AddContentFooterAction_GetFontColorSize](functions.md#mip_cc_addcontentfooteraction_getfontcolorsize) | Ruft die Größe des Puffers ab, der zum Speichern der Schriftfarbe der Aktion "Content Footer" hinzugefügt wird. |
| [MIP_CC_AddContentFooterAction_GetFontColor](functions.md#mip_cc_addcontentfooteraction_getfontcolor) | Ruft die Schriftfarbe für die Aktion "Inhalts Fußzeile hinzufügen" (z. b. "#000000") ab. |
| [MIP_CC_AddContentFooterAction_GetAlignment](functions.md#mip_cc_addcontentfooteraction_getalignment) | Ruft die Ausrichtung ab. |
| [MIP_CC_AddContentFooterAction_GetMargin](functions.md#mip_cc_addcontentfooteraction_getmargin) | Ruft die Rand Größe ab. |
| [MIP_CC_AddContentHeaderAction_GetUIElementNameSize](functions.md#mip_cc_addcontentheaderaction_getuielementnamesize) | Ruft die Größe des Puffers ab, der zum Speichern des Benutzeroberflächen Element namens für die Aktion "Content Header hinzufügen" |
| [MIP_CC_AddContentHeaderAction_GetUIElementName](functions.md#mip_cc_addcontentheaderaction_getuielementname) | Ruft den Benutzeroberflächen Elementnamen für die Aktion "Content Header hinzufügen" ab. |
| [MIP_CC_AddContentHeaderAction_GetTextSize](functions.md#mip_cc_addcontentheaderaction_gettextsize) | Ruft die Größe des Puffers ab, der zum Speichern eines Aktions Texts für "Inhalts Header hinzufügen" erforderlich ist |
| [MIP_CC_AddContentHeaderAction_GetText](functions.md#mip_cc_addcontentheaderaction_gettext) | Ruft den Text der Aktion "Content Header hinzufügen" ab. |
| [MIP_CC_AddContentHeaderAction_GetFontNameSize](functions.md#mip_cc_addcontentheaderaction_getfontnamesize) | Ruft die Größe des Puffers ab, der zum Speichern des Schriftart namens der Aktion "Inhalts Header hinzufügen" erforderlich ist |
| [MIP_CC_AddContentHeaderAction_GetFontName](functions.md#mip_cc_addcontentheaderaction_getfontname) | Ruft den Schriftart Namen der Aktion "Content-Header hinzufügen" ab. |
| [MIP_CC_AddContentHeaderAction_GetFontSize](functions.md#mip_cc_addcontentheaderaction_getfontsize) | Ruft den Schrift Grad der ganzen Zahl ab |
| [MIP_CC_AddContentHeaderAction_GetFontColorSize](functions.md#mip_cc_addcontentheaderaction_getfontcolorsize) | Ruft die Größe des Puffers ab, der zum Speichern der Schriftfarbe der Aktion "Inhalts Header hinzufügen" erforderlich ist |
| [MIP_CC_AddContentHeaderAction_GetFontColor](functions.md#mip_cc_addcontentheaderaction_getfontcolor) | Ruft die Schriftfarbe für die Aktion "Content-Header hinzufügen" (z. b. "#000000") ab. |
| [MIP_CC_AddContentHeaderAction_GetAlignment](functions.md#mip_cc_addcontentheaderaction_getalignment) | Ruft die Ausrichtung ab. |
| [MIP_CC_AddContentHeaderAction_GetMargin](functions.md#mip_cc_addcontentheaderaction_getmargin) | Ruft die Rand Größe ab. |
| [MIP_CC_AddWatermarkAction_GetUIElementNameSize](functions.md#mip_cc_addwatermarkaction_getuielementnamesize) | Ruft die Größe des Puffers ab, der zum Speichern des Benutzeroberflächen Element namens der Aktion "Wasserzeichen hinzufügen" erforderlich |
| [MIP_CC_AddWatermarkAction_GetUIElementName](functions.md#mip_cc_addwatermarkaction_getuielementname) | Ruft den Benutzeroberflächen Elementnamen der Aktion "Wasserzeichen hinzufügen" ab. |
| [MIP_CC_AddWatermarkAction_GetLayout](functions.md#mip_cc_addwatermarkaction_getlayout) | Ruft das Wasserzeichen Layout ab. |
| [MIP_CC_AddWatermarkAction_GetTextSize](functions.md#mip_cc_addwatermarkaction_gettextsize) | Ruft die Größe des Puffers ab, der zum Speichern des Texts der Aktion "Wasserzeichen hinzufügen" erforderlich ist |
| [MIP_CC_AddWatermarkAction_GetText](functions.md#mip_cc_addwatermarkaction_gettext) | Ruft den Text der Aktion "Wasserzeichen hinzufügen" ab. |
| [MIP_CC_AddWatermarkAction_GetFontNameSize](functions.md#mip_cc_addwatermarkaction_getfontnamesize) | Ruft die Größe des Puffers ab, der zum Speichern des Schriftart namens "Wasserzeichen hinzufügen" erforderlich ist. |
| [MIP_CC_AddWatermarkAction_GetFontName](functions.md#mip_cc_addwatermarkaction_getfontname) | Ruft den Schriftart Namen der Aktion "Wasserzeichen hinzufügen" ab. |
| [MIP_CC_AddWatermarkAction_GetFontSize](functions.md#mip_cc_addwatermarkaction_getfontsize) | Ruft den Schrift Grad der ganzen Zahl ab |
| [MIP_CC_AddWatermarkAction_GetFontColorSize](functions.md#mip_cc_addwatermarkaction_getfontcolorsize) | Ruft die Größe des Puffers ab, der zum Speichern der Schriftart Farbe für "Wasserzeichen hinzufügen" erforderlich ist. |
| [MIP_CC_AddWatermarkAction_GetFontColor](functions.md#mip_cc_addwatermarkaction_getfontcolor) | Ruft die Schriftfarbe der Aktion "Wasserzeichen hinzufügen" (z. b. "#000000") ab. |
| [MIP_CC_ReleaseContentLabel](functions.md#mip_cc_releasecontentlabel) | Freigeben von Ressourcen, die einer Inhalts Bezeichnung zugeordnet sind |
| [MIP_CC_ContentLabel_GetCreationTime](functions.md#mip_cc_contentlabel_getcreationtime) | Ruft die Zeit ab, zu der Bezeichnung angewendet wurde |
| [MIP_CC_ContentLabel_GetAssignmentMethod](functions.md#mip_cc_contentlabel_getassignmentmethod) | Ruft die Bezeichnung für die Bezeichnung ab |
| [MIP_CC_ContentLabel_GetExtendedProperties](functions.md#mip_cc_contentlabel_getextendedproperties) | Ruft erweiterte Eigenschaften ab. |
| [MIP_CC_ContentLabel_IsProtectionAppliedFromLabel](functions.md#mip_cc_contentlabel_isprotectionappliedfromlabel) | Ruft ab, ob ein Schutz durch eine Bezeichnung angewendet wurde. |
| [MIP_CC_ContentLabel_GetLabel](functions.md#mip_cc_contentlabel_getlabel) | Ruft generische Bezeichnungs Eigenschaften aus einer Instanz der Inhalts Bezeichnung ab. |
| [MIP_CC_CustomAction_GetNameSize](functions.md#mip_cc_customaction_getnamesize) | Ruft die Größe des Puffers ab, der zum Speichern des Namens einer benutzerdefinierten Aktion erforderlich ist. |
| [MIP_CC_CustomAction_GetName](functions.md#mip_cc_customaction_getname) | Ruft den Namen der benutzerdefinierten Aktion ab. |
| [MIP_CC_CustomAction_GetProperties](functions.md#mip_cc_customaction_getproperties) | Ruft die Eigenschaften der benutzerdefinierten Aktion ab. |
| [mip_cc_metadata_callback](functions.md#mip_cc_metadata_callback) | Rückruf Funktionsdefinition zum Abrufen von Dokument Metatdaten, gefiltert nach Name/Präfix |
| [MIP_CC_ReleaseLabel](functions.md#mip_cc_releaselabel) | Freigeben von Ressourcen, die einer Bezeichnung zugeordnet sind |
| [MIP_CC_Label_GetId](functions.md#mip_cc_label_getid) | Bezeichnungs-ID abrufen |
| [MIP_CC_Label_GetNameSize](functions.md#mip_cc_label_getnamesize) | Ruft die Größe des zum Speichern des Namens erforderlichen Puffers ab |
| [MIP_CC_Label_GetName](functions.md#mip_cc_label_getname) | Ruft den Bezeichnung |
| [MIP_CC_Label_GetDescriptionSize](functions.md#mip_cc_label_getdescriptionsize) | Ruft die Größe des Puffers zum Speichern der Beschreibung ab. |
| [MIP_CC_Label_GetDescription](functions.md#mip_cc_label_getdescription) | Beschreibung der Bezeichnung wird abgerufen |
| [MIP_CC_Label_GetColorSize](functions.md#mip_cc_label_getcolorsize) | Ruft die Größe des Puffers zum Speichern der Farbe ab. |
| [MIP_CC_Label_GetColor](functions.md#mip_cc_label_getcolor) | Ruft die Bezeichnung ab. |
| [MIP_CC_Label_GetSensitivity](functions.md#mip_cc_label_getsensitivity) | Ruft die Vertraulichkeits Stufe der Bezeichnung ab. Ein höherer Wert bedeutet mehr sensitiv. |
| [MIP_CC_Label_GetTooltipSize](functions.md#mip_cc_label_gettooltipsize) | Ruft die Größe des Puffers zum Speichern der QuickInfo ab |
| [MIP_CC_Label_GetTooltip](functions.md#mip_cc_label_gettooltip) | QuickInfo für Bezeichnung abrufen |
| [MIP_CC_Label_GetAutoTooltipSize](functions.md#mip_cc_label_getautotooltipsize) | Ruft die Größe des Puffers zum Speichern der QuickInfo für die automatische Klassifizierung ab |
| [MIP_CC_Label_GetAutoTooltip](functions.md#mip_cc_label_getautotooltip) | Ruft die Bezeichnung für die automatische Klassifizierung der Bezeichnung ab |
| [MIP_CC_Label_IsActive](functions.md#mip_cc_label_isactive) | Ruft ab, ob eine Bezeichnung aktiv ist. |
| [MIP_CC_Label_GetParent](functions.md#mip_cc_label_getparent) | Ruft die übergeordnete Bezeichnung ab, sofern vorhanden. |
| [MIP_CC_Label_GetChildrenSize](functions.md#mip_cc_label_getchildrensize) | Ruft die Anzahl der untergeordneten Bezeichnungen ab. |
| [MIP_CC_Label_GetChildren](functions.md#mip_cc_label_getchildren) | Ruft die untergeordneten Bezeichnungen ab. |
| [MIP_CC_Label_GetCustomSettings](functions.md#mip_cc_label_getcustomsettings) | Ruft Richtlinien definierte benutzerdefinierte Einstellungen einer Bezeichnung ab. |
| [MIP_CC_MetadataAction_GetMetadataToRemove](functions.md#mip_cc_metadataaction_getmetadatatoremove) | Ruft die zu entfern aus den Metadaten der metadatenaktion ab. |
| [MIP_CC_MetadataAction_GetMetadataToAdd](functions.md#mip_cc_metadataaction_getmetadatatoadd) | Ruft die hinzu zufügenden Metadaten der metadatenaktion ab. |
| [MIP_CC_ReleasePolicyEngine](functions.md#mip_cc_releasepolicyengine) | Freigeben von Ressourcen, die einer Richtlinie-Engine zugeordnet sind |
| [MIP_CC_PolicyEngine_GetEngineIdSize](functions.md#mip_cc_policyengine_getengineidsize) | Ruft die Größe des für Engine-ID erforderlichen Puffers ab |
| [MIP_CC_PolicyEngine_GetEngineId](functions.md#mip_cc_policyengine_getengineid) | Ruft Engine-ID ab |
| [MIP_CC_PolicyEngine_GetMoreInfoUrlSize](functions.md#mip_cc_policyengine_getmoreinfourlsize) | Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab. |
| [MIP_CC_PolicyEngine_GetMoreInfoUrl](functions.md#mip_cc_policyengine_getmoreinfourl) | Client Daten mit einer Richtlinien-Engine |
| [MIP_CC_PolicyEngine_IsLabelingRequired](functions.md#mip_cc_policyengine_islabelingrequired) | Ruft ab, ob die Richtlinie festlegt, dass ein Dokument mit einer Bezeichnung versehen werden muss. |
| [MIP_CC_PolicyEngine_GetPolicyFileIdSize](functions.md#mip_cc_policyengine_getpolicyfileidsize) | Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab. |
| [MIP_CC_PolicyEngine_GetPolicyFileId](functions.md#mip_cc_policyengine_getpolicyfileid) | Client Daten mit einer Richtlinien-Engine |
| [MIP_CC_PolicyEngine_GetSensitivityFileIdSize](functions.md#mip_cc_policyengine_getsensitivityfileidsize) | Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab. |
| [MIP_CC_PolicyEngine_GetSensitivityFileId](functions.md#mip_cc_policyengine_getsensitivityfileid) | Client Daten mit einer Richtlinien-Engine |
| [MIP_CC_PolicyEngine_HasClassificationRules](functions.md#mip_cc_policyengine_hasclassificationrules) | Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt. |
| [MIP_CC_PolicyEngine_GetLastPolicyFetchTime](functions.md#mip_cc_policyengine_getlastpolicyfetchtime) | Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde. |
| [MIP_CC_PolicyEngine_GetSensitivityLabelsSize](functions.md#mip_cc_policyengine_getsensitivitylabelssize) | Ruft die Anzahl der der Richtlinien-Engine zugeordneten Vertraulichkeits Bezeichnungen ab. |
| [MIP_CC_PolicyEngine_GetSensitivityLabels](functions.md#mip_cc_policyengine_getsensitivitylabels) | Ruft die der Richtlinien-Engine zugeordneten Vertraulichkeits Bezeichnungen ab. |
| [MIP_CC_PolicyEngine_GetLabelById](functions.md#mip_cc_policyengine_getlabelbyid) | Ruft die Vertraulichkeits Bezeichnung nach ID ab |
| [MIP_CC_PolicyEngine_GetSensitivityTypesSize](functions.md#mip_cc_policyengine_getsensitivitytypessize) | Ruft die Anzahl der Empfindlichkeits Typen ab, die der Richtlinien-Engine zugeordnet sind |
| [MIP_CC_PolicyEngine_GetSensitivityTypes](functions.md#mip_cc_policyengine_getsensitivitytypes) | Ruft die der Richtlinien-Engine zugeordneten Empfindlichkeits Typen ab. |
| [MIP_CC_PolicyEngine_CreatePolicyHandler](functions.md#mip_cc_policyengine_createpolicyhandler) | Erstellen eines Richtlinien Handlers zum Ausführen von Richtlinien bezogenen Funktionen |
| [MIP_CC_PolicyEngine_SendApplicationAuditEvent](functions.md#mip_cc_policyengine_sendapplicationauditevent) | Protokolliert ein anwendungsspezifisches Ereignis in der Überwachungs Pipeline. |
| [MIP_CC_PolicyEngine_GetPolicyDataXmlSize](functions.md#mip_cc_policyengine_getpolicydataxmlsize) | Ruft die Größe der Richtlinien Daten-XML ab. |
| [MIP_CC_PolicyEngine_GetPolicyDataXml](functions.md#mip_cc_policyengine_getpolicydataxml) | Ruft Richtlinien Daten-XML ab. |
| [MIP_CC_PolicyEngine_GetSensitivityTypesDataXmlSize](functions.md#mip_cc_policyengine_getsensitivitytypesdataxmlsize) | Ruft die Größe der Vertraulichkeits Typen Daten-XML ab. |
| [MIP_CC_PolicyEngine_GetSensitivityTypesDataXml](functions.md#mip_cc_policyengine_getsensitivitytypesdataxml) | Ruft Daten der Vertraulichkeits Typen ab. |
| [MIP_CC_PolicyEngine_GetClientDataSize](functions.md#mip_cc_policyengine_getclientdatasize) | Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab. |
| [MIP_CC_PolicyEngine_GetClientData](functions.md#mip_cc_policyengine_getclientdata) | Client Daten mit einer Richtlinien-Engine |
| [MIP_CC_CreatePolicyEngineSettingsWithIdentity](functions.md#mip_cc_createpolicyenginesettingswithidentity) | Erstellen eines Einstellungs Objekts, das zum Erstellen einer neuen Richtlinien-Engine verwendet wird |
| [MIP_CC_PolicyEngineSettings_SetClientData](functions.md#mip_cc_policyenginesettings_setclientdata) | Legt die Client Daten fest, die mit dieser Engine verdeckt gespeichert werden und Sitzungs übergreifend beibehalten werden |
| [MIP_CC_PolicyEngineSettings_SetCustomSettings](functions.md#mip_cc_policyenginesettings_setcustomsettings) | Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden. |
| [MIP_CC_PolicyEngineSettings_SetSessionId](functions.md#mip_cc_policyenginesettings_setsessionid) | Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann. |
| [MIP_CC_PolicyEngineSettings_SetCloudEndpointBaseUrl](functions.md#mip_cc_policyenginesettings_setcloudendpointbaseurl) | Legt die Basis-URL für alle Service Requests fest. |
| [MIP_CC_PolicyEngineSettings_SetDelegatedUserEmail](functions.md#mip_cc_policyenginesettings_setdelegateduseremail) | Legt Delegierten Benutzer fest. |
| [MIP_CC_ReleasePolicyEngineSettings](functions.md#mip_cc_releasepolicyenginesettings) | Freigeben von Ressourcen, die einem Richtlinien Modul-Einstellungen zugeordnet sind |
| [MIP_CC_ReleasePolicyHandler](functions.md#mip_cc_releasepolicyhandler) | Freigeben von Ressourcen, die einem Richtlinien Handler zugeordnet sind |
| [MIP_CC_PolicyHandler_GetSensitivityLabel](functions.md#mip_cc_policyhandler_getsensitivitylabel) | Ruft die aktuelle Bezeichnung eines Dokuments ab. |
| [MIP_CC_PolicyHandler_ComputeActions](functions.md#mip_cc_policyhandler_computeactions) | Führt Richtlinien Regeln basierend auf dem angegebenen Status aus und bestimmt die entsprechenden Aktionen. |
| [MIP_CC_PolicyHandler_NotifyCommittedActions](functions.md#mip_cc_policyhandler_notifycommittedactions) | Wird von der Anwendung nach dem Anwenden berechneter Aktionen und dem Commit der Daten auf den Datenträger aufgerufen |
| [MIP_CC_LoadPolicyProfile](functions.md#mip_cc_loadpolicyprofile) | Profil laden |
| [MIP_CC_ReleasePolicyProfile](functions.md#mip_cc_releasepolicyprofile) | Freigeben von Ressourcen, die einem Richtlinien Profil zugeordnet sind |
| [MIP_CC_PolicyProfileSettings_SetSessionId](functions.md#mip_cc_policyprofilesettings_setsessionid) | Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann. |
| [MIP_CC_PolicyProfileSettings_SetHttpDelegate](functions.md#mip_cc_policyprofilesettings_sethttpdelegate) | Standard-HTTP-Stapel mit eigenem Client überschreiben |
| [MIP_CC_PolicyProfileSettings_SetTaskDispatcherDelegate](functions.md#mip_cc_policyprofilesettings_settaskdispatcherdelegate) | Standardmäßiger asynchroner Aufgaben Verteiler mit eigenem Client überschreiben |
| [MIP_CC_PolicyProfileSettings_SetCustomSettings](functions.md#mip_cc_policyprofilesettings_setcustomsettings) | Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden. |
| [MIP_CC_ReleasePolicyProfileSettings](functions.md#mip_cc_releasepolicyprofilesettings) | Freigeben von Ressourcen, die mit Richtlinien Profileinstellungen verknüpft sind |
| [MIP_CC_ProtectByTemplateAction_GetTemplateId](functions.md#mip_cc_protectbytemplateaction_gettemplateid) | Ruft die Vorlagen-ID "Schutz nach Vorlage" ab. |
| [MIP_CC_RemoveContentFooterAction_GetUIElementNames](functions.md#mip_cc_removecontentfooteraction_getuielementnames) | Ruft die zu entfern Endes UI-Elementnamen der Aktion "Inhalts Fußzeile entfernen" ab. |
| [MIP_CC_RemoveContentHeaderAction_GetUIElementNames](functions.md#mip_cc_removecontentheaderaction_getuielementnames) | Ruft die zu entfern Endes UI-Elementnamen der Aktion "Inhalts Header entfernen" ab. |
| [MIP_CC_RemoveWatermarkAction_GetUIElementNames](functions.md#mip_cc_removewatermarkaction_getuielementnames) | Ruft die zu entfern Endes UI-Elementnamen der Aktion "Wasserzeichen entfernen" ab. |
| [MIP_CC_ReleaseSensitivityType](functions.md#mip_cc_releasesensitivitytype) | Freigeben von Ressourcen, die einem Vertraulichkeits Typ zugeordnet sind |
| [MIP_CC_SensitivityType_GetRulePackageIdSize](functions.md#mip_cc_sensitivitytype_getrulepackageidsize) | Ruft die Größe des Puffers ab, der zum Speichern der Regelpaket-ID eines Vertraulichkeits Typs |
| [MIP_CC_SensitivityType_GetRulePackageId](functions.md#mip_cc_sensitivitytype_getrulepackageid) | Ruft die Regelpaket-ID eines Vertraulichkeits Typs ab. |
| [MIP_CC_SensitivityType_GetRulePackageSize](functions.md#mip_cc_sensitivitytype_getrulepackagesize) | Ruft die Größe des Puffers ab, der zum Speichern des Regel Pakets für sensible Typen erforderlich ist |
| [MIP_CC_SensitivityType_GetRulePackage](functions.md#mip_cc_sensitivitytype_getrulepackage) | Ruft das Regelpaket eines Vertraulichkeits Typs ab. |
