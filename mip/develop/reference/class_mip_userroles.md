---
title: Klassen Benutzer Rollen
description: 'Dokumentiert die userrollen:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: ef881f184fd370665006c8fb4d73138b7c5e2f3c
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98214132"
---
# <a name="class-userroles"></a>Klassen Benutzer Rollen 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Benutzer Rollen (konstant Std:: Vector \<std::string\>& users, Konstante Std:: Vector \<std::string\>& Rollen)  |  UserRoles-Konstruktor
Public Konstanten Std:: Vector \<std::string\>& users () konstant  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
Public Konstanten Std:: Vector \<std::string\>& Rollen () konstant  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
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