---
title: Userrights-Klasse
description: 'Dokumentiert die Userrights:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 37943d284eaa00524797605158e320c25e52e17b
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567391"
---
# <a name="class-userrights"></a>Userrights-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public User Rights (Konstante Std:: Vector \<std::string\>& users, Konst Std:: Vector \<std::string\>& Rights)  |  UserRights-Konstruktor
Public Konstanten Std:: Vector \<std::string\>& users () konstant  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
Public Konstanten Std:: Vector \<std::string\>& Rights () konstant  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Members
  
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