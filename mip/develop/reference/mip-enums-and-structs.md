---
title: MIP SDK für C++ Referenzstrukturen und-aufblendaten
description: Referenz Dokumentation für MIP C++ SDK-Strukturen und-aufblendaten.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 2a641ace68d6999e3d452fa7f5c014ec1215556a
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556009"
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
"labelfiltertype"-Klasse       |  Bezeichnungs Filtertypen, optionaler Satz von Eigenschaften, der zum Filtern von Bezeichnungen beim Aufrufen von Listen Vertraulichkeits Bezeichnungen verwendet werden kann.
Consent-Enumeration       |  Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
cachestoragetype-Klasse       |  Der Speichertyp für die Caches.
Aufzählung von pfileextensionbehavior       |  Beschreibt das Verhalten von Pfile-Erweiterungen.
ErrorType-Enumeration       | Noch nicht dokumentiert.
' inspec'-Aufzählungs Typen       |  Der Inspektortyp korreliert die unterstützten Dateitypen.
"tyum BodyType"       |  Texttyp-Enumerator.
"Enumeration flightingfeature"       |  Definiert neue Features anhand des Namens.
enum HttpRequestType       |  Typ der HTTP-Anforderung
LogLevel-Enumeration       |  Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
ProtectionType-Enumeration       |  Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.
ActionType-Enumeration       |  Verschiedene Aktionstypen
' labelstate ' aufzählen       | Noch nicht dokumentiert.
umeration Aktionstyp       | Noch nicht dokumentiert.
Enumeration conditiondatatype       | Noch nicht dokumentiert.
"contentmarkplacement" aufzählen       | Noch nicht dokumentiert.
"Denum labelaktiondatatype"       | Noch nicht dokumentiert.
schutzaktionstyp "konum"       | Noch nicht dokumentiert.
Struktur MIP:: ApplicationInfo  |  Eine Struktur, die anwendungsspezifische Informationen umfasst
Struktur MIP:: telemetryconfiguration  |  Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)

### <a name="enumerations"></a>Enumerationen

#### <a name="watermarklayout-enum"></a>Watermarklayout-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Ales            | Wasserzeichen Layout ist horizontal
Aler            | Wasserzeichen Layout ist diagonal
Layout für Wasserzeichen.
  
#### <a name="contentmarkalignment-enum"></a>Contentmarkalignment-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
LEFT            | Die Inhalts Markierung wird linksbündig ausgerichtet.
RIGHT            | Die Inhalts Markierung wird rechtsbündig ausgerichtet.
ZENTRUM            | Das Markieren von Inhalten wird zentriert.
Ausrichtung für Inhalts Markierungen (Content Header oder Content Footer).
  
#### <a name="assignmentmethod-enum"></a>Zutragmethod-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
STANDARD            | Bezeichnungs Zuweisungs Methode ist Standard
Privilegierten            | Bezeichnungs Zuweisungs Methode ist privilegiert
AUTO            | Bezeichnungs Zuweisungs Methode ist automatisch
Die Zuweisungs Methode der Bezeichnung im Dokument. Gibt an, ob die Zuweisung der Bezeichnung automatisch durchgeführt wurde, Standard oder als privilegierter Vorgang (entspricht einem Administrator Vorgang).
  
#### <a name="actionsource-enum"></a>Aktions Quellen-Enumeration
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
MANUAL            | Manuell vom Benutzer ausgewählt
AUTOMATIC            | Durch Richtlinien Bedingungen festlegen
EMPFOHLEN            | Vom Benutzer festgelegt, nachdem die Bezeichnung von Richtlinien Bedingungen empfohlen wurde
DEFAULT            | Standardmäßig in Richtlinie festlegen
definiert, was das Ereignis "setlabel" ausgelöst hat.
  
#### <a name="datastate-enum"></a>Datastate-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
REST            | Inaktive Daten, die physisch in Datenbanken/Dateien/Lager speichern gespeichert
Entschließungs            | Daten, die ein Netzwerk durchlaufen oder sich vorübergehend im zu lesenden oder zu aktualisierenden Computerspeicher befinden
USE            | Aktive Daten unter konstanter Änderung werden physisch in Datenbanken/Dateien/Lagerhäusern gespeichert usw.
Definiert den Zustand der Daten, auf den die Anwendung angewendet wird.
  
#### <a name="contentformat-enum"></a>Contentformat-Enumeration
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
DEFAULT            | Inhalts Format ist Standarddatei Format
E-MAIL            | Inhalts Format ist e-Mail-Format
Inhalts Format.
  
#### <a name="labelfiltertype-enum"></a>Labelfiltertype-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Keine            | Standardmäßige Beschriftungs Filterung deaktivieren
Benutzerdefiniert            | Bezeichnungen filtern, die zu einem benutzerdefinierten Schutz führen können
Templateprotection            | Bezeichnungen filtern, die möglicherweise nicht weiterleiten
Donotforwardprotection            | Bezeichnungen filtern, die möglicherweise zum Schutz von Vorlagen führen
Adhucprotection            | Bezeichnungen filtern, die möglicherweise zu einem Ad-hoc-Schutz führen
Hyokprotection            | Bezeichnungen filtern, die zum Hyok-Schutz führen können
Predefinedtemplate            | Bezeichnungen filtern, die zu vordefiniertem Vorlagen Schutz führen können
Bezeichnungs Filtertypen, optionaler Satz von Eigenschaften, der zum Filtern von Bezeichnungen beim Aufrufen von Listen Vertraulichkeits Bezeichnungen verwendet werden kann.
  
#### <a name="consent-enum"></a>Zustimmungs-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
AcceptAlways            | Zustimmung; Speichern dieser Entscheidung
Annehmen            | Zustimmung; einmalig
Ablehnen            | Keine Zustimmung
Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
  
#### <a name="cachestoragetype-enum"></a>Cachestoragetype-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
InMemory            | Im Speicher Speicher
OnDisk            | Auf Datenträger Speicher
Ondiskverschlüsselt            | Auf Datenträger Speicher mit Verschlüsselung (sofern von der Plattform unterstützt)
Der Speichertyp für die Caches.
  
#### <a name="pfileextensionbehavior-enum"></a>Pfileextensionbehavior-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Standardwert            | Erweiterungen werden als SDK-Standardverhalten verwendet.
Pfilesuffix            | Erweiterungen werden <EXT>. PFILE
Pprefix            | Erweiterungen werden zu P<EXT>
Beschreibt das Verhalten von Pfile-Erweiterungen.
  
#### <a name="errortype-enum"></a>ErrorType-Aufzählung
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
CONSENT_DENIED            | Einem Vorgang, der die Einwilligung vom Benutzer erfordert, wurde keine Einwilligung erteilt.
POLICY_SYNC_ERROR            | Ein fehlgeschlagener Versuch, Richtliniendaten zu synchronisieren.
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
  
#### <a name="inspectortype-enum"></a>Inspector Type-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Unbekannt            | Unkown-Datei Inspektor.
Nachricht            | Datei Inspektor im Nachrichten Stil, rpmsg/msg-basiert.
Der Inspektortyp korreliert die unterstützten Dateitypen.
  
#### <a name="bodytype-enum"></a>BodyType-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
UNBEKANNT            | Unkown-Texttyp
TXT            | Text Stiltyp, Codierung wird als UTF8 zurückgegeben
HTML            | HTML-Style-Texttyp, Codierung wird als UTF8 zurückgegeben
RTF            | RTF-Texttyp, binäres Format
Texttyp-Enumerator.
  
#### <a name="flightingfeature-enum"></a>Flightingfeature-Enumeration
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Servicediscovery            | Zum Ermitteln von RMS-Dienst Endpunkten einen separaten HTTP-Befehl einsetzen
Authinfocache            | Cache OAuth2 Anforderungen pro Domäne/Mandant, um unnötige 401-Antworten zu verringern. Deaktivieren Sie für Apps/Dienste, die ihre eigene HTTP-Authentifizierung verwalten (z. b. SPO, Edge).
Linuxencryptedcache            | Aktivieren Sie das verschlüsselte Caching für Linux-Plattformen (Lesen Sie die Voraussetzungen für dieses Feature).
Singledomainname            | Aktivieren Sie den einzelnen Firmennamen für die DNS-Suche. z. b. [https://corprights](https://corprights)
Policyauth            | Aktivieren Sie die automatische HTTP-Authentifizierung für an den Richtlinien Dienst gesendete Anforderungen. Deaktivieren Sie für Apps/Dienste, die ihre eigene HTTP-Authentifizierung verwalten (z. b. SPO, Edge).
Definiert neue Features anhand des Namens.
  
#### <a name="httprequesttype-enum"></a>Httprequesttype-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Abrufen            | GET
POST            | POST
Typ der HTTP-Anforderung
  
#### <a name="loglevel-enum"></a>LogLevel-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Ablaufverfolgung            | 
Info            | 
Warning            | 
Error            | 
Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
  
#### <a name="protectiontype-enum"></a>Schutztyp-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
TemplateBased            | Handle wurde aus einer Vorlage erstellt.
Benutzerdefiniert            | Handle wurde Ad-hoc erstellt.
Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.
  
#### <a name="actiontype-enum"></a>Aktionstyp-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Fügt eine Fußzeile mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_CONTENT_HEADER            | Fügt einen Header mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_WATERMARK            | Fügt ein Wasserzeichen zum Aktionstyp für das gesamte Dokument hinzu.
BENUTZERDEFINIERT            | Ein benutzerdefinierter Aktionstyp
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
Verschiedene Aktionstypen
CUSTOM ist ein allgemeiner Aktionstyp. Bei jedem anderen Aktionstyp handelt es sich um eine spezifische Aktion mit einer speziellen Bedeutung.
  
#### <a name="labelstate-enum"></a>Labelstate-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
NoChange            | 
Remove            | 
Update/Aktualisieren            | 
  
#### <a name="actiondatatype-enum"></a>Aktiondatatype-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Benutzerdefiniert            | 
Protection            | 
Contentmarking            | 
Addwatermark            | 
Label            | 
  
#### <a name="conditiondatatype-enum"></a>Conditiondatatype-Enumeration
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Standardwert            | 
Vertraulichkeit            | 
  
#### <a name="contentmarkplacement-enum"></a>Contentmarkplacement-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Header            | 
Fußzeile            | 
  
#### <a name="labelactiondatatype-enum"></a>Labelaktiondatatype-Aufzählung
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Recommend            | 
Übernehmen            | 
  
#### <a name="protectionactiontype-enum"></a>Schutzaktionstyp-Aufzählung
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

### <a name="structures"></a>Strukturen

#### <a name="struct-mipapplicationinfo"></a>Struktur MIP:: ApplicationInfo 
Eine Struktur, die anwendungsspezifische Informationen umfasst
  
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string applicationId  |  Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
public std::string applicationName  |  Anwendungsname (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
public std::string applicationVersion  |  Die Version der verwendeten Anwendung (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
  

##### <a name="applicationid-struct-member"></a>ApplicationId-Strukturmember
Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
  
##### <a name="applicationname-struct-member"></a>ApplicationName-Strukturmember
Anwendungsname (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
  
##### <a name="applicationversion-struct-member"></a>applicationVersion-Strukturmember
Die Version der verwendeten Anwendung (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)

#### <a name="struct-miptelemetryconfiguration"></a>Struktur MIP:: telemetryconfiguration 
Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)
  
Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String hostnameoverride  |  Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
Public Std:: String librarynameoverride  |  Dateiname der alternativen telemetriebibliothek (dll).
Public Std:: shared_ptr\<httpdelegat\> httpdelegateoverride  |  Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
Public Std:: shared_ptr\<taskdispatcherdelegaten\> taskdispatcherdelegateoverride  |  Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
public bool isnetworkdetectionaktivierte  |  Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
public bool islocalcachingenabled  |  Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
public bool istraceloggingenabled  |  Wenn festgelegt, schreibt die telemetriekomponente Warn-/Fehlerprotokolle auf den Datenträger.
public bool istelemetryoptedout  |  Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
public bool isfastshutdownaktivierte  |  Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
Public Std:: Map\<Std:: String, Std:: String\> CustomSettings  |  Benutzerdefinierte telemetrieeinstellungen >
    
##### <a name="hostnameoverride-struct-member"></a>hostnameoverride-Strukturmember
Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
  
##### <a name="librarynameoverride-struct-member"></a>librarynameoverride-Strukturmember
Dateiname der alternativen telemetriebibliothek (dll).
  
##### <a name="httpdelegate"></a>HttpDelegate
Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
  
##### <a name="taskdispatcherdelegate"></a>TaskDispatcherDelegate
Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
  
##### <a name="isnetworkdetectionenabled-struct-member"></a>isnetworkdetectionaktivierter Strukturmember
Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
  
##### <a name="islocalcachingenabled-struct-member"></a>islocalcachingenabled-Strukturmember
Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
  
##### <a name="istraceloggingenabled-struct-member"></a>istraceloggingenabled-Strukturmember
Wenn festgelegt, schreibt die telemetriekomponente Warn-/Fehlerprotokolle auf den Datenträger.
  
##### <a name="istelemetryoptedout-struct-member"></a>istelemetryoptedout-Strukturmember
Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
  
##### <a name="isfastshutdownenabled-struct-member"></a>isfastshutdownaktivierter Strukturmember
Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
  
##### <a name="customsettings-struct-member"></a>CustomSettings-Strukturmember
Benutzerdefinierte telemetrieeinstellungen >

## <a name="namespace-mipauditmetadatakeys"></a>Namespace MIP:: auditmetadatakeys
  
### <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String Sender ()       |  Überwachen von metadatenschlüsseln in der Zeichen folgen Darstellung.
Public Std:: String-Empfänger ()       | Noch nicht dokumentiert.
Public Std:: String LastModifiedBy ()       | Noch nicht dokumentiert.
Public Std:: String LastModifiedDate ()       | Noch nicht dokumentiert.
  
### <a name="members"></a>Member
  
#### <a name="sender-function"></a>Sender-Funktion
Überwachen von metadatenschlüsseln in der Zeichen folgen Darstellung.
  
#### <a name="recipients-function"></a>Empfänger Funktion
_Noch nicht dokumentiert._

  
#### <a name="lastmodifiedby-function"></a>LastModifiedBy-Funktion
_Noch nicht dokumentiert._

  
#### <a name="lastmodifieddate-function"></a>LastModifiedDate-Funktion
_Noch nicht dokumentiert._

## <a name="namespace-miprights"></a>Namespace MIP:: Rights
  
### <a name="summary"></a>Zusammenfassung
 
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string Owner()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.
public std::string View()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.
public std::string AuditedExtract()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.
public std::string Edit()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.
public std::string Export()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.
public std::string Extract()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.
public std::string Print()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.
public std::string Comment()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.
public std::string Reply()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.
public std::string ReplyAll()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.
public std::string Forward()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.
Public Std:: Vector\<Std:: String\> emailrights ()       |  Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.
Public Std:: Vector\<Std:: String\> editabledocumentrights ()       |  Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.
Public Std:: Vector\<Std:: String\> commonrights ()       |  Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.
  
### <a name="members"></a>Member
  
#### <a name="owner-function"></a>Owner-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „owner“
  
#### <a name="view-function"></a>View-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „view“
  
#### <a name="auditedextract-function"></a>Auditedextract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „audited extract“
  
#### <a name="edit-function"></a>Funktion Bearbeiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „edit“
  
#### <a name="export-function"></a>Export-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „export“
  
#### <a name="extract-function"></a>Extract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „extract“
  
#### <a name="print-function"></a>Print-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „print“
  
#### <a name="comment-function"></a>Comment-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „comment“
  
#### <a name="reply-function"></a>Reply-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply“
  
#### <a name="replyall-function"></a>ReplyAll-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply all“
  
#### <a name="forward-function"></a>Forward-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „forward“
  
#### <a name="emailrights-function"></a>Emailrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für E-Mails gelten
  
#### <a name="editabledocumentrights-function"></a>Editabledocumentrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für Dokumente gelten
  
#### <a name="commonrights-function"></a>Commonrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für alle Szenarien gelten

## <a name="namespace-miproles"></a>Namespace MIP:: Rollen
  
### <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string Viewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.
public std::string Reviewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.
public std::string Author()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.
public std::string CoOwner()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.
  
### <a name="members"></a>Member
  
#### <a name="viewer-function"></a>Viewer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „viewer“. Benutzer mit der Rolle „viewer“ können Inhalte nur anzeigen. Sie können die Inhalte nicht bearbeiten, kopieren oder drucken.
  
#### <a name="reviewer-function"></a>Reviewer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „reviewer“. Ein Prüfer kann Inhalte anzeigen und bearbeiten. Ein Prüfer kann die Inhalte nicht kopieren oder drucken.
  
#### <a name="author-function"></a>Author-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „author“. Ein Autor kann Inhalte anzeigen, bearbeiten, kopieren und drucken.
  
#### <a name="coowner-function"></a>Coowner-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „Mitbesitzer“. Ein Mitbesitzer verfügt über alle Berechtigungen.

