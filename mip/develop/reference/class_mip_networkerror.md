---
title: mip::NetworkError-Klasse
description: 'Beschreibt die Klasse:: NetworkError-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 3a53683e910a380fed1adc0498ccf170be7087b2
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651223"
---
# <a name="class-mipnetworkerror"></a>mip::NetworkError-Klasse 
Ein Netzwerkfehler Durch unerwartetes Verhalten verursacht, das bei Netzwerkaufrufen an Dienstendpunkte auftritt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public char const* what() const  |  Ruft die Fehlermeldung ab
Public Std:: shared_ptr\<Fehler\> Clone() const  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
public virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
public virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
public virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="what-function"></a>Welche Funktion
Ruft die Fehlermeldung ab

  
**Gibt**: Die Fehlermeldung
  
### <a name="clone-function"></a>Clone-Funktion
Klont den Fehler

  
**Gibt**: Ein Klon des Fehlers.
  
### <a name="geterrortype-function"></a>GetErrorType-Funktion
Ruft den Fehlertyp ab

  
**Gibt**: Der Fehlertyp.
  
### <a name="geterrorname-function"></a>GetErrorName-Funktion
Ruft den Fehlernamen ab

  
**Gibt**: Der fehlername
  
### <a name="getmessage-function"></a>GetMessage-Funktion
Ruft die Fehlermeldung ab

  
**Gibt**: Die Fehlermeldung.
  
### <a name="setmessage-function"></a>SetMessage-Funktion
Legt die Fehlermeldung fest

Parameter:  
* **msg**: Fehlermeldung.

