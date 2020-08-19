---
title: Klassen
description: Functions
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.date: 01/28/2019
ms.author: mbaldwin
ms.openlocfilehash: 73c56e5a5e2facf31eeadd59b36197dea8bbecc2
ms.sourcegitcommit: dc50f9a6c2f66544893278a7fd16dff38eef88c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88563704"
---
# <a name="functions-c"></a>Funktionen (C++) 

## <a name="namespace-mip"></a>Namespace MIP

| Funktionen nach Namespace-Gültigkeitsbereich   | Beschreibungen                                |
|--------------------------------|---------------------------------------------|
Public Std:: String getaccessmentmethodstring (zuder Methode Method)       |  Konvertiert die zuder zuder zuder zuder Methode in eine Zeichen folgen Beschreibung
public static Std:: String getaktionsourcestring (Aktions Quelle Aktions Quelle)       |  Der Name der Aktions Quelle wird angezeigt.
public static Std:: String getdatastatestring (MIP::D atastate-Status)       |  Den Namen des Inhalts Zustands erhalten.
public const std::string& GetCustomSettingPolicyDataName()       |  Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.
public const std::string& GetCustomSettingExportPolicyFileName()       |  Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.
Public Konstanten Std:: String& getcustomsettingsensitivitytypesdataname ()       |  Der Name der Einstellung, um die Vertraulichkeits Daten explizit anzugeben.
public const std::string& GetCustomSettingPolicyDataFile()       |  Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.
Public Konstanten Std:: String& getcustomsettingsensitivitytypesdatafile ()       |  Der Name der Einstellung, um den Datendatei Pfad für sensible Typen explizit anzugeben.
Public Konstanten Std:: String& getcustomsettinglabelcustompropertiessyncenabled ()       |  Der Name der Einstellung, die das Aktivieren der Bezeichnung durch benutzerdefinierte Eigenschaften und benutzerdefinierte Eigenschaften durch Bezeichnungs Features ermöglicht.
Public Konstanten Std:: String& getcustomsettingpolicyttldays ()       |  Der Name der Einstellung, die das Überschreiben der Richtlinie für die Gültigkeitsdauer der Gültigkeitsdauer in Tagen aktiviert. Werte sollten als Zeichen folgen Integer festgelegt werden, < 0 bedeutet unbegrenzte Gültigkeitsdauer.
Public Konstanten Std:: String& getcustomsettingsensitivitypolicyttldays ()       |  Der Name der Einstellung, die das außer Kraft setzen der Gültigkeitsdauer Gültigkeitsdauer der Gültigkeitsdauer der Gültigkeitsdauer (TTL) Werte sollten als Zeichen folgen Integer festgelegt werden, < 0 bedeutet unbegrenzte Gültigkeitsdauer.
Public Konstanten Std:: map- \<FlightingFeature, bool\>& getdefaultfeaturesettings ()       |  Ruft ab, ob eine Funktion standardmäßig aktiviert ist.
Public MIP_API Std:: shared_ptr \<mip::Stream\> kreatestreamfromstdstream (konstant Std:: shared_ptr \<std::istream\>& stdistream)       |  Erstellt einen Stream aus einem std::istream.
Public MIP_API Std:: shared_ptr " \<mip::Stream\> kreatestreamfromstdstream" (konstant Std:: shared_ptr \<std::ostream\>& stdostream)       |  Erstellt einen Stream aus einem std::ostream.
Public MIP_API Std:: shared_ptr \<mip::Stream\> kreatestreamfromstdstream (konstant Std:: shared_ptr \<std::iostream\>& stdiostream)       |  Erstellt einen Stream aus einem std::iostream.
Public MIP_API Std:: shared_ptr \<mip::Stream\> kreatestreamfrombuffer (uint8_t * Puffer, Konstante int64_t Größe)       |  Erstellt einen Stream aus einem Puffer.
öffentliches MIP_API Std:: Vector Read \<uint8_t\> FromStream (Konstanten Std:: shared_ptr \<mip::Stream\>& Stream)       |  Liest alle Bytes des Streams.
öffentlicher Aktionstyp-Operator& (Aktionstyp a, Aktionstyp b)       |  Und (&)-Operator für Aktionstyp-Enum.
Public-Aktionstyp Operator ^ (Aktionstyp a, Aktionstyp b)       |  XOR-Operator (^) für eine Enumeration vom Typ Action

### <a name="getassignmentmethodstring-function"></a>Getbelegmentmethodstring-Funktion
Konvertiert die zuder zuder zuder zuder Methode in eine Zeichen folgen Beschreibung

Parameter:  
* **method**: eine Zuweisungs Methode. 


**Returns**: eine Zeichen folgen Beschreibung der Zuweisungs Methode.
  
### <a name="getactionsourcestring-function"></a>Getaktionsourcestring-Funktion
Der Name der Aktions Quelle wird angezeigt.

Parameter:  
* **Action Source**: die Aktions Quelle. 

**Returns**: eine Zeichen folgen Darstellung der Aktions Quelle.
  
### <a name="getdatastatestring-function"></a>Getdatastatestring-Funktion
Den Namen des Inhalts Zustands erhalten.

Parameter:  
* **Aktions Quelle**: der Zustand des Inhalts, an dem gearbeitet wird. 



  
**Returns**: eine Zeichen folgen Darstellung des Inhalts Zustands.
  
### <a name="getcustomsettingpolicydataname-function"></a>Getcustomsettingpolicydataname-Funktion
Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingexportpolicyfilename-function"></a>Getcustomsettingexportpolicyfilename-Funktion
Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingsensitivitytypesdataname-function"></a>Getcustomsettingsensitivitytypesdataname-Funktion
Der Name der Einstellung, um die Vertraulichkeits Daten explizit anzugeben.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingpolicydatafile-function"></a>Getcustomsettingpolicydatafile-Funktion
Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingsensitivitytypesdatafile-function"></a>Getcustomsettingsensitivitytypesdatafile-Funktion
Der Name der Einstellung, um den Datendatei Pfad für sensible Typen explizit anzugeben.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettinglabelcustompropertiessyncenabled-function"></a>Getcustomsettinglabelcustompropertiessyncenabled-Funktion
Der Name der Einstellung, die das Aktivieren der Bezeichnung durch benutzerdefinierte Eigenschaften und benutzerdefinierte Eigenschaften durch Bezeichnungs Features ermöglicht.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingpolicyttldays-function"></a>Getcustomsettingpolicyttldays-Funktion
Der Name der Einstellung, die das Überschreiben der Richtlinie für die Gültigkeitsdauer der Gültigkeitsdauer in Tagen aktiviert. Werte sollten als Zeichen folgen Integer festgelegt werden, < 0 bedeutet unbegrenzte Gültigkeitsdauer.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingsensitivitypolicyttldays-function"></a>Getcustomsettingsensitivitypolicyttldays-Funktion
Der Name der Einstellung, die das außer Kraft setzen der Gültigkeitsdauer Gültigkeitsdauer der Gültigkeitsdauer der Gültigkeitsdauer (TTL) Werte sollten als Zeichen folgen Integer festgelegt werden, < 0 bedeutet unbegrenzte Gültigkeitsdauer.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getdefaultfeaturesettings-function"></a>Getdefaultfeaturesettings-Funktion
Ruft ab, ob eine Funktion standardmäßig aktiviert ist.

  
**Returns**: Standardstatus der flighting-Funktionen
  
### <a name="createstreamfromstdstream-function"></a>Funktion "deestreamfromstdstream"
Erstellt einen Stream aus einem std::istream.

Parameter:  
* **stdIStream**: Schützt std::istream



  
**Gibt Folgendes zurück**: Stream Wrapping eines Std:: IStream
  
### <a name="createstreamfromstdstream-function"></a>Funktion "deestreamfromstdstream"
Erstellt einen Stream aus einem std::ostream.

Parameter:  
* **stdOStream**: Schützt std::ostream



  
**Gibt Folgendes zurück**: Stream Wrapping eines Std:: ostream
  
### <a name="createstreamfromstdstream-function"></a>Funktion "deestreamfromstdstream"
Erstellt einen Stream aus einem std::iostream.

Parameter:  
* **stdIOStream**: Schützt std::iostream



  
**Gibt Folgendes zurück**: Stream Wrapping von "Std:: iostream"
  
### <a name="createstreamfrombuffer-function"></a>Funktion "kreatestreamfrombuffer"
Erstellt einen Stream aus einem Puffer.

Parameter:  
* **buffer**: Zeiger auf einen Puffer



  
**Rückgabe**: Größe des Puffers
  
### <a name="readfromstream-function"></a>Read FromStream-Funktion
Liest alle Bytes des Streams.

Parameter:  
* **Zeiger**: auf einen Stream.



  
**Gibt Folgendes zurück**: ein Vektor von Bytes.
  
### <a name="operator-function"></a>Operator | Funktion
OR-Operator (|) für eine Enumeration vom Typ Action
  
### <a name="operator-function"></a>Operator&-Funktion
Und (&)-Operator für Aktionstyp-Enum.
  
### <a name="operator-function"></a>Operator ^-Funktion
XOR-Operator (^) für eine Enumeration vom Typ Action

## <a name="namespace-mipauditmetadatakeys"></a>Namespace MIP:: auditmetadatakeys

Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String Sender ()       |  Überwachen von metadatenschlüsseln in der Zeichen folgen Darstellung.
Public Std:: String-Empfänger ()       | _Noch nicht dokumentiert._
Public Std:: String LastModifiedBy ()       | _Noch nicht dokumentiert._
Public Std:: String LastModifiedDate ()       | _Noch nicht dokumentiert._
  
### <a name="sender-function"></a>Sender-Funktion
Überwachen von metadatenschlüsseln in der Zeichen folgen Darstellung.
  
### <a name="recipients-function"></a>Empfänger Funktion
_Noch nicht dokumentiert._

  
### <a name="lastmodifiedby-function"></a>LastModifiedBy-Funktion
_Noch nicht dokumentiert._

  
### <a name="lastmodifieddate-function"></a>LastModifiedDate-Funktion
_Noch nicht dokumentiert._


## <a name="namespace-miprights"></a>Namespace `mip::rights` 
  
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
Public Std:: Vector \<std::string\> emailrights ()       |  Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.
Public Std:: Vector \<std::string\> editabledocumentrights ()       |  Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.
Public Std:: Vector \<std::string\> commonrights ()       |  Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.
  
### <a name="owner-function"></a>Owner-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „owner“
  
### <a name="view-function"></a>View-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „view“
  
### <a name="auditedextract-function"></a>Auditedextract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „audited extract“
  
### <a name="edit-function"></a>Funktion Bearbeiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „edit“
  
### <a name="export-function"></a>Export-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „export“
  
### <a name="extract-function"></a>Extract-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „extract“
  
### <a name="print-function"></a>Print-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „print“
  
### <a name="comment-function"></a>Comment-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „comment“
  
### <a name="reply-function"></a>Reply-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply“
  
### <a name="replyall-function"></a>ReplyAll-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply all“
  
### <a name="forward-function"></a>Forward-Funktion
Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „forward“
  
### <a name="emailrights-function"></a>Emailrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für E-Mails gelten
  
### <a name="editabledocumentrights-function"></a>Editabledocumentrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für Dokumente gelten
  
### <a name="commonrights-function"></a>Commonrights-Funktion
Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für alle Szenarien gelten

## <a name="namespace-miproles"></a>Namespace `mip::roles` 
  
Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string Viewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.
public std::string Reviewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.
public std::string Author()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.
public std::string CoOwner()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.
  
### <a name="viewer-function"></a>Viewer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „viewer“. Benutzer mit der Rolle „viewer“ können Inhalte nur anzeigen. Sie können die Inhalte nicht bearbeiten, kopieren oder drucken.
  
### <a name="reviewer-function"></a>Reviewer-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „reviewer“. Ein Prüfer kann Inhalte anzeigen und bearbeiten. Ein Prüfer kann die Inhalte nicht kopieren oder drucken.
  
### <a name="author-function"></a>Author-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „author“. Ein Autor kann Inhalte anzeigen, bearbeiten, kopieren und drucken.
  
### <a name="coowner-function"></a>Coowner-Funktion
Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Rolle „Mitbesitzer“. Ein Mitbesitzer verfügt über alle Berechtigungen.
