---
title: Klasse mip::ServiceDisabledError
description: Dokumentiert die mip::servicedisablederror-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 2d64d576ead748adff7804e9068aab71fd9672c0
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333023"
---
# <a name="class-mipservicedisablederror"></a>Klasse mip::ServiceDisabledError 
Der Benutzer konnte Zugriff auf den Inhalt, da ein Dienst, der deaktiviert werden nicht abgerufen werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Extent GetExtent() const  |  Ruft den Umfang für den der Dienst deaktiviert ist.
public char const* what() const  |  Ruft die Fehlermeldung ab
Public Std:: shared_ptr\<Fehler\> Clone() const  |  Klont den Fehler
public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
public virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
public virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
public virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
Extent-Enumeration  |  Beschreibt das Ausmaß, die für das der Dienst deaktiviert ist.
  
## <a name="members"></a>Member
  
### <a name="getextent-function"></a>GetExtent-Funktion
Ruft den Umfang für den der Dienst deaktiviert ist.

  
**Gibt**: Umfang, die für die der Dienst deaktiviert ist
  
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


  
### <a name="extent-enum"></a>Extent-Enumeration
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Benutzer            | Dienst ist für den Benutzer deaktiviert.
Gerät            | Dienst ist für das Gerät deaktiviert.
Platform            | Für die Plattform ist der Dienst deaktiviert.
Mandant            | Dienst ist für den Mandanten deaktiviert.
Beschreibt das Ausmaß, die für das der Dienst deaktiviert ist.
