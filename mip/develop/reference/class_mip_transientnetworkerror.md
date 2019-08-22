---
title: class mip::TransientNetworkError
description: 'Dokumentiert die MIP:: transientnetworkerror-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 5787c5742edc2daefee00a3c5a9b2bf826b81529
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69882904"
---
# <a name="class-miptransientnetworkerror"></a>class mip::TransientNetworkError 
Vorübergehender Netzwerkfehler. Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt. Es kann erneut versucht werden, den Vorgang auszuführen, da es sich um einen vorübergehenden Fehler handelt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public char const* what() const  |  Ruft die Fehlermeldung ab
Public Std:: shared_ptr\<Error\> Clone () Konstanten  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
public virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
public virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
public virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="what-function"></a>What-Funktion
Ruft die Fehlermeldung ab

  
**Gibt Folgendes zurück**: Die Fehlermeldung
  
### <a name="clone-function"></a>Clone-Funktion
Klont den Fehler

  
**Gibt Folgendes zurück**: Ein Klon des Fehlers.
  
### <a name="geterrortype-function"></a>Geterrortype-Funktion
Ruft den Fehlertyp ab

  
**Gibt Folgendes zurück**: Der Fehlertyp.
  
### <a name="geterrorname-function"></a>Geterrorname-Funktion
Ruft den Fehlernamen ab

  
**Gibt Folgendes zurück**: Der Fehler Name.
  
### <a name="getmessage-function"></a>GetMessage-Funktion
Ruft die Fehlermeldung ab

  
**Gibt Folgendes zurück**: Die Fehlermeldung.
  
### <a name="setmessage-function"></a>SetMessage-Funktion
Legt die Fehlermeldung fest

Parameter:  
* **msg**: Fehlermeldung.

