---
title: 'MIP:: authdelegat:: OAuth2Token-Klasse'
description: 'Dokumentiert die MIP:: authdelegatklasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 6053a282d162dc2b0f316b265fe6878a4c535a7f
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77490437"
---
# <a name="class-mipauthdelegateoauth2token"></a>MIP:: authdelegat:: OAuth2Token-Klasse 
Eine Klasse, die von einer Anwendung bereitgestellte zugriffstokeninformationen enthält.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches OAuth2Token ()  |  Erstellen Sie ein neues OAuth2Token-Objekt.
Public OAuth2Token (Konstante Std:: String & accesstoken)  |  Erstellen Sie ein neues OAuth2Token-Objekt aus dem JWT-Zugriffs Token.
Public Konstanten Std:: String & getaccesstoken () konstant  |  Abrufen der zugriffstokenzeichenfolge.
öffentliches void setaccesstoken (Konstante Std:: String & accesstoken)  |  Legen Sie die Zugriffs Token-Zeichenfolge fest.
Public Konstante Std:: String & getErrorMessage () konstant  |  Erhalten Sie ggf. die Fehlermeldung.
öffentliches void seterrormessage (Konstante Std:: String & ErrorMessage)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Member
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellen Sie ein neues OAuth2Token-Objekt.
  
### <a name="oauth2token-function"></a>OAuth2Token-Funktion
Erstellen Sie ein neues OAuth2Token-Objekt aus dem JWT-Zugriffs Token.

Parameter:  
* **accesstoken**: JWT-Zugriffs Token.


  
### <a name="getaccesstoken-function"></a>Getaccesstoken-Funktion
Abrufen der zugriffstokenzeichenfolge.

  
**Returns**: zugriffstokenzeichenfolge.
  
### <a name="setaccesstoken-function"></a>Setaccesstoken-Funktion
Legen Sie die Zugriffs Token-Zeichenfolge fest.

Parameter:  
* **Access**Token: zugriffstokenzeichenfolge.


  
### <a name="geterrormessage-function"></a>GetErrorMessage-Funktion
Erhalten Sie ggf. die Fehlermeldung.

  
**Gibt Folgendes zurück**: Fehlermeldung.
  
### <a name="seterrormessage-function"></a>Die Funktion "-terrormessage"
Legt die Fehlermeldung fest

Parameter:  
* **ErrorMessage**: Fehlermeldung.

