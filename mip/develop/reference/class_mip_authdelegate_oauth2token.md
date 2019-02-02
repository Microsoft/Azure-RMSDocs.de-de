---
title: Klasse mip::AuthDelegate::OAuth2Token
description: Dokumentiert die mip::authdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 7ce9e336edfeeee07725b30c4d76c3b3c2073bc6
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652046"
---
# <a name="class-mipauthdelegateoauth2token"></a>Klasse mip::AuthDelegate::OAuth2Token 
Eine Klasse definiert, wie das MIP SDK für die oauth2-Token wieder in das SDK übergeben werden erwartet.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Öffentliche OAuth2Token()  |  Erstellt ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) Objekt.
Öffentliche OAuth2Token (const Std:: String & AccessToken)  |  Erstellt ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) Objekt aus einem AccessToken.
Public const Std:: String & GetAccessToken() const  |  Die Tokenzeichenfolge für den Zugriff zu erhalten.
Öffentliche void SetAccessToken (const Std:: String & AccessToken)  |  Legen Sie die Access-Token-Zeichenfolge.
  
## <a name="members"></a>Member
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellt ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) Objekt.
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellt ein neues [OAuth2Token](class_mip_authdelegate_oauth2token.md) Objekt aus einem AccessToken.

Parameter:  
* **accessToken**: Das aktuelle Zugriffstoken in das SDK übergeben.


  
### <a name="getaccesstoken-function"></a>GetAccessToken-Funktion
Die Tokenzeichenfolge für den Zugriff zu erhalten.

  
**Gibt**: Die Access-token-Zeichenfolge.
  
### <a name="setaccesstoken-function"></a>SetAccessToken-Funktion
Legen Sie die Access-Token-Zeichenfolge.

Parameter:  
* **AccessToken**: die Access-token-Zeichenfolge.

