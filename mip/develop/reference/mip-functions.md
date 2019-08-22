---
title: Funktionen
description: Funktionen
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.date: 01/28/2019
ms.author: mbaldwin
ms.openlocfilehash: 80d13de3778648c2e0230ac37c559b0ca1f62a07
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69882799"
---
# <a name="functions"></a>Funktionen

## <a name="summary"></a>Zusammenfassung 

### <a name="namespace-mip"></a>Namespace MIP
| Funktionen nach Namespace-Gültigkeitsbereich   | Beschreibungen                                |
|--------------------------------|---------------------------------------------|
Public Std:: String getaccessmentmethodstring (zuder Methode Method)       |  Konvertiert die zuder zuder zuder zuder Methode in eine Zeichen folgen Beschreibung
public static Std:: String getaktionsourcestring (Aktions Quelle Aktions Quelle)       |  Der Name der Aktions Quelle wird angezeigt.
public static Std:: String getdatastatestring (MIP::D atastate-Status)       |  Den Namen des Inhalts Zustands erhalten.
public const std::string& GetCustomSettingPolicyDataName()       |  Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.
public const std::string& GetCustomSettingExportPolicyFileName()       |  Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.
Public Konstanten Std:: String & getcustomsettingsensitivitytypesdataname ()       |  Der Name der Einstellung, um die Vertraulichkeits Daten explizit anzugeben.
public const std::string& GetCustomSettingPolicyDataFile()       |  Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.
Public Konstanten Std:: String & getcustomsettingsensitivitytypesdatafile ()       |  Der Name der Einstellung, um den Datendatei Pfad für sensible Typen explizit anzugeben.
Public Konstanten Std:: String & getcustomsettinglabelcustompropertiessyncenabled ()       |  Der Name der Einstellung, die das Aktivieren der Bezeichnung durch benutzerdefinierte Eigenschaften und benutzerdefinierte Eigenschaften durch Bezeichnungs Features ermöglicht.
Public Konstanten Std:: map\<flightingfeature, bool\>& getdefaultfeaturesettings ()       |  Ruft ab, ob eine Funktion standardmäßig aktiviert ist.
Public MIP_API void __CDECL ReleaseAllResources ()       |  Gibt alle Ressourcen (Threads usw.) vor dem Herunterfahren frei.
Public MIP_API Std:: shared_ptr\<MIP:: Stream\> "kreatestreamfromstdstream" (konstant Std::\<shared_ptr Std:: IStream\>& stdistream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.
Public MIP_API Std:: shared_ptr\<MIP:: Stream\> "kreatestreamfromstdstream" (konstant Std::\<shared_ptr Std:: ostream\>& stdostream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.
Public MIP_API Std:: shared_ptr\<MIP:: Stream\> "kreatestreamfromstdstream" (Konstante Std::\<shared_ptr Std:: iostream\>& stdiostream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.
Public MIP_API Std:: shared_ptr\<MIP:: Stream\> "kreatestreamfrombuffer" (uint8_t * Puffer, Konstante int64_t Größe)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.
Public MIP_API Std:: Vector\<uint8_t\> Read FromStream (Konstante Std:: shared_ptr\<MIP:: Stream\>& Stream)       |  Liest alle Bytes des Streams.

### <a name="namespace-mipauditmetadatakeys"></a>Namespace MIP:: auditmetadatakeys
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String Sender ()       |  Überwachen von metadatenschlüsseln in der Zeichen folgen Darstellung.
Public Std:: String-Empfänger ()       | _Noch nicht dokumentiert._
Public Std:: String LastModifiedBy ()       | _Noch nicht dokumentiert._
Public Std:: String LastModifiedDate ()       | _Noch nicht dokumentiert._


### <a name="namespace-miprights"></a>Namespace MIP:: Rights

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

### <a name="namespace-miproles"></a>Namespace MIP:: Rollen

 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string Viewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.
public std::string Reviewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.
public std::string Author()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.
public std::string CoOwner()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

## <a name="namespace-mip"></a>Namespace MIP

### <a name="getassignmentmethodstring-function"></a>Getbelegmentmethodstring-Funktion
Konvertiert die zuder zuder zuder zuder Methode in eine Zeichen folgen Beschreibung

Parameter:  
* **method**: eine Zuweisungs Methode. 



  
**Gibt Folgendes zurück**: Eine Zeichen folgen Beschreibung der Zuweisungs Methode.
  
### <a name="getactionsourcestring-function"></a>Getaktionsourcestring-Funktion
Der Name der Aktions Quelle wird angezeigt.

Parameter:  
* **actionSource**: Die Aktions Quelle. 



  
**Gibt Folgendes zurück**: Eine Zeichen folgen Darstellung der Aktions Quelle.
  
### <a name="getdatastatestring-function"></a>Getdatastatestring-Funktion
Den Namen des Inhalts Zustands erhalten.

Parameter:  
* **actionSource**: Der Zustand des Inhalts, an dem gearbeitet wird. 



  
**Gibt Folgendes zurück**: Eine Zeichen folgen Darstellung des Inhalts Zustands.
  
### <a name="getcustomsettingpolicydataname-function"></a>Getcustomsettingpolicydataname-Funktion
Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.

  
**Gibt Folgendes zurück**: Der Schlüssel für die benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingexportpolicyfilename-function"></a>Getcustomsettingexportpolicyfilename-Funktion
Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.

  
**Gibt Folgendes zurück**: Der Schlüssel für die benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingsensitivitytypesdataname-function"></a>Getcustomsettingsensitivitytypesdataname-Funktion
Der Name der Einstellung, um die Vertraulichkeits Daten explizit anzugeben.

  
**Gibt Folgendes zurück**: Der Schlüssel für die benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingpolicydatafile-function"></a>Getcustomsettingpolicydatafile-Funktion
Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.

  
**Gibt Folgendes zurück**: Der Schlüssel für die benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingsensitivitytypesdatafile-function"></a>Getcustomsettingsensitivitytypesdatafile-Funktion
Der Name der Einstellung, um den Datendatei Pfad für sensible Typen explizit anzugeben.

  
**Gibt Folgendes zurück**: Der Schlüssel für die benutzerdefinierte Einstellungen.
  
### <a name="getcustomsettingexternallabelsenabled-function"></a>Getcustomsettingexternallabelsenabled-Funktion
Der Name der Einstellung, mit der die Funktion "externe Bezeichnungen" aktiviert werden kann.

  
**Gibt Folgendes zurück**: Der Schlüssel für die benutzerdefinierte Einstellungen.
  
### <a name="releaseallresources-function"></a>ReleaseAllResources-Funktion
Gibt alle Ressourcen (Threads usw.) vor dem Herunterfahren frei.
Diese Funktion muss vor der Beendigung des Prozesses genau einmal aufgerufen werden. Es bietet MIP die Möglichkeit, sich selbst zu initialisieren, wenn die abhängigen Bibliotheken weiterhin geladen sind und der Thread Beitritt weiterhin möglich ist. Anwendungen müssen vor dem Aufruf dieser Funktion Verweise auf sämtliche MIP-Objekte freigeben (z.B. Profile, Engines und Handler).
Wenn diese Funktion nicht aufgerufen wird, wird MIP im Rahmen der Standardprozess Löschung natürlich entladen. Auf einigen Plattformen führt dies möglicherweise zu Deadlocks (z. b., wenn Threads nicht in Win32 als Antwort auf das Verarbeiten von Prozessen zusammengeführt werden können) oder Abstürze (z. b. wird die dll-Entlade Reihenfolge für verzögert geladene Bibliotheken in Win32 nicht durch MIP gesteuert, sodass die abhängigen Bibliotheken möglicherweise wurden von dem Zeitpunkt der Ausführung von MIP-Shutdown-Code entladen, was zu ungültigen Lesefehlern führt.
  
### <a name="createstreamfromstdstream-function"></a>Funktion "deestreamfromstdstream"
Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.

Parameter:  
* **stdIStream**: Unterstützen von Std:: IStream



  
**Gibt Folgendes zurück**: [Stream](class_mip_stream.md) Wrapping eines Std:: IStream
  
### <a name="createstreamfromstdstream-function"></a>Funktion "deestreamfromstdstream"
Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.

Parameter:  
* **stdOStream**: Unterstützen von Std:: ostream



  
**Gibt Folgendes zurück**: [Stream](class_mip_stream.md) Wrapping von "Std:: ostream"
  
### <a name="createstreamfromstdstream-function"></a>Funktion "deestreamfromstdstream"
Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.

Parameter:  
* **stdIOStream**: Unterstützen von Std:: iostream



  
**Gibt Folgendes zurück**: [Stream](class_mip_stream.md) Wrapping von "Std:: iostream"
  
### <a name="createstreamfrombuffer-function"></a>Funktion "kreatestreamfrombuffer"
Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.

Parameter:  
* **Puffer**: Zeiger auf einen Puffer



  
**Gibt Folgendes zurück**: Größe des Puffers
  



## <a name="namespace-mipauditmetadatakeys"></a>Namespace MIP:: auditmetadatakeys

### <a name="sender-function"></a>Sender-Funktion
Überwachen von metadatenschlüsseln in der Zeichen folgen Darstellung.
  
### <a name="recipients-function"></a>Empfänger Funktion
_Noch nicht dokumentiert._

  
### <a name="lastmodifiedby-function"></a>LastModifiedBy-Funktion
_Noch nicht dokumentiert._

  
### <a name="lastmodifieddate-function"></a>LastModifiedDate-Funktion
_Noch nicht dokumentiert._






## <a name="namespace-miprights"></a>Namespace MIP:: Rights

### <a name="owner-function"></a>Owner-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für "Owner" Right
  
### <a name="view-function"></a>View-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für "View" Right
  
### <a name="auditedextract-function"></a>Auditedextract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für "überwachter Extract"-Recht
  
### <a name="edit-function"></a>Funktion Bearbeiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für das Recht "Bearbeiten"
  
### <a name="export-function"></a>Export-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für "Export" nach rechts
  
### <a name="extract-function"></a>Extract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für ' Extract ' rechts
  
### <a name="print-function"></a>Print-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für ' Drucken ' rechts
  
### <a name="comment-function"></a>Comment-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für ' Comment ' rechts
  
### <a name="reply-function"></a>Reply-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für ' Reply ' Right
  
### <a name="replyall-function"></a>ReplyAll-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für "allen Antworten" rechts
  
### <a name="forward-function"></a>Forward-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für Forward-right
  
### <a name="emailrights-function"></a>Emailrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.

  
**Gibt Folgendes zurück**: Eine Liste der Rechte, die für e-Mails gelten
  
### <a name="editabledocumentrights-function"></a>Editabledocumentrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.

  
**Gibt Folgendes zurück**: Eine Liste der Rechte, die auf Dokumente angewendet werden.
  
### <a name="commonrights-function"></a>Commonrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.

  
**Gibt Folgendes zurück**: Eine Liste der Rechte, die in allen Szenarien gelten


## <a name="namespace-miproles"></a>Namespace MIP:: Rollen

### <a name="viewer-function"></a>Viewer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für die Rolle "Viewer". ein Viewer kann den Inhalt nur anzeigen. Sie können die Inhalte nicht bearbeiten, kopieren oder drucken.
  
### <a name="reviewer-function"></a>Reviewer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für die Reviewer-Rolle, den der Reviewer anzeigen und bearbeiten kann. Ein Prüfer kann die Inhalte nicht kopieren oder drucken.
  
### <a name="author-function"></a>Author-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für die Rolle "Autor", den ein Autor zum Anzeigen, bearbeiten, kopieren und Drucken des Inhalts hat.
  
### <a name="coowner-function"></a>Coowner-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

  
**Gibt Folgendes zurück**: Zeichen folgen Bezeichner für die Rolle "Mitbesitzer" ein Mitbesitzer verfügt über alle Berechtigungen