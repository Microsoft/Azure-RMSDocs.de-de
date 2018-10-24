---
title: Die Klasse „mip::FileHandler::Observer“
description: Referenz zur Klasse „mip::FileHandler::Observer“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a587107afc2b8963d64c31ad47af81761bf2b9f8
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446171"
---
# <a name="class-mipfilehandlerobserver"></a>mip::FileHandler::Observer-Klasse 
[Observer](class_mip_filehandler_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse im Zusammenhang mit dem Dateihandler.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnCreateFileHandlerSuccess(const std::shared_ptr<FileHandler>& fileHandler, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
public virtual void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
public virtual void OnGetLabelSuccess(const std::shared_ptr<ContentLabel>& label, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Bezeichnung erfolgreich abgerufen wird
public virtual void OnGetLabelFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Abrufen der Bezeichnung ein Fehler aufgetreten ist
public virtual void OnGetProtectionSuccess(const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Schutzrichtlinie erfolgreich abgerufen wird
public virtual void OnGetProtectionFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn beim Abrufen der Schutzrichtlinie ein Fehler aufgetreten ist
public virtual void OnCommitSuccess(bool committed, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
public virtual void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt
  
## <a name="members"></a>Member
  
### <a name="oncreatefilehandlersuccess"></a>OnCreateFileHandlerSuccess
Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
  
### <a name="oncreatefilehandlerfailure"></a>OnCreateFileHandlerFailure
Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Wird aufgerufen, wenn die Bezeichnung erfolgreich abgerufen wird
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Wird aufgerufen, wenn beim Abrufen der Bezeichnung ein Fehler aufgetreten ist
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Wird aufgerufen, wenn die Schutzrichtlinie erfolgreich abgerufen wird
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Wird aufgerufen, wenn beim Abrufen der Schutzrichtlinie ein Fehler aufgetreten ist
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
  
### <a name="oncommitfailure"></a>OnCommitFailure
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt