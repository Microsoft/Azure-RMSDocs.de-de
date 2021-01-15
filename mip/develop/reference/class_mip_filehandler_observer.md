---
title: 'Class fileHandler:: Observer'
description: 'Dokumentiert die fileHandler:: Observer-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 7cc73d0a81d6a620a411035bb0aae4258794e978
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215288"
---
# <a name="class-filehandlerobserver"></a>Class fileHandler:: Observer 
Observer-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse, die im Zusammenhang mit dem Dateihandler stehen.
Alle Fehler erben von mip::Error. Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnCreateFileHandlerSuccess(const std::shared_ptr\<FileHandler\>& fileHandler, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
public virtual void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
public virtual void onclassifysuccess (Konstante Std:: Vector \<std::shared_ptr\<Action\> \>& Actions, Konstanten Std:: shared_ptr \<void\>& context)  |  Wird beim Klassifizieren von Erfolg aufgerufen.
public virtual void onclassifyfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn eine Klassifizierung fehlgeschlagen
public virtual void ongetdecryptedtemporaryfilesuccess (Konstante Std:: String& decryptedfilepath, Konstanten Std:: shared_ptr \<void\>& Kontext)  |  Wird aufgerufen, wenn die entschlüsselte temporäre Datei erfolgreich abgerufen wird.
öffentliches virtuelles void-ongetdecryptedtemporaryfilefailure (konstant Std:: exception_ptr& Fehler, Konstante Std:: shared_ptr \<void\>& Kontext)  |  Wird aufgerufen, wenn die entschlüsselte temporäre Datei nicht abgerufen werden konnte.
public virtual void ongetdecryptedtemporarystreamsuccess (konstant Std:: shared_ptr \<Stream\>& decryptedstream, Konstante Std:: shared_ptr \<void\>& Kontext)  |  Wird aufgerufen, wenn der entschlüsselte temporäre Stream erfolgreich abgerufen wurde.
public virtual void ongetdecryptedtemporarystreamfailure (Konstante Std:: exception_ptr& Error, Konstante Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn der entschlüsselte temporäre Stream abgerufen wurde.
public virtual void OnCommitSuccess(bool committed, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
public virtual void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt
public virtual void oninspectsuccess (konstant Std:: shared_ptr \<FileInspector\>& fileinspector, Konstanten Std:: shared_ptr \<void\>& Kontext)  |  Wird aufgerufen, wenn Erfolg überprüfen.
public virtual void oninspectfailure (Konstante Std:: exception_ptr& Error, Konstanten Std:: shared_ptr \<void\>& context)  |  Wird aufgerufen, wenn bei der Überprüfung
  
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