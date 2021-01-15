---
title: 'Class authdelegat:: OAuth2Challenge'
description: 'Dokumentiert die authdelegat:: oauth2challenge-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 3062130037142ebe3b5c227da0dd12a8f38065c1
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212075"
---
# <a name="class-authdelegateoauth2challenge"></a>Class authdelegat:: OAuth2Challenge 
eine Klasse, die alle Informationen enthält, die von der aufrufenden Anwendung benötigt werden, um ein oauth2-Token zu generieren.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public OAuth2Challenge (Konstante Std:: String& Authority, Konstanten Std:: String& Resource, Konstanten Std:: String& Scope, Konstante Std:: String& Claims)  |  Erstellen Sie ein neues OAuth2Challenge-Objekt.
Public Konstanten Std:: String& getauthority () Konstanten  |  Die Autoritäts Zeichenfolge erhalten.
Public Konstanten Std:: String& getResource () Konstanten  |  Die Ressourcen Zeichenfolge erhalten.
Public Konstanten Std:: String& GetScope () Konstanten  |  Die Bereichs Zeichenfolge erhalten.
Public Konstanten Std:: String& getclaims () Konstanten  |  Die Anspruchs Zeichenfolge erhalten.
  
## <a name="members"></a>Member
  
### <a name="oauth2challenge-function"></a>OAuth2Challenge-Funktion
Erstellen Sie ein neues OAuth2Challenge-Objekt.

Parameter:  
* **Authority**: die Autorität, für die das Token generiert werden muss. 


* **Ressource**: die Ressource, auf die das Token festgelegt ist. 


* **Bereich**: der Gültigkeitsbereich, auf den das Token festgelegt ist.


  
### <a name="getauthority-function"></a>Getauthority-Funktion
Die Autoritäts Zeichenfolge erhalten.

  
**Gibt zurück**: die Autoritäts Zeichenfolge.
  
### <a name="getresource-function"></a>GetResource-Funktion
Die Ressourcen Zeichenfolge erhalten.

  
**Gibt Folgendes zurück**: die Ressourcen Zeichenfolge.
  
### <a name="getscope-function"></a>GetScope-Funktion
Die Bereichs Zeichenfolge erhalten.

  
**Gibt Folgendes zurück**: die Bereichs Zeichenfolge.
  
### <a name="getclaims-function"></a>Getclaims-Funktion
Die Anspruchs Zeichenfolge erhalten.

  
**Gibt Folgendes zurück**: die Anspruchs Zeichenfolge.