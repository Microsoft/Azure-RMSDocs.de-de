---
title: Klassen Benutzer Rollen
description: 'Dokumentiert die userrollen:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: fc6e5f77c68ecde2582cfd622624c0c6b986500b
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566622"
---
# <a name="class-userroles"></a>Klassen Benutzer Rollen 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Benutzer Rollen (konstant Std:: Vector \<std::string\>& users, Konstante Std:: Vector \<std::string\>& Rollen)  |  UserRoles-Konstruktor
Public Konstanten Std:: Vector \<std::string\>& users () konstant  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
Public Konstanten Std:: Vector \<std::string\>& Rollen () konstant  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Members
  
### <a name="userroles-function"></a>Userrollen-Funktion
UserRoles-Konstruktor

Parameter:  
* **Benutzer**: Gruppe von Benutzern, die die gleichen Rollen gemeinsam verwenden 


* **roles**: Rollen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="users-function"></a>Benutzerfunktion
Ruft Benutzer ab, denen Rollen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Rollen zugeordnet sind
  
### <a name="roles-function"></a>Rollen Funktion
Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Rollen, die einer Gruppe von Benutzern zugeordnet sind