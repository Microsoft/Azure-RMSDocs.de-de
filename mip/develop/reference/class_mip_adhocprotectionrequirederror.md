---
title: class mip::AdhocProtectionRequiredError
description: Dokumentiert die mip::adhocprotectionrequirederror-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: a109c9f235e950e428aa000d34af95a337c6eb4d
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60184823"
---
# <a name="class-mipadhocprotectionrequirederror"></a>class mip::AdhocProtectionRequiredError 
Ad-hoc-Schutz muss zum Abschließen der Aktion auf die Datei festgelegt werden.
  
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
