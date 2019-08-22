---
title: 'MIP:: authdelegat:: OAuth2Challenge-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 836704d51d1afa55bc296681c863ee10a072ea79
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885910"
---
# <a name="class-mipauthdelegateoauth2challenge"></a>MIP:: authdelegat:: OAuth2Challenge-Klasse 
eine Klasse, die alle Informationen enthält, die von der aufrufenden Anwendung benötigt werden, um ein oauth2-Token zu generieren.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public OAuth2Challenge (Konstante Std:: String & Authority, Konstanten Std:: String & Resource, Konstanten Std:: String & Scope, Konstante Std:: String & Claims)  |  Erstellen Sie ein neues [OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md) -Objekt.
Public Konstanten Std:: String & getauthority () Konstanten  |  Die Autoritäts Zeichenfolge erhalten.
Public Konstanten Std:: String & getResource () Konstanten  |  Die Ressourcen Zeichenfolge erhalten.
Public Konstanten Std:: String & GetScope () Konstanten  |  Die Bereichs Zeichenfolge erhalten.
Public Konstanten Std:: String & getclaims () Konstanten  |  Die Anspruchs Zeichenfolge erhalten.
  
## <a name="members"></a>Member
  
### <a name="oauth2challenge-function"></a>OAuth2Challenge-Funktion
Erstellen Sie ein neues [OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md) -Objekt.

Parameter:  
* **Authority**: die Autorität, für die das Token generiert werden muss. 


* **Ressource**: die Ressource, auf die das Token festgelegt ist. 


* **Bereich**: der Gültigkeitsbereich, auf den das Token festgelegt ist.


  
### <a name="getauthority-function"></a>Getauthority-Funktion
Die Autoritäts Zeichenfolge erhalten.

  
**Gibt Folgendes zurück**: Die Autoritäts Zeichenfolge.
  
### <a name="getresource-function"></a>GetResource-Funktion
Die Ressourcen Zeichenfolge erhalten.

  
**Gibt Folgendes zurück**: Die Ressourcen Zeichenfolge.
  
### <a name="getscope-function"></a>GetScope-Funktion
Die Bereichs Zeichenfolge erhalten.

  
**Gibt Folgendes zurück**: Die Bereichs Zeichenfolge.
  
### <a name="getclaims-function"></a>Getclaims-Funktion
Die Anspruchs Zeichenfolge erhalten.

  
**Gibt Folgendes zurück**: Die Anspruchs Zeichenfolge.