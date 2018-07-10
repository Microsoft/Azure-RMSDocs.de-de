# <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 Consent-Enumeration       |  Stellt die Entscheidung eines Benutzers bezüglich einer Zustimmung zu einer Verbindung mit einem Dienstendpunkt dar.
 ApplicationInfo-Struktur  |  Anwendungs-ID, wie im Azure AD-Portal festgelegt.
**MIP** |
 ActionType-Enumeration       |  Verschiedene Aktionstypen
 ErrorType-Enumeration       | _Noch nicht dokumentiert._
 LogLevel-Enumeration       |  Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
 ProtectionHandlerCreationOptions-Enumeration       |  Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.
 ProtectionType-Enumeration       |  Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.

  
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
  
**ActionType**-Werte unterstützen die folgenden Operatoren:

* OR-Operator (|) für eine Enumeration vom Typ [Action](class_mip_action.md)  
* AND-Operator (&) für eine Enumeration vom Typ [Action](class_mip_action.md)  
* XOR-Operator (^) für eine Enumeration vom Typ [Action](class_mip_action.md)  

### <a name="errortype"></a>ErrorType

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Übergabe einer fehlerhaften Eingabe durch Aufrufer
FILE_IO_ERROR            | Allgemeiner Datei-E/A-Fehler
NETWORK_ERROR            | Allgemeine Netzwerkprobleme, z.B. nicht erreichbarer Dienst
INTERNAL_ERROR            | Unerwartete interne Fehler, z.B. im Clientserverprotokoll (Empfang einer unerwarteten Antwort)
JUSTIFICATION_REQUIRED            | Eine Legitimierung ist erforderlich, um die Aktion für die Datei abzuschließen.
NOT_SUPPORTED_OPERATION            | Der angeforderte Vorgang wird noch nicht unterstützt.
PRIVILEGED_REQUIRED            | Privilegierte Bezeichnung kann nicht außer Kraft gesetzt werden, wenn standardmäßig die neue Bezeichnungsmethode verwendet wird.
ACCESS_DENIED            | Der Benutzer konnte nicht auf den Inhalt zugreifen. Beispiele: keine Berechtigungen, Inhalt widerrufen usw.
  
### <a name="loglevel"></a>LogLevel

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Ablaufverfolgung            | 
Info            | 
Warning            | 
Fehler            | 
Verschiedene Protokollebenen, die vom MIP SDK verwendet werden
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Keine            | Keine
OfflineOnly            | Benutzeroberflächen- und Netzwerkvorgänge werden nicht zugelassen.
AllowAuditedExtraction            | Inhalt kann in einer App geöffnet werden, die nicht SDK-fähig und für derartigen Schutz von Daten ausgelegt ist.
PreferDeprecatedAlgorithms            | Verwendet Kryptografiealgorithmus für Abwärtskompatibilität
Bitflags, die das Verhalten beim Erstellen zusätzlicher Richtlinien vorgeben.
  
### <a name="protectiontype"></a>ProtectionType

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
TemplateBased            | Handle wurde aus einer Vorlage erstellt.
Benutzerdefiniert            | Handle wurde Ad-hoc erstellt.
Beschreibt, ob der Schutz anhand einer Vorlage oder Ad-hoc (benutzerdefiniert) erfolgt.
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

ProtectionHandlerCreationOptions ist bitweiser OR-Operator.

Parameter: 
 
* **a**: Der linke Wert 

* **b**: Der rechte Wert
  
**Rückgabe**: Bitweises OR von Parametern
  


## <a name="structures"></a>Strukturen

### <a name="applicationinfo"></a>ApplicationInfo 
Anwendungs-ID, wie im Azure AD-Portal festgelegt.
  
 Felder                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public std::string applicationId  | Anwendungs-ID im Azure AD-Portal
 public std::string friendlyName  | Anzeigename der App, wie im Portal festgelegt.
  
