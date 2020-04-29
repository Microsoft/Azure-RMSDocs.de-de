---
title: Userrights-Klasse
description: 'Dokumentiert die Userrights:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 1a3bf2c6c8f417d30fac24263f672f2603347960
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764244"
---
# <a name="class-userrights"></a>Userrights-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public User Rights (Konst Std:: Vector\<Std:: String\>& users, Konstanten Std:: Vector\<Std:: String\>& Rights)  |  UserRights-Konstruktor
Public Konstanten Std:: Vector\<Std:: String\>& users () Konstanten  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
Public Konstanten Std:: Vector\<Std:: String\>& Rights () Konstanten  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userrights-function"></a>Userrights-Funktion
UserRights-Konstruktor

Parameter:  
* **users**: Gruppe von Benutzern, die alle über die gleichen Berechtigungen verfügen 


* **rights**: Berechtigungen, die allen Benutzern einer Gruppe zugeordnet sind


  
### <a name="users-function"></a>Benutzerfunktion
Ruft Benutzer ab, denen Berechtigungen zugeordnet sind

  
**Rückgabe**: Benutzer, denen Berechtigungen zugeordnet sind
  
### <a name="rights-function"></a>Rights-Funktion
Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Rückgabe**: Berechtigungen, die einer Gruppe von Benutzern zugeordnet sind