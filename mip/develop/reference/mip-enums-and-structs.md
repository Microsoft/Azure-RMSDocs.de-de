---
title: MIP SDK für C++ Referenzstrukturen und-Aufstände
description: Referenz Dokumentation für MIP C++ SDK-Strukturen und-aufblendaten.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: e602b13ce5dedb8ff210372d1d06e03625611e0e
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98214098"
---
# <a name="enumerations-and-structures"></a>Enumerationen und Strukturen


Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Wasserzeichen Layout für Aufzählung       |  Layout für Wasserzeichen.
"contentmarkalignment" aufzählen       |  Ausrichtung für Inhalts Markierungen (Content Header oder Content Footer).
"ZUUM Zustellungs Methode"       |  Die Zuweisungs Methode der Bezeichnung im Dokument. Gibt an, ob die Zuweisung der Bezeichnung automatisch durchgeführt wurde, Standard oder als privilegierter Vorgang (entspricht einem Administrator Vorgang).
Enumeration-Aktions Quelle       |  definiert, was das Ereignis "setlabel" ausgelöst hat.
datastate aufzählen       |  Definiert den Zustand der Daten, auf den die Anwendung angewendet wird.
Enumeration-contentformat       |  Inhalts Format.
"labelfiltertype"-Klasse       |  Bezeichnungs Filtertypen, optionaler Satz von Eigenschaften, der zum Filtern von Bezeichnungen beim Aufrufen von Listen Vertraulichkeits Bezeichnungen verwendet werden kann.
"-FeatureId" einschließen       |  Definiert neue Features anhand des Namens.
Aufzählung von variabletextmarkingtype       |  verschiedene dynamische Felder können in der Textnachricht der Anwendung festgelegt werden: $ {Item. Label} $ {Item.Name} $ {Item. Location} $ {User.Name} $ {User. PrincipalName} $ {Event. DateTime} andere sind immer noch nicht definiert: das SDK ersetzt Sie durch die richtigen Werte mithilfe dieser Steuerungsflags.
Consent-Enumeration       |  Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
cachestoragetype-Klasse       |  Der Speichertyp für die Caches.
Aufzählung von pfileextensionbehavior       |  Beschreibt das Verhalten von Pfile-Erweiterungen.
ErrorType-Enumeration       | _Noch nicht dokumentiert._
' inspec'-Aufzählungs Typen       |  Der Inspektortyp korreliert die unterstützten Dateitypen.
"tyum BodyType"       |  Texttyp-Enumerator.
"Enumeration flightingfeature"       |  Definiert neue Features anhand des Namens.
enum HttpRequestType       |  Typ der HTTP-Anforderung
LogLevel-Enumeration       |  Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
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

## <a name="enumerations"></a>Enumerationen

### <a name="watermarklayout-enum"></a>Watermarklayout-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Ales            | Wasserzeichen Layout ist horizontal
Aler            | Wasserzeichen Layout ist diagonal

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
STANDARD            | Bezeichnungs Zuweisungs Methode ist Standard
Privilegierten            | Bezeichnungs Zuweisungs Methode ist privilegiert
AUTO            | Bezeichnungs Zuweisungs Methode ist automatisch

Die Zuweisungs Methode der Bezeichnung im Dokument. Gibt an, ob die Zuweisung der Bezeichnung automatisch durchgeführt wurde, Standard oder als privilegierter Vorgang (entspricht einem Administrator Vorgang).
  
### <a name="actionsource-enum"></a>Aktions Quellen-Enumeration
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
MANUAL            | Manuell vom Benutzer ausgewählt
AUTOMATIC            | Durch Richtlinien Bedingungen festlegen
EMPFOHLEN            | Vom Benutzer festgelegt, nachdem die Bezeichnung von Richtlinien Bedingungen empfohlen wurde
DEFAULT            | Standardmäßig in Richtlinie festlegen

Definiert, was das Ereignis "setlabel" ausgelöst hat.
  
### <a name="datastate-enum"></a>Datastate-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
REST            | Inaktive Daten, die physisch in Datenbanken/Dateien/Lager speichern gespeichert
Entschließungs            | Daten, die ein Netzwerk durchlaufen oder sich vorübergehend im zu lesenden oder zu aktualisierenden Computerspeicher befinden
USE            | Aktive Daten unter konstanter Änderung werden physisch in Datenbanken/Dateien/Lagerhäusern gespeichert usw.

Definiert den Zustand der Daten, auf den die Anwendung angewendet wird.
  
### <a name="contentformat-enum"></a>Contentformat-Enumeration
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
DEFAULT            | Inhalts Format ist Standarddatei Format
E-Mail            | Inhalts Format ist e-Mail-Format

Inhalts Format.
  
### <a name="labelfiltertype-enum"></a>Labelfiltertype-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Keine            | Standardmäßige Beschriftungs Filterung deaktivieren
Customprotection            | Bezeichnungen filtern, die zu einem benutzerdefinierten Schutz führen können
Templateprotection            | Bezeichnungen filtern, die möglicherweise nicht weiterleiten
Donotforwardprotection            | Bezeichnungen filtern, die möglicherweise zum Schutz von Vorlagen führen
Adhucprotection            | Bezeichnungen filtern, die möglicherweise zu einem Ad-hoc-Schutz führen
Hyokprotection            | Bezeichnungen filtern, die zum Hyok-Schutz führen können
Predefinedtemplateprotection            | Bezeichnungen filtern, die zu vordefiniertem Vorlagen Schutz führen können
Doublekeyprotection            | Bezeichnungen filtern, die zu einem Schutz führen können, der einen doppelten Schlüssel erfordert, kann Template, Adhoc, DNF sein.

Bezeichnungs Filtertypen, optionaler Satz von Eigenschaften, der zum Filtern von Bezeichnungen beim Aufrufen von Listen Vertraulichkeits Bezeichnungen verwendet werden kann.
  
### <a name="featureid-enum"></a>FeatureId-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Nur verschlüsseln            | Überprüfen, ob der Server das Verschlüsselungs Feature unterstützt

Definiert neue Features anhand des Namens.
  
### <a name="variabletextmarkingtype-enum"></a>Variabletextmarkingtype-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Standard            | Bekannte Markierungen werden konvertiert, unbekannte Markierung werden entfernt
Passthrough            | Bekannte Markierungen werden konvertiert, unbekannte Markierung werden übermittelt.
Keine            | Alle Markierungen werden durchlaufen

Verschiedene dynamische Felder können in der Textnachricht der Anwendung festgelegt werden: $ {Item. Label} $ {Item.Name} $ {Item. Location} $ {User.Name} $ {User. PrincipalName} $ {Event. DateTime} andere sind immer noch nicht definiert: das SDK ersetzt Sie durch die richtigen Werte mithilfe dieser Steuerungsflags.
  
### <a name="consent-enum"></a>Zustimmungs-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
AcceptAlways            | Zustimmung; Speichern dieser Entscheidung
Akzeptieren            | Zustimmung; einmalig
Reject            | Keine Zustimmung

Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
  
### <a name="cachestoragetype-enum"></a>Cachestoragetype-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
InMemory            | Im Speicher Speicher
OnDisk            | Auf Datenträger Speicher
Ondiskverschlüsselt            | Auf Datenträger Speicher mit Verschlüsselung (sofern von der Plattform unterstützt)

Der Speichertyp für die Caches.
  
### <a name="pfileextensionbehavior-enum"></a>Pfileextensionbehavior-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Standard            | Erweiterungen werden als SDK-Standardverhalten verwendet.
Pfilesuffix            | Erweiterungen werden zu <EXT> . PFILE
Pprefix            | Erweiterungen werden zu P<EXT>

Beschreibt das Verhalten von Pfile-Erweiterungen.
  
### <a name="errortype-enum"></a>ErrorType-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Übergabe einer fehlerhaften Eingabe durch Aufrufer
INSUFFICIENT_BUFFER_ERROR            | Der Aufrufer hat einen zu kleinen Puffer übergeben.
FILE_IO_ERROR            | Allgemeiner Datei-E/A-Fehler
NETWORK_ERROR            | Allgemeine Netzwerkprobleme beispielsweise nicht erreichbarer Dienst.
INTERNAL_ERROR            | Unerwartete interne Fehler,
JUSTIFICATION_REQUIRED            | Eine Legitimierung ist erforderlich, um die Aktion für die Datei abzuschließen.
NOT_SUPPORTED_OPERATION            | Der angeforderte Vorgang wird noch nicht unterstützt.
PRIVILEGED_REQUIRED            | Privilegierte Bezeichnung kann nicht außer Kraft gesetzt werden, wenn standardmäßig die neue Bezeichnungsmethode verwendet wird.
ACCESS_DENIED            | Der Benutzer konnte keinen Zugriff auf die Dienste erhalten.
CONSENT_DENIED            | Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
NO_PERMISSIONS            | Der Benutzer konnte nicht auf den Inhalt zugreifen. Beispielsweise keine Berechtigungen, der Inhalt wurde widerrufen.
NO_AUTH_TOKEN            | Der Benutzer konnte aufgrund eines leeren Authentifizierungs Tokens keinen Zugriff auf den Inhalt erhalten.
DISABLED_SERVICE            | Der Benutzer konnte aufgrund deaktiviertem Dienst keinen Zugriff auf den Inhalt erhalten.
PROXY_AUTH_ERROR            | Fehler bei der Proxyauthentifizierung.
NO_POLICY            | Es ist keine Richtlinie für den Benutzer/Mandanten konfiguriert.
OPERATION_CANCELLED            | Vorgang abgebrochen.
ADHOC_PROTECTION_REQUIRED            | Der Ad-hoc-Schutz sollte festgelegt werden, um die Aktion für die Datei abzuschließen.
DEPRECATED_API            | Aufrufer hat eine veraltete API aufgerufen
TEMPLATE_NOT_FOUND            | Die Vorlagen-ID wurde nicht erkannt.
LABEL_NOT_FOUND            | Bezeichnungs-ID wurde nicht erkannt.
LABEL_DISABLED            | Die Bezeichnung ist deaktiviert oder inaktiv.
  
### <a name="inspectortype-enum"></a>Inspector Type-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Unbekannt            | Unkown-Datei Inspektor.
Meldung            | Datei Inspektor im Nachrichten Stil, rpmsg/msg-basiert.

Der Inspektortyp korreliert die unterstützten Dateitypen.
  
### <a name="bodytype-enum"></a>BodyType-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
UNKNOWN            | Unkown-Texttyp
TXT            | Text Stiltyp, Codierung wird als UTF8 zurückgegeben
HTML            | HTML-Style-Texttyp, Codierung wird als UTF8 zurückgegeben
RTF            | RTF-Texttyp, binäres Format

Texttyp-Enumerator.
  
### <a name="flightingfeature-enum"></a>Flightingfeature-Enumeration
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Servicediscovery            | Zum Ermitteln von RMS-Dienst Endpunkten einen separaten HTTP-Befehl einsetzen
Authinfocache            | Cache OAuth2 Anforderungen pro Domäne/Mandant, um unnötige 401-Antworten zu verringern. Deaktivieren Sie für Apps/Dienste, die ihre eigene HTTP-Authentifizierung verwalten (z. b. SPO, Edge).
Linuxencryptedcache            | Aktivieren Sie das verschlüsselte Caching für Linux-Plattformen (Lesen Sie die Voraussetzungen für dieses Feature).
Singledomainname            | Aktivieren Sie den einzelnen Firmennamen für die DNS-Suche. e.g. [https://corprights](https://corprights)
Policyauth            | Aktivieren Sie die automatische HTTP-Authentifizierung für an den Richtlinien Dienst gesendete Anforderungen. Deaktivieren Sie für Apps/Dienste, die ihre eigene HTTP-Authentifizierung verwalten (z. b. SPO, Edge).
Urlredirectcache            | Cache-URL-Umleitungen zum Reduzieren der Anzahl von http-Vorgängen
Vorlizenzierung            | Aktivieren der Pre License API-Überprüfung
Doublekey            | Aktivieren der doppelten Schlüsselschutz Funktion zur Verwendung eines Kunden Schlüssels für die Verschlüsselung mit
Variablepolicyttl            | Aktivieren der Gültigkeitsdauer von Variablen Richtlinien, Deaktivieren der Wiederherstellung auf eine unbegrenzte Richtlinie
Variabletextmarking            | Variablen Textmarkierung aktivieren

Definiert neue Features anhand des Namens.
  
### <a name="httprequesttype-enum"></a>Httprequesttype-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Herunterladen            | GET
Posten            | POST

Typ der HTTP-Anforderung
  
### <a name="loglevel-enum"></a>LogLevel-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Trace            | 
Info            | 
Warnung            | 
Fehler            | 

Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
  
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
CUSTOM            | Ein benutzerdefinierter Aktionstyp
JUSTIFY            | Ein Aktionstyp für die Legitimierung
METADATA            | Ein Aktionstyp zum Ändern von Metadaten
PROTECT_ADHOC            | Ein Aktionstyp zum Schutz anhand von benutzerdefinierten Richtlinien
PROTECT_BY_TEMPLATE            | Ein Aktionstyp zum Schutz anhand von Vorlagen
PROTECT_DO_NOT_FORWARD            | Ein Aktionstyp zum Schutz durch Verhinderung einer Weiterleitung
REMOVE_CONTENT_FOOTER            | Ein Aktionstyp, der Fußzeilen mit Inhalt entfernt
REMOVE_CONTENT_HEADER            | Ein Aktionstyp, der Header mit Inhalt entfernt
REMOVE_PROTECTION            | Ein Aktionstyp, der einen Schutz entfernt
REMOVE_WATERMARK            | Ein Aktionstyp, der Wasserzeichen entfernt
APPLY_LABEL            | Ein Aktionstyp, der eine Bezeichnung anwendet
RECOMMEND_LABEL            | Ein Aktionstyp, der eine Bezeichnung empfiehlt
PROTECT_ADHOC_DK            | Ein Aktionstyp zum Schutz anhand von benutzerdefinierten Richtlinien
PROTECT_BY_TEMPLATE_DK            | Ein Aktionstyp zum Schutz anhand von Vorlagen
PROTECT_DO_NOT_FORWARD_DK            | Ein Aktionstyp zum Schutz durch Verhinderung einer Weiterleitung

Verschiedene Aktionstypen CUSTOM ist ein allgemeiner Aktionstyp. Bei jedem anderen Aktionstyp handelt es sich um eine spezifische Aktion mit einer speziellen Bedeutung.
  
### <a name="labelstate-enum"></a>Labelstate-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
NoChange            | 
Entfernen            | 
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
Standard            | 
Sensitivität            | 
  
### <a name="contentmarkplacement-enum"></a>Contentmarkplacement-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Header            | 
Fußzeile            | 
  
### <a name="labelactiondatatype-enum"></a>Labelaktiondatatype-Aufzählung
Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Empfehlen            | 
Anwenden            | 
  
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

### <a name="struct-mipapplicationinfo"></a>Struktur MIP:: ApplicationInfo 
Eine Struktur, die anwendungsspezifische Informationen umfasst
  
Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string applicationId  |  Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
public std::string applicationName  |  Anwendungsname (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
public std::string applicationVersion  |  Die Version der verwendeten Anwendung (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
  

#### <a name="applicationid-struct-member"></a>ApplicationId-Strukturmember
Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
  
#### <a name="applicationname-struct-member"></a>ApplicationName-Strukturmember
Anwendungsname (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
  
#### <a name="applicationversion-struct-member"></a>applicationVersion-Strukturmember
Die Version der verwendeten Anwendung (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)

### <a name="struct-diagnosticconfiguration"></a>Struktur diagnosticconfiguration

Benutzerdefinierte Diagnose Konfigurationen (nicht häufig verwendet)
  
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String hostnameoverride  |  Name der Host Überwachung/telemetrieinstanz. Wenn nicht festgelegt, fungiert MIP als eigener Host.
Public Std:: String librarynameoverride  |  Alternativer Dateiname der Audit/Telemetry Library (dll).
Public Std:: shared_ptr \<HttpDelegate\> httpdelegateoverride  |  Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
Public Std:: shared_ptr \<TaskDispatcherDelegate\> taskdispatcherdelegateoverride  |  Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie Überwachungs-/telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
public bool isnetworkdetectionaktivierte  |  Wenn festgelegt, Pingt die Audit/Telemetry-Komponente den Netzwerkstatus im Hintergrund Thread.
public bool islocalcachingenabled  |  Wenn festgelegt, verwendet die Audit/Telemetry-Komponente das Caching auf dem Datenträger.
public bool istraceloggingenabled  |  Wenn festgelegt, schreibt die Audit/Telemetry-Komponente Warn-/Fehlerprotokolle auf den Datenträger.
public bool isminimaltelemetryaktivierte  |  Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
public bool isfastshutdownaktivierte  |  Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
Public Std:: map \<std::string, std::string\> CustomSettings  |  Benutzerdefinierte Überwachungs-/telemetrieeinstellungen >
Public Std:: map \<std::string, std::vector\<std::string\> \> maskedproperties  |  Überwachungs-/telemetrieereignisse/-Eigenschaften, die maskiert werden sollten
Public Std:: shared_ptr \<AuditDelegate\> auditpipelinedelegateoverride  |  Überschreiben von Überwachungs Delegaten zum Schreiben von Überwachungs Ereignissen
Public Cloud-Cloud  |  Cloudtyp zum Steuern von Telemetriedaten und Überwachungs Ereignissen für Sovereign Cloud Szenario
  
  
#### <a name="hostnameoverride-struct-member"></a>hostnameoverride-Strukturmember
Name der Host Überwachung/telemetrieinstanz. Wenn nicht festgelegt, fungiert MIP als eigener Host.
  
#### <a name="librarynameoverride-struct-member"></a>librarynameoverride-Strukturmember
Alternativer Dateiname der Audit/Telemetry Library (dll).
  
#### <a name="httpdelegate"></a>HttpDelegate
Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
  
#### <a name="taskdispatcherdelegate"></a>TaskDispatcherDelegate
Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie Überwachungs-/telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
  
#### <a name="isnetworkdetectionenabled-struct-member"></a>isnetworkdetectionaktivierter Strukturmember
Wenn festgelegt, Pingt die Audit/Telemetry-Komponente den Netzwerkstatus im Hintergrund Thread.
  
#### <a name="islocalcachingenabled-struct-member"></a>islocalcachingenabled-Strukturmember
Wenn festgelegt, verwendet die Audit/Telemetry-Komponente das Caching auf dem Datenträger.
  
#### <a name="istraceloggingenabled-struct-member"></a>istraceloggingenabled-Strukturmember
Wenn festgelegt, schreibt die Audit/Telemetry-Komponente Warn-/Fehlerprotokolle auf den Datenträger.
  
#### <a name="isminimaltelemetryenabled-struct-member"></a>isminimaltelemetryaktivitätsmember
Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
  
#### <a name="isfastshutdownenabled-struct-member"></a>isfastshutdownaktivierter Strukturmember
Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
  
#### <a name="customsettings-struct-member"></a>CustomSettings-Strukturmember
Benutzerdefinierte Überwachungs-/telemetrieeinstellungen >
  
#### <a name="maskedproperties-struct-member"></a>maskedproperties-Strukturmember
Überwachungs-/telemetrieereignisse/-Eigenschaften, die maskiert werden sollten
  
#### <a name="auditdelegate"></a>Auditdelegat
Überschreiben von Überwachungs Delegaten zum Schreiben von Überwachungs Ereignissen
  
#### <a name="cloud"></a>Cloud
Cloudtyp zum Steuern von Telemetriedaten und Überwachungs Ereignissen für Sovereign Cloud Szenario

### <a name="struct-miptelemetryconfiguration"></a>Struktur MIP:: telemetryconfiguration 
Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)
  
Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String hostnameoverride  |  Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
Public Std:: String librarynameoverride  |  Dateiname der alternativen telemetriebibliothek (dll).
Public Std:: shared_ptr \<HttpDelegate\> httpdelegateoverride  |  Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
Public Std:: shared_ptr \<TaskDispatcherDelegate\> taskdispatcherdelegateoverride  |  Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
public bool isnetworkdetectionaktivierte  |  Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
public bool islocalcachingenabled  |  Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
public bool istraceloggingenabled  |  Wenn festgelegt, schreibt die telemetriekomponente Warn-/Fehlerprotokolle auf den Datenträger.
public bool istelemetryoptedout  |  Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
public bool isfastshutdownaktivierte  |  Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
Public Std:: map \<std::string, std::string\> CustomSettings  |  Benutzerdefinierte telemetrieeinstellungen >
  

#### <a name="hostnameoverride-struct-member"></a>hostnameoverride-Strukturmember
Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
  
#### <a name="librarynameoverride-struct-member"></a>librarynameoverride-Strukturmember
Dateiname der alternativen telemetriebibliothek (dll).
  
#### <a name="httpdelegate"></a>HttpDelegate
Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
  
#### <a name="taskdispatcherdelegate"></a>TaskDispatcherDelegate
Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
  
#### <a name="isnetworkdetectionenabled-struct-member"></a>isnetworkdetectionaktivierter Strukturmember
Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
  
#### <a name="islocalcachingenabled-struct-member"></a>islocalcachingenabled-Strukturmember
Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
  
#### <a name="istraceloggingenabled-struct-member"></a>istraceloggingenabled-Strukturmember
Wenn festgelegt, schreibt die telemetriekomponente Warn-/Fehlerprotokolle auf den Datenträger.
  
#### <a name="istelemetryoptedout-struct-member"></a>istelemetryoptedout-Strukturmember
Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
  
#### <a name="isfastshutdownenabled-struct-member"></a>isfastshutdownaktivierter Strukturmember
Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
  
#### <a name="customsettings-struct-member"></a>CustomSettings-Strukturmember
Benutzerdefinierte telemetrieeinstellungen.

### <a name="struct-uniqueidsandcontentformats"></a>Struktur uniqueidsandcontentformats 
  
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: unordered_map \<std::string, std::string\> UniqueIds  | _Noch nicht dokumentiert._
Public Std:: Vector- \<std::string\> contentformats  | _Noch nicht dokumentiert._
  

  
#### <a name="uniqueids-struct-member"></a>UniqueIds-Strukturmember

_Noch nicht dokumentiert._

  
#### <a name="contentformats-struct-member"></a>contentformats-Strukturmember

_Noch nicht dokumentiert._
