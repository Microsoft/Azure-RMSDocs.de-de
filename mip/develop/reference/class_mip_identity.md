---
title: klassenidentität
description: 'Dokumentiert die Identity:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: ae89ed32a48deae7132bc65adabf86f7fb63ffe1
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566871"
---
# <a name="class-identity"></a>klassenidentität 
Abstraktion für Identity.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Identität ()  |  Standardmäßiger identitätskonstruktor, der verwendet wird, wenn eine Benutzer-e-Mail-Adresse
öffentliche Identität (Konstante Identität& andere)  |  Der identitätskopierkonstruktor.
öffentliche explizite Identität (konstant Std:: String& e-Mail)  |  Identitätskonstruktor, der verwendet wird, wenn eine e-Mail-Adresse des Benutzers
öffentliche explizite Identität (konstant Std:: String& Email, Konstanten Std:: String& Name)  |  Identitätskonstruktor, der verwendet wird, wenn eine e-Mail-Adresse und ein Benutzername des Benutzers
Public Konstanten Std:: String& GetEmail () konstant  |  Senden Sie die e-Mail.
public const std::string& GetName() const  |  Den anzeigen amen des Benutzers erhalten. wird zum Markieren von Text verwendet.
  
## <a name="members"></a>Members
  
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