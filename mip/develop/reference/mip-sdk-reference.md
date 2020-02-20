---
title: MIP SDK für C++ Referenz
description: MIP SDK für C++ Referenz
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: fb1657bc39f49b161c5ed986cd381cfd5d4cab49
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489230"
---
# <a name="mip-sdk-for-c-reference"></a>MIP SDK für C++ Referenz

Das Microsoft Information Protection (MIP) SDK für C++ ermöglicht Entwicklern das Verwalten und Anwenden von Datenschutzrichtlinien auf Daten und andere digitale Ressourcen.

Das MIP SDK für C++ enthält:

- [Enumerationen und Strukturen](mip-enums-and-structs.md)
- [Functions (Funktionen)](mip-functions.md)
- Die folgenden Klassen:

## <a name="namespace-mip-classes"></a>Namespace-MIP-Klassen

 Klasse                         | Beschreibung                                
--------------------------------|---------------------------------------------
[MIP:: accessdeniederror-Klasse](class_mip_accessdeniederror.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
[MIP:: Action-Klasse](class_mip_action.md)  |  Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
[MIP:: aktiondata-Klasse](class_mip_actiondata.md)  | Noch nicht dokumentiert.
[MIP:: addcontentfooteraction-Klasse](class_mip_addcontentfooteraction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Fußzeileninhalt hinzugefügt wird.
[MIP:: addcontenderaderaction-Klasse](class_mip_addcontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
[MIP:: addwatermarkaction-Klasse](class_mip_addwatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
[MIP:: addwatermarkaktiondata-Klasse](class_mip_addwatermarkactiondata.md)  | Noch nicht dokumentiert.
[MIP:: adhucschutzrequirements derror-Klasse](class_mip_adhocprotectionrequirederror.md)  |  Der Ad-hoc-Schutz sollte festgelegt werden, um die Aktion für die Datei abzuschließen.
[MIP:: applicationaktionstate-Klasse](class_mip_applicationactionstate.md)  | Noch nicht dokumentiert.
[MIP:: applylabelaction-Klasse](class_mip_applylabelaction.md)  |  Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
[MIP:: argumentdata-Klasse](class_mip_argumentdata.md)  | Noch nicht dokumentiert.
[MIP:: AsyncControl-Klasse](class_mip_asynccontrol.md)  |  Klasse zum Abbrechen des asynchronen Vorgangs.
[MIP:: authdelegat-Klasse](class_mip_authdelegate.md)  |  Delegat für Vorgänge im Zusammenhang mit der Authentifizierung.
[MIP:: badinputerror-Klasse](class_mip_badinputerror.md)  |  Der Fehler bei ungültiger Eingabe wird ausgegeben, wenn die Eingabe in eine SDK-API ungültig ist.
[MIP:: classificationdata-Klasse](class_mip_classificationdata.md)  | Noch nicht dokumentiert.
[MIP:: classificationrequest-Klasse](class_mip_classificationrequest.md)  |  Eine Klasse, die die Anforderung eines Klassifizierungs Aufrufes für den Ausführungs Status enthält.
[MIP:: classificationresult-Klasse](class_mip_classificationresult.md)  |  Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
[MIP:: computeengine-Klasse](class_mip_computeengine.md)  | Noch nicht dokumentiert.
[MIP:: computeenginecontext-Klasse](class_mip_computeenginecontext.md)  | Noch nicht dokumentiert.
[MIP:: conditiondata-Klasse](class_mip_conditiondata.md)  | Noch nicht dokumentiert.
[MIP:: einvernehmdelegat-Klasse](class_mip_consentdelegate.md)  |  Delegat für Vorgänge, die eine Zustimmung erfordern.
[MIP:: genehmideniederror-Klasse](class_mip_consentdeniederror.md)  |  Einem Vorgang, der die Einwilligung vom Benutzer erfordert, wurde keine Einwilligung erteilt.
[MIP:: contentlabel-Klasse](class_mip_contentlabel.md)  |  Abstraktion für eine Microsoft Information Protection-Bezeichnung, die für einen Teil des Inhalts, in der Regel ein Dokument, gilt.
[MIP:: contentmarkingaktiondata-Klasse](class_mip_contentmarkingactiondata.md)  | Noch nicht dokumentiert.
[MIP:: CustomAction-Klasse](class_mip_customaction.md)  |  CustomAction ist eine generische Aktionsklasse, die alle untergeordneten Eigenschaften der Aktion als Eigenschaften Sammlung erfasst. Der Aufrufer muss sich über die Bedeutung der Aktion im Klaren sein.
[MIP::D eprecatedapierror-Klasse](class_mip_deprecatedapierror.md)  |  Der Aufrufer hat eine veraltete API aufgerufen.
[MIP::D ocenumentstate-Klasse](class_mip_documentstate.md)  | Noch nicht dokumentiert.
[MIP:: Error-Klasse](class_mip_error.md)  |  Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
[MIP:: executionstate-Klasse](class_mip_executionstate.md)  |  Eine Schnittstelle für sämtliche Status, die für die Ausführung der Engine erforderlich sind.
[MIP:: fileengine-Klasse](class_mip_fileengine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[MIP:: fileexecutionstate-Klasse](class_mip_fileexecutionstate.md)  | Noch nicht dokumentiert.
[MIP:: fileHandler-Klasse](class_mip_filehandler.md)  |  Eine Schnittstelle für alle Funktionen für die Dateiverarbeitung.
[MIP:: filinput Spector-Klasse](class_mip_fileinspector.md)  | Noch nicht dokumentiert.
[MIP:: fleioerror-Klasse](class_mip_fileioerror.md)  |  Datei-E/A-Fehler.
[MIP:: fileprofile-Klasse](class_mip_fileprofile.md)  |  Die File Profile-Klasse ist die Stamm Klasse für die Verwendung der Microsoft Information Protection-Vorgänge.
[MIP:: httpdelegatklasse](class_mip_httpdelegate.md)  |  Schnittstelle zum Überschreiben der HTTP-Verarbeitung.
[MIP:: httpoperation-Klasse](class_mip_httpoperation.md)  |  Schnittstelle, die einen einzelnen http-Vorgang beschreibt, der von der Client-App beim Überschreiben von httpdelegaten
[MIP:: HttpRequest-Klasse](class_mip_httprequest.md)  |  Schnittstelle, die eine einfache HTTP-Anforderung beschreibt.
[MIP:: HttpResponse-Klasse](class_mip_httpresponse.md)  |  Schnittstelle, die eine einzelne HTTP-Antwort beschreibt, die von der Client-App beim Überschreiben von httpdelegaten
[MIP:: Identity-Klasse](class_mip_identity.md)  |  Abstraktion für Identity.
[MIP:: insuffizientbuffererror-Klasse](class_mip_insufficientbuffererror.md)  |  Nicht genügend Puffer Fehler.
[MIP:: InternalError-Klasse](class_mip_internalerror.md)  |  Interner Fehler. Dieser Fehler tritt auf, wenn während der Ausführung etwas Unerwartetes passiert.
[MIP:: Recht cationrequirements derror-Klasse](class_mip_justificationrequirederror.md)  | Noch nicht dokumentiert.
[MIP:: justifyaction-Klasse](class_mip_justifyaction.md)  |  Die Aktion zum begründen erfordert die Bereitstellung einer Begründung für eine Bezeichnungs Herabstufung und das Festlegen der Antwort im Ausführungs Status.
[MIP:: Label-Klasse](class_mip_label.md)  |  Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
[MIP:: labelaktiondata-Klasse](class_mip_labelactiondata.md)  | Noch nicht dokumentiert.
[MIP:: labeldisablederror-Klasse](class_mip_labeldisablederror.md)  |  Die Bezeichnung ist deaktiviert oder inaktiv.
[MIP:: labelgroupdata-Klasse](class_mip_labelgroupdata.md)  | Noch nicht dokumentiert.
[MIP:: labelingoptions-Klasse](class_mip_labelingoptions.md)  |  Schnittstelle für die Konfiguration von Bezeichnungsoptionen für die Methoden „SetLabel“ und „DeleteLabel“
[MIP:: labelnotfounderror-Klasse](class_mip_labelnotfounderror.md)  |  Die Bezeichnungs-ID wurde nicht erkannt.
[MIP:: loggerdelegat-Klasse](class_mip_loggerdelegate.md)  |  Eine Klasse, die die Schnittstelle zur MIP SDK-Protokollierung definiert
[MIP:: MetadataAction-Klasse](class_mip_metadataaction.md)  |  Eine Aktion, mit der dem Inhalt Metadateninformationen hinzugefügt werden.
[MIP:: mipcontext-Klasse](class_mip_mipcontext.md)  |  Mipcontext stellt den Status dar, der von allen Profilen, Engines und Handlern gemeinsam genutzt wird.
[MIP:: msgattachmentdata-Klasse](class_mip_msgattachmentdata.md)  | Noch nicht dokumentiert.
[MIP:: msginspector-Klasse](class_mip_msginspector.md)  | Noch nicht dokumentiert.
[MIP:: NetworkError-Klasse](class_mip_networkerror.md)  |  Ein Netzwerkfehler Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
[MIP:: noauthdekenerror-Klasse](class_mip_noauthtokenerror.md)  |  Der Benutzer konnte aufgrund eines fehlenden Authentifizierungs Tokens keinen Zugriff auf den Inhalt erhalten.
[MIP:: nopermissionserror-Klasse](class_mip_nopermissionserror.md)  |  Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
[MIP:: nopolicyerror-Klasse](class_mip_nopolicyerror.md)  |  Die Mandanten Richtlinie ist nicht für Klassifizierung/Bezeichnungen konfiguriert.
[MIP:: notsupportederror-Klasse](class_mip_notsupportederror.md)  |  Der von der Anwendung angeforderte Vorgang wird vom SDK nicht unterstützt.
[MIP:: operationcancellederror-Klasse](class_mip_operationcancellederror.md)  |  Vorgang wurde abgebrochen.
[MIP::P olicyengine-Klasse](class_mip_policyengine.md)  |  Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
[MIP::P olicyhandler-Klasse](class_mip_policyhandler.md)  |  Diese Klasse stellt eine Schnittstelle für alle Funktionen des Richtlinienhandler bereit.
[MIP::P olicypackagedata-Klasse](class_mip_policypackagedata.md)  | Noch nicht dokumentiert.
[MIP::P olicyprofile-Klasse](class_mip_policyprofile.md)  |  Die policyprofile-Klasse ist die Stamm Klasse für die Verwendung von Microsoft Information Protection-Vorgängen. Eine typische Anwendung benötigt nur ein policyprofile, aber Sie kann bei Bedarf mehrere Profile erstellen.
[MIP::P olicyruledata-Klasse](class_mip_policyruledata.md)  | Noch nicht dokumentiert.
[MIP::P rivilegedrequirederror-Klasse](class_mip_privilegedrequirederror.md)  |  Die aktuelle Bezeichnung wurde als privilegierter Vorgang zugewiesen (das Äquivalent zu einem Administratorvorgang), daher kann sie nicht außer Kraft gesetzt werden.
[MIP::P ropertydata](class_mip_propertydata.md)  | Noch nicht dokumentiert.
[MIP::P rotectadhocaction](class_mip_protectadhocaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Ad-hoc-Schutz hinzugefügt wird.
[MIP::P rotectbytemplateaction-Klasse](class_mip_protectbytemplateaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
[MIP::P rotectdonotforwardaction-Klasse](class_mip_protectdonotforwardaction.md)  |  Eine Aktionsklasse, die angibt, dass dem Dokument Schutz in Form von Nichtweiterleitung hinzugefügt wird.
[MIP::P rotectionaktiondata](class_mip_protectionactiondata.md)  | Noch nicht dokumentiert.
[MIP::P rotectiondescriptor-Klasse](class_mip_protectiondescriptor.md)  |  Beschreibung des Schutzes, der einem Inhaltselement zugeordnet ist.
[MIP::P rotectiondescriptorbuilder-Klasse](class_mip_protectiondescriptorbuilder.md)  |  Erstellt einen Schutz Deskriptor, der den dem Inhalt zugeordneten Schutz beschreibt.
[MIP::P rotectionengine](class_mip_protectionengine.md)  |  Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
[MIP::P rotectionhandler](class_mip_protectionhandler.md)  |  Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
[MIP::P rotectionprofile](class_mip_protectionprofile.md)  |  Schutzprofile ist die Stamm Klasse für die Durchführung von Schutz Vorgängen.
[MIP::P rotectionsettings-Klasse](class_mip_protectionsettings.md)  |  Schnittstelle zum Konfigurieren von Schutz Optionen für die setlabel-Methode.
[MIP::P roxyauthenticationerror-Klasse](class_mip_proxyauthenticationerror.md)  |  Fehler bei der Proxy Authentifizierung.
[MIP::P ublishinglicenseingefo-Klasse](class_mip_publishinglicenseinfo.md)  |  Enthält die Details einer Veröffentlichungslizenz, die zum Erstellen eines Schutzhandlers verwendet wird.
[MIP:: RecommendLabelAction-Klasse](class_mip_recommendlabelaction.md)  |  Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
[MIP:: removecontentfooteraction-Klasse](class_mip_removecontentfooteraction.md)  |  Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt aus dem Dokument entfernt wird.
[MIP:: removecontenderaderaction-Klasse](class_mip_removecontentheaderaction.md)  |  Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird.
[MIP:: removeschutzaction-Klasse](class_mip_removeprotectionaction.md)  |  Eine Aktionsklasse, die angibt, dass der Schutz aus dem Dokument entfernt wird.
[MIP:: removewatermarkaction-Klasse](class_mip_removewatermarkaction.md)  |  Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
[MIP:: rulepackagedata-Klasse](class_mip_rulepackagedata.md)  | Noch nicht dokumentiert.
[MIP:: sensitivityconditiondata-Klasse](class_mip_sensitivityconditiondata.md)  | Noch nicht dokumentiert.
[MIP:: sensitivitytypesrulepackage-Klasse](class_mip_sensitivitytypesrulepackage.md)  | Noch nicht dokumentiert.
[MIP:: servicedisablederror-Klasse](class_mip_servicedisablederror.md)  |  Der Benutzer konnte aufgrund eines deaktivierten diensdienstanbieter keinen Zugriff auf den Inhalt erhalten.
[MIP:: Stream-Klasse](class_mip_stream.md)  |  Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
[MIP:: syncfilebasedata-Klasse](class_mip_syncfilebasedata.md)  | Noch nicht dokumentiert.
[MIP:: syncfilepolicydata-Klasse](class_mip_syncfilepolicydata.md)  | Noch nicht dokumentiert.
[MIP:: syncfilesensitivitydata-Klasse](class_mip_syncfilesensitivitydata.md)  | Noch nicht dokumentiert.
[MIP:: taskdispatcherdelegat-Klasse](class_mip_taskdispatcherdelegate.md)  |  Eine Klasse, die die Schnittstelle zum MIP SDK-Aufgaben Verteiler definiert.
[MIP:: templateDescriptor-Klasse](class_mip_templatedescriptor.md)  | Noch nicht dokumentiert.
[MIP:: templatenumerotfounderror-Klasse](class_mip_templatenotfounderror.md)  |  Die Vorlagen-ID wird vom RMS-Dienst nicht erkannt.
[MIP:: Userrights-Klasse](class_mip_userrights.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
[MIP:: userrollen-Klasse](class_mip_userroles.md)  |  Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
Struktur MIP:: ApplicationInfo  |  Eine Struktur, die anwendungsspezifische Informationen umfasst
Struktur MIP:: telemetryconfiguration  |  Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)


