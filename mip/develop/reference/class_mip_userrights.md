---
title: mip::UserRights-Klasse
description: 'Dokumentiert die MIP:: Userrights-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 110f8bc12a019788d031c4ea3711bc22b04234ad
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056749"
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