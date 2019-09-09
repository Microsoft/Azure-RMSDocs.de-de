---
title: MIP SDK für C++ Referenz
description: MIP SDK für C++ Referenz
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 2fab85dfd5b5d0d1103f9c3ee4b0d3725a10cb8f
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884834"
---
# <a name="mip-sdk-for-c-reference"></a>MIP SDK für C++ Referenz

Das Microsoft Information Protection (MIP) SDK für C++ ermöglicht Entwicklern das Verwalten und Anwenden von Datenschutzrichtlinien auf Daten und andere digitale Ressourcen.

Das MIP SDK für C++ enthält:

- [Enumerationen und Strukturen](mip-enums-and-structs.md)
- [Funktionen](mip-functions.md)
- Die folgenden Klassen:

 Klasse                         | Beschreibung                                
--------------------------------|---------------------------------------------
mip::AccessDeniedError-Klasse  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
mip::Action-Klasse  |  Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
MIP:: aktiondata-Klasse  | _Noch nicht dokumentiert._
mip::AddContentFooterAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Fußzeileninhalt hinzugefügt wird.
mip::AddContentHeaderAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
mip::AddWatermarkAction-Klasse  |  Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
MIP:: addwatermarkaktiondata-Klasse  | _Noch nicht dokumentiert._
MIP:: adhucschutzrequirements derror-Klasse  |  Der Ad-hoc-Schutz sollte festgelegt werden, um die Aktion für die Datei abzuschließen.
MIP:: applicationaktionstate-Klasse  | _Noch nicht dokumentiert._
mip::ApplyLabelAction-Klasse  |  Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
MIP:: argumentdata-Klasse  | _Noch nicht dokumentiert._
MIP:: authdelegat-Klasse  |  Delegat für Vorgänge im Zusammenhang mit der Authentifizierung.
mip::BadInputError-Klasse  |  Der Fehler bei ungültiger Eingabe wird ausgegeben, wenn die Eingabe in eine SDK-API ungültig ist.
MIP:: classificationdata-Klasse  | _Noch nicht dokumentiert._
MIP:: classificationrequest-Klasse  |  Eine Klasse, die die Anforderung eines Klassifizierungs Aufrufes für den Ausführungs Status enthält.
mip::ClassificationResult-Klasse  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
MIP:: computeengine-Klasse  | _Noch nicht dokumentiert._
MIP:: computeenginecontext-Klasse  | _Noch nicht dokumentiert._
MIP:: conditiondata-Klasse  | _Noch nicht dokumentiert._
MIP:: einvernehmdelegat-Klasse  |  Delegat für Vorgänge, die eine Zustimmung erfordern
class mip::ConsentDeniedError  |  Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
mip::ContentLabel-Klasse  |  Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
MIP:: contentmarkingaktiondata-Klasse  | _Noch nicht dokumentiert._
mip::CustomAction-Klasse  |  [CustomAction](class_mip_customaction.md) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
MIP::D eprecatedapierror-Klasse  |  Der Aufrufer hat eine veraltete API aufgerufen.
MIP::D ocenumentstate-Klasse  | _Noch nicht dokumentiert._
mip::Error-Klasse  |  Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
mip::ExecutionState-Klasse  |  Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
mip::FileEngine-Klasse  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
MIP:: fileexecutionstate-Klasse  | _Noch nicht dokumentiert._
mip::FileHandler-Klasse  |  Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
MIP:: filinput Spector-Klasse  | _Noch nicht dokumentiert._
mip::FileIOError-Klasse  |  Datei-E/A-Fehler.
mip::FileProfile-Klasse  |  Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
class mip::HttpDelegate  |  Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
MIP:: httpoperation-Klasse  |  Schnittstelle, die einen einzelnen http-Vorgang beschreibt, der von der Client-App beim Überschreiben von [httpdelegaten](class_mip_httpdelegate.md)
class mip::HttpRequest  |  Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
class mip::HttpResponse  |  Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
MIP:: Identity-Klasse  |  Abstraktion für Identity.
mip::InternalError-Klasse  |  Interner Fehler. Dieser Fehler tritt auf, wenn während der Ausführung etwas Unerwartetes passiert.
mip::JustificationRequiredError-Klasse  | _Noch nicht dokumentiert._
mip::JustifyAction-Klasse  |  Diese [Aktion](class_mip_action.md) fordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Einstellen der Antwort im Ausführungsstatus an.
mip::Label-Klasse  |  Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
MIP:: labelaktiondata-Klasse  | _Noch nicht dokumentiert._
MIP:: labeldisablederror-Klasse  |  Die [Bezeichnung](class_mip_label.md) ist deaktiviert oder inaktiv.
MIP:: labelgroupdata-Klasse  | _Noch nicht dokumentiert._
mip::LabelingOptions-Klasse  |  Schnittstelle für die Konfiguration von Bezeichnungsoptionen für die Methoden „SetLabel“ und „DeleteLabel“
MIP:: labelnotfounderror-Klasse  |  [Bezeichnung](class_mip_label.md) Die ID wurde nicht erkannt.
mip::LoggerDelegate-Klasse  |  Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
mip::MetadataAction-Klasse  |  Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
MIP:: mipcontext-Klasse  | Mipcontext stellt den Status dar, der von allen Profilen, Engines und Handlern gemeinsam genutzt wird.
MIP:: msgattachmentdata-Klasse  | _Noch nicht dokumentiert._
MIP:: msginspector-Klasse  | _Noch nicht dokumentiert._
mip::NetworkError-Klasse  |  Ein Netzwerkfehler Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
MIP:: noauthdekenerror-Klasse  |  Der Benutzer konnte aufgrund eines fehlenden Authentifizierungs Tokens keinen Zugriff auf den Inhalt erhalten.
MIP:: nopermissionserror-Klasse  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
MIP:: nopolicyerror-Klasse  |  Die Mandanten Richtlinie ist nicht für Klassifizierung/Bezeichnungen konfiguriert.
mip::NotSupportedError-Klasse  |  Der von der Anwendung angeforderte Vorgang wird vom SDK nicht unterstützt.
MIP:: operationcancellederror-Klasse  |  Der Vorgang wurde abgebrochen.
mip::PolicyEngine-Klasse  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
Die Klasse „mip::PolicyHandler“  |  Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
MIP::P olicypackagedata-Klasse  | _Noch nicht dokumentiert._
mip::PolicyProfile-Klasse  |  Die [PolicyProfile](class_mip_policyprofile.md)-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine [PolicyProfile](class_mip_policyprofile.md)-Klasse, kann bei Bedarf aber mehrere erstellen.
MIP::P olicyruledata-Klasse  | _Noch nicht dokumentiert._
mip::PolicySyncError-Klasse  |  Ein fehlgeschlagener Versuch, Richtliniendaten zu synchronisieren.
mip::PrivilegedRequiredError-Klasse  |  Die aktuelle Bezeichnung wurde als privilegierter Vorgang zugewiesen (das Äquivalent zu einem Administratorvorgang), daher kann sie nicht außer Kraft gesetzt werden.
MIP::P ropertydata  | _Noch nicht dokumentiert._
mip::ProtectAdhocAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Ad-hoc-Schutz hinzugefügt wird.
mip::ProtectByTemplateAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
mip::ProtectDoNotForwardAction-Klasse  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form von Nichtweiterleitung hinzugefügt wird.
MIP::P rotectionaktiondata  | _Noch nicht dokumentiert._
mip::ProtectionDescriptor-Klasse  |  Beschreibung des Schutzes, der einem Inhaltselement zugeordnet ist.
mip::ProtectionDescriptorBuilder-Klasse  |  Erstellt eine [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
mip::ProtectionEngine-Klasse  |  Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
mip::ProtectionHandler-Klasse  |  Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
mip::ProtectionProfile-Klasse  |  [ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
MIP::P rotectionsettings-Klasse  |  Schnittstelle zum Konfigurieren von Schutz Optionen für die setlabel-Methode.
MIP::P roxyauthenticationerror-Klasse  |  Fehler bei der Proxy Authentifizierung.
MIP::P ublishinglicenseingefo-Klasse  |  Enthält die Details einer Veröffentlichungslizenz, die zum Erstellen eines Schutzhandlers verwendet wird.
mip::RecommendLabelAction-Klasse  |  Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
mip::RemoveContentFooterAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt aus dem Dokument entfernt wird.
mip::RemoveContentHeaderAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird.
mip::RemoveProtectionAction-Klasse  |  Eine Aktionsklasse, die angibt, dass der Schutz aus dem Dokument entfernt wird.
mip::RemoveWatermarkAction-Klasse  |  Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
MIP:: rulepackagedata-Klasse  | _Noch nicht dokumentiert._
MIP:: sensitivityconditiondata-Klasse  | _Noch nicht dokumentiert._
MIP:: sensitivitytypesrulepackage-Klasse  | _Noch nicht dokumentiert._
MIP:: servicedisablederror-Klasse  |  Der Benutzer konnte aufgrund eines deaktivierten diensdienstanbieter keinen Zugriff auf den Inhalt erhalten.
mip::Stream-Klasse  |  Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
MIP:: syncfilebasedata-Klasse  | _Noch nicht dokumentiert._
MIP:: syncfilepolicydata-Klasse  | _Noch nicht dokumentiert._
MIP:: syncfilesensitivitydata-Klasse  | _Noch nicht dokumentiert._
MIP:: taskdispatcherdelegat-Klasse  |  Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
MIP:: templatenumerotfounderror-Klasse  |  Die Vorlagen-ID wird vom RMS-Dienst nicht erkannt.
class mip::TransientNetworkError  |  Vorübergehender Netzwerkfehler. Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt. Es kann erneut versucht werden, den Vorgang auszuführen, da es sich um einen vorübergehenden Fehler handelt.
mip::UserRights-Klasse  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
mip::UserRoles-Klasse  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
