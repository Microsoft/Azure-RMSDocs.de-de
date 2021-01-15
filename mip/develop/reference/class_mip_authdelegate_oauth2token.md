---
title: 'Class authdelegat:: OAuth2Token'
description: 'Dokumentiert die authdelegat:: oauth2token-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 4db3d2fbb2299b30b85516047ec237d2f23d7cd9
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212041"
---
# <a name="class-authdelegateoauth2token"></a>Class authdelegat:: OAuth2Token 
Eine Klasse, die von einer Anwendung bereitgestellte zugriffstokeninformationen enthält.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches OAuth2Token ()  |  Erstellen Sie ein neues OAuth2Token-Objekt.
Public OAuth2Token (Konstante Std:: String& accesstoken)  |  Erstellen Sie ein neues OAuth2Token-Objekt aus dem JWT-Zugriffs Token.
Public Konstanten Std:: String& getaccesstoken () konstant  |  Abrufen der zugriffstokenzeichenfolge.
öffentliches void setaccesstoken (Konstante Std:: String& accesstoken)  |  Legen Sie die Zugriffs Token-Zeichenfolge fest.
Public Konstante Std:: String& getErrorMessage () konstant  |  Erhalten Sie ggf. die Fehlermeldung.
öffentliches void seterrormessage (Konstante Std:: String& ErrorMessage)  |  Legt die Fehlermeldung fest
  
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
* **Access** Token: zugriffstokenzeichenfolge.


  
### <a name="geterrormessage-function"></a>GetErrorMessage-Funktion
Erhalten Sie ggf. die Fehlermeldung.

  
**Gibt Folgendes zurück**: Fehlermeldung.
  
### <a name="seterrormessage-function"></a>Die Funktion "-terrormessage"
Legt die Fehlermeldung fest

Parameter:  
* **ErrorMessage**: Fehlermeldung.

