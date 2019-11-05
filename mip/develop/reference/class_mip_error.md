---
title: mip::Error-Klasse
description: 'Dokumentiert die MIP:: Error-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: f59a2b394cbf0bfa5deb555e2c4cdd8c427ed7ea
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560299"
---
# <a name="class-miperror"></a>mip::Error-Klasse 
Die Basisklasse für alle Fehler, die über eine ausgelöste Ausnahme oder als Rückgabewert vom MIP SDK gemeldet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public char const* what() const  |  Ruft die Fehlermeldung ab
Public Std:: shared_ptr\<Error\> Clone ()-Konstanten  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
public virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
public virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
public virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="what-function"></a>What-Funktion
Ruft die Fehlermeldung ab

  
**Rückgabe**: Die Fehlermeldung.
  
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

