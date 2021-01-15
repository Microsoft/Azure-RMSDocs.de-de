---
title: Klasse templatenumotfounderror
description: 'Dokumentiert die templatenumotfounderror:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 48182ae5d821aeed65e8c28b086dce0349b9af03
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212857"
---
# <a name="class-templatenotfounderror"></a>Klasse templatenumotfounderror 
Die Vorlagen-ID wird vom RMS-Dienst nicht erkannt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String mmess Age  | _Noch nicht dokumentiert._
Public Std:: map \<std::string, std::string\> mdebuginfo  | _Noch nicht dokumentiert._
Public Std:: String mname  | _Noch nicht dokumentiert._
Public ErrorCode getErrorCode () konstant  |  Ruft den ErrorCode der ungültigen Eingabe ab.
public char const* what() const  |  Ruft die Fehlermeldung ab
public std::shared_ptr\<Error\> Clone() const  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
Public Konstanten Std:: String& geterrorname () Konstanten  |  Ruft den Fehlernamen ab
Public Konstanten Std:: String& getMessage () Konstanten  |  Ruft die Fehlermeldung ab
öffentliches void SetMessage (Konstante Std:: String& msg)  |  Legt die Fehlermeldung fest
öffentliches void adddebuginfo (Konstanten Std:: String& Key, Konstanten Std:: String& Wert)  |  Debuganformationen hinzufügen.
Public Konstanten Std:: map \<std::string, std::string\>& GetDebugInfo () Konstanten  |  Debuginformationen erhalten.
ErrorCode-Aufzählung  |  ErrorCode des ungültigen Eingabe Fehlers.
  
## <a name="members"></a>Member
  
### <a name="mmessage"></a>mmess Age
_Noch nicht dokumentiert._

  
### <a name="mdebuginfo"></a>mdebuginfo
_Noch nicht dokumentiert._

  
### <a name="mname"></a>mname
_Noch nicht dokumentiert._

  
### <a name="geterrorcode-function"></a>GetErrorCode-Funktion
Ruft den ErrorCode der ungültigen Eingabe ab.

  
**Gibt Folgendes zurück**: errorCode des ungültigen Eingabe Fehlers
  
### <a name="what-function"></a>What-Funktion
Ruft die Fehlermeldung ab

  
**Gibt Folgendes zurück**: die Fehlermeldung
  
### <a name="clone-function"></a>Clone-Funktion
Klont den Fehler

  
**Rückgabe**: Klon des Fehlers.
  
### <a name="geterrortype-function"></a>Geterrortype-Funktion
Ruft den Fehlertyp ab

  
**Rückgabe**: Fehlertyp.
  
### <a name="geterrorname-function"></a>Geterrorname-Funktion
Ruft den Fehlernamen ab

  
**Rückgabe**: Fehlername.
  
### <a name="getmessage-function"></a>GetMessage-Funktion
Ruft die Fehlermeldung ab

  
**Gibt Folgendes zurück**: die Fehlermeldung.
  
### <a name="setmessage-function"></a>SetMessage-Funktion
Legt die Fehlermeldung fest

Parameter:  
* **msg**: die Fehlermeldung.


  
### <a name="adddebuginfo-function"></a>Adddebuginfo-Funktion
Debuganformationen hinzufügen.

Parameter:  
* **Key**: info-Schlüssel Debuggen 


* **Wert**: debuginfowert


  
### <a name="getdebuginfo-function"></a>GetDebugInfo-Funktion
Debuginformationen erhalten.

  
**Gibt Folgendes zurück**: Debuginformationen (Schlüssel/Werte)
  
### <a name="errorcode-enum"></a>ErrorCode-Aufzählung

ErrorCode des ungültigen Eingabe Fehlers.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Allgemein            | Allgemeiner Fehler bei ungültiger Eingabe.
"Fleistoolargeforprotection"            | Die Datei ist zu groß für den Schutz.
