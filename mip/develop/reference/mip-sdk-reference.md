---
title: MIP SDK für C++-Referenz
description: MIP SDK für C++-Referenz
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 80b0ae49220cfb745e0fa0a0a0ce004d132c4d3f
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333771"
---
# <a name="mip-sdk-for-c-reference"></a>MIP SDK für C++-Referenz

Das Microsoft Information Protection (MIP) SDK für C++ können Entwickler verwalten und Datenschutzrichtlinien auf Daten und andere digitale Objekte anzuwenden.  

Das MIP SDK für C++ enthält:

- [Enumerationen und Strukturen](mip-enums-and-structs.md)
- [Functions (Funktionen)](mip-functions.md)
- Die folgenden Klassen:

| Namespace::Class-name | Beschreibung |
| :----------|:------------|
[mip::AccessDeniedError](class_mip_AccessDeniedError.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
[mip::Action](class_mip_Action.md)  |  Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
[mip::AddContentFooterAction](class_mip_AddContentFooterAction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Fußzeileninhalt hinzugefügt wird.
[mip::AddContentHeaderAction](class_mip_AddContentHeaderAction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
[mip::AddWatermarkAction](class_mip_AddWatermarkAction.md)  |  Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
[mip::ApplyLabelAction](class_mip_ApplyLabelAction.md)  |  Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
[mip::AuthDelegate](class_mip_AuthDelegate.md)  |  Delegat für die Authentifizierung bezogene Vorgänge.
[mip::BadInputError](class_mip_BadInputError.md)  |  Der Fehler bei ungültiger Eingabe wird ausgegeben, wenn die Eingabe in eine SDK-API ungültig ist.
[mip::ClassificationRequest](class_mip_ClassificationRequest.md)  |  Klasse, die die Anforderung eines Aufrufs der Klassifizierung für den Ausführungsstatus enthält.
[mip::ClassificationResult](class_mip_ClassificationResult.md)  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
[mip::ConsentDelegate](class_mip_ConsentDelegate.md)  |  Delegat für Vorgänge, die eine Zustimmung erfordern
[mip::ConsentDeniedError](class_mip_ConsentDeniedError.md)  |  Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
[mip::ContentLabel](class_mip_ContentLabel.md)  |  Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
[mip::CustomAction](class_mip_CustomAction.md)  |  [CustomAction](class_mip_customaction.md) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
[mip::Error](class_mip_Error.md)  |  Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
[mip::ExecutionState](class_mip_ExecutionState.md)  |  Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
[mip::FileEngine](class_mip_FileEngine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[mip::FileExecutionState](class_mip_FileExecutionState.md)  | _Noch nicht dokumentiert._
[mip::FileHandler](class_mip_FileHandler.md)  |  Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
[mip::FileIOError](class_mip_FileIOError.md)  |  Datei-E/A-Fehler.
[mip::FileProfile](class_mip_FileProfile.md)  |  Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
[mip::HttpDelegate](class_mip_HttpDelegate.md)  |  Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
[mip::HttpRequest](class_mip_HttpRequest.md)  |  Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
[mip::HttpResponse](class_mip_HttpResponse.md)  |  Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
[mip::Identity](class_mip_Identity.md)  |  Abstraktion für die Identität.
[mip::InternalError](class_mip_InternalError.md)  |  Interner Fehler. Dieser Fehler tritt auf, wenn während der Ausführung etwas Unerwartetes passiert.
[mip::JustificationRequiredError](class_mip_JustificationRequiredError.md)  | _Noch nicht dokumentiert._
[mip::JustifyAction](class_mip_JustifyAction.md)  |  Diese [Aktion](class_mip_action.md) fordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Einstellen der Antwort im Ausführungsstatus an.
[mip::Label](class_mip_Label.md)  |  Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
[mip::LabelingOptions](class_mip_LabelingOptions.md)  |  Schnittstelle für die Konfiguration von Bezeichnungsoptionen für die Methoden „SetLabel“ und „DeleteLabel“
[mip::LoggerDelegate](class_mip_LoggerDelegate.md)  |  Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
[mip::MetadataAction](class_mip_MetadataAction.md)  |  Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
[mip::NetworkError](class_mip_NetworkError.md)  |  Ein Netzwerkfehler Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
[mip::NoAuthTokenError](class_mip_NoAuthTokenError.md)  |  Der Benutzer konnte Zugriff auf den Inhalt aufgrund fehlender Authentifizierungstoken nicht abgerufen werden.
[mip::NoPermissionsError](class_mip_NoPermissionsError.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
[mip::NoPolicyError](class_mip_NoPolicyError.md)  |  Richtlinien für Mandanten ist nicht für klassifizierungsbezeichnungen/konfiguriert.
[mip::NotSupportedError](class_mip_NotSupportedError.md)  |  Der von der Anwendung angeforderte Vorgang wird vom SDK nicht unterstützt.
[mip::PolicyEngine](class_mip_PolicyEngine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[mip::PolicyHandler](class_mip_PolicyHandler.md)  |  Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
[mip::PolicyProfile](class_mip_PolicyProfile.md)  |  Die [PolicyProfile](class_mip_policyprofile.md)-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine [PolicyProfile](class_mip_policyprofile.md)-Klasse, kann bei Bedarf aber mehrere erstellen.
[mip::PolicySyncError](class_mip_PolicySyncError.md)  |  Ein fehlgeschlagener Versuch, Richtliniendaten zu synchronisieren.
[mip::PrivilegedRequiredError](class_mip_PrivilegedRequiredError.md)  |  Die aktuelle Bezeichnung wurde als privilegierter Vorgang zugewiesen (das Äquivalent zu einem Administratorvorgang), daher kann sie nicht außer Kraft gesetzt werden.
[mip::ProtectAdhocAction](class_mip_ProtectAdhocAction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Ad-hoc-Schutz hinzugefügt wird.
[mip::ProtectByTemplateAction](class_mip_ProtectByTemplateAction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
[mip::ProtectDoNotForwardAction](class_mip_ProtectDoNotForwardAction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form von Nichtweiterleitung hinzugefügt wird.
[mip::ProtectionDescriptor](class_mip_ProtectionDescriptor.md)  |  Beschreibung des Schutzes, der einem Inhaltselement zugeordnet ist.
[mip::ProtectionDescriptorBuilder](class_mip_ProtectionDescriptorBuilder.md)  |  Erstellt eine [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
[mip::ProtectionEngine](class_mip_ProtectionEngine.md)  |  Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
[mip::ProtectionHandler](class_mip_ProtectionHandler.md)  |  Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
[mip::ProtectionProfile](class_mip_ProtectionProfile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
[mip::ProxyAuthenticationError](class_mip_ProxyAuthenticationError.md)  |  Fehler bei der Proxyauthentifizierung.
[mip::RecommendLabelAction](class_mip_RecommendLabelAction.md)  |  Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
[mip::RemoveContentFooterAction](class_mip_RemoveContentFooterAction.md)  |  Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt aus dem Dokument entfernt wird.
[mip::RemoveContentFooterAction](class_mip_RemoveContentHeaderAction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird.
[mip::RemoveContentFooterAction](class_mip_RemoveProtectionAction.md)  |  Eine Aktionsklasse, die angibt, dass der Schutz aus dem Dokument entfernt wird.
[mip::RemoveContentFooterAction](class_mip_RemoveWatermarkAction.md)  |  Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
[mip::SensitivityTypesRulePackage](class_mip_SensitivityTypesRulePackage.md)  | _Noch nicht dokumentiert._
[mip::ServiceDisabledError](class_mip_ServiceDisabledError.md)  |  Der Benutzer konnte Zugriff auf den Inhalt, da ein Dienst, der deaktiviert werden nicht abgerufen werden.
[mip::Stream](class_mip_Stream.md)  |  Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
[mip::TransientNetworkError](class_mip_TransientNetworkError.md)  |  Vorübergehender Netzwerkfehler. Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt. Es kann erneut versucht werden, den Vorgang auszuführen, da es sich um einen vorübergehenden Fehler handelt.
[mip::UserRights](class_mip_UserRights.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
[mip::UserRoles](class_mip_UserRoles.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
