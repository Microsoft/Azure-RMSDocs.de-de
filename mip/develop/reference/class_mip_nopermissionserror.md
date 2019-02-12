---
title: Klasse mip::NoPermissionsError
description: Dokumentiert die mip::nopermissionserror-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 28068c80bc7d6e7fea5dc1bbeed3f64001fc47cc
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652063"
---
# <a name="class-mipnopermissionserror"></a>Klasse mip::NoPermissionsError 
Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetReferrer() const  |  Ruft den Kontakt bei fehlenden Berechtigungen für das Dokument ab.
public std::string GetOwner() const  | _Noch nicht dokumentiert._
public char const* what() const  |  Ruft die Fehlermeldung ab
Public Std:: shared_ptr\<Fehler\> Clone() const  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
public virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
public virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
public virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="getreferrer-function"></a>GetReferrer-Funktion
Ruft den Kontakt bei fehlenden Berechtigungen für das Dokument ab.

  
**Gibt**: Der Kontakt bei fehlenden Berechtigungen für das Dokument.
  
### <a name="getowner-function"></a>GetOwner-Funktion
_Noch nicht dokumentiert._

  
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
