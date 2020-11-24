---
title: 'Class authdelegat:: OAuth2Challenge'
description: 'Dokumentiert die authdelegat:: oauth2challenge-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: f422b99674213904316eab622bfc915f128228ec
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567271"
---
# <a name="class-authdelegateoauth2challenge"></a>Class authdelegat:: OAuth2Challenge 
eine Klasse, die alle Informationen enthält, die von der aufrufenden Anwendung benötigt werden, um ein oauth2-Token zu generieren.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public OAuth2Challenge (Konstante Std:: String& Authority, Konstanten Std:: String& Resource, Konstanten Std:: String& Scope, Konstante Std:: String& Claims)  |  Erstellen Sie ein neues OAuth2Challenge-Objekt.
Public Konstanten Std:: String& getauthority () Konstanten  |  Die Autoritäts Zeichenfolge erhalten.
Public Konstanten Std:: String& getResource () Konstanten  |  Die Ressourcen Zeichenfolge erhalten.
Public Konstanten Std:: String& GetScope () Konstanten  |  Die Bereichs Zeichenfolge erhalten.
Public Konstanten Std:: String& getclaims () Konstanten  |  Die Anspruchs Zeichenfolge erhalten.
  
## <a name="members"></a>Members
  
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