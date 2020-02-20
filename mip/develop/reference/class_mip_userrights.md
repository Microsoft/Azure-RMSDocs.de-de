---
title: mip::UserRights-Klasse
description: 'Dokumentiert die MIP:: Userrights-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: f44ff30c890a5a8ab3dbce2426a6c1898df1f0e5
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489298"
---
# <a name="class-mipuserrights"></a>mip::UserRights-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public User Rights (Konstante Std:: Vector\<Std:: String\>& users, Konst Std:: Vector\<Std:: String\>& Rights)  |  Userrights-Konstruktor.
Public Konstanten Std:: Vector\<Std:: String\>& users () konstant  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
Public Konstanten Std:: Vector\<Std:: String\>& Rights () Konstanten  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userrights-function"></a>Userrights-Funktion
Userrights-Konstruktor.

Parameter:  
* **users**: Gruppe von Benutzern, die alle über die gleichen Berechtigungen verfügen 


* **rights**: Berechtigungen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="users-function"></a>Benutzerfunktion
Ruft Benutzer ab, denen Berechtigungen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Berechtigungen zugeordnet sind
  
### <a name="rights-function"></a>Rights-Funktion
Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Berechtigungen, die einer Gruppe von Benutzern zugeordnet sind