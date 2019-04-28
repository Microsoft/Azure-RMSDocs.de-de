---
title: mip::UserRoles-Klasse
description: 'Beschreibt die Klasse:: UserRoles-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 7e9e750f5b327dbad5e9b46fa1eca2a3291abdd3
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60173236"
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