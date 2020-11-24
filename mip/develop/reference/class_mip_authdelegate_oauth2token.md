---
title: 'Class authdelegat:: OAuth2Token'
description: 'Dokumentiert die authdelegat:: oauth2token-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: a8532e1950977e421fa25b426fa4e4061e610d8d
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567262"
---
# <a name="class-authdelegateoauth2token"></a>Class authdelegat:: OAuth2Token 
Eine Klasse, die von einer Anwendung bereitgestellte zugriffstokeninformationen enthält.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliches OAuth2Token ()  |  Erstellen Sie ein neues OAuth2Token-Objekt.
Public OAuth2Token (Konstante Std:: String& accesstoken)  |  Erstellen Sie ein neues OAuth2Token-Objekt aus dem JWT-Zugriffs Token.
Public Konstanten Std:: String& getaccesstoken () konstant  |  Abrufen der zugriffstokenzeichenfolge.
öffentliches void setaccesstoken (Konstante Std:: String& accesstoken)  |  Legen Sie die Zugriffs Token-Zeichenfolge fest.
Public Konstante Std:: String& getErrorMessage () konstant  |  Erhalten Sie ggf. die Fehlermeldung.
öffentliches void seterrormessage (Konstante Std:: String& ErrorMessage)  |  Legt die Fehlermeldung fest
  
## <a name="members"></a>Members
  
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

