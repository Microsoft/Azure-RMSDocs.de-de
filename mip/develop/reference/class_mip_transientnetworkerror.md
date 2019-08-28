---
title: class mip::TransientNetworkError
description: 'Dokumentiert die MIP:: transientnetworkerror-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: c39c1e512a266009c6cf635f66c5d6cc8a931be1
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056811"
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

