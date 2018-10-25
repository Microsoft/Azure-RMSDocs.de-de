---
title: Referenz zu MIP SDK für C++ (Vorschau)
description: Referenz zu MIP SDK für C++ (Vorschau)
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06d8bb26a8e3026562006d68d4ae8d1630eba81c
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446327"
---
# <a name="mip-sdk-for-c-preview-reference"></a>Referenz zu MIP SDK für C++ (Vorschau)

Mit dem Microsoft Information Protection (MIP) SDK für C++ (Vorschau) können Entwickler Datenschutzrichtlinien für Daten und andere digitale Objekte verwalten und anwenden.  

Weitere Informationen hierzu finden Sie im [Blog für MIP-Entwickler](https://aka.ms/MIPDevelopers)<!-- and [MIP samples](https://aka.ms/mipsdksamples)-->.

Das MIP SDK für C++ enthält:

- [Enumerationen und Strukturen](mip-enums-and-structs.md)
- [Functions (Funktionen)](mip-functions.md)
- Die folgenden Klassen:

| Klassenname | Beschreibung |
| :----------|:------------|
[AccessDeniedError](class_mip_accessdeniederror.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
[Aktion](class_mip_action.md)  |  Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
[AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Fußzeileninhalt hinzugefügt wird.
[AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
[AddWatermarkAction](class_mip_addwatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
[ApplyLabelAction](class_mip_applylabelaction.md)  |  Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
[BadInputError](class_mip_badinputerror.md)  |  Der Fehler bei ungültiger Eingabe wird ausgegeben, wenn die Eingabe in eine SDK-API ungültig ist.
[ClassificationResult](class_mip_classificationresult.md)  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
[ConsentDelegate](class_consentdelegate.md)  |  Delegat für Vorgänge, die eine Zustimmung erfordern
[ConsentDeniedError](class_mip_consentdeniederror.md)  |  Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
[ContentLabel](class_mip_contentlabel.md)  |  Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
[CustomAction](class_mip_customaction.md)  |  [CustomAction](class_mip_customaction.md) ist eine generische Aktionsklasse, die die untergeordneten Eigenschaften der Aktion als Eigenschaftensammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
[Fehler](class_mip_error.md)  |  Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
[ExecutionState](class_mip_executionstate.md)  |  Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
[FileEngine::Settings](class_mip_fileengine_settings.md)  | _Noch nicht dokumentiert._
[FileEngine](class_mip_fileengine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[FileHandler::Observer](class_mip_filehandler_observer.md)  |  [Observer](class_mip_filehandler_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse, die im Zusammenhang mit dem Dateihandler stehen.
[FileHandler](class_mip_filehandler.md)  |  Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
[FileIOError](class_mip_fileioerror.md)  |  Datei-E/A-Fehler.
[FileProfile::Observer](class_mip_fileprofile_observer.md)  |  [Observer](class_mip_fileprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
[FileProfile::Settings](class_mip_fileprofile_settings.md)  |  [Einstellungen](class_mip_fileprofile_settings.md), die während der Erstellung und Lebensdauer von [FileProfile](class_mip_fileprofile.md) verwendet werden
[FileProfile](class_mip_fileprofile.md)  |  Die [FileProfile](class_mip_fileprofile.md)-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
[HttpDelegate](class_mip_httpdelegate.md)  |  Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
[HttpRequest](class_mip_httprequest.md)  |  Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
[HttpResponse](class_mip_httpresponse.md)  |  Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des [HttpDelegate](class_mip_httpdelegate.md) implementiert wird.
[InternalError](class_mip_internalerror.md)  |  Interner Fehler. Dieser Fehler tritt auf, wenn während der Ausführung etwas Unerwartetes passiert.
[JustificationRequiredError](class_mip_justificationrequirederror.md)  | _Noch nicht dokumentiert._
[JustifyAction](class_mip_justifyaction.md)  |  Diese [Aktion](class_mip_action.md) fordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Einstellen der Antwort im Ausführungsstatus an.
[Label](class_mip_label.md)  |  Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
[LabelingOptions](class_mip_labelingoptions.md)  |  Schnittstelle für die Konfiguration von Bezeichnungsoptionen für die Methoden „SetLabel“ und „DeleteLabel“
[LoggerDelegate](class_mip_loggerdelegate.md)  |  Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
[MetadataAction](class_mip_metadataaction.md)  |  Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
[NetworkError](class_mip_networkerror.md)  |  Ein Netzwerkfehler Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
[NotSupportedError](class_mip_notsupportederror.md)  |  Der von der Anwendung angeforderte Vorgang wird vom SDK nicht unterstützt.
[PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  Definiert die einer [PolicyEngine](class_mip_policyengine.md)-Klasse zugeordneten Einstellungen.
[PolicyEngine](class_mip_policyengine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[PolicyHandler](class_mip_policyhandler.md)  |  Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
[PolicyProfile::Observer](class_mip_policyprofile_observer.md)  |  [Observer](class_mip_policyprofile_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
[PolicyProfile::Settings](class_mip_policyprofile_settings.md)  |  [Einstellungen](class_mip_policyprofile_settings.md), die während der Erstellung und Lebensdauer von [PolicyProfile](class_mip_policyprofile.md) verwendet werden
[PolicyProfile](class_mip_policyprofile.md)  |  Die [PolicyProfile](class_mip_policyprofile.md)-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine [PolicyProfile](class_mip_policyprofile.md)-Klasse, kann bei Bedarf aber mehrere erstellen.
[PolicySyncError](class_mip_policysyncerror.md)  |  Ein fehlgeschlagener Versuch, Richtliniendaten zu synchronisieren.
[PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  Die aktuelle Bezeichnung wurde als privilegierter Vorgang zugewiesen (das Äquivalent zu einem Administratorvorgang), daher kann sie nicht außer Kraft gesetzt werden.
[ProtectAdhocAction](class_mip_protectadhocaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Ad-hoc-Schutz hinzugefügt wird.
[ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
[ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form von Nichtweiterleitung hinzugefügt wird.
[ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  Beschreibung des Schutzes, der einem Inhaltselement zugeordnet ist.
[ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  Erstellt eine [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
[ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionEngine](class_mip_protectionengine.md) empfängt
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  [Einstellungen](class_mip_protectionengine_settings.md), die während der Erstellung und Lebensdauer von [ProtectionEngine](class_mip_protectionengine.md) verwendet werden
[ProtectionEngine](class_mip_protectionengine.md)  |  Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
[ProtectionHandler::Observer](class_mip_protectionhandler.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionHandler](class_mip_protectionhandler.md) empfängt
[ProtectionHandler](class_mip_protectionhandler.md)  |  Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md) empfängt.
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  [Einstellungen](class_mip_protectionprofile_settings.md), die während der Erstellung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden.
[ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) ist die Stammklasse für Schutzvorgänge.
[RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
[RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt aus dem Dokument entfernt wird.
[RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird.
[RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  Eine Aktionsklasse, die angibt, dass der Schutz aus dem Dokument entfernt wird.
[RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
[Stream](class_mip_stream.md)  |  Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
[TransientNetworkError](class_mip_transientnetworkerror.md)  |  Vorübergehender Netzwerkfehler. Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt. Es kann erneut versucht werden, den Vorgang auszuführen, da es sich um einen vorübergehenden Fehler handelt.
[UserRights](class_mip_userrights.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
[UserRoles](class_mip_userroles.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
