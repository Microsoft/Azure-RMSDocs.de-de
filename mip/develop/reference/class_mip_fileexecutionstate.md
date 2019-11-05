---
title: 'MIP:: fileexecutionstate-Klasse'
description: 'Dokumentiert die MIP:: fileexecutionstate-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 063f1b0227415dc413e0c56d26f60fc39274a817
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560238"
---
# <a name="class-mipfileexecutionstate"></a>MIP:: fileexecutionstate-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual datastate getdatastate () Konstanten  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
public virtual Std:: shared_ptr\<classificationresults\> getclassificationresults (Konst Std:: shared_ptr\<fileHandler\> &, Konstanten Std:: Vector\<Std:: shared_ptr\<classificationrequest\>\> &) konstant  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual Std:: Map\<Std:: String, Std:: String\> getauditmetadata () Konstanten  |  Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.
  
## <a name="members"></a>Member
  
### <a name="getdatastate-function"></a>Getdatastate-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Rückgabe:** Status der Inhaltsdaten
  
### <a name="getclassificationresults-function"></a>Getclassificationresults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **fileHandler**: der Datei Handler der verwendeten Datei. 


* **classificationids**: eine Liste der Klassifizierungs-IDs. 



  
**Returns**: eine Liste der Klassifizierungs Ergebnisse.
  
### <a name="getauditmetadata-function"></a>Getauditmetadata-Funktion
Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.

  
**Gibt Folgendes zurück**: eine Liste von anwendungsspezifischen Überwachungs Metadaten registrierter Schlüssel: Wert Paare Absender: e-Mail-ID für Absender Empfänger: stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy: e-Mail-ID für den Benutzer dar, der den Inhalt zuletzt geändert hat. LastModifiedDate: Datum, an dem der Inhalt zuletzt geändert wurde