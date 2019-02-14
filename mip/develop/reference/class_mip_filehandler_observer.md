---
title: mip::FileHandler::Observer-Klasse
description: 'Beschreibt die Klasse:: fileHandler-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: f6362eab61228cdb161f514c643563f9c45a0857
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254746"
---
# <a name="class-mipfilehandlerobserver"></a>mip::FileHandler::Observer-Klasse 
[Observer](class_mip_filehandler_observer.md)-Schnittstelle für Clients zum Abrufen von Benachrichtigungen für verknüpfte Ereignisse, die im Zusammenhang mit dem Dateihandler stehen.
Alle Fehler erben von [mip::Error](class_mip_error.md). Der Client sollte die Engine nicht in dem Thread aufrufen, der den Beobachter aufruft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual void OnCreateFileHandlerSuccess(const std::shared_ptr\<FileHandler\>& fileHandler, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
public virtual void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
öffentliche virtuelle "void" OnClassifySuccess (const Std:: vector\<Std:: shared_ptr\<Aktion\>\>& Aktionen, const Std:: shared_ptr\<"void"\>& Kontext)  |  Wird aufgerufen, wenn erfolgreich zu klassifizieren.
public virtual void OnClassifyFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn klassifizieren ist fehlgeschlagen.
public virtual void OnGetDecryptedTemporaryFileSuccess(const std::string& decryptedFilePath, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn es sich bei den Erfolg der entschlüsselte temporäre Datei abrufen.
public virtual void OnGetDecryptedTemporaryFileFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die entschlüsselte temporäre Datei konnte nicht abgerufen.
public virtual void OnCommitSuccess(bool committed, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
public virtual void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt
  
## <a name="members"></a>Member
  
### <a name="oncreatefilehandlersuccess-function"></a>OnCreateFileHandlerSuccess-Funktion
Wird aufgerufen, wenn der Handler erfolgreich erstellt wurde.
  
### <a name="oncreatefilehandlerfailure-function"></a>OnCreateFileHandlerFailure-Funktion
Wird aufgerufen, wenn der Handler einen Fehler ausgelöst hat
  
### <a name="onclassifysuccess-function"></a>OnClassifySuccess-Funktion
Wird aufgerufen, wenn erfolgreich zu klassifizieren.
  
### <a name="onclassifyfailure-function"></a>OnClassifyFailure-Funktion
Wird aufgerufen, wenn klassifizieren ist fehlgeschlagen.
  
### <a name="ongetdecryptedtemporaryfilesuccess-function"></a>OnGetDecryptedTemporaryFileSuccess-Funktion
Wird aufgerufen, wenn es sich bei den Erfolg der entschlüsselte temporäre Datei abrufen.
  
### <a name="ongetdecryptedtemporaryfilefailure-function"></a>OnGetDecryptedTemporaryFileFailure-Funktion
Wird aufgerufen, wenn die entschlüsselte temporäre Datei konnte nicht abgerufen.
  
### <a name="oncommitsuccess-function"></a>OnCommitSuccess-Funktion
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen erfolgreich ist und diese erfolgreich in der Datei übernommen werden
  
### <a name="oncommitfailure-function"></a>OnCommitFailure-Funktion
Wird aufgerufen, wenn die Ausführung des Commits für die Änderungen fehlschlägt
