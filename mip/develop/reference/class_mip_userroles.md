---
title: Microsoft Information Protection-Klasse „UserRoles“
description: Referenz für die Microsoft Information Protection-Klasse „UserRoles“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 1cc1da6f443fa22095f216bb2ec2f0e51e75bf78
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445256"
---
# <a name="class-mipuserroles"></a>mip::UserRoles-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public UserRoles(const std::vector<std::string>& users, const std::vector<std::string>& roles)  |  [UserRoles](class_mip_userroles.md)-Konstruktor
public const std::vector<std::string>& Users() const  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
public const std::vector<std::string>& Roles() const  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userroles"></a>UserRoles
[UserRoles](class_mip_userroles.md)-Konstruktor

Parameter:  
* **users**: Gruppe von Benutzern, in der allen Mitgliedern die gleichen Rollen zugeordnet sind 


* **roles**: Rollen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="users"></a>Users
Ruft Benutzer ab, denen Rollen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Rollen zugeordnet sind
  
### <a name="roles"></a>Rollen
Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Rollen, die einer Gruppe von Benutzern zugeordnet sind