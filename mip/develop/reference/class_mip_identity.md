---
title: 'MIP:: Identity Klasse'
description: 'Dokumentiert die MIP:: Identity-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 75d11fae7d79cadc4dd8909be371cbde2e87f289
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60173540"
---
# <a name="class-mipidentity"></a>MIP:: Identity Klasse 
Abstraktion für die Identität.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Öffentliche Identity()  |  Standard [Identität](class_mip_identity.md) Konstruktor verwendet, wenn eine e-Mail-Adresse des Benutzers nicht bekannt ist.
Öffentliche Identität (const Identity & andere)  |  [Identität](class_mip_identity.md) Kopierkonstruktor.
Öffentliche explizite Identität (const Std:: String & e-Mail-Adresse)  |  [Identität](class_mip_identity.md) Konstruktor verwendet, wenn eine e-Mail-Adresse des Benutzers bekannt ist.
public const std::string& GetEmail() const  |  Rufen Sie die e-Mail-Adresse ein.
public void SetDelegatedEmail(const std::string& delegatedEmail)  |  Legt delegierte e-Mail, eine delegierte e-Mail-Adresse ist die Namen des Benutzers, der die Opertations ausgeführt werden.
public const std::string& GetDelegatedEmail() const  |  Die delegierte e-Mail-Adresse zu erhalten, die eine delegierte e-Mail-Adresse wird den Namen des Benutzers, der die Opertations ausgeführt werden.
  
## <a name="members"></a>Member
  
### <a name="identity-function"></a>Identity-Funktion
Standard [Identität](class_mip_identity.md) Konstruktor verwendet, wenn eine e-Mail-Adresse des Benutzers nicht bekannt ist.
  
### <a name="identity-function"></a>Identity-Funktion
[Identität](class_mip_identity.md) Kopierkonstruktor.

Parameter:  
* **[Identität](class_mip_identity.md)**: verwendet, um die Kopie zu erstellen.


  
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