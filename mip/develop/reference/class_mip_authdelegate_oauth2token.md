---
title: 'MIP:: authdelegat:: OAuth2Token-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: b7b9b73d9f1f3952af1d6a9bdea94c75a8032fb7
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885903"
---
# <a name="class-mipauthdelegateoauth2token"></a>MIP:: authdelegat:: OAuth2Token-Klasse 
Eine Klasse, die festlegt, wie das MIP SDK erwartet, dass das oauth2-Token zurück an das SDK zurückgegeben wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches OAuth2Token ()  |  Erstellen Sie ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) -Objekt.
Public OAuth2Token (Konstante Std:: String & accesstoken)  |  Erstellen Sie ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) -Objekt aus einem accesstoken.
Public Konstanten Std:: String & getaccesstoken () konstant  |  Abrufen der zugriffstokenzeichenfolge.
öffentliches void setaccesstoken (Konstante Std:: String & accesstoken)  |  Legen Sie die Zugriffs Token-Zeichenfolge fest.
  
## <a name="members"></a>Member
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellen Sie ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) -Objekt.
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellen Sie ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) -Objekt aus einem accesstoken.

Parameter:  
* **accessToken**: Das tatsächliche Zugriffs Token, das an das SDK übermittelt wird.


  
### <a name="getaccesstoken-function"></a>Getaccesstoken-Funktion
Abrufen der zugriffstokenzeichenfolge.

  
**Gibt Folgendes zurück**: Die Zugriffs Token-Zeichenfolge.
  
### <a name="setaccesstoken-function"></a>Setaccesstoken-Funktion
Legen Sie die Zugriffs Token-Zeichenfolge fest.

Parameter:  
* **Access**Token: die zugriffstokenzeichenfolge.

