---
title: Zusammenfassung
description: Zusammenfassung
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5af209d5a627263399c8c60f474495dcadab24a0
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446497"
---
# <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
**common** |
Consent-Enumeration       |  Die Antwort eines Benutzers, wenn zum Herstellen einer Verbindung mit dem Dienstendpunkt eine Einwilligung angefordert wird
ApplicationInfo-Struktur  |  Eine Struktur, die anwendungsspezifische Informationen umfasst
**MIP** |
ErrorType-Enumeration       | _Noch nicht dokumentiert._
enum HttpRequestType       |  Typ der HTTP-Anforderung
LogLevel-Enumeration       |  Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
ProtectionHandlerCreationOptions-Enumeration       |  Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.
ProtectionType-Enumeration       |  Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.
ActionType-Enumeration       |  Verschiedene Aktionstypen
struct mip::PublishingLicenseContext | Enthält die Details einer Veröffentlichungslizenz, die zum Erstellen eines Schutzhandlers verwendet wird.

  
## <a name="enumerations-common"></a>Enumerationen (allgemein)
  
### <a name="consent"></a>Consent
Stellt die Entscheidung eines Benutzers bezüglich einer Zustimmung zu einer Verbindung mit einem Dienstendpunkt dar.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
AcceptAlways            | Zustimmung; Speichern dieser Entscheidung
Annehmen            | Zustimmung; einmalig
Ablehnen            | Keine Zustimmung
  
## <a name="enumerations-mip"></a>Enumerationen (MIP)

### <a name="actiontype"></a>ActionType

Verschiedene Aktionstypen

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Fügt eine Fußzeile mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_CONTENT_HEADER            | Fügt einen Header mit Inhalt zum Aktionstyp für das Dokument hinzu.
ADD_WATERMARK            | Fügt ein Wasserzeichen zum Aktionstyp für das gesamte Dokument hinzu.
BENUTZERDEFINIERT            | Ein benutzerdefinierter Aktionstyp
JUSTIFY            | Ein Aktionstyp für die Legitimierung
METADATA            | Ein Aktionstyp zum Ändern von Metadaten
PROTECT_ADHOC            | Ein Aktionstyp zum Schutz anhand von Ad-hoc-Richtlinien
PROTECT_BY_TEMPLATE            | Ein Aktionstyp zum Schutz anhand von Vorlagen
PROTECT_DO_NOT_FORWARD            | Ein Aktionstyp zum Schutz durch Verhinderung einer Weiterleitung
REMOVE_CONTENT_FOOTER            | Ein Aktionstyp, der Fußzeilen mit Inhalt entfernt
REMOVE_CONTENT_HEADER            | Ein Aktionstyp, der Header mit Inhalt entfernt
REMOVE_PROTECTION            | Ein Aktionstyp, der einen Schutz entfernt
REMOVE_WATERMARK            | Ein Aktionstyp, der Wasserzeichen entfernt
APPLY_LABEL            | Ein Aktionstyp, der eine Bezeichnung anwendet
RECOMMEND_LABEL            | Ein Aktionstyp, der eine Bezeichnung empfiehlt

CUSTOM ist ein allgemeiner Aktionstyp. Bei jedem anderen Aktionstyp handelt es sich um eine spezifische Aktion mit einer speziellen Bedeutung.

ActionType-Werte können mithilfe der folgenden Operatoren kombiniert werden:

- AND-Operator (&) für die [Aktion](class_mip_action.md) (`operator &(ActionType a, ActionType b)`)
- Logischer OR-Operator (Xor) (^) für die [Aktion](class_mip_action.md) (`operator ^(ActionType a, ActionType b)`)


### <a name="errortype"></a>ErrorType
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Übergabe einer fehlerhaften Eingabe durch Aufrufer
FILE_IO_ERROR            | Allgemeiner Datei-E/A-Fehler
NETWORK_ERROR            | Allgemeine Netzwerkprobleme, z.B. nicht erreichbarer Dienst
TRANSIENT_NETWORK_ERROR            | Vorübergehende Netzwerkprobleme, z.B. durch ein ungültiges Gateway ausgelöst
INTERNAL_ERROR            | Unerwartete interne Fehler, z.B. im Clientserverprotokoll (Empfang einer unerwarteten Antwort)
JUSTIFICATION_REQUIRED            | Eine Legitimierung ist erforderlich, um die Aktion für die Datei abzuschließen.
NOT_SUPPORTED_OPERATION            | Der angeforderte Vorgang wird noch nicht unterstützt.
PRIVILEGED_REQUIRED            | Privilegierte Bezeichnung kann nicht außer Kraft gesetzt werden, wenn standardmäßig die neue Bezeichnungsmethode verwendet wird.
ACCESS_DENIED            | Der Benutzer konnte nicht auf den Inhalt zugreifen. Beispiele: keine Berechtigungen, Inhalt widerrufen usw.
CONSENT_DENIED            | Ein Vorgang, der die Einwilligung vom Benutzer erfordert, wurde nicht genehmigt.
  
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
Warning            | 
Fehler            | 
Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Keine            | Keine
OfflineOnly            | Benutzeroberflächen- und Netzwerkvorgänge werden nicht zugelassen.
AllowAuditedExtraction            | Inhalt kann in einer App geöffnet werden, die nicht SDK-fähig und für derartigen Schutz von Daten ausgelegt ist
PreferDeprecatedAlgorithms            | Verwendet Kryptografiealgorithmus für Abwärtskompatibilität


### <a name="protectiontype"></a>ProtectionType
Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
TemplateBased            | Handle wurde aus einer Vorlage erstellt.
Benutzerdefiniert            | Handle wurde Ad-hoc erstellt.

  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions
ProtectionHandlerCreationOptions ist bitweiser OR-Operator.

Parameter:  
* **a**: Der linke Wert 

* **b**: Der rechte Wert

### <a name="releaseallresources"></a>ReleaseAllResources
Gibt alle Ressourcen (z.B. Threads) vor dem Herunterfahren frei.
Wenn dynamische MIP-Bibliotheken verzögert von einer Anwendung geladen werden, muss diese Funktion aufgerufen werden, bevor die Anwendung diese Bibliotheken explizit entlädt, um Deadlocks zu vermeiden. Unter win32 muss diese Funktion beispielsweise aufgerufen werden, bevor weitere Aufrufe durchgeführt werden, damit MIP-DLLs explizit über FreeLibrary oder \__FUnloadDelayLoadedDLL2 entladen werden können. Anwendungen müssen vor dem Aufruf dieser Funktion Verweise auf sämtliche MIP-Objekte freigeben (z.B. Profile, Engines und Handler).
  
**Rückgabe**: Bitweises OR von Parametern
  
## <a name="structures"></a>Strukturen

### <a name="applicationinfo"></a>ApplicationInfo 
Eine Struktur, die anwendungsspezifische Informationen umfasst

 Felder                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public std::string applicationId  |  Anwendungs-ID, wie im Azure AD-Portal festgelegt.
 public std::string applicationName  |  Anwendungsname
 public std::string applicationVersion  |  Die verwendete Anwendungsversion
  
### <a name="mippublishinglicensecontext"></a>mip::PublishingLicenseContext 
Enthält die Details einer Veröffentlichungslizenz, die zum Erstellen eines Schutzhandlers verwendet wird.
  
 Felder                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector<uint8_t> licenseInfo  | _Noch nicht dokumentiert._
public const std::vector<uint8_t> serializedPublishingLicense  | _Noch nicht dokumentiert._
public PublishingLicenseContext(const std::vector<uint8_t>& licenseInfo, const std::vector<uint8_t>& serializedPublishingLicense)  | _Noch nicht dokumentiert._
  
