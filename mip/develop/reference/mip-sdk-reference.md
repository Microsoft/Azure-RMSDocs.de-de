---
title: MIP SDK für C++-Referenz
description: MIP SDK für C++-Referenz
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: da5ee17fbb177fe9b6e37461a5d35425a3945e59
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566760"
---
# <a name="mip-sdk-for-c-reference"></a>MIP SDK für C++-Referenz

Das Microsoft Information Protection (MIP) SDK für C++ ermöglicht Entwicklern das Verwalten und Anwenden von Datenschutzrichtlinien auf Daten und andere digitale Ressourcen.

Das MIP SDK für C++ enthält:

- [Enumerationen und Strukturen](mip-enums-and-structs.md)
- [Funktionen](mip-functions.md)
- Die folgenden Klassen:

## <a name="namespace-mip-classes"></a>Namespace-MIP-Klassen

 Klasse                         | BESCHREIBUNG                                
--------------------------------|---------------------------------------------
[Class accessdeniederror](class_mip_accessdeniederror.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
[Class-Aktion](class_mip_action.md)  |  Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
[Klasse "Aktions Daten"](class_mip_actiondata.md)  | Noch nicht dokumentiert.
[addcontentfooteraction-Klasse](class_mip_addcontentfooteraction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Fußzeileninhalt hinzugefügt wird.
[addcontenderaderaction-Klasse](class_mip_addcontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
[addwatermarkaction-Klasse](class_mip_addwatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
[Klasse addwatermarkaktiondata](class_mip_addwatermarkactiondata.md)  | Noch nicht dokumentiert.
[adhucschutzrequirements derror-Klasse](class_mip_adhocprotectionrequirederror.md)  |  Der Ad-hoc-Schutz sollte festgelegt werden, um die Aktion für die Datei abzuschließen.
[applicationaktionstate-Klasse](class_mip_applicationactionstate.md)  | Noch nicht dokumentiert.
[Class applylabelaction](class_mip_applylabelaction.md)  |  Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
[Klasse argumentdata](class_mip_argumentdata.md)  | Noch nicht dokumentiert.
[AsyncControl-Klasse](class_mip_asynccontrol.md)  |  Klasse zum Abbrechen des asynchronen Vorgangs.
[klassenauthdelegat](class_mip_authdelegate.md)  |  Delegat für Vorgänge im Zusammenhang mit der Authentifizierung.
[Class badinputerror](class_mip_badinputerror.md)  |  Der Fehler bei ungültiger Eingabe wird ausgegeben, wenn die Eingabe in eine SDK-API ungültig ist.
[Class classificationdata](class_mip_classificationdata.md)  | Noch nicht dokumentiert.
[Class classificationrequest](class_mip_classificationrequest.md)  |  Eine Klasse, die die Anforderung eines Klassifizierungs Aufrufes für den Ausführungs Status enthält.
[Class classificationresult](class_mip_classificationresult.md)  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
[Class computeengine](class_mip_computeengine.md)  | Noch nicht dokumentiert.
[Class computeenginecontext](class_mip_computeenginecontext.md)  | Noch nicht dokumentiert.
[conditiondata-Klasse](class_mip_conditiondata.md)  | Noch nicht dokumentiert.
[ConsentDelegate-Klasse](class_mip_consentdelegate.md)  |  Delegat für Vorgänge, die eine Zustimmung erfordern
[Klasse "genehmideniederror"](class_mip_consentdeniederror.md)  |  Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
[Class Protection Handler:: consumptionsettings](class_mip_protectionhandler_consumptionsettings.md)  |  Einstellungen zum Erstellen eines Schutz Handlers, um vorhandenen Inhalt zu nutzen.
[Klasse "contentlabel"](class_mip_contentlabel.md)  |  Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
[Klasse contentmarkingaktiondata](class_mip_contentmarkingactiondata.md)  | Noch nicht dokumentiert.
[CustomAction-Klasse](class_mip_customaction.md)  |  CustomAction ist eine generische Aktionsklasse, die alle untergeordneten Eigenschaften der Aktion als Eigenschaften Sammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
[Klasse deprecatedapierror](class_mip_deprecatedapierror.md)  |  Der Aufrufer hat eine veraltete API aufgerufen.
[Klasse detailedclassificationresult](class_mip_detailedclassificationresult.md)  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
[Klasse DocumentState](class_mip_documentstate.md)  | Noch nicht dokumentiert.
[Klassen Fehler](class_mip_error.md)  |  Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
[Klasse executionstate](class_mip_executionstate.md)  |  Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
[Klassen-fileengine](class_mip_fileengine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[Class fileexecutionstate](class_mip_fileexecutionstate.md)  | Noch nicht dokumentiert.
[Klassen-Datei Handler](class_mip_filehandler.md)  |  Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
[Class filinput Spector](class_mip_fileinspector.md)  | Noch nicht dokumentiert.
[class "fleioerror"](class_mip_fileioerror.md)  |  Datei-E/A-Fehler.
[class file profile](class_mip_fileprofile.md)  |  Die FileProfile-Klasse ist die Stammklasse für Microsoft Information Protection-Vorgänge.
[Klasse httpdelegat](class_mip_httpdelegate.md)  |  Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
[httpoperation-Klasse](class_mip_httpoperation.md)  |  Schnittstelle, die einen einzelnen http-Vorgang beschreibt, der von der Client-App beim Überschreiben von httpdelegaten
[HttpRequest-Klasse](class_mip_httprequest.md)  |  Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
[HttpResponse-Klasse](class_mip_httpresponse.md)  |  Schnittstelle, die eine einfache HTTP-Antwort beschreibt und von der Client-App beim Überschreiben des HttpDelegate implementiert wird.
[klassenidentität](class_mip_identity.md)  |  Abstraktion für Identity.
[Class insuffizientbuffererror](class_mip_insufficientbuffererror.md)  |  Nicht genügend Puffer Fehler.
[Class InternalError](class_mip_internalerror.md)  |  Interner Fehler. Dieser Fehler tritt auf, wenn während der Ausführung etwas Unerwartetes passiert.
[Class Recht cationrequirements derror](class_mip_justificationrequirederror.md)  | Noch nicht dokumentiert.
[Klasse "justifyaction"](class_mip_justifyaction.md)  |  Diese Aktion fordert eine Legitimation zum Herabstufen einer Bezeichnung und zum Einstellen der Antwort im Ausführungsstatus an.
[Klassenbezeichnung](class_mip_label.md)  |  Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
[Klasse ' labelaktionsdaten '](class_mip_labelactiondata.md)  | Noch nicht dokumentiert.
[Klasse "labeldisablederror"](class_mip_labeldisablederror.md)  |  Die Bezeichnung ist deaktiviert oder inaktiv.
[Klasse labelgroupdata](class_mip_labelgroupdata.md)  | Noch nicht dokumentiert.
[Klasse "labelingoptions"](class_mip_labelingoptions.md)  |  Schnittstelle für die Konfiguration von Bezeichnungsoptionen für die Methoden „SetLabel“ und „DeleteLabel“
[Klasse "labelnotfounderror"](class_mip_labelnotfounderror.md)  |  Die Bezeichnungs-ID wurde nicht erkannt.
[Klasse licensenotregisterederror](class_mip_licensenotregisterederror.md)  |  Die Lizenz ist nicht registriert.
[Klasse loggerdelegat](class_mip_loggerdelegate.md)  |  Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
[Class MetadataAction](class_mip_metadataaction.md)  |  Eine Aktion, die Metadateninformationen zum Inhalt hinzufügt
[Class MetadataEntry](class_mip_metadataentry.md)  |  Eine Abstraktions Klasse für den Metadateneintrag.
[Class MetadataVersion](class_mip_metadataversion.md)  |  Eine Schnittstelle für eine MetadataVersion. MetadataVersion bestimmt, welche Metadaten aktiv sind und wie Sie verarbeitet werden.
[Class mipcontext](class_mip_mipcontext.md)  |  Mipcontext stellt den Status dar, der von allen Profilen, Engines und Handlern gemeinsam genutzt wird.
[Klasse msgattachmentdata](class_mip_msgattachmentdata.md)  | Noch nicht dokumentiert.
[Klasse msginspector](class_mip_msginspector.md)  | Noch nicht dokumentiert.
[Klasse NetworkError](class_mip_networkerror.md)  |  Netzwerkfehler. Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
[noauthdekenerror-Klasse](class_mip_noauthtokenerror.md)  |  Der Benutzer konnte aufgrund eines fehlenden Authentifizierungs Tokens keinen Zugriff auf den Inhalt erhalten.
[Class nopermissionserror](class_mip_nopermissionserror.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
[Klasse nopolicyerror](class_mip_nopolicyerror.md)  |  Die Mandanten Richtlinie ist nicht für Klassifizierung/Bezeichnungen konfiguriert.
[Klasse notsupportederror](class_mip_notsupportederror.md)  |  Der von der Anwendung angeforderte Vorgang wird vom SDK nicht unterstützt.
[Class authdelegat:: OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md)  |  eine Klasse, die alle Informationen enthält, die von der aufrufenden Anwendung benötigt werden, um ein oauth2-Token zu generieren.
[Class authdelegat:: OAuth2Token](class_mip_authdelegate_oauth2token.md)  |  Eine Klasse, die von einer Anwendung bereitgestellte zugriffstokeninformationen enthält.
[Class fileHandler:: Observer](class_mip_filehandler_observer.md)  |  Observer-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse, die im Zusammenhang mit dem Dateihandler stehen.
[Class schutzengine:: Observer](class_mip_protectionengine_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionEngine empfängt
[class file profile:: Observer](class_mip_fileprofile_observer.md)  |  Observer-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
[Class policyprofile:: Observer](class_mip_policyprofile_observer.md)  |  Observer-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für profilbezogene Ereignisse.
[Class Protection Handler:: Observer](class_mip_protectionhandler_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionHandler empfängt
[Class Protection profile:: Observer](class_mip_protectionprofile_observer.md)  |  Schnittstelle, die Benachrichtigungen im Zusammenhang mit ProtectionProfile empfängt.
[Klasse operationcancellederror](class_mip_operationcancellederror.md)  |  Vorgang wurde abgebrochen.
[Klasse policyengine](class_mip_policyengine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[Class policyhandler](class_mip_policyhandler.md)  |  Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
[Class policypackagedata](class_mip_policypackagedata.md)  | Noch nicht dokumentiert.
[Class policyprofile](class_mip_policyprofile.md)  |  Die PolicyProfile-Klasse ist die Stammklasse zum Verwenden von Microsoft Information Protection-Vorgängen. Eine gewöhnliche Anwendung benötigt nur eine PolicyProfile-Klasse, kann bei Bedarf aber mehrere erstellen.
[Klasse policyruledata](class_mip_policyruledata.md)  | Noch nicht dokumentiert.
[Klasse privilegedrequirederror](class_mip_privilegedrequirederror.md)  |  Die aktuelle Bezeichnung wurde als privilegierter Vorgang zugewiesen (das Äquivalent zu einem Administratorvorgang), daher kann sie nicht außer Kraft gesetzt werden.
[PropertyData-Klasse](class_mip_propertydata.md)  | Noch nicht dokumentiert.
[Klasse protectadhocaction](class_mip_protectadhocaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Ad-hoc-Schutz hinzugefügt wird.
[Klasse protectadhocdkaction](class_mip_protectadhocdkaction.md)  |  Eine Aktionsklasse, die angibt, dass ein Ad-hoc-doppelter Schlüsselschutz zum Dokument hinzugefügt wird.
[Klasse protectbyverschlüsseltonlyaction](class_mip_protectbyencryptonlyaction.md)  |  Eine Aktionsklasse, die das Hinzufügen von nur verschlüsseltem Schutz zum Dokument angibt.
[Klasse protectbytemplateaction](class_mip_protectbytemplateaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
[Klasse protectdonotforwardaction](class_mip_protectdonotforwardaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form von Nichtweiterleitung hinzugefügt wird.
[Klasse protectdonotforwarddkaction](class_mip_protectdonotforwarddkaction.md)  |  Eine Aktionsklasse, die angibt, dass kein doppelter Schlüsselschutz für das Dokument hinzugefügt wird.
[Class schutzaktionsdaten](class_mip_protectionactiondata.md)  | Noch nicht dokumentiert.
[Klassen Schutz Deskriptor](class_mip_protectiondescriptor.md)  |  Beschreibung des Schutzes, der einem Inhaltselement zugeordnet ist.
[Class schutzdescriptorbuilder](class_mip_protectiondescriptorbuilder.md)  |  Erstellt eine ProtectionDescriptor-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
[Class Protection Engine](class_mip_protectionengine.md)  |  Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
[Klassen Schutz Handler](class_mip_protectionhandler.md)  |  Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
[Class Protection profile](class_mip_protectionprofile.md)  |  ProtectionProfile ist die Stammklasse für Schutzvorgänge.
[Klassen Schutzeinstellungen](class_mip_protectionsettings.md)  |  Schnittstelle zum Konfigurieren von Schutz Optionen für die setlabel-Methode.
[Klasse proxyauthenticationerror](class_mip_proxyauthenticationerror.md)  |  Fehler bei der Proxy Authentifizierung.
[publishinglicenseingefo-Klasse](class_mip_publishinglicenseinfo.md)  |  Enthält die Details einer Veröffentlichungslizenz, die zum Erstellen eines Schutzhandlers verwendet wird.
[Class Protection Handler::P ublishingsettings](class_mip_protectionhandler_publishingsettings.md)  |  Einstellungen zum Erstellen eines Schutz Handlers zum Schutz neuer Inhalte.
[Class RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
[Klasse removecontentfooteraction](class_mip_removecontentfooteraction.md)  |  Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt aus dem Dokument entfernt wird.
[Klasse removecontenderaderaction](class_mip_removecontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird.
[Class removeschutzaction](class_mip_removeprotectionaction.md)  |  Eine Aktionsklasse, die angibt, dass der Schutz aus dem Dokument entfernt wird.
[removewatermarkaction-Klasse](class_mip_removewatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
[Class rulepackagedata](class_mip_rulepackagedata.md)  | Noch nicht dokumentiert.
[Klasse sensitivetypeclassificationdata](class_mip_sensitivetypeclassificationdata.md)  | Noch nicht dokumentiert.
[Klasse sensitivityconditiondata](class_mip_sensitivityconditiondata.md)  | Noch nicht dokumentiert.
[Klasse sensitivitytypesrulepackage](class_mip_sensitivitytypesrulepackage.md)  | Noch nicht dokumentiert.
[Class servicedisablederror](class_mip_servicedisablederror.md)  |  Der Benutzer konnte aufgrund eines deaktivierten diensdienstanbieter keinen Zugriff auf den Inhalt erhalten.
[Class fileengine:: Settings](class_mip_fileengine_settings.md)  | Noch nicht dokumentiert.
[Class policyengine:: Settings](class_mip_policyengine_settings.md)  |  Definiert die einer PolicyEngine-Klasse zugeordneten Einstellungen.
[Class policyprofile:: Settings](class_mip_policyprofile_settings.md)  |  Einstellungen, die während der Erstellung und Lebensdauer von PolicyProfile verwendet werden
[Class Protection profile:: Settings](class_mip_protectionprofile_settings.md)  |  Einstellungen, die während der Erstellung und Lebensdauer von ProtectionProfile verwendet werden.
[class file profile:: Settings](class_mip_fileprofile_settings.md)  |  Einstellungen, die während der Erstellung und Lebensdauer von FileProfile verwendet werden
[Class computeengine:: Settings](class_mip_computeengine_settings.md)  | Noch nicht dokumentiert.
[Class schutzengine:: Settings](class_mip_protectionengine_settings.md)  |  Einstellungen, die während der Erstellung und Lebensdauer von ProtectionEngine verwendet werden
[Klassen Datenstrom](class_mip_stream.md)  |  Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
[syncfilebasedata-Klasse](class_mip_syncfilebasedata.md)  | Noch nicht dokumentiert.
[syncfilepolicydata-Klasse](class_mip_syncfilepolicydata.md)  | Noch nicht dokumentiert.
[syncfilesensitivitydata der Klasse](class_mip_syncfilesensitivitydata.md)  | Noch nicht dokumentiert.
[Klasse taskdispatcherdelegat](class_mip_taskdispatcherdelegate.md)  |  Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
[Klasse templateDescriptor](class_mip_templatedescriptor.md)  | Noch nicht dokumentiert.
[Klasse templatenumotfounderror](class_mip_templatenotfounderror.md)  |  Die Vorlagen-ID wird vom RMS-Dienst nicht erkannt.
[Userrights-Klasse](class_mip_userrights.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
[Klassen Benutzer Rollen](class_mip_userroles.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.