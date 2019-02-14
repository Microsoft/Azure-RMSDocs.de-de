---
title: Klasse mip::AuthDelegate::OAuth2Challenge
description: Dokumentiert die mip::authdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 64a485c30dc6fdb8154c85c3afbd548bbc78ce9a
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259407"
---
# <a name="class-mipauthdelegateoauth2challenge"></a>Klasse mip::AuthDelegate::OAuth2Challenge 
eine Klasse, die alle die erforderlichen aus der aufrufenden Anwendung Informationen um ein oauth2-Token zu generieren.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Öffentliche OAuth2Challenge (const Std:: String & Autorität, const Std:: String & Ressource, const Std:: String und Scope)  |  Erstellt ein neues [OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md) Objekt.
Public const Std:: String & GetAuthority() const  |  Rufen Sie die Autorität für die Zeichenfolge ein.
Public const Std:: String & GetResource() const  |  Rufen Sie die Ressourcenzeichenfolge.
Public const Std:: String & GetScope() const  |  Rufen Sie die Bereichszeichenfolge.
  
## <a name="members"></a>Member
  
### <a name="oauth2challenge-function"></a>OAuth2Challenge-Funktion
Erstellt ein neues [OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md) Objekt.

Parameter:  
* **Autorität für die**: die Autorität für die das Token für generiert werden muss. 


* **Ressource**: die Ressource, die das Token auf festgelegt ist. 


* **Bereich**: der Bereich das Token auf festgelegt ist.


  
### <a name="getauthority-function"></a>GetAuthority-Funktion
Rufen Sie die Autorität für die Zeichenfolge ein.

  
**Gibt**: Die Autorität für die Zeichenfolge.
  
### <a name="getresource-function"></a>GetResource-Funktion
Rufen Sie die Ressourcenzeichenfolge.

  
**Gibt**: Die Ressourcenzeichenfolge.
  
### <a name="getscope-function"></a>GetScope-Funktion
Rufen Sie die Bereichszeichenfolge.

  
**Gibt**: Die Scope-Zeichenfolge.
