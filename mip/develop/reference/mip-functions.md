---
title: Funktionen
description: Funktionen
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3bb9cd594022085c24c45bde428cb11f6734caab
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446514"
---
# <a name="functions"></a>Funktionen

| Funktionen (Bereich)              | Beschreibungen                                |
|--------------------------------|---------------------------------------------|
**common** |
public const std::string& GetCustomSettingPolicyDataName()       |  Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.
public const std::string& GetCustomSettingExportPolicyFileName()       |  Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.
public const std::string& GetCustomSettingPolicyDataFile()       |  Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.
 **mip-Funktionen** |
public std::shared_ptr<mip::Stream> CreateStreamFromBuffer(uint8_t* buffer, const int64_t size)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::iostream>& stdIOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::istream>& stdIStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::ostream>& stdOStream)       |  Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.
public void ReleaseAllResources()       |  Gibt alle Ressourcen (z.B. Threads) vor dem Herunterfahren frei
**mip::Rights functions**|
public std::string AuditedExtract()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.
public std::string Comment()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.
public std::vector<std::string> CommonRights()       |  Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.
public std::string Edit()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.
public std::vector<std::string> EditableDocumentRights()       |  Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.
public std::vector<std::string> EmailRights()       |  Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.
public std::string Export()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.
public std::string Extract()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.
public std::string Forward()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.
public std::string Owner()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.
public std::string Print()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.
public std::string Reply()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.
public std::string ReplyAll()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.
public std::string View()       |  Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.
**mip::Roles functions**|
public std::string Author()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.
public std::string CoOwner()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.
public std::string Reviewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.
public std::string Viewer()       |  Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

  
## <a name="functions-common"></a>Funktionen (allgemein)

### <a name="getcustomsettingpolicydataname"></a>GetCustomSettingPolicyDataName
Name der Einstellung, mit der explizit Richtliniendaten angegeben wird.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingexportpolicyfilename"></a>GetCustomSettingExportPolicyFileName
Name der Einstellung, mit der explizit der Dateipfad angegeben wird, in den SCC-Richtliniendaten exportiert werden sollen.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel
  
### <a name="getcustomsettingpolicydatafile"></a>GetCustomSettingPolicyDataFile
Name der Einstellung, mit der explizit der Pfad für Richtliniendatendateien angegeben wird.

  
**Rückgabe**: der benutzerdefinierte Einstellungsschlüssel

## <a name="functions-mip"></a>Funktionen (mip)

### <a name="mipcreatestreamfrombufferbuffer"></a>mip::CreateStreamFromBuffer(buffer)

Erstellt einen [Stream](class_mip_stream.md) aus einem Puffer.

Parameter:  
* **buffer**: Zeiger auf einen Puffer

**Rückgabe**: **Größe** des Puffers
  

### <a name="mipcreatestreamfromstdstreamistream"></a>mip::CreateStreamFromStdStream(istream)

Erstellt einen [Stream](class_mip_stream.md) aus einem std::istream.

Parameter:  

* **stdIStream**: Schützt std::istream
  
**Rückgabe**: ein [Stream](class_mip_stream.md), der einen std::istream umschließt
  
### <a name="mipcreatestreamfromstdstreamiostream"></a>mip::CreateStreamFromStdStream(iostream)

Erstellt einen [Stream](class_mip_stream.md) aus einem std::iostream.

Parameter:  
* **stdIOStream**: Schützt std::iostream
  
**Rückgabe**: ein [Stream](class_mip_stream.md), der einen std::iostream umschließt
  
### <a name="mipcreatestreamfromstdstreamostream"></a>mip::CreateStreamFromStdStream(ostream)

Erstellt einen [Stream](class_mip_stream.md) aus einem std::ostream.

Parameter:  
* **stdOStream**: Schützt std::ostream
  
**Rückgabe**: ein [Stream](class_mip_stream.md), der einen std::ostream umschließt
  
### <a name="mipreleaseallresources"></a>mip::ReleaseAllResources

Gibt alle Ressourcen (z.B. Threads) vor dem Herunterfahren frei  

Wenn dynamische MIP-Bibliotheken verzögert von einer Anwendung geladen werden, muss diese Funktion aufgerufen werden, bevor die Anwendung diese Bibliotheken explizit entlädt, um Deadlocks zu vermeiden. Unter win32 muss diese Funktion beispielsweise aufgerufen werden, bevor weitere Aufrufe durchgeführt werden, damit MIP-DLLs explizit über FreeLibrary oder \__FUnloadDelayLoadedDLL2 entladen werden können. Anwendungen müssen vor dem Aufruf dieser Funktion Verweise auf sämtliche MIP-Objekte freigeben (z.B. Profile, Engines und Handler).

## <a name="functions-miprights"></a>Funktionen (mip::rights)

### <a name="owner"></a>Besitzer
Ruft den Zeichenfolgenbezeichner für die Berechtigung „owner“ (Besitzer) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „owner“
  
### <a name="auditedextract"></a>AuditedExtract
Ruft den Zeichenfolgenbezeichner für die Berechtigung „audited extract“ (überwachtes Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „audited extract“
  
### <a name="comment"></a>Anmerkungen
Ruft den Zeichenfolgenbezeichner für die Berechtigung „comment“ (Kommentieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „comment“
  
### <a name="commonrights"></a>CommonRights
Ruft eine Liste der Berechtigungen ab, die für alle Szenarien gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für alle Szenarien gelten

### <a name="edit"></a>Bearbeiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „edit“ (Bearbeiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „edit“
  
### <a name="editabledocumentrights"></a>EditableDocumentRights
Ruft eine Liste der Berechtigungen ab, die für Dokumente gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für Dokumente gelten
  
### <a name="emailrights"></a>EmailRights
Ruft eine Liste der Berechtigungen ab, die für E-Mails gelten.

  
**Rückgabe**: eine Liste der Berechtigungen, die für E-Mails gelten
  
### <a name="export"></a>Exportieren
Ruft den Zeichenfolgenbezeichner für die Berechtigung „export“ (Exportieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „export“
  
### <a name="extract"></a>Extrahieren
Ruft den Zeichenfolgenbezeichner für die Berechtigung „extract“ (Extrahieren) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „extract“
  
### <a name="forward"></a>Weiterleiten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „forward“ (Weiterleiten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „forward“
  
### <a name="print"></a>Drucken
Ruft den Zeichenfolgenbezeichner für die Berechtigung „print“ (Drucken) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „print“
  
### <a name="reply"></a>Antworten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply“ (Antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply“
  
### <a name="replyall"></a>Allen antworten
Ruft den Zeichenfolgenbezeichner für die Berechtigung „reply all“ (Allen antworten) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „reply all“
  
### <a name="view"></a>Anzeigen
Ruft den Zeichenfolgenbezeichner für die Berechtigung „view“ (Anzeigen) ab.

  
**Rückgabe**: Zeichenfolgenbezeichner für die Berechtigung „view“
  

## <a name="functions-miproles"></a>Funktionen (mip::roles)

### <a name="author"></a>Autor
Ruft den Zeichenfolgenbezeichner für die Rolle „author“ (Autor) ab.

Autoren können den Inhalt abrufen, bearbeiten, kopieren und drucken.
  
**Rückgabe:** Zeichenfolgenbezeichner für die Rolle „Autor“
  
### <a name="coowner"></a>CoOwner
Ruft den Zeichenfolgenbezeichner für die Rolle „co-owner“ (Mitbesitzer) ab.

Mitbesitzer haben sämtliche Berechtigungen
  
**Rückgabe:** Zeichenfolgenbezeichner für die Rolle „Mitbesitzer“

### <a name="reviewer"></a>Prüfer
Ruft den Zeichenfolgenbezeichner für die Rolle „reviewer“ (Prüfer) ab.

Prüfer können den Inhalt abrufen und bearbeiten Ein Prüfer kann die Inhalte nicht kopieren oder drucken.
  
**Rückgabe:** Zeichenfolgenbezeichner für die Rolle „Prüfer“
  
### <a name="viewer"></a>Anzeigender Benutzer
Ruft den Zeichenfolgenbezeichner für die Rolle „viewer“ (Anzeigen) ab.

Betrachter können den Inhalt nur abrufen. Sie können die Inhalte nicht bearbeiten, kopieren oder drucken.
  
**Rückgabe:** Zeichenfolgenbezeichner für die Rolle „Betrachter“
  
