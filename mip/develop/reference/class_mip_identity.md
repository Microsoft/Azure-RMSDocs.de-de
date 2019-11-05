---
title: 'MIP:: Identity-Klasse'
description: 'Dokumentiert die MIP:: Identity-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 633a0ac8536f7bbd285eee67934f27d65b399bf4
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560161"
---
# <a name="class-mipidentity"></a>MIP:: Identity-Klasse 
Abstraktion für Identity.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Identität ()  |  Standardmäßiger identitätskonstruktor, der verwendet wird, wenn eine Benutzer-e-Mail-Adresse
öffentliche Identität (Konstante Identität & andere)  |  Der identitätskopierkonstruktor.
öffentliche explizite Identität (konstant Std:: String & e-Mail)  |  Identitätskonstruktor, der verwendet wird, wenn eine e-Mail-Adresse des Benutzers
Public Konstanten Std:: String & GetEmail () konstant  |  Senden Sie die e-Mail.
  
## <a name="members"></a>Member
  
### <a name="identity-function"></a>Identity-Funktion
Standardmäßiger identitätskonstruktor, der verwendet wird, wenn eine Benutzer-e-Mail-Adresse
  
### <a name="identity-function"></a>Identity-Funktion
Der identitätskopierkonstruktor.

Parameter:  
* **Identität**: wird zum Erstellen der Kopie verwendet.


  
### <a name="identity-function"></a>Identity-Funktion
Identitätskonstruktor, der verwendet wird, wenn eine e-Mail-Adresse des Benutzers

Parameter:  
* **e-Mail**: e-Mail-Adresse des Benutzers.


  
### <a name="getemail-function"></a>GetEmail-Funktion
Senden Sie die e-Mail.

  
**Gibt Folgendes zurück**: die e-Mail.