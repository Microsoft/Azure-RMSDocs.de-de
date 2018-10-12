---
title: Microsoft Information Protection-Klasse „AccessDeniedError“
description: Referenz für die Microsoft Information Protection-Klasse „AccessDeniedError“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fd2e1990a315324a43fffe5f547c2f72c61e9539
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445817"
---
# <a name="class-mipaccessdeniederror"></a>mip::AccessDeniedError-Klasse 
Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public char const* what() const  |  Ruft die Fehlermeldung ab
public std::shared_ptr<Error> Clone() const  |  Klont den Fehler
 public virtual ErrorType GetErrorType() const  |  Ruft den Fehlertyp ab
 public virtual const std::string& GetErrorName() const  |  Ruft den Fehlernamen ab
 public virtual const std::string& GetMessage() const  |  Ruft die Fehlermeldung ab
 public virtual void SetMessage(const std::string& msg)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="what"></a>what
Ruft die Fehlermeldung ab

  
**Rückgabe**: Fehlermeldung.
  
### <a name="error"></a>Fehler
Klont den Fehler

  
**Rückgabe**: Klon des Fehlers.
  
### <a name="errortype"></a>ErrorType
Ruft den Fehlertyp ab

  
**Rückgabe**: Fehlertyp.
  
### <a name="geterrorname"></a>GetErrorName
Ruft den Fehlernamen ab

  
**Rückgabe**: Fehlername.
  
### <a name="getmessage"></a>GetMessage
Ruft die Fehlermeldung ab

  
**Rückgabe**: Fehlermeldung.
  
### <a name="setmessage"></a>SetMessage
Legt die Fehlermeldung fest

Parameter:  
* **msg**: Fehlermeldung.

