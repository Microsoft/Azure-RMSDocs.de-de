---
title: MIP SDK für C++-Referenz
description: MIP SDK für C++-Referenz
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 1db2faeca6c2ff00a0053a7d65d16872190d306f
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60172792"
---
# <a name="mip-sdk-for-c-reference"></a>MIP SDK für C++-Referenz

Das Microsoft Information Protection (MIP) SDK für C++ können Entwickler verwalten und Datenschutzrichtlinien auf Daten und andere digitale Objekte anzuwenden.

Das MIP SDK für C++ enthält:

- [Enumerationen und Strukturen](mip-enums-and-structs.md)
- [Functions (Funktionen)](mip-functions.md)
- Die folgenden Klassen:

 Klasse                         | Beschreibung                                
--------------------------------|---------------------------------------------
mip::AccessDeniedError-Klasse  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
mip::Action-Klasse  |  Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
mip::AddContentFooterAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Fußzeileninhalt hinzugefügt wird.
mip::AddContentHeaderAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
mip::AddWatermarkAction-Klasse  |  Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
class mip::AdhocProtectionRequiredError  |  Ad-hoc-Schutz muss zum Abschließen der Aktion auf die Datei festgelegt werden.
mip::ApplyLabelAction-Klasse  |  Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
Klasse mip::AuthDelegate  |  Delegat für die Authentifizierung bezogene Vorgänge.
Klasse mip::AuthDelegate::OAuth2Challenge  |  eine Klasse, die alle die erforderlichen aus der aufrufenden Anwendung Informationen um ein oauth2-Token zu generieren.
Klasse mip::AuthDelegate::OAuth2Token  |  Eine Klasse definiert, wie das MIP SDK für die oauth2-Token wieder in das SDK übergeben werden erwartet.
mip::BadInputError-Klasse  |  Der Fehler bei ungültiger Eingabe wird ausgegeben, wenn die Eingabe in eine SDK-API ungültig ist.
Klasse mip::ClassificationRequest  |  Klasse, die die Anforderung eines Aufrufs der Klassifizierung für den Ausführungsstatus enthält.
mip::ClassificationResult-Klasse  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
Klasse mip::ConsentDelegate  |  Delegat für Vorgänge, die eine Zustimmung erfordern
class mip::ConsentDeniedError  |  Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
mip::ContentLabel-Klasse  |  Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
mip::CustomAction-Klasse  |  [CustomAction](class_mip_customaction.md) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
mip::Error-Klasse  |  Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
mip::ExecutionState-Klasse  |  Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
mip::FileEngine-Klasse  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
mip::FileEngine::Settings-Klasse  | _Noch nicht dokumentiert._
Klasse mip::FileExecutionState  | _Noch nicht dokumentiert._
mip::FileHandler-Klasse  |  Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
mip::FileHandler::Observer-Klasse  |  [Observer](class_mip_filehandler_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse, die im Zusammenhang mit dem Dateihandler stehen.
mip::FileIOError-Klasse  |  Datei-E/A-Fehler.
mip::FileProfile-Klasse  |  Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
mip::FileProfile::Observer-Klasse  |  [Observer](class_mip_fileprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
mip::FileProfile::Settings-Klasse  |  [Einstellungen](class_mip_fileprofile_settings.md), die während der Erstellung und Lebensdauer von [FileProfile](class_mip_fileprofile.md) verwendet werden
class mip::HttpDelegate  |  Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
Klasse mip::HttpOperation  |  Schnittstelle, die einem HTTP-Vorgang, durch die Client-app implementiert werden, beim Überschreiben von beschreibt [HttpDelegate](class_mip_httpdelegate.md).
class mip::HttpRequest  |  Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
class mip::HttpResponse  |  Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
MIP:: Identity Klasse  |  Abstraktion für die Identität.
mip::InternalError-Klasse  |  Interner Fehler. Dieser Fehler tritt auf, wenn während der Ausführung etwas Unerwartetes passiert.
mip::JustificationRequiredError-Klasse  | _Noch nicht dokumentiert._
mip::JustifyAction-Klasse  |  Diese [Aktion](class_mip_action.md) fordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Einstellen der Antwort im Ausführungsstatus an.
mip::Label-Klasse  |  Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
mip::LabelingOptions-Klasse  |  Schnittstelle für die Konfiguration von Bezeichnungsoptionen für die Methoden „SetLabel“ und „DeleteLabel“
mip::LoggerDelegate-Klasse  |  Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
mip::MetadataAction-Klasse  |  Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
mip::NetworkError-Klasse  |  Ein Netzwerkfehler Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
Klasse mip::NoAuthTokenError  |  Der Benutzer konnte Zugriff auf den Inhalt aufgrund fehlender Authentifizierungstoken nicht abgerufen werden.
Klasse mip::NoPermissionsError  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
Klasse mip::NoPolicyError  |  Richtlinien für Mandanten ist nicht für klassifizierungsbezeichnungen/konfiguriert.
mip::NotSupportedError-Klasse  |  Der von der Anwendung angeforderte Vorgang wird vom SDK nicht unterstützt.
Klasse mip::OperationCancelledError  |  Vorgang wurde abgebrochen.
mip::PolicyEngine-Klasse  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
mip::PolicyEngine::Settings-Klasse  |  Definiert die einer [PolicyEngine](class_mip_policyengine.md)-Klasse zugeordneten Einstellungen.
Die Klasse „mip::PolicyHandler“  |  Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
mip::PolicyProfile-Klasse  |  Die [PolicyProfile](class_mip_policyprofile.md)-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine [PolicyProfile](class_mip_policyprofile.md)-Klasse, kann bei Bedarf aber mehrere erstellen.
mip::PolicyProfile::Observer-Klasse  |  [Observer](class_mip_policyprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
mip::PolicyProfile::Settings-Klasse  |  [Einstellungen](class_mip_policyprofile_settings.md), die während der Erstellung und Lebensdauer von [PolicyProfile](class_mip_policyprofile.md) verwendet werden
mip::PolicySyncError-Klasse  |  Ein fehlgeschlagener Versuch, Richtliniendaten zu synchronisieren.
mip::PrivilegedRequiredError-Klasse  |  Die aktuelle Bezeichnung wurde als privilegierter Vorgang zugewiesen (das Äquivalent zu einem Administratorvorgang), daher kann sie nicht außer Kraft gesetzt werden.
mip::ProtectAdhocAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Ad-hoc-Schutz hinzugefügt wird.
mip::ProtectByTemplateAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
mip::ProtectDoNotForwardAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form von Nichtweiterleitung hinzugefügt wird.
mip::ProtectionDescriptor-Klasse  |  Beschreibung des Schutzes, der einem Inhaltselement zugeordnet ist.
mip::ProtectionDescriptorBuilder-Klasse  |  Erstellt eine [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
mip::ProtectionEngine-Klasse  |  Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
mip::ProtectionEngine::Observer-Klasse  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionEngine](class_mip_protectionengine.md) empfängt
mip::ProtectionEngine::Settings-Klasse  |  [Einstellungen](class_mip_protectionengine_settings.md), die während der Erstellung und Lebensdauer von [ProtectionEngine](class_mip_protectionengine.md) verwendet werden
mip::ProtectionHandler-Klasse  |  Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
mip::ProtectionHandler::Observer-Klasse  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionHandler](class_mip_protectionhandler.md) empfängt
mip::ProtectionProfile-Klasse  |  [ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
mip::ProtectionProfile::Observer-Klasse  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md) empfängt.
mip::ProtectionProfile::Settings-Klasse  |  [Einstellungen](class_mip_protectionprofile_settings.md), die während der Erstellung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden.
Klasse mip::ProxyAuthenticationError  |  Fehler bei der Proxyauthentifizierung.
mip::RecommendLabelAction-Klasse  |  Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
mip::RemoveContentFooterAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt aus dem Dokument entfernt wird.
mip::RemoveContentHeaderAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird.
mip::RemoveProtectionAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Schutz aus dem Dokument entfernt wird.
mip::RemoveWatermarkAction-Klasse  |  Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
class mip::SensitivityTypesRulePackage  | _Noch nicht dokumentiert._
Klasse mip::ServiceDisabledError  |  Der Benutzer konnte Zugriff auf den Inhalt, da ein Dienst, der deaktiviert werden nicht abgerufen werden.
mip::Stream-Klasse  |  Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
Klasse mip::TaskDispatcherDelegate  |  Eine Klasse, die die Schnittstelle an den Verteiler des MIP SDK Aufgabe definiert.
class mip::TransientNetworkError  |  Vorübergehender Netzwerkfehler. Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt. Es kann erneut versucht werden, den Vorgang auszuführen, da es sich um einen vorübergehenden Fehler handelt.
mip::UserRights-Klasse  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
mip::UserRoles-Klasse  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.