---
title: Funktionen
description: Funktionen
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 01/28/2019
ms.author: bryanla
ms.openlocfilehash: ab176e53547ebb773b7cf8b3933fddfc1566d62b
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651189"
---
# <a name="functions"></a>Funktionen

## <a name="summary"></a>Zusammenfassung

| Funktionen von Namespace-Gültigkeitsbereich   | Beschreibungen                                |
|--------------------------------|---------------------------------------------|
**Namespace `mip` :** |
Public Std:: String GetAssignmentMethodString (AssignmentMethod-Methode)       |  AssignmentMethod-Enumeration, der eine zeichenfolgenbeschreibung konvertiert.
public static std::string GetActionSourceString(ActionSource actionSource)       |  Ruft den Namen der Aktion-Quelle.
public static std::string GetContentStateString(mip::ContentState state)       |  Ruft den Namen des Inhaltszustands.
public const std::string& GetCustomSettingPolicyDataName()       |  Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.
public const std::string& GetCustomSettingExportPolicyFileName()       |  Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.
public const std::string& GetCustomSettingSensitivityTypesDataName()       |  Der Name der Einstellung, um die Vertraulichkeit von Daten explizit angeben.
public const std::string& GetCustomSettingPolicyDataFile()       |  Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.
public const std::string& GetCustomSettingSensitivityTypesDataFile()       |  Der Name der Einstellung, um die Vertraulichkeit Datendateipfad für Typen explizit angeben.
Öffentliche MIP_API "void" __CDECL ReleaseAllResources()       |  Gibt alle Ressourcen (z.B. Threads) vor dem Herunterfahren frei
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const Std:: shared_ptr\<std::istream\>& StdIStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const Std:: shared_ptr\<std::ostream\>& StdOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const Std:: shared_ptr\<std::iostream\>& StdIOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.
Öffentliche MIP_API Std:: shared_ptr\<mip::Stream\> CreateStreamFromBuffer (Puffer uint8_t *, const int64_t Größe)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.
 | 
**Namespace `mip::auditmetadatakeys` :** |
Public Std:: String Sender()       |  Überwachen Sie die Metadatenschlüssel in eine Zeichenfolgendarstellung.
Public Std:: String Recipients()       | _Noch nicht dokumentiert._
Public Std:: String LastModifiedBy()       | _Noch nicht dokumentiert._
public std::string LastModifiedDate()       | _Noch nicht dokumentiert._
 | 
**Namespace `mip::rights` :** |
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
 | 
**Namespace `mip::roles` :** |
public std::string Viewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.
public std::string Reviewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.
public std::string Author()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.
public std::string CoOwner()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.



## <a name="namespace-mip"></a>Namespace `mip`

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
  
### <a name="getcontentstatestring-function"></a>GetContentStateString-Funktion
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
  
### <a name="releaseallresources-function"></a>ReleaseAllResources-Funktion
Gibt alle Ressourcen (z.B. Threads) vor dem Herunterfahren frei
Wenn dynamische MIP-Bibliotheken verzögert von einer Anwendung geladen werden, muss diese Funktion aufgerufen werden, bevor die Anwendung diese Bibliotheken explizit entlädt, um Deadlocks zu vermeiden. Auf win32 muss z. B. diese Funktion aufgerufen werden, bevor Aufrufe an explizit über FreeLibrary oder __FUnloadDelayLoadedDLL2 MIP-DLLs entladen. Anwendungen müssen vor dem Aufruf dieser Funktion Verweise auf sämtliche MIP-Objekte freigeben (z.B. Profile, Engines und Handler).
  
### <a name="operator-function"></a>Operator | Funktion
ProtectionHandlerCreationOptions ist bitweiser OR-Operator.

Parameter:  
* **a**: Linker Wert 


* **b**: Rechter Wert



  
**Gibt**: Bitweise OR von ProtectionHandlerCreationOptions
  
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
  



## <a name="namespace-mipauditmetadatakeys"></a>Namespace `mip::auditmetadatakeys`

### <a name="sender-function"></a>Sender-Funktion
Überwachen Sie die Metadatenschlüssel in eine Zeichenfolgendarstellung.
  
### <a name="recipients-function"></a>Empfänger-Funktion
_Noch nicht dokumentiert._

  
### <a name="lastmodifiedby-function"></a>LastModifiedBy-Funktion
_Noch nicht dokumentiert._
  
### <a name="lastmodifieddate-function"></a>LastModifiedDate & lt; Funktion
_Noch nicht dokumentiert._





## <a name="namespace-miprights"></a>Namespace `mip::rights`

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




## <a name="namespace-miproles"></a>Namespace `mip::roles`

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
