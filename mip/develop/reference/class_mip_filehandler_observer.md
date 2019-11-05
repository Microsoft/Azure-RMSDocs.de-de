---
title: mip::FileHandler::Observer-Klasse
description: 'Dokumentiert die MIP:: fileHandler-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: d1c1a66ce3821bf3d552ee0daa0648940b645fcb
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560263"
---
# <a name="class-mipfilehandlerobserver"></a>mip::FileHandler::Observer-Klasse 
Beobachter Schnittstelle für Clients zum erhalten von Benachrichtigungs Ereignissen im Zusammenhang mit dem Datei Handler.
Alle Fehler erben von MIP:: Error. Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onkreatefilehandlersuccess (Konstante Std:: shared_ptr\<fileHandler\>& fileHandler, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
public virtual void onkreatefilehandlerfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
public virtual void onclassifysuccess (konstant Std:: Vector\<Std:: shared_ptr\<Action\>\>& Actions, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird beim Klassifizieren von Erfolg aufgerufen.
public virtual void onclassifyfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn eine Klassifizierung fehlgeschlagen
public virtual void ongetdecryptedtemporaryfilesuccess (Konstante Std:: String & decryptedfilepath, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die entschlüsselte temporäre Datei erfolgreich abgerufen wird.
public virtual void ongetdecryptedtemporaryfilefailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die entschlüsselte temporäre Datei nicht abgerufen werden konnte.
public virtual void ongetdecryptedtemporarystreamsuccess (konstant Std:: shared_ptr\<Stream\>& decryptedstream, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn der entschlüsselte temporäre Stream erfolgreich abgerufen wurde.
public virtual void ongetdecryptedtemporarystreamfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn der entschlüsselte temporäre Stream abgerufen wurde.
öffentliches virtuelles void-oncommitsuccess (boolcommit, Konst Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
public virtual void oncommitfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt
public virtual void oninspectsuccess (konstant Std:: shared_ptr\<fileinspector\>& fileinspector, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Erfolg überprüfen.
public virtual void oninspectfailure (konstant Std:: exception_ptr & Error, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn bei der Überprüfung
  
## <a name="members"></a>Member
  
### <a name="oncreatefilehandlersuccess-function"></a>Onkreatefilehandlersuccess-Funktion
Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
  
### <a name="oncreatefilehandlerfailure-function"></a>Onkreatefilehandlerfailure-Funktion
Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
  
### <a name="onclassifysuccess-function"></a>Onclassifysuccess-Funktion
Wird beim Klassifizieren von Erfolg aufgerufen.
  
### <a name="onclassifyfailure-function"></a>Onclassifyfailure-Funktion
Wird aufgerufen, wenn eine Klassifizierung fehlgeschlagen
  
### <a name="ongetdecryptedtemporaryfilesuccess-function"></a>Ongetdecryptedtemporaryfilesuccess-Funktion
Wird aufgerufen, wenn die entschlüsselte temporäre Datei erfolgreich abgerufen wird.
  
### <a name="ongetdecryptedtemporaryfilefailure-function"></a>Ongetdecryptedtemporaryfilefailure-Funktion
Wird aufgerufen, wenn die entschlüsselte temporäre Datei nicht abgerufen werden konnte.
  
### <a name="ongetdecryptedtemporarystreamsuccess-function"></a>Ongetdecryptedtemporarystreamsuccess-Funktion
Wird aufgerufen, wenn der entschlüsselte temporäre Stream erfolgreich abgerufen wurde.
  
### <a name="ongetdecryptedtemporarystreamfailure-function"></a>Ongetdecryptedtemporarystreamfailure-Funktion
Wird aufgerufen, wenn der entschlüsselte temporäre Stream abgerufen wurde.
  
### <a name="oncommitsuccess-function"></a>Oncommitsuccess-Funktion
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
  
### <a name="oncommitfailure-function"></a>Oncommitfailure-Funktion
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt
  
### <a name="oninspectsuccess-function"></a>Oninspectsuccess-Funktion
Wird aufgerufen, wenn Erfolg überprüfen.
  
### <a name="oninspectfailure-function"></a>Oninspectfailure-Funktion
Wird aufgerufen, wenn bei der Überprüfung