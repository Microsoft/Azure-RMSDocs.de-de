---
title: MIP SDK für C++ Referenzstrukturen und-aufblendaten
description: Referenz Dokumentation für MIP C++ SDK-Strukturen und-aufblendaten.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6efe7910769dffe809e0661475f9adc8226b37b3
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884912"
---
# <a name="enumerations-and-structures"></a>Enumerationen und Strukturen

## <a name="namespace-mip"></a>Namespace MIP

 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Wasserzeichen Layout für Aufzählung       |  Layout für Wasserzeichen.
"contentmarkalignment" aufzählen       |  Ausrichtung für Inhalts Markierungen (Content Header oder Content Footer).
"ZUUM Zustellungs Methode"       |  Die Zuweisungs Methode der Bezeichnung im Dokument. Gibt an, ob die Zuweisung der Bezeichnung automatisch durchgeführt wurde, Standard oder als privilegierter Vorgang (entspricht einem Administrator Vorgang).
Enumeration-Aktions Quelle       |  definiert, was das Ereignis "setlabel" ausgelöst hat.
datastate aufzählen       |  Definiert den Zustand der Daten, auf den die Anwendung angewendet wird.
Enumeration-contentformat       |  Inhalts Format.
Consent-Enumeration       |  Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
cachestoragetype-Klasse       |  Der Speichertyp für die Caches.
ErrorType-Enumeration       | _Noch nicht dokumentiert._
' inspec'-Aufzählungs Typen       |  Der Inspektortyp korreliert die unterstützten Dateitypen.
"tyum BodyType"       |  Texttyp-Enumerator.
"Enumeration flightingfeature"       |  Definiert neue Features anhand des Namens.
enum HttpRequestType       |  Typ der HTTP-Anforderung
LogLevel-Enumeration       |  Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
ProtectionHandlerCreationOptions-Enumeration       |  Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.
ProtectionType-Enumeration       |  Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.
ActionType-Enumeration       |  Verschiedene Aktionstypen
' labelstate ' aufzählen       | _Noch nicht dokumentiert._
umeration Aktionstyp       | _Noch nicht dokumentiert._
Enumeration conditiondatatype       | _Noch nicht dokumentiert._
"contentmarkplacement" aufzählen       | _Noch nicht dokumentiert._
"Denum labelaktiondatatype"       | _Noch nicht dokumentiert._
schutzaktionstyp "konum"       | _Noch nicht dokumentiert._
Struktur MIP:: ApplicationInfo  |  Eine Struktur, die anwendungsspezifische Informationen umfasst
Struktur MIP:: telemetryconfiguration  |  Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)


## <a name="enumerations-mip"></a>Enumerationen (MIP)

### <a name="watermarklayout-enum"></a>Watermarklayout-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
ALES            | Wasserzeichen Layout ist horizontal
ALER            | Wasserzeichen Layout ist diagonal

Layout für Wasserzeichen.
  
### <a name="contentmarkalignment-enum"></a>Contentmarkalignment-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
LEFT            | Die Inhalts Markierung wird linksbündig ausgerichtet.
RIGHT            | Die Inhalts Markierung wird rechtsbündig ausgerichtet.
ZENTRUM            | Das Markieren von Inhalten wird zentriert.

Ausrichtung für Inhalts Markierungen (Content Header oder Content Footer).
  
### <a name="assignmentmethod-enum"></a>Zutragmethod-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
NORM            | Bezeichnungs [Zuweisungs Methode](class_mip_label.md) ist Standard
PRIVILEGIERTEN            | Bezeichnungs [Zuweisungs Methode](class_mip_label.md) ist privilegiert
AUTO            | Bezeichnungs [Zuweisungs Methode](class_mip_label.md) ist automatisch

Die Zuweisungs Methode der Bezeichnung im Dokument. Gibt an, ob die Zuweisung der Bezeichnung automatisch durchgeführt wurde, Standard oder als privilegierter Vorgang (entspricht einem Administrator Vorgang).
  
### <a name="actionsource-enum"></a>Aktions Quellen-Enumeration

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
MANUELL            | Manuell vom Benutzer ausgewählt
AUTOMATISCH            | Durch Richtlinien Bedingungen festlegen
EMPFOHLEN            | Vom Benutzer festgelegt, nachdem die Bezeichnung von Richtlinien Bedingungen empfohlen wurde
DEFAULT            | Standardmäßig in Richtlinie festlegen

Definiert, was das Ereignis "setlabel" ausgelöst hat.
  
### <a name="datastate-enum"></a>Datastate-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
STÜTZE            | Inaktive Daten, die physisch in Datenbanken/Dateien/Lager speichern gespeichert
ENTSCHLIESSUNGS            | Daten, die ein Netzwerk durchlaufen oder sich vorübergehend im zu lesenden oder zu aktualisierenden Computerspeicher befinden
KONSUM            | Aktive Daten unter konstanter Änderung werden physisch in Datenbanken/Dateien/Lagerhäusern gespeichert usw.

Definiert den Zustand der Daten, auf den die Anwendung angewendet wird.
  
### <a name="contentformat-enum"></a>Contentformat-Enumeration

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
DEFAULT            | Inhalts Format ist Standarddatei Format
E-MAIL            | Inhalts Format ist e-Mail-Format

Inhalts Format.
  
### <a name="consent-enum"></a>Zustimmungs-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
AcceptAlways            | Zustimmung; Speichern dieser Entscheidung
Annehmen            | Zustimmung; einmalig
Ablehnen            | Keine Zustimmung

Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
  
### <a name="cachestoragetype-enum"></a>Cachestoragetype-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
InMemory            | Im Speicher Speicher
OnDisk            | Auf Datenträger Speicher
Ondiskverschlüsselt            | Auf Datenträger Speicher mit Verschlüsselung (sofern von der Plattform unterstützt)

Der Speichertyp für die Caches.
  
### <a name="errortype-enum"></a>ErrorType-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Übergabe einer fehlerhaften Eingabe durch Aufrufer
FILE_IO_ERROR            | Allgemeiner Datei-E/A-Fehler
NETWORK_ERROR            | Allgemeine Netzwerkprobleme beispielsweise nicht erreichbarer Dienst.
TRANSIENT_NETWORK_ERROR            | Vorübergehende Netzwerkprobleme; Beispiel: Ungültiges Gateway.
INTERNAL_ERROR            | Unerwartete interne Fehler,
JUSTIFICATION_REQUIRED            | Eine Legitimierung ist erforderlich, um die Aktion für die Datei abzuschließen.
NOT_SUPPORTED_OPERATION            | Der angeforderte Vorgang wird noch nicht unterstützt.
PRIVILEGED_REQUIRED            | Privilegierte Bezeichnung kann nicht außer Kraft gesetzt werden, wenn standardmäßig die neue Bezeichnungsmethode verwendet wird.
ACCESS_DENIED            | Der Benutzer konnte keinen Zugriff auf die Dienste erhalten.
CONSENT_DENIED            | Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
POLICY_SYNC_ERROR            | Ein fehlgeschlagener Versuch, Richtliniendaten zu synchronisieren.
NO_PERMISSIONS            | Der Benutzer konnte nicht auf den Inhalt zugreifen. Beispielsweise keine Berechtigungen, der Inhalt wurde widerrufen.
NO_AUTH_TOKEN            | Der Benutzer konnte aufgrund eines leeren Authentifizierungs Tokens keinen Zugriff auf den Inhalt erhalten.
DISABLED_SERVICE            | Der Benutzer konnte aufgrund deaktiviertem Dienst keinen Zugriff auf den Inhalt erhalten.
PROXY_AUTH_ERROR            | Fehler bei der Proxy Authentifizierung.
NO_POLICY            | Es ist keine Richtlinie für den Benutzer/Mandanten konfiguriert.
OPERATION_CANCELLED            | Vorgang abgebrochen
ADHOC_PROTECTION_REQUIRED            | Der Ad-hoc-Schutz sollte festgelegt werden, um die Aktion für die Datei abzuschließen.
DEPRECATED_API            | Aufrufer hat eine veraltete API aufgerufen
TEMPLATE_NOT_FOUND            | Die Vorlagen-ID wurde nicht erkannt.
LABEL_NOT_FOUND            | [Bezeichnung](class_mip_label.md) Die ID wurde nicht erkannt.
LABEL_DISABLED            | Die [Bezeichnung](class_mip_label.md) ist deaktiviert oder inaktiv.
  
### <a name="inspectortype-enum"></a>Inspector Type-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Unbekannt            | Unkown-Datei Inspektor.
Meldung            | Datei Inspektor im Nachrichten Stil, rpmsg/msg-basiert.

Der Inspektortyp korreliert die unterstützten Dateitypen.
  
### <a name="bodytype-enum"></a>BodyType-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
UNBEKANNT            | Unkown-Texttyp
TXT            | Text Stiltyp, Codierung wird als UTF8 zurückgegeben
HTML            | HTML-Style-Texttyp, Codierung wird als UTF8 zurückgegeben
RTF            | RTF-Texttyp, binäres Format

Texttyp-Enumerator.
  
### <a name="flightingfeature-enum"></a>Flightingfeature-Enumeration

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Servicediscovery            | Zum Ermitteln von RMS-Dienst Endpunkten einen separaten HTTP-Befehl einsetzen
Authinfocache            | Cache OAuth2 Anforderungen pro Domäne/Mandant, um unnötige 401-Antworten zu verringern. Deaktivieren Sie für Apps/Dienste, die ihre eigene HTTP-Authentifizierung verwalten (wie z. b. SPO).
Linuxencryptedcache            | Aktivieren Sie das verschlüsselte Caching für Linux-Plattformen (Lesen Sie die Voraussetzungen für dieses Feature).

Definiert neue Features anhand des Namens.
  
### <a name="httprequesttype-enum"></a>Httprequesttype-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Abrufen            | GET
POST            | POST

Typ der HTTP-Anforderung
  
### <a name="loglevel-enum"></a>LogLevel-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Ablaufverfolgung            | 
Info            | 
Warnung            | 
Fehler            | 

Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
  
### <a name="protectionhandlercreationoptions-enum"></a>Schutzhandlerkreationoptions-Enumeration

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
None            | None
OfflineOnly            | UI-und Netzwerk Vorgänge nicht zulassen
AllowAuditedExtraction            | Inhalt kann in einer App geöffnet werden, die nicht SDK-fähig und für derartigen Schutz von Daten ausgelegt ist
PreferDeprecatedAlgorithms            | Verwendet Kryptografiealgorithmus für Abwärtskompatibilität

Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.

> Veraltet Diese Aufzählung wird bald als veraltet markiert, wenn "initiateschutzhandlerfromdescriptor" und "kreateschutzhandlerfrompublishinglicense" entfernt werden.
  
### <a name="protectiontype-enum"></a>Schutztyp-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
TemplateBased            | Handle wurde aus einer Vorlage erstellt.
Benutzerdefiniert            | Handle wurde Ad-hoc erstellt.

Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.
  
### <a name="actiontype-enum"></a>Aktionstyp-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Fügt eine Fußzeile mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_CONTENT_HEADER            | Fügt einen Header mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_WATERMARK            | Fügt ein Wasserzeichen zum Aktionstyp für das gesamte Dokument hinzu.
BENUTZERDEFINIERT            | Ein benutzerdefinierter Aktionstyp
JUSTIFY            | Ein Aktionstyp für die Legitimierung
BENÖTIGTEN            | Ein Aktionstyp zum Ändern von Metadaten
PROTECT_ADHOC            | Ein Aktionstyp zum Schutz anhand von benutzerdefinierten Richtlinien
PROTECT_BY_TEMPLATE            | Ein Aktionstyp zum Schutz anhand von Vorlagen
PROTECT_DO_NOT_FORWARD            | Ein Aktionstyp zum Schutz durch Verhinderung einer Weiterleitung
REMOVE_CONTENT_FOOTER            | Ein Aktionstyp, der Fußzeilen mit Inhalt entfernt
REMOVE_CONTENT_HEADER            | Ein Aktionstyp, der Header mit Inhalt entfernt
REMOVE_PROTECTION            | Ein Aktionstyp, der einen Schutz entfernt
REMOVE_WATERMARK            | Ein Aktionstyp, der Wasserzeichen entfernt
APPLY_LABEL            | Ein Aktionstyp, der eine Bezeichnung anwendet
RECOMMEND_LABEL            | Ein Aktionstyp, der eine Bezeichnung empfiehlt

Verschiedene Aktionstypen CUSTOM ist ein allgemeiner Aktionstyp. Bei jedem anderen Aktionstyp handelt es sich um eine spezifische Aktion mit einer speziellen Bedeutung.
  
### <a name="labelstate-enum"></a>Labelstate-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
NoChange            | 
Remove            | 
Update            | 
  
### <a name="actiondatatype-enum"></a>Aktiondatatype-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Benutzerdefiniert            | 
Schutz            | 
Contentmarking            | 
Addwatermark            | 
Bezeichnung            | 
  
### <a name="conditiondatatype-enum"></a>Conditiondatatype-Enumeration

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Default            | 
Vertraulichkeit            | 
  
### <a name="contentmarkplacement-enum"></a>Contentmarkplacement-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Header            | 
Fußzeile            | 
  
### <a name="labelactiondatatype-enum"></a>Labelaktiondatatype-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Empfehlen            | 
Übernehmen            | 
  
### <a name="protectionactiontype-enum"></a>Schutzaktionstyp-Aufzählung

Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Benutzerdefiniert            | 
Vorlage            | 
Donotforward            | 
Adhoc            | 
Donotforwardwithprompt            | 
Hyok            | 
Predefinedtemplate            | 
RemoveProtection            | 
  


## <a name="structures"></a>Strukturen 

### <a name="mipapplicationinfo"></a>mip::ApplicationInfo 
Eine Struktur, die anwendungsspezifische Informationen umfasst
  
#### <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string applicationId  |  Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
public std::string applicationName  |  Anwendungsname (sollte nur Container gültiges ASCII-Zeichen mit Ausnahme von '; ')
public std::string applicationVersion  |  Die Version der verwendeten Anwendung (nur Container gültiges ASCII-Zeichen ohne ";")
  
#### <a name="members"></a>Member
  
##### <a name="applicationid-struct-member"></a>ApplicationId-Strukturmember
Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
  
##### <a name="applicationname-struct-member"></a>ApplicationName-Strukturmember
Anwendungsname (sollte nur Container gültiges ASCII-Zeichen mit Ausnahme von '; ')
  
##### <a name="applicationversion-struct-member"></a>applicationVersion-Strukturmember
Die Version der verwendeten Anwendung (nur Container gültiges ASCII-Zeichen ohne ";")

### <a name="miptelemetryconfiguration"></a>MIP:: telemetryconfiguration 
Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)
  
#### <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String hostnameoverride  |  Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
Public Std:: String librarynameoverride  |  Dateiname der alternativen telemetriebibliothek (dll).
Public Std:: shared_ptr\<\> httpdelegat httpdelegateoverride  |  Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
Public Std:: shared_ptr\<\> taskdispatcherdelegaten taskdispatcherdelegateoverride  |  Wenn festgelegt, wird die asynchrone Aufgaben Behandlung von dieser Instanz verwaltet.
public bool isnetworkdetectionaktivierte  |  Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
public bool islocalcachingenabled  |  Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
public bool istelemetryoptedout  |  Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
  
#### <a name="members"></a>Member
  
##### <a name="hostnameoverride-struct-member"></a>hostnameoverride-Strukturmember
Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
  
##### <a name="librarynameoverride-struct-member"></a>librarynameoverride-Strukturmember
Dateiname der alternativen telemetriebibliothek (dll).
  
##### <a name="httpdelegate"></a>HttpDelegate
Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
  
##### <a name="taskdispatcherdelegate"></a>TaskDispatcherDelegate
Wenn festgelegt, wird die asynchrone Aufgaben Behandlung von dieser Instanz verwaltet.
  
##### <a name="isnetworkdetectionenabled-struct-member"></a>isnetworkdetectionaktivierter Strukturmember
Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
  
##### <a name="islocalcachingenabled-struct-member"></a>islocalcachingenabled-Strukturmember
Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
  
##### <a name="istelemetryoptedout-struct-member"></a>istelemetryoptedout-Strukturmember
Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.