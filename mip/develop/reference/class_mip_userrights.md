---
title: mip::UserRights-Klasse
description: 'Beschreibt die Klasse:: userrights-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 148b1b1a9f70cc87c3297c69e1e9ffa67af34cf4
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573580"
---
# <a name="class-mipuserrights"></a>mip::UserRights-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Öffentliche UserRights (const Std:: vector\<Std:: String\>& Benutzer, const Std:: vector\<Std:: String\>& Rights)  |  [UserRights](class_mip_userrights.md)-Konstruktor
public const std::vector\<std::string\>& Users() const  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
Public const Std:: vector\<Std:: String\>& Rights() const  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userrights-function"></a>UserRights-Funktion
[UserRights](class_mip_userrights.md)-Konstruktor

Parameter:  
* **Benutzer**: Gruppe von Benutzern, die die gleichen Berechtigungen verfügen 


* **Rechte**: Rechte, die von einer Gruppe von Benutzern gemeinsam verwendet werden


  
### <a name="users-function"></a>Benutzer-Funktion
Ruft Benutzer ab, denen Berechtigungen zugeordnet sind

  
**Gibt**: Benutzer, denen Berechtigungen zugeordnet sind
  
### <a name="rights-function"></a>Rechte-Funktion
Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Gibt**: Die Berechtigungen, die einer Gruppe von Benutzern zugeordnet sind