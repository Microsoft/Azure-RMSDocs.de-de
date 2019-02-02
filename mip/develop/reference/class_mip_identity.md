---
title: 'MIP:: Identity Klasse'
description: 'Dokumentiert die MIP:: Identity-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 8c2946e312caeb6d87d66004fa306ca1c68e7f92
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651876"
---
# <a name="class-mipidentity"></a>MIP:: Identity Klasse 
Abstraktion für die Identität.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Öffentliche Identity()  |  Standard [Identität](class_mip_identity.md) Konstruktor verwendet, wenn eine e-Mail-Adresse des Benutzers nicht bekannt ist.
Öffentliche explizite Identität (const Std:: String & e-Mail-Adresse)  |  [Identität](class_mip_identity.md) Konstruktor verwendet, wenn eine e-Mail-Adresse des Benutzers bekannt ist.
public const std::string& GetEmail() const  |  Rufen Sie die e-Mail-Adresse ein.
public void SetDelegatedEmail(const std::string& delegatedEmail)  |  Legt delegierte e-Mail, eine delegierte e-Mail-Adresse ist die Namen des Benutzers, der die Opertations ausgeführt werden.
public const std::string& GetDelegatedEmail() const  |  Die delegierte e-Mail-Adresse zu erhalten, die eine delegierte e-Mail-Adresse wird den Namen des Benutzers, der die Opertations ausgeführt werden.
  
## <a name="members"></a>Member
  
### <a name="identity-function"></a>Identity-Funktion
Standard [Identität](class_mip_identity.md) Konstruktor verwendet, wenn eine e-Mail-Adresse des Benutzers nicht bekannt ist.
  
### <a name="identity-function"></a>Identity-Funktion
[Identität](class_mip_identity.md) Konstruktor verwendet, wenn eine e-Mail-Adresse des Benutzers bekannt ist.

Parameter:  
* **e-Mail-Adresse**: Benutzer-e-Mail-Adresse.


  
### <a name="getemail-function"></a>GetEmail-Funktion
Rufen Sie die e-Mail-Adresse ein.

  
**Gibt**: Die e-Mail-Adresse.
  
### <a name="setdelegatedemail-function"></a>SetDelegatedEmail-Funktion
Legt delegierte e-Mail, eine delegierte e-Mail-Adresse ist die Namen des Benutzers, der die Opertations ausgeführt werden.

Parameter:  
* **DelegatedEmail**: die Delegierung e-Mail-Adresse.


  
### <a name="getdelegatedemail-function"></a>GetDelegatedEmail-Funktion
Die delegierte e-Mail-Adresse zu erhalten, die eine delegierte e-Mail-Adresse wird den Namen des Benutzers, der die Opertations ausgeführt werden.

  
**Gibt**: Die delegierte e-Mail-Adresse.