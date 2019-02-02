---
title: mip::UserRoles-Klasse
description: 'Beschreibt die Klasse:: UserRoles-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 1a060652ea61ed452867bb67d281c9531f4e1b98
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651512"
---
# <a name="class-mipuserroles"></a>mip::UserRoles-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rollen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Öffentliche UserRoles (const Std:: vector\<Std:: String\>& Benutzer, const Std:: vector\<Std:: String\>& Rollen)  |  [UserRoles](class_mip_userroles.md)-Konstruktor
public const std::vector\<std::string\>& Users() const  |  Ruft Benutzer ab, denen Rollen zugeordnet sind
Public const Std:: vector\<Std:: String\>& Roles() const  |  Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userroles-function"></a>UserRoles-Funktion
[UserRoles](class_mip_userroles.md)-Konstruktor

Parameter:  
* **Benutzer**: Gruppe von Benutzern, die gemeinsam die gleichen Rollen 


* **Rollen**: Rollen, die von einer Gruppe von Benutzern gemeinsam verwendet werden


  
### <a name="users-function"></a>Benutzer-Funktion
Ruft Benutzer ab, denen Rollen zugeordnet sind

  
**Gibt**: Benutzer, denen Rollen zugeordnet sind
  
### <a name="roles-function"></a>Rollen-Funktion
Ruft die Rollen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Gibt**: Eine Gruppe von Benutzern zugeordnete Rollen