---
title: 'MIP:: Identity-Klasse'
description: 'Dokumentiert die MIP:: Identity-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: d50092be5277d5e88e6ec408280ca76bbc333a4c
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77488023"
---
# <a name="class-mipidentity"></a>MIP:: Identity-Klasse 
Abstraktion für Identity.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Identität ()  |  Standardmäßiger identitätskonstruktor, der verwendet wird, wenn eine Benutzer-e-Mail-Adresse
öffentliche Identität (Konstante Identität & andere)  |  Der identitätskopierkonstruktor.
öffentliche explizite Identität (konstant Std:: String & e-Mail)  |  Identitätskonstruktor, der verwendet wird, wenn eine e-Mail-Adresse des Benutzers
öffentliche explizite Identität (konstant Std:: String & Email, Konstanten Std:: String & Name)  |  Identitätskonstruktor, der verwendet wird, wenn eine e-Mail-Adresse und ein Benutzername des Benutzers
Public Konstanten Std:: String & GetEmail () konstant  |  Senden Sie die e-Mail.
public const std::string& GetName() const  |  Den anzeigen amen des Benutzers erhalten. wird zum Markieren von Text verwendet.
  
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
* **e-Mail**: muss eine gültige e-Mail-Adresse sein.


  
### <a name="identity-function"></a>Identity-Funktion
Identitätskonstruktor, der verwendet wird, wenn eine e-Mail-Adresse und ein Benutzername des Benutzers

Parameter:  
* **e-Mail**: muss eine gültige e-Mail-Adresse sein. 


* **Name**: Benutzername.


  
### <a name="getemail-function"></a>GetEmail-Funktion
Senden Sie die e-Mail.

  
**Gibt Folgendes zurück**: die e-Mail.
  
### <a name="getname-function"></a>GetName-Funktion
Den anzeigen amen des Benutzers erhalten. wird zum Markieren von Text verwendet.

  
**Gibt Folgendes zurück**: der Anzeige Name.