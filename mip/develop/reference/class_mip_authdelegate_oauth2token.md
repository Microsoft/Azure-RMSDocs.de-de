---
title: Klasse mip::AuthDelegate::OAuth2Token
description: Dokumentiert die mip::authdelegate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: a3a634c99f278d1e8eb27d4c37da0cec566c6aa2
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60184806"
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

