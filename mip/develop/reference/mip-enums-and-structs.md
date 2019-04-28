---
title: MIP SDK für C++-Verweis-Strukturen und Enumerationen
description: Referenzdokumentation für C++-MIP-SDK-Strukturen und Enumerationen.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: c9e634d436d02b147fc10a734c8c3d5b1fcdec71
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60173355"
---
# <a name="enumerations-and-structures"></a>Enumerationen und Strukturen

## <a name="namespace-mip"></a>Namespace mip

 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Enum ActionSource       |  definiert, wodurch die SetLabel-Ereignis ausgelöst wurde
ActionType-Enumeration       |  Verschiedene Aktionstypen
Enum AssignmentMethod       |  Die Zuweisungsmethode der Bezeichnung für das Dokument. Gibt an, ob die Zuweisung der Bezeichnung automatisch, standard oder als ein privilegierter Vorgang (das Äquivalent zu einem Administrator-Vorgang) durchgeführt wurde.
Consent-Enumeration       |  Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
Enum ContentFormat       |  Content-Format.
enum ContentMarkAlignment       |  Ausrichtung für den Inhalt markiert (Content-Header oder Fußzeile mit Inhalt).
Enum DataState       |  Definiert, welchem Zustand der Daten die Anwendung ausgeführt wird.
ErrorType-Enumeration       | _Noch nicht dokumentiert._
enum HttpRequestType       |  Typ der HTTP-Anforderung
LogLevel-Enumeration       |  Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
ProtectionHandlerCreationOptions-Enumeration       |  Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.
ProtectionType-Enumeration       |  Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.
WatermarkLayout-Enumeration       |  Layout für Wasserzeichen.
ApplicationInfo-Struktur  |  Eine Struktur, die anwendungsspezifische Informationen umfasst
Struktur PublishingLicenseContext  |  Enthält die Details einer Veröffentlichungslizenz, die zum Erstellen eines Schutzhandlers verwendet wird.
  
## <a name="enumerations-mip"></a>Enumerationen (MIP)

### <a name="actionsource"></a>ActionSource

Definiert, wodurch die SetLabel-Ereignis ausgelöst wurde.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
MANUELL            | Manuell durch Benutzer ausgewählt
AUTOMATISCH            | Festlegen von Bedingungen für Richtlinien
EMPFOHLEN            | Vom Benutzer festgelegt werden, nachdem Bezeichnung, indem Sie Bedingungen für Richtlinien empfohlen wurde
DEFAULT            | In der Richtlinie standardmäßig festgelegt
OBLIGATORISCH            | Vom Benutzer festgelegt werden, nachdem Richtlinie erzwungen, um eine Bezeichnung festlegen



### <a name="actiontype"></a>ActionType

Verschiedene Aktionstypen CUSTOM ist ein allgemeiner Aktionstyp. Bei jedem anderen Aktionstyp handelt es sich um eine spezifische Aktion mit einer speziellen Bedeutung.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Fügt eine Fußzeile mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_CONTENT_HEADER            | Fügt einen Header mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_WATERMARK            | Fügt ein Wasserzeichen zum Aktionstyp für das gesamte Dokument hinzu.
BENUTZERDEFINIERT            | Ein benutzerdefinierter Aktionstyp
JUSTIFY            | Ein Aktionstyp für die Legitimierung
METADATEN            | Ein Aktionstyp zum Ändern von Metadaten
PROTECT_ADHOC            | Ein Aktionstyp zum Schutz anhand von benutzerdefinierten Richtlinien
PROTECT_BY_TEMPLATE            | Ein Aktionstyp zum Schutz anhand von Vorlagen
PROTECT_DO_NOT_FORWARD            | Ein Aktionstyp zum Schutz durch Verhinderung einer Weiterleitung
REMOVE_CONTENT_FOOTER            | Ein Aktionstyp, der Fußzeilen mit Inhalt entfernt
REMOVE_CONTENT_HEADER            | Ein Aktionstyp, der Header mit Inhalt entfernt
REMOVE_PROTECTION            | Ein Aktionstyp, der einen Schutz entfernt
REMOVE_WATERMARK            | Ein Aktionstyp, der Wasserzeichen entfernt
APPLY_LABEL            | Ein Aktionstyp, der eine Bezeichnung anwendet
RECOMMEND_LABEL            | Ein Aktionstyp, der eine Bezeichnung empfiehlt


### <a name="assignmentmethod"></a>AssignmentMethod

Die Zuweisungsmethode der Bezeichnung für das Dokument. Gibt an, ob die Zuweisung der Bezeichnung automatisch, standard oder als ein privilegierter Vorgang (das Äquivalent zu einem Administrator-Vorgang) durchgeführt wurde.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
STANDARD            | [Bezeichnung](class_mip_label.md) Zuweisungsmethode ist standard
BERECHTIGUNGEN            | [Bezeichnung](class_mip_label.md) Zuweisungsmethode ist privilegiert
AUTO            | [Bezeichnung](class_mip_label.md) Zuweisungsmethode erfolgt automatisch


### <a name="consent"></a>Zustimmung

Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
AcceptAlways            | Zustimmung; Speichern dieser Entscheidung
Annehmen            | Zustimmung; einmalig
Ablehnen            | Keine Zustimmung


### <a name="contentformat"></a>ContentFormat

Content-Format.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
DEFAULT            | Inhalt ist standard-Datei-format
E-MAIL            | Inhalt ist-e-Mail-format

### <a name="contentmarkalignment"></a>ContentMarkAlignment

Ausrichtung für den Inhalt markiert (Content-Header oder Fußzeile mit Inhalt).

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
LEFT            | Content-Kennzeichnung ist linksbündig ausgerichtet angezeigt.
RIGHT            | Content-Kennzeichnung wird rechts ausgerichtet.
ZENTRUM            | Content-Kennzeichnung wird zentriert.

### <a name="datastate"></a>DataState
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
REST            | Inaktive Daten physisch in Datenbanken/Datei/warehouses
WÄHREND DER ÜBERTRAGUNG            | Daten durchlaufen ein Netzwerk oder vorübergehend befinden, im Arbeitsspeicher des Computers gelesen oder aktualisiert werden
VERWENDUNG            | Aktive Daten unter ständigen Änderungen, die in Datenbanken/Datei/Warehouses Etc physisch gespeichert


### <a name="errortype"></a>ErrorType
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Übergabe einer fehlerhaften Eingabe durch Aufrufer
FILE_IO_ERROR            | Allgemeiner Datei-E/A-Fehler
NETWORK_ERROR            | Allgemeine Netzwerkprobleme; Beispielsweise ist nicht erreichbar-Dienst.
TRANSIENT_NETWORK_ERROR            | Vorübergehende Netzwerkprobleme; Beispiel: aufgrund eines ungültigen Gateways.
INTERNAL_ERROR            | Unerwartete interne Fehler,
JUSTIFICATION_REQUIRED            | Eine Legitimierung ist erforderlich, um die Aktion für die Datei abzuschließen.
NOT_SUPPORTED_OPERATION            | Der angeforderte Vorgang wird noch nicht unterstützt.
PRIVILEGED_REQUIRED            | Privilegierte Bezeichnung kann nicht außer Kraft gesetzt werden, wenn standardmäßig die neue Bezeichnungsmethode verwendet wird.
ACCESS_DENIED            | Der Benutzer konnten den Zugriff auf Dienste nicht abgerufen werden.
CONSENT_DENIED            | Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
POLICY_SYNC_ERROR            | Ein fehlgeschlagener Versuch, Richtliniendaten zu synchronisieren.
NO_PERMISSIONS            | Der Benutzer konnte nicht auf den Inhalt zugreifen. Widerrufen z. B. keine Berechtigungen, die Inhalt
NO_AUTH_TOKEN            | Der Benutzer konnte Zugriff auf den Inhalt aufgrund einer leeren Auth-Token nicht abgerufen werden.
DISABLED_SERVICE            | Der Benutzer konnte Zugriff auf den Inhalt aufgrund der Deaktivierung nicht abgerufen werden.
PROXY_AUTH_ERROR            | Fehler bei der Proxyauthentifizierung.
NO_POLICY_ERROR            | Keine Richtlinie ist für Benutzer/Mandanten konfiguriert.
OPERATION_CANCELLED            | Vorgang wurde abgebrochen.
ADHOC_PROTECTION_REQUIRED            | Ad-hoc-Schutz muss zum Abschließen der Aktion auf die Datei festgelegt werden
  
### <a name="httprequesttype"></a>HttpRequestType

Typ der HTTP-Anforderung

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Abrufen            | GET
POST            | POST

  
### <a name="loglevel"></a>LogLevel

Verschiedene Protokollebenen, die vom MIP SDK verwendet werden

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Ablaufverfolgung            | 
Info            | 
Warnung            | 
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Keine            | Keine
OfflineOnly            | Benutzeroberflächen- und Netzwerkvorgänge werden nicht zugelassen.
AllowAuditedExtraction            | Inhalt kann in einer App geöffnet werden, die nicht SDK-fähig und für derartigen Schutz von Daten ausgelegt ist
PreferDeprecatedAlgorithms            | Verwendet Kryptografiealgorithmus für Abwärtskompatibilität


### <a name="protectiontype"></a>ProtectionType

Beschreibt, ob der Schutz aus einer Vorlage oder Ad-hoc-(Benutzerdefiniert) basiert.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
TemplateBased            | Handle wurde aus einer Vorlage erstellt.
Benutzerdefiniert            | Handle wurde Ad-hoc erstellt.

  
### <a name="watermarklayout"></a>WatermarkLayout

Layout für Wasserzeichen.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
HORIZONTAL            | Layout des Wasserzeichens ist horizontal
DIAGONAL            | Layout des Wasserzeichens ist eine diagonale


## <a name="structures"></a>Strukturen 

### <a name="mipapplicationinfo"></a>mip::ApplicationInfo 
Eine Struktur, die anwendungsspezifische Informationen umfasst
  
#### <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string applicationId  |  Anwendungs-ID als legen Sie in der AAD-Portal, (muss eine GUID ohne eckige Klammern).
public std::string applicationName  |  Name der Anwendung (darf nur gültige Ausschließen von ASCII-Zeichen enthalten. ';')
public std::string applicationVersion  |  Die Version der Anwendung verwendet wird, (darf nur gültige Ausschließen von ASCII-Zeichen enthalten. ';')
  
#### <a name="members"></a>Member
  
##### <a name="applicationid-struct-member"></a>ApplicationId-Strukturmember
Anwendungs-ID als legen Sie in der AAD-Portal, (muss eine GUID ohne eckige Klammern).
  
##### <a name="applicationname-struct-member"></a>ApplicationName-Strukturmember
Name der Anwendung (darf nur gültige Ausschließen von ASCII-Zeichen enthalten. ';')
  
##### <a name="applicationversion-struct-member"></a>Strukturmember applicationVersion
Die Version der Anwendung verwendet wird, (darf nur gültige Ausschließen von ASCII-Zeichen enthalten. ';')  

### <a name="mippublishinglicensecontext"></a>mip::PublishingLicenseContext 
Enthält die Details einer Veröffentlichungslizenz, die zum Erstellen eines Schutzhandlers verwendet wird.
  
#### <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public const Std:: vector\<uint8_t\> LicenseInfo  | _Noch nicht dokumentiert._
Public const Std:: vector\<uint8_t\> SerializedPublishingLicense  | _Noch nicht dokumentiert._
Öffentliche PublishingLicenseContext (const Std:: vector\<uint8_t\>& LicenseInfo, const Std:: vector\<uint8_t\>& SerializedPublishingLicense)  | _Noch nicht dokumentiert._
  
#### <a name="members"></a>Member
  
##### <a name="licenseinfo-struct-member"></a>Strukturmember licenseInfo
_Noch nicht dokumentiert._

  
##### <a name="serializedpublishinglicense-struct-member"></a>Strukturmember serializedPublishingLicense
_Noch nicht dokumentiert._

  
##### <a name="publishinglicensecontext-function"></a>PublishingLicenseContext-Funktion
_Noch nicht dokumentiert._
