---
title: mip::UserRoles-Klasse
description: 'Dokumentiert die MIP:: userrollen-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: e77ed6ae4d4b5467964f855a081cc22780d9869c
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73560460"
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