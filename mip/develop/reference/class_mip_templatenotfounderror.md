---
title: 'MIP:: templatenumerotfounderror-Klasse'
description: 'Dokumentiert die MIP:: templatenumerotfounderror-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: babcf77de224a75b2beec7e0b15c867698b49c15
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489315"
---
# <a name="class-miptemplatenotfounderror"></a>MIP:: templatenumerotfounderror-Klasse 
Die Vorlagen-ID wird vom RMS-Dienst nicht erkannt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String mmess Age  | _Noch nicht dokumentiert._
Public Std:: Map\<Std:: String, Std:: String\> mdebuginfo  | _Noch nicht dokumentiert._
public char const* what() const  |  Ruft die Fehlermeldung ab
Public Std:: shared_ptr\<Fehler\> Clone ()-Konstante  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
Public Konstanten Std:: String & geterrorname () Konstanten  |  Ruft den Fehlernamen ab
Public Konstanten Std:: String & getMessage () Konstanten  |  Ruft die Fehlermeldung ab
öffentliches void SetMessage (Konstante Std:: String & msg)  |  Legt die Fehlermeldung fest
öffentliches void adddebuginfo (Konstanten Std:: String & Key, Konstanten Std:: String & Wert)  |  Debuganformationen hinzufügen.
Public Konstanten Std:: Map\<Std:: String, Std:: String\>& GetDebugInfo () Konstanten  |  Debuginformationen erhalten.
  
## <a name="members"></a>Member
  
### <a name="mmessage"></a>mmess Age
_Noch nicht dokumentiert._

  
### <a name="mdebuginfo"></a>mdebuginfo
_Noch nicht dokumentiert._

  
### <a name="what-function"></a>What-Funktion
Ruft die Fehlermeldung ab

  
**Rückgabe**: Fehlermeldung.
  
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

  
**Rückgabe**: Fehlermeldung.
  
### <a name="setmessage-function"></a>SetMessage-Funktion
Legt die Fehlermeldung fest

Parameter:  
* **msg**: Fehlermeldung.


  
### <a name="adddebuginfo-function"></a>Adddebuginfo-Funktion
Debuganformationen hinzufügen.

Parameter:  
* **Key**: info-Schlüssel Debuggen 


* **Wert**: debuginfowert


  
### <a name="getdebuginfo-function"></a>GetDebugInfo-Funktion
Debuginformationen erhalten.

  
**Gibt Folgendes zurück**: Debuginformationen (Schlüssel/Werte)