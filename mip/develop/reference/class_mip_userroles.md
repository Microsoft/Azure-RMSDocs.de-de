---
title: mip::UserRoles-Klasse
description: 'Dokumentiert die MIP:: userrollen-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: d22f66c8fff22b54e5e7e30f425adc2c889e5db0
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489281"
---
# <a name="class-mipuserroles"></a>mip::UserRoles-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public User Rollen (Konstante Std:: Vector\<Std:: String\>& users, Konstanten Std:: Vector\<Std:: String\>& Rollen)  |  Userrollen-Konstruktor.
Public Konstanten Std:: Vector\<Std:: String\>& users () konstant  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
Public Konstanten Std:: Vector\<Std:: String\>& Rollen () konstant  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userroles-function"></a>Userrollen-Funktion
Userrollen-Konstruktor.

Parameter:  
* **users**: Gruppe von Benutzern, in der allen Mitgliedern die gleichen Rollen zugeordnet sind 


* **roles**: Rollen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="users-function"></a>Benutzerfunktion
Ruft Benutzer ab, denen Rollen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Rollen zugeordnet sind
  
### <a name="roles-function"></a>Rollen Funktion
Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Rollen, die einer Gruppe von Benutzern zugeordnet sind