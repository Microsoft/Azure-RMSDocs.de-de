---
title: Klasse templatenumotfounderror
description: 'Dokumentiert die templatenumotfounderror:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 9c8a1f1d89c581950bc1760a7bcb339e10114c2a
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764230"
---
# <a name="class-templatenotfounderror"></a>Klasse templatenumotfounderror 
Die Vorlagen-ID wird vom RMS-Dienst nicht erkannt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String mmess Age  | _Noch nicht dokumentiert._
Public Std:: map\<Std:: String, Std:: String\> mdebuginfo  | _Noch nicht dokumentiert._
public char const* what() const  |  Ruft die Fehlermeldung ab
Public Std:: shared_ptr\<Error\> Clone () konstant  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
Public Konstanten Std:: String& geterrorname () Konstanten  |  Ruft den Fehlernamen ab
Public Konstanten Std:: String& getMessage () Konstanten  |  Ruft die Fehlermeldung ab
öffentliches void SetMessage (Konstante Std:: String& msg)  |  Legt die Fehlermeldung fest
öffentliches void adddebuginfo (Konstanten Std:: String& Key, Konstanten Std:: String& Wert)  |  Debuganformationen hinzufügen.
Public Konstanten Std:: map\<Std:: String, Std:: String\>& GetDebugInfo () Konstanten  |  Debuginformationen erhalten.
  
## <a name="members"></a>Member
  
### <a name="mmessage"></a>mmess Age
_Noch nicht dokumentiert._

  
### <a name="mdebuginfo"></a>mdebuginfo
_Noch nicht dokumentiert._

  
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