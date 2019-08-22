---
title: mip::UserRights-Klasse
description: 'Dokumentiert die MIP:: Userrights-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: c26c7d1aa31cf8fb2ea562582a2ebaad8417615d
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884972"
---
# <a name="class-mipuserrights"></a>mip::UserRights-Klasse 
Eine Gruppe von Benutzern und die ihnen zugeordneten Rechte.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public User Rights (Konst Std:: Vector\<Std:: String\>& users, Konstanten Std:: Vector\<Std:: String\>& Rights)  |  [UserRights](class_mip_userrights.md)-Konstruktor
Public Konstanten Std:: Vector\<Std:: String\>& users () Konstanten  |  Ruft Benutzer ab, denen Berechtigungen zugeordnet sind
Public Konstanten Std:: Vector\<Std:: String\>& Rights () Konstanten  |  Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind
  
## <a name="members"></a>Member
  
### <a name="userrights-function"></a>Userrights-Funktion
[UserRights](class_mip_userrights.md)-Konstruktor

Parameter:  
* **Benutzer**: Gruppe von Benutzern, die die gleichen Rechte haben 


* **Rechte**: Rechte, die von einer Benutzergruppe gemeinsam genutzt werden


  
### <a name="users-function"></a>Benutzerfunktion
Ruft Benutzer ab, denen Berechtigungen zugeordnet sind

  
**Gibt Folgendes zurück**: Benutzer, denen Berechtigungen zugeordnet sind
  
### <a name="rights-function"></a>Rights-Funktion
Ruft die Berechtigungen ab, die einer Gruppe von Benutzern zugeordnet sind

  
**Gibt Folgendes zurück**: Die Berechtigungen, die einer Gruppe von Benutzern zugeordnet sind