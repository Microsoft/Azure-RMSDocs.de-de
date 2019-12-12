---
title: 'MIP:: authdelegat:: OAuth2Token-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: d8bce56e02778d48e6e3c0cfdb02f1c3f1f4054a
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73560346"
---
# <a name="class-mipauthdelegateoauth2token"></a>MIP:: authdelegat:: OAuth2Token-Klasse 
Eine Klasse, die festlegt, wie das MIP SDK erwartet, dass das oauth2-Token zurück an das SDK zurückgegeben wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches OAuth2Token ()  |  Erstellen Sie ein neues OAuth2Token-Objekt.
Public OAuth2Token (Konstante Std:: String & accesstoken)  |  Erstellen Sie ein neues OAuth2Token-Objekt aus einem accesstoken.
Public Konstanten Std:: String & getaccesstoken () konstant  |  Abrufen der zugriffstokenzeichenfolge.
öffentliches void setaccesstoken (Konstante Std:: String & accesstoken)  |  Legen Sie die Zugriffs Token-Zeichenfolge fest.
  
## <a name="members"></a>Member
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellen Sie ein neues OAuth2Token-Objekt.
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellen Sie ein neues OAuth2Token-Objekt aus einem accesstoken.

Parameter:  
* **accesstoken**: das tatsächliche Zugriffs Token, das an das SDK übermittelt wird.


  
### <a name="getaccesstoken-function"></a>Getaccesstoken-Funktion
Abrufen der zugriffstokenzeichenfolge.

  
**Returns**: die zugriffstokenzeichenfolge.
  
### <a name="setaccesstoken-function"></a>Setaccesstoken-Funktion
Legen Sie die Zugriffs Token-Zeichenfolge fest.

Parameter:  
* **Access**Token: die zugriffstokenzeichenfolge.

