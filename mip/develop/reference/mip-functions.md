---
title: Funktionen
description: Funktionen
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.date: 01/28/2019
ms.author: mbaldwin
ms.openlocfilehash: ced8339fa93ec349644a1f9e386489bb02c8eff0
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60173416"
---
# <a name="functions"></a>Funktionen

## <a name="summary"></a>Zusammenfassung 

### <a name="namespace-mip"></a>Namespace mip
| Funktionen von Namespace-Gültigkeitsbereich   | Beschreibungen                                |
|--------------------------------|---------------------------------------------|
Public Std:: String GetAssignmentMethodString (AssignmentMethod-Methode)       |  AssignmentMethod-Enumeration, der eine zeichenfolgenbeschreibung konvertiert.
public static std::string GetActionSourceString(ActionSource actionSource)       |  Ruft den Namen der Aktion-Quelle.
public static std::string GetDataStateString(mip::DataState state)       |  Ruft den Namen des Inhaltszustands.
public const std::string& GetCustomSettingPolicyDataName()       |  Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.
public const std::string& GetCustomSettingExportPolicyFileName()       |  Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.
public const std::string& GetCustomSettingSensitivityTypesDataName()       |  Der Name der Einstellung, um die Vertraulichkeit von Daten explizit angeben.
public const std::string& GetCustomSettingPolicyDataFile()       |  Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.
public const std::string& GetCustomSettingSensitivityTypesDataFile()       |  Der Name der Einstellung, um die Vertraulichkeit Datendateipfad für Typen explizit angeben.
public const std::string& GetCustomSettingExternalLabelsEnabled()       |  Der Name der Einstellung, mit dem "externe Bezeichnungen"-Feature aktivieren kann.
Öffentliche MIP_API "void" __CDECL ReleaseAllResources()       |  Gibt alle Ressourcen (Threads, usw.) vor dem Herunterfahren.
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const Std:: shared_ptr\<std::istream\>& StdIStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const Std:: shared_ptr\<std::ostream\>& StdOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const Std:: shared_ptr\<std::iostream\>& StdIOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromBuffer (Puffer uint8_t *, const int64_t Größe)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.


### <a name="namespace-mipauditmetadatakeys"></a>Namespace mip::auditmetadatakeys
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String Sender()       |  Überwachen Sie die Metadatenschlüssel in eine Zeichenfolgendarstellung.
Public Std:: String Recipients()       | _Noch nicht dokumentiert._
Public Std:: String LastModifiedBy()       | _Noch nicht dokumentiert._
public std::string LastModifiedDate()       | _Noch nicht dokumentiert._


### <a name="namespace-miprights"></a>Namespace mip::rights

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
Public Std:: vector\<Std:: String\> EmailRights()       |  Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.
Public Std:: vector\<Std:: String\> EditableDocumentRights()       |  Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.
Public Std:: vector\<Std:: String\> CommonRights()       |  Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.

### <a name="namespace-miproles"></a>Namespace mip::roles

 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string Viewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.
public std::string Reviewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.
public std::string Author()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.
public std::string CoOwner()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

## <a name="namespace-mip"></a>Namespace mip

### <a name="getassignmentmethodstring-function"></a>GetAssignmentMethodString-Funktion
AssignmentMethod-Enumeration, der eine zeichenfolgenbeschreibung konvertiert.

Parameter:  
* **Methode**: einer Zuweisungsmethode. 



  
**Gibt**: Eine zeichenfolgenbeschreibung der Zuweisungsmethode.
  
### <a name="getactionsourcestring-function"></a>GetActionSourceString-Funktion
Ruft den Namen der Aktion-Quelle.

Parameter:  
* **actionSource**: Die aktionsquelle. 



  
**Gibt**: Eine Zeichenfolgendarstellung der aktionsquelle.
  
### <a name="getdatastatestring-function"></a>GetDataStateString-Funktion
Ruft den Namen des Inhaltszustands.

Parameter:  
* **actionSource**: Der Status des Inhalts, die bei bearbeitet werden. 



  
**Gibt**: Eine Zeichenfolgendarstellung des Inhalts Status.
  
### <a name="getcustomsettingpolicydataname-function"></a>GetCustomSettingPolicyDataName function
Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.

  
**Gibt**: Der Schlüssel für benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingexportpolicyfilename-function"></a>GetCustomSettingExportPolicyFileName-Funktion
Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.

  
**Gibt**: Der Schlüssel für benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingsensitivitytypesdataname-function"></a>GetCustomSettingSensitivityTypesDataName function
Der Name der Einstellung, um die Vertraulichkeit von Daten explizit angeben.

  
**Gibt**: Der Schlüssel für benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingpolicydatafile-function"></a>GetCustomSettingPolicyDataFile-Funktion
Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.

  
**Gibt**: Der Schlüssel für benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingsensitivitytypesdatafile-function"></a>GetCustomSettingSensitivityTypesDataFile-Funktion
Der Name der Einstellung, um die Vertraulichkeit Datendateipfad für Typen explizit angeben.

  
**Gibt**: Der Schlüssel für benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingexternallabelsenabled-function"></a>GetCustomSettingExternalLabelsEnabled-Funktion
Der Name der Einstellung, mit dem "externe Bezeichnungen"-Feature aktivieren kann.

  
**Gibt**: Der Schlüssel für benutzerdefinierte Einstellungen.
  
### <a name="releaseallresources-function"></a>ReleaseAllResources-Funktion
Gibt alle Ressourcen (Threads, usw.) vor dem Herunterfahren.
Diese Funktion muss genau einmal vor der prozessbeendigung aufgerufen werden. Es ermöglicht MIP Aufhebung der Initialisierung der selbst in einen Moment Zeit, in dem ihre abhängigen Bibliotheken werden noch geladen werden garantiert und Thread zu verknüpfen ist weiterhin möglich. Anwendungen müssen vor dem Aufruf dieser Funktion Verweise auf sämtliche MIP-Objekte freigeben (z.B. Profile, Engines und Handler).
Wenn diese Funktion nicht aufgerufen wird, werden MIP auf natürliche Weise als Teil der standardmäßigen Vorgang zur Beendigung entfernt. Auf manchen Plattformen ist dies Deadlock führen kann (z. B. Threads können nicht verknüpft werden, auf win32 als Reaktion auf die Beendigung verarbeiten) oder abstürzt (z. B. die DLL entladen-Reihenfolge für verzögert geladene Bibliotheken auf win32 nicht vom kontrolliert MIP, damit ihre abhängigen Bibliotheken möglicherweise haben mit der Zeit, wenn Code für das Herunterfahren MIP ausgeführt wird, ungültige lesen Fehler führt, entladen wurden).
  
### <a name="createstreamfromstdstream-function"></a>CreateStreamFromStdStream-Funktion
Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.

Parameter:  
* **stdIStream**: Sichern von std::istream



  
**Gibt**: [Stream](class_mip_stream.md) umschließen einer std::istream
  
### <a name="createstreamfromstdstream-function"></a>CreateStreamFromStdStream-Funktion
Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.

Parameter:  
* **stdOStream**: Sichern von std::ostream



  
**Gibt**: [Stream](class_mip_stream.md) umschließen einer std::ostream
  
### <a name="createstreamfromstdstream-function"></a>CreateStreamFromStdStream-Funktion
Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.

Parameter:  
* **stdIOStream**: Sichern von std::iostream



  
**Gibt**: [Stream](class_mip_stream.md) umschließen einer std::iostream
  
### <a name="createstreamfrombuffer-function"></a>CreateStreamFromBuffer-Funktion
Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.

Parameter:  
* **buffer**: Zeiger auf einen Puffer



  
**Gibt**: Größe der Größe des Puffers
  



## <a name="namespace-mipauditmetadatakeys"></a>Namespace mip::auditmetadatakeys

### <a name="sender-function"></a>Sender-Funktion
Überwachen Sie die Metadatenschlüssel in eine Zeichenfolgendarstellung.
  
### <a name="recipients-function"></a>Empfänger-Funktion
_Noch nicht dokumentiert._

  
### <a name="lastmodifiedby-function"></a>LastModifiedBy-Funktion
_Noch nicht dokumentiert._

  
### <a name="lastmodifieddate-function"></a>LastModifiedDate & lt; Funktion
_Noch nicht dokumentiert._






## <a name="namespace-miprights"></a>Namespace mip::rights

### <a name="owner-function"></a>Besitzer-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.

  
**Gibt**: Die Zeichenfolgen Sie-ID für "Owner" rechts
  
### <a name="view-function"></a>Ansichtsfunktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.

  
**Gibt**: Bezeichner für die 'Ansicht' Zeichenfolge von rechts
  
### <a name="auditedextract-function"></a>AuditedExtract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "überwacht extrahieren" nach rechts
  
### <a name="edit-function"></a>Funktion bearbeiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "Bearbeiten" rechts
  
### <a name="export-function"></a>Export-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "Export" rechts
  
### <a name="extract-function"></a>Extract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für die Rechte "extrahieren"
  
### <a name="print-function"></a>Print-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "print" rechts
  
### <a name="comment-function"></a>Kommentar-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "Kommentar" rechts
  
### <a name="reply-function"></a>Antwort-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "Antworten" rechts
  
### <a name="replyall-function"></a>ReplyAll-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "allen Antworten" rechts
  
### <a name="forward-function"></a>Forward-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "forward" rechts
  
### <a name="emailrights-function"></a>EmailRights-Funktion
Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.

  
**Gibt**: Eine Liste der Rechte, die auf die e-Mails angewendet werden soll.
  
### <a name="editabledocumentrights-function"></a>EditableDocumentRights-Funktion
Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.

  
**Gibt**: Eine Liste der Rechte, die auf Dokumente angewendet werden soll.
  
### <a name="commonrights-function"></a>CommonRights-Funktion
Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.

  
**Gibt**: Eine Liste der Rechte, die in allen Szenarien angewendet werden soll.


## <a name="namespace-miproles"></a>Namespace mip::roles

### <a name="viewer-function"></a>Viewer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

  
**Gibt**: Zeichenfolgenbezeichner für "Viewer" Rolle einen Viewer kann den Inhalt nur anzeigen. Sie können die Inhalte nicht bearbeiten, kopieren oder drucken.
  
### <a name="reviewer-function"></a>Prüfer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.

  
**Gibt**: Zeichenfolgen Sie-ID für "Prüfer"-Rolle ein Reviewer kann anzeigen und bearbeiten Sie den Inhalt. Ein Prüfer kann die Inhalte nicht kopieren oder drucken.
  
### <a name="author-function"></a>Author-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.

  
**Gibt**: Zeichenfolgenbezeichner für 'Author'-Rolle ein Autor anzeigen, bearbeiten, kopieren und Drucken des Inhalts.
  
### <a name="coowner-function"></a>CoOwner-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

  
**Gibt**: Zeichenfolgenbezeichner für "CO-Owner" Rolle Mitbesitzer verfügt über alle Berechtigungen