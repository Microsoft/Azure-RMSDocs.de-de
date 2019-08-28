---
title: 'MIP:: fileexecutionstate-Klasse'
description: 'Dokumentiert die MIP:: fileexecutionstate-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: d6159bf22bf1c887ed74232472163f74440c2051
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056046"
---
# <a name="class-mipfileexecutionstate"></a>MIP:: fileexecutionstate-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual datastate getdatastate () Konstanten  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
public virtual Std:: shared_ptr\<classificationresults\> getclassificationresults (Konst Std:: shared_ptr\<fileHandler\> &, Konstanten Std:: Vector\<Std:: shared_ptr\<Classificationrequest\> \> &) konstant  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual Std:: map\<Std:: String, Std:: String\> getauditmetadata () Konstanten  |  Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.
  
## <a name="members"></a>Member
  
### <a name="getdatastate-function"></a>Getdatastate-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Gibt Folgendes zurück**: Zustand der Inhaltsdaten
  
### <a name="getclassificationresults-function"></a>Getclassificationresults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **fileHandler**: der Datei Handler der verwendeten Datei. 


* **classificationids**: eine Liste der Klassifizierungs-IDs. 



  
**Gibt Folgendes zurück**: Eine Liste der Klassifizierungs Ergebnisse.
  
### <a name="getauditmetadata-function"></a>Getauditmetadata-Funktion
Gibt eine Zuordnung von anwendungsspezifischen Überwachungs Schlüssel-Wert-Paaren zurück.

  
**Gibt Folgendes zurück**: Eine Liste von anwendungsspezifischen Überwachungs Metadaten registrierter Schlüssel: Wert Paare Absender: E-Mail-ID für die Absender Empfänger: Stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy dar: E-Mail-ID für den Benutzer, der den Inhalt LastModifiedDate zuletzt geändert hat: Datum, an dem der Inhalt zuletzt geändert wurde