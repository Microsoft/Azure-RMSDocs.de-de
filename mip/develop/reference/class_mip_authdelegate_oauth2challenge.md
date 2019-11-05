---
title: 'MIP:: authdelegat:: OAuth2Challenge-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 8205d207a48d90832b5961b14d37c7a7226293a2
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73559014"
---
# <a name="class-mipauthdelegateoauth2challenge"></a>MIP:: authdelegat:: OAuth2Challenge-Klasse 
eine Klasse, die alle Informationen enthält, die von der aufrufenden Anwendung benötigt werden, um ein oauth2-Token zu generieren.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public OAuth2Challenge (Konstante Std:: String & Authority, Konstanten Std:: String & Resource, Konstanten Std:: String & Scope, Konstante Std:: String & Claims)  |  Erstellen Sie ein neues OAuth2Challenge-Objekt.
Public Konstanten Std:: String & getauthority () Konstanten  |  Die Autoritäts Zeichenfolge erhalten.
Public Konstanten Std:: String & getResource () Konstanten  |  Die Ressourcen Zeichenfolge erhalten.
Public Konstanten Std:: String & GetScope () Konstanten  |  Die Bereichs Zeichenfolge erhalten.
Public Konstanten Std:: String & getclaims () Konstanten  |  Die Anspruchs Zeichenfolge erhalten.
  
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