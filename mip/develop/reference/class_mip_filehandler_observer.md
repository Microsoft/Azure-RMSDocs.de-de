---
title: mip::FileHandler::Observer-Klasse
description: 'Dokumentiert die MIP:: fileHandler-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 9c550f2d678995a4438f22246d00b383574533fd
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885641"
---
# <a name="class-mipfilehandlerobserver"></a>mip::FileHandler::Observer-Klasse 
[Observer](class_mip_filehandler_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse, die im Zusammenhang mit dem Dateihandler stehen.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void onkreatefilehandlersuccess (Konstante Std::\<shared_ptr fileHandler\>& fileHandler, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
public virtual void onkreatefilehandlerfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
public virtual void onclassifysuccess (Konstante Std:: Vector\<Std:: shared_ptr\>\>\<Action & Actions, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird beim Klassifizieren von Erfolg aufgerufen.
public virtual void onclassifyfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn eine Klassifizierung fehlgeschlagen
public virtual void ongetdecryptedtemporaryfilesuccess (konstant Std:: String & decryptedfilepath, Konstante Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die entschlüsselte temporäre Datei erfolgreich abgerufen wird.
öffentliches virtuelles void-ongetdecryptedtemporaryfilefailure (konstant Std:: exception_ptr & Error, Konstante Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die entschlüsselte temporäre Datei nicht abgerufen werden konnte.
public virtual void ongetdecryptedtemporarystreamsuccess (konstant Std::\<shared_ptr Stream\>& decryptedstream, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn der entschlüsselte temporäre Stream erfolgreich abgerufen wurde.
public virtual void ongetdecryptedtemporarystreamfailure (konstant Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn der entschlüsselte temporäre Stream abgerufen wurde.
öffentliches virtuelles void-oncommitsuccess (boolcommit, Konst Std::\<shared_ptr\>void & Kontext)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
public virtual void oncommitfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt
public virtual void oninspectsuccess (Konst Std:: shared_ptr\<fileinspector\>& fileinspector, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Wird aufgerufen, wenn Erfolg überprüfen.
public virtual void oninspectfailure (Konstante Std:: exception_ptr & Error, Konstanten Std:: shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn bei der Überprüfung
  
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